RING 0 for kernel mode
RING 1 for VMs and Hypervisors on modern processors
RING 3 for user mode

RING 0 has the least privileges—that is, the processes in this
ring cannot affect the system, they cannot access the memory of other processes, and they
cannot access physical memory

RING 0 can do anything—it can directly affect the system and its resources. Therefore, it's only
accessible to the Windows kernel and the device drivers.