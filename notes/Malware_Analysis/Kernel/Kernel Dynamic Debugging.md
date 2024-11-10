
In most cases, we don't have
symbol information for the analyzed sample, so we can't use common WinDbg commands such as bp <driver_name>!DriverEntry

By setting unresolved breakpoints: The following command can be used to set a breakpoint that will trigger once the module is loaded

bu <driver_name>!<any_string>

**By breaking on the module load:** The following command allows you to intercept all new modules being loaded

sxe ld:<driver_name>.sys

![[Pasted image 20240828223302.png]]
Once the debugger breaks, it is possible to set a breakpoint on the driver's entry

**By intercepting the API responsible for loading drivers**
drivers: This technique allows
us to stop exactly at the driver's entry point with a single command. The idea here is to find an offset of the place where the IopLoadDriver API transferscontrol to the driver

.shell -ci "uf /c nt!IopLoadDriver" grep -B 1 -i "call.*ptr
\[.*h"

Once the offset is found (it will look like nt!IopLoadDriver+N), it is possible to set a breakpoint at this address and intercept all moments when the system transfers control to the newly loaded drivers.

**By patching the sample:** Here, we can patch the driver's entry point with an 0xCC (the int 3 instruction representing a software breakpoint), recalculatethe checksum field in its header (in Hiew editor, this can be done by selecting this field in the header, pressing F3 once to recalculate it, and then F9 to save the
changes), and load it. The debugger will break at this instruction

**Loading the driver**
You aren't allowed to load unsigned drivers on modern 64-bit Windows systems, or 32-bit
systems with Secure Boot turned on. If the sample driver is not signed, it generally makes
sense to figure out the way it is being executed in the wild

Disable system security mechanisms
advanced options for the booting process and
selecting the Disable driver signature enforcement option

Another approach that involves
using the bcdedit.exe /set testsigning on command is not recommended for analysis as it still requires the driver to be correctly signed by some certificate.

Load the driver
sc create <any_name> type= kernel binpath= "<path_to_driver>"
sc start <same_name>