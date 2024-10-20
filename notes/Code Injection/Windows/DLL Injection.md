**DLL Injection**
inject the path of the malicious DLL into the process using the VirtualAllocEx API and WriteProcessMemory. Then, it creates a thread into that process using CreateRemoteThread, with the address of the LoadLibrary API as the thread start
address.

this technique won't work for fileless malware since the malware DLL file must be present on a hard disk
before it can be loaded using LoadLibraryA.