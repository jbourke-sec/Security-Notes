System calls (syscalls) is the interface between the program and the kernel of the OS it is running on.

**signal:** This can be used to set a new handler for a particular signal and then invoke it to disrupt debugging, for example, for SIGTRAP, which is
commonly used for breakpoints
**ptrace:** This syscall is commonly used by debugging tools in order to trace executable files, but it can also be used by malware to detect their presence or to prevent them from doing it by tracing itself