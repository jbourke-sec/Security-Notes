Services are controlled by the Service Control Manager (SCM) implemented in %SystemRoot%\System32\services.exe.

have the corresponding
HKLM\SYSTEM\CurrentControlSet\services\<service_name> registry key

Key contains

ImagePath
Type: Type of service
0x00000001 (kernel)
0x00000010 (own):
0x00000020 (shared):
Start:
0x00000000 (boot) - boatloader
0x00000001 (system) - Kernel initialization
0x00000002 (auto) - automatic when machine restarts
0x00000003 (demand): - Has to be started manually

Common designs
Service implemented from a dedicated executable
**As a DLL (own loader**):The full command line is stored in the ImagePath key

**As a DLL (svchost):**
DLL loaded into the address space of one of the svchost.exe
malware generally creates a new group in the
HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Svchost
registry key and later passes this value to the svchost.exe using the -k
argument
Path is specified in HKLM\SYSTEM\CurrentControlSet\services\<service_name>\Parameter

A user-mode service with a dedicated executable (or a DLL with its own loader) can be
registered using the standard sc command line tool

Attaching to the service
Creating a dedicated registry key: It is possible to create a key such as
HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File
Execution Options\<filename> with the corresponding string data value
Debugger containing the full path to the debugger to be attached to the service
once the program with the specified <filename> starts. Here, there is a nuance
that the window of the attached debugger may not appear if the service is not
interactive. It can be fixed using one of the following ways:
Open services.msc, then open Properties for the debugged
service, then go to the Log On tab and set a tick against the Allow
service to interact with desktop option.
It can also be done manually by opening the Type value of the
HKLM\SYSTEM\\CurrentControlSet\\services\\\<service_name\> registry key and replacing its data with the result of a bitwise OR
operation with the current value and 0x00000100 DWORD
(SERVICE_INTERACTIVE_PROCESS flag). For example,
0x00000010 will become 0x00000110.
In addition, it can be originally created as interactive when using the sc tool with
the type= interact type= own or type= interact type= share
arguments. Another option here is to use remote debugging.