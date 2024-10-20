manages all the resources
memory
files
UI
sound
graphics

communicates with device drivers that directly send commands or receive inputs from the hardware

**Path to the Kernel**
Subsystem DLL API call

Subsystem API calls ntdll API

NTDLL calls ZW API

All ZW APIs execute syscall

Now moved to Kernel mode and redirected to SSD KiSystemService

KiSystemService searches for the function that represents the command ID that was in eax in the System Service Dispatch Table (SSDT).

NT API sends an IRP fastfat.sys or ntfs.sys

passes through multiple device drivers attached to the filesystem
driver

device drivers are able to modify the inputs in any request and the
outputs (or responses) from the filesystem

The IRP request makes its
way back to Nt API and KiSystemService with an
instruction called sysexit. Then, it returns to the user-mode process with the results