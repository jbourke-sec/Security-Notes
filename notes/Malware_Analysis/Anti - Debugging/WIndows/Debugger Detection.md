**Direct checks**
==IsDebuggerPresent==
==CheckRemoteDebuggerPresent==
==NtQueryInformationProcess== (with the ==ProcessDebugPort (7)== argument)
==BeingDebugged== flag in the ==PEB==
==OutputDebugString== - Works if being debugged, fails otherwise

mov eax, dword ptr fs:\[30h\] ; PEB
cmp byte ptr \[eax+2\], 1 ; PEB.BeingDebugged
jz <debugger_detected>

**Mitigation while debugging:** NOP patching, modifying API return values

**NTGlobal flag**: offset ==0x68== of the PEB in 32-bit systems and ==0xBC== in 64-bit systems. 

==Null when not being debugged==

==Set with 3 values when being debugged==
FLG_HEAP_ENABLE_TAIL_CHECK (0x10)
FLG_HEAP_ENABLE_FREE_CHECK (0x20)
FLG_HEAP_VALIDATE_PARAMETERS (0x40)

Assembly
mov eax, fs:\[30h\] ;Process Environment Block
mov al, \[eax+68h\] ;NtGlobalFlag
and al, 70h ;Other flags can also be checked this way
cmp al, 70h ;0x10 | 0x20 | 0x40
je <debugger_detected>
The following flags can be used in the x64 environment:
push 60h
pop rsi
gs:lodsq ;Process Environment Block
mov al, \[rsi*2+rax-14h\] ;NtGlobalFlag
and al, 70h
cmp al, 70h
je <debugger_detected>

**Detecting a debugger using parent processes**
CreateToolhelp32Snapshot,
and Process32First, Process32Next

NtQueryInformationProcess API.
Given ProcessBasicInformation as an argument

Now they have to get the parent name from the ID

Use same tactics as others given the Parent ID

the GetProcessImageFileNameA API to get the filename of a process
given its handle. To do this, they need to execute the OpenProcess API in order to get permission to access this process to query for information (by using PROCESS_QUERY_INFORMATION
This will return the executable name

**Scan for INT3 breakpoints**
Scans code in memory like below
![[Pasted image 20240820223936.png]]

only drawback of this approach is that some ==C++ compilers write INT3 instructions==

Other techniques include ==calculating two checksums==, with one being the code section in memory being executed

mov esi,CodeStart
mov ecx,CodeSize
xor eax,eax
ChecksumLoop:
movzx edx,byte [esi]
add eax,edx
rol eax,1
inc esi
loop .checksum_loop
cmp eax, Correct_Checksum
jne breakpoint_detected

**INT 2D scanning**
The INT 2D anti-debugging technique functions like INT 3—the INT 0x2D instruction is used to access the kernel debugger. Because INT 0x2D is the way that kernel debuggers set breakpoints,

**Trap flag**
Not normally accessible in the EFLAGS register except through the special instruction ==pushf== but is ==always set to false after returning to debugger==
Popping ==SS(Stack register)== ==allows the Trap flag to remain set== and for malware to check it for debugger presence
![[Pasted image 20240820225309.png]]


**Detecting through timing techniques**
GetLocalTime
GetSystemTime
GetTickCount
KiGetTickCount (in kernel mode)
QueryPerformanceCounter
timeGetTime
timeGetSystemTime
rdtsc assemby instruction - 64-bit value placed into EDX:EAX.

**Searching for the tool window**
Using ==FindWindow==: Malware can use either the full window title,
Using ==EnumWindows==: Another way to avoid searching for the window class name
With the EnumWindows API, ==you need to set a callback== to receive all windows.
this callback will receive the handle of this window, from which it can get its name using the GetWindowText API.

**Prevention**: There are plugins for popular tools, such as OllyDbg and IDA, that can help rename their title window to avoid detection

**Checking for System Residue**
Debuggers leave traces on systems they exist on

Common debugger registry key
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug

**Causing a debugger crash**
Process that work fine normally but crash when run with a debugger


