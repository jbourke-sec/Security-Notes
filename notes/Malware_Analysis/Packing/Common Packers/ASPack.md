ASPack uses self-modifying code, which makes it difficult
to set breakpoints and to analyze in general

Setting a breakpoint can cause programs packed with ASPack to terminate prematurely, but these programs can still be manually unpacked using  hardware breakpoints set on the stack address

ASPack is so popular that there are many automated unpackers available. Their effectiveness
varies

**Begin by**
opening the code for the unpacking stub. 
Early in the code, you will see a
PUSHAD instruction. 
Determine which stack addresses are used to store the
registers
set a hardware breakpoint on one of those addresses. Ensure
that it is set to break on a read instruction. 

When the corresponding POPAD
instruction is called, the breakpoint will be triggered and you will be just a few instructions away from the tail jump that leads to the OEP