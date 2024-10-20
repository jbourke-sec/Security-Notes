CIL language instruction set
doesn't include any registers, and all the variables, classes, fields, methods, and
so on are accessed through their ID in the streams and their tables. Local variables are also
accessed through their ID in methods

Pushing into stack instructions
![[Pasted image 20240901111440.png]]

Pulling values from the stack
![[Pasted image 20240901113458.png]]

Data Types
![[Pasted image 20240901111556.png]]

**Mathematical and logical operations**
same operations that you will see in any assembly language, such as add, sub, shl, shr, xor, or, and, mul, div, not, neg, rem

These instructions take their arguments from the stack and save the result back into the
stack

**Branching instructions**
![[Pasted image 20240901113715.png]]depend on the stack values for comparing and branching:

If condition
![[Pasted image 20240901125317.png]]
Loops
![[Pasted image 20240901125426.png]]
