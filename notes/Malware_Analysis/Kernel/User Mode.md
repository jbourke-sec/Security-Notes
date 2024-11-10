contains all the processes running in the system

processes are running under subsystems such as POSIX, the Win32 subsystem, and (more recently) the Windows subsystem for
Linux

these subsystems call different APIs

All of these Dynamic-Link Libraries (DLLs) call APIs in one DLL (ntdll.dll), which communicates directly to the kernel mode

sends requests to the kernel using special instructions, such
as sysenter or syscall

Sends request ID in EAX

