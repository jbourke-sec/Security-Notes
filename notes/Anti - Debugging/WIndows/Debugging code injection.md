**Debug where it is**
1. BP on ==VirtualAllocEx== and save returned address
2. BP on ==WriteProcessMemory== and save the source and destination address
3. Destination will probably be VirtualAllocs return address
4. BP on ==CreateRemoteThread== and get the entry point or any other arguments
5. From the entry point on CreateRemoteThread,  subtract the return address and add the source address on ==WriteProcessMemory==
6. Take a VM snapshot
7. Only works on simple injection

**Attach to the process**

==BP on CreateRemoteThread==
CreateRemoteThread(Process, NULL, NULL,
(LPTHREAD_START_ROUTINE)LoadLibrary, (LPVOID)Memory, CREATE_SUSPENDED,
NULL);
Search for the targeted process using *CreateToolhelp32Snapshot* then
- Process32First, andProcess32Next
- Get the process handle using the OpenProcess API