**CPUID hypervisor bit:** The CPUID instruction returns information about the
CPU and provides a leaf/ID of this information in eax.

This is changed from 31 to 1 for VMs/hypervisors

**Virtualization brand**: ==CPUID instruction==, for some virtualization tools,
given eax = 0x40000000, it could return the name of the virtualization tool in EBX,ECX,EDX

**MMX registers:** ==Some VMs do not support them==

**Process Enumeration:** the CreateToolhelp32Snapshot, Process32First, and Process32Next APIs

**Registry Keys:** 
HKLM\SOFTWARE\Vmware Inc.\Vmware Tools
SYSTEM\CurrentControlSet\Control\VirtualDeviceDrivers
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Class\{4D36E968
-E325-11CE-BFC1-08002BE10318}\0000\ProviderName
HKEY_LOCAL_MACHINE\HARDWARE\ACPI\DSDT\VBOX__
HKEY_LOCAL_MACHINE\SOFTWARE\Oracle\VirtualBox Guest Additions

**WMI**
This information can also be accessed through a WMI query, such as the following:
SELECT * FROM Win32_ComputerSystem WHERE Manufacturer LIKE "%VMware%" AND Model LIKE "%VMware Virtual Platform%"

**Detecting sandboxes by using default settings**
Lots of default settings to check

**Delayed/skipped execution to  avoid sandboxes**
Some malware families use APIs such as ==Sleep== to skip the execution for quite some time or run it
after a machine restart

**Other Techniques**
Connecting to VirtualBox inter-process communication:
\\.\pipe\VBoxTrayIPC
Detecting other virtualization software files, such as VBoxHook.dll
Detecting their window title or window class name, such
as VBoxTrayToolWndClass or VBoxTrayToolWnd
The MAC address of their network adapter

**Vulnerable instructions**
 the sidt instruction which stores the contents of IDTR into a memory location. The virtual machine monitor must relocate the
guest’s IDTR to avoid conflict with the host’s IDTR. Since the virtual machine monitor is not notified when the virtual machine runs the sidt instruction, the IDTR for the virtual machine is returned. The Red Pill tests for this discrepancy to detect the usage of VMware.

The sgdt and sldt instruction technique for VMware detection is commonly known as No Pill. Unlike Red Pill, No Pill relies on the fact that the LDT structure is assigned to a processor, not an operating system. And because Windows does not normally use the LDT structure, but VMware provides virtual
support for it, the table will differ predictably:

**Escaping the Virtual Machine**
VMware has its vulnerabilities, which can be exploited to crash the host operating
system or even run code in it

**Mitigations** 
Patch assembly, either modify flags, bytes or strings e.g - vmware-Xxx


