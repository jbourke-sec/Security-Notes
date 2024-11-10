
**stdcall**

Save return address to the top of the stack

Arguments are pushed LIFO

Local variables are allocated by decreasing ESP

push ebp
mov ebp,esp
sub esp, 8

the ==ret instruction cleans the stack== given the number of bytes

**cdecl**
Only difference is the only difference being that ==the
caller cleans the stack== after the callee function

Caller:
push Arg02
push Arg01
call Callee
add esp, 8 ;cleans the stack

**fastcall**
Microsoft C++ compiler and GCC. This calling convention passes the ==first two arguments in
ecx and edx==, and ==pushes the remaining arguments to the stack==