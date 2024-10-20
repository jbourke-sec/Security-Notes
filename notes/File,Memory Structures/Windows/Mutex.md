Mutexes are global objects that coordinate multiple processes
and threads.
Mutexes are mainly used to control access to shared resources, and are
often used by malware. For example, if two threads must access a memory
structure, but only one can safely access it at a time, a mutex can be used to control access

Only one thread can own a mutex at a time

Good malware indicator due to hardcoded names

A mutex can be created with the CreateMutex function. 

One process can get a handle to another process’s mutex by using the OpenMutex call