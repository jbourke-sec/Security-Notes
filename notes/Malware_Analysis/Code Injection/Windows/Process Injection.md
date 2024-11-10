 Search for the targeted process using *CreateToolhelp32Snapshot* then
- Process32First, andProcess32Next
- Get the process handle using the OpenProcess API
- Allocate memory inside this process using VirtualAllocEx (or
- CreateSectionEx, which can be used in pretty much the same way) with the size of the whole piece of the assembly code to be injected.
- Copy that code into the targeted process using WriteProcessMemory,
- Execute this code using the CreateRemoteThread API.