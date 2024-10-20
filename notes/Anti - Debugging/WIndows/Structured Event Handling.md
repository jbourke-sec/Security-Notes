Hardware breakpoints are not available in user mode to access

To access malware families can use SEH

Windows mechanism for exception handling

Callbacks are set to handle exceptions, if one cannot handle it is passed to the next

If the last callback was unable to handle the exception, the
operating system terminates the process and informs the user

Pointer to the 1st callback stored in TIB

==Can be accessed via FS:\[0x00\]==

**x64 Instruction Handling**

Structured exception handling in x64 uses a static exception information
table stored in the PE file and does not store any data on the stack.
Also, there is an _IMAGE_RUNTIME_FUNCTION_ENTRY structure in the .pdata section
for every function in the executable that stores the beginning and ending
address of the function, as well as a pointer to exception-handling information
for that function.

Linked list structure

![[Pasted image 20240829011758.png]]
The setup of the SEH callback generally looks like this:
PUSH <callback_func> // Address of the callback function
PUSH FS:\[0\] // Address of the previous callback item in the
list
MOV FS:\[0\],ESP // Install the new EXCEPTION_REGISTRATION

The important arguments are the following:
ExceptionRecord: Contains information related to the exception or the error
that has been generated. It contains the exception code number, the address, and
other information.
ContextRecord: This is a structure that represents the state of that thread at the
time of the exception. It's a long structure that contains all the registers and other
information. A snippet of this structure would look as follows

==Malware can use SEH to get the thread context and clear the breakpoints== 

Another way