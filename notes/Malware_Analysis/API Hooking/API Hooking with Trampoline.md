**Hooking with Trampoline**
Modifies the return arguments of an API by ==adding a JMP to a hooking function==
![[Pasted image 20240820220535.png]]
change API parameters
push API_argument03
push API_argument02
push API_argument01
call trampoline ;jmp to the API and return with the API return value
.change API return value
ret ;return back to the main program

==Gives malware more control over the API== and its output, which makes it possible, for example, to inject JavaScript code into the output of InternetReadFile