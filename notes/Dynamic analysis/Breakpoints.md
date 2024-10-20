**Step into/step over breakpoint**: allows the processor to execute one instruction only
This breakpoint is done by modifying a flag in a register called EFlags.

**INT3 breakpoint**
Created my modifying or adding a byte to 0xCC

Once the debugger returns back on this INT3 breakpoint, it replaces the 0xCC back to 0xB8
and executes this instruction normally

**Memory breakpoints**
This type of breakpoint is
done by modifying the memory protection of this page of memory

Another way how many debuggers set a ==memory breakpoint== on access is by adding ==PAGE_GUARD (0x100)==

**Hardware breakpoints**
Hardware breakpoints are based on eight registers that are not accessible from the user mode, which are ==DR0== to ==DR7==.

Maximum 4 breakpoints given specific address for read/write/execute

SEH

way to remove hardware breakpoints is to use the GetThreadContext() API to
access the current thread (or another thread) context and check for the presence of
hardware breakpoints or clear them using the SetThreadContext() API.