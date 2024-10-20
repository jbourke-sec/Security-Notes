device drivers that hook different functions in kernel mode to hide the malware's presence and give the malware the power of kernel
mode
**SYSENTER Hooking**: they change the address that sysenter will transfer
the execution to

**SSDT hooking**: modifies the SSDT to redirect requests to a malicious function
Layered drivers/IRP hooking: