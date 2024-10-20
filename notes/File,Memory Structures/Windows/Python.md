.pyc: These are standard compiled bytecode files
.pyo: These are compiled bytecode files that are built with the -O (or -OO) option
.pyd: These are traditional Windows DLL files that implement the MZ-PE
structure

**.pyc structure**
![[Pasted image 20240902230213.png]]
![[Pasted image 20240902230243.png]]

**Bytecode**
all bytecode instructions
for a particular Python version can be also found in the corresponding source code files, mainly ceval.c.

![[Pasted image 20240902231427.png]]

the marshal.load and
dis.disassemble methods can be used to translate the bytecode into a readable format.

**Dynamic analysis**
Step-by-step execution is supported by any major IDE supporting the Python language