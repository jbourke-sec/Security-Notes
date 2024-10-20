
The idea behind it is to
randomize addresses where the application and the DLLs are loaded in the process
memory

make it very hard for the attackers to construct their ROP chains

For ASLR to be effective, it is required to have the application and all its libraries compiled with an ASLR enabling flag

If there is at least one module that doesn't support ASLR, it becomes possible for the attacker to find the required ROP gadgets there

**DEP and full ASLR – heap spray technique**

The idea behind this technique is to make multiple addresses lead to the shellcode by filling the memory of the application with lots of copies of it, which will lead to its execution with a very high probability

This can be achieved by having a huge amount of
nop bytes
