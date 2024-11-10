In terms of syscalls, the most common way to detect debuggers and tools such as strace is to use ptrace with the PTRACE_TRACEME argument

Can also try to fork and then trace itself using this syscall in order to prevent debuggers from doing so.