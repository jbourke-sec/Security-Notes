**Process injection in kernel mode**
Once the driver is attached to this process's memory space, it can see this process's virtual
memory

For a driver to be able to attach to the process memory, it needs to get its EPROCESS using
the ==PsLookupProcessByProcessId== API and then use the
==KeStackAttachProcess== API to attach to this process's memory space.

it can read and write to its memory space and allocate memory
using the ==ZwAllocateVirtualMemory== API

to detach from the process memory, it can execute
the ==KeUnstackDetachProcess== API,

Executing the inject code
Get the ETHREAD object of the thread it wants to queue an APC function by providing its Thread ID (TID). This can be done by using the PsLookupThreadByThreadId API.
2. Attach the user-mode function to this thread using the KeInitializeApc API.
3. Add this function to the queue of the APC functions to be executed in this thread using the KeInsertQueueApc API

If the thread didn't execute any of the previously mentioned APIs and never enters an alertable state until it is terminated, none of the queued APC functions will be executed.
Therefore, some malware families tend to attach their APC thread to multiple running threads in the application.