common structure of its instructions is opcode, dest, src.

**opcode**
opcode is the name of the instruction. Some instructions have only opcode without any
dest or src such as the following:
Nop, pushad, popad, movsb

**dest**
dest represents the destination or where the result of the calculations will be saved

Also, it could play a role of a source and a destination with some opcode instructions that take only dest without a source:
inc eax
dec ecx

Or, it could be only the source or the destination, such as in case of these instructions that
save the value on the stack and then out it back:
push rdx
pop rcx

dest could look like the following:
**REG:** A register such as eax and edx.
**r/m:** A place in memory such as the following:
DWORD PTR \[00401000h\]
BYTE PTR \[EAX + 00401000h\]
WORD PTR \[EDX*4 + EAX+ 30\]
A value in the stack (used to represent local variables), such as the following:
DWORD PTR \[ESP+4\]
DWORD PTR \[EBP-8\]

**src**
src represents the source or another value in the calculations, but it doesn't save the results
afterward. It may look like this:
REG: For instance, add rcx, r8
r/m: For instance, add ecx, dword ptr \[00401000h\]
imm: An immediate value such as mov eax, 00100000h