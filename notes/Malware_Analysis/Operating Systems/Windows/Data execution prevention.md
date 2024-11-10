The idea behind it is to stop the execution inside
any memory page that doesn't have EXECUTE permission. This technique can be
supported by hardware that raises an exception once shellcode gets executed in the stack or
in the heap (or any place in memory that doesn't have this permission).
