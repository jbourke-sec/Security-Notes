For running 32 bit processes in a 64 bit environment

Windows has a WOW emulator comprising of 

wow64.dll
wow64cpu.dll
wow64win.dll

includes a 32-bit ntdll.dll and a 32-bit kernel32.dll

rather than connecting directly to the Windows kernel, call an API
X86SwitchTo64BitMode, which then switches to x64 and calls the 64-bit ntdll.dll

![[Pasted image 20240817174423.png]]

In analyzing 32-bit malware on a 64-bit system, if you find that it writes a file to C:\\Windows\\System32, you will need to go to C:\Windows\\WOW64 to find that file.

Another redirection exists for 32-bit applications that access the HKEY_
LOCAL_MACHINE\Software registry key, which is mapped to HKEY_LOCAL_MACHINE\
Software\Wow6432Node. Any 32-bit applications accessing the software registry key will be redirected

IsWow64Process function, which can be used by 32-bit applications to determine if they are running in a WOW64 process. Applications can access the real \System32 directory by accessing C:\\Windows\\Sysnative, even when the \\System32 is being redirected to WOW64.