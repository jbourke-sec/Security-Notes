Windows creates an object called EPROCESS for each process

**Virtual Address Descriptors** - mappers between virtual memory and their equivalent physical memory

Stored in a linked list with the next object being flink and previous blink

Both addresses are stored in ActiveProcessLinks:

structure of EPROCESS changes from one version of OS to another

**ETHREAD**
ETHREAD, and its core, KTHREAD, includes all the information
related to a specific thread, including its context, status, and an address of the
corresponding process object (EPROCESS)

When windows switches threads, it follows the links between them in
the ETHREAD structure (that is, the linked list that connects all ETHREAD objects).

DKOM attack
Get the current process's EPROCESS using
the PsLookupProcessByProcessId API.
2. Follow the ActiveProcessLinks to find the EPROCESS of the process that you want to hide.
3. Change the FLink of the previous EPROCESS so that it doesn't point to this EPROCESS but to the next one instead.
4. Change the BLink of the next process so that it doesn't point to this EPROCESS but to the previous one instead.