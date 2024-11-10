**Thread Information Block (TIB):**
Contains some information about the thread, including the list of functions that are used for **error handling**

**Thread Environment Block (TEB):**
Has more information about the thread, including the thread ID

**Process Environment Block (PEB):** Includes information about the process, such as the process name, process ID (PID), loaded modules

These structures are stored inside the process memory and
accessible through its code.

They are all accessible through a special segment register FS, like this:
==mov eax, DWORD PTR FS:\[XX\]==