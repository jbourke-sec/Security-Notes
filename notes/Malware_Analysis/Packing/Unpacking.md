**The official unpacking process:** Some packers, such as UPX or WinRAR, are self-extracting packages that include an
unpacking technology that's shipped with the tool
**Using generic unpackers:** Generic unpackers are debuggers that have been prescripted to unpack specific packers or to automate the manual unpacking process,
**Memory Dumps:** involves executing the malware and
taking a memory snapshot of its process and every process it injects code into.
Some common sandboxing tools provide a process's memory dump as a core feature or as
one of their plugins' features, such as Cuckoo Sandbox.
**Memory breakpoint on execution:**
Many packers encrypt the first few sections (including the code section), and the unpacker stub just unpacks each of them and then transfers control to the original entry point (OEP) for the application to run normally

Hardware breakpoints can work but only apply to up to 4 bytes

Change upacking stub to read write in x64 dbg

Patch VirtualProtect API calls to prevent malware from setting the stub to execute again

The debugged process will break directly on the OEP, which will cause
an access violation error to appear,

**Call stack backtracing:** 
Set breakpoints on common API calls
Retrace the call stack until you get to the first return address
Slide up from here to find the OEP

**Monitoring memory allocated**
**spaces for unpacked code**

Memory allocation in user mode
VirtualAlloc/VirtualAllocEx
LocalAlloc
GlobalAlloc
HeapAlloc

C samples
Malloc
Calloc

WriteProcessMemory: Often used in order to inject the unpacked payload, either to some other process or to itself

**In-place unpacking**
Search for a big encrypted block (usually, it has high entropy and is visible to the
naked eye in a hex editor).
Find the exact place where it will be read (the first bytes of the block may serve other purposes—for example, they might store various types of metadata, such
as sizes or checksums/hashes, to verify the decryption).
Put a breakpoint on read and/or write there.
Run the program and wait for the breakpoint to be triggered.

**Stack restoration-based**
In this case, it is possible to set a breakpoint on access to the [ebp-4] value while staying at
the entry point of the sample and then executing it so that the breakpoint will hopefully
trigger just before transferring control to the unpacked code.