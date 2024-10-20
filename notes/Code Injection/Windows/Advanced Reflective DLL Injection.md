
**Advanced code injection-reflective DLL injection**
loads a malicious
DLL into the targeted process's memory ==from memory== rather than from the disk

**custom PE loader**

First, malware ==allocates memory with the size of the ImageBase== and follows the PE loading
steps including ==import table loading== and fixing the ==relocation entries==

**Debugging code injection in memory**

When a module (an executable file) gets loaded using Windows PE Loader, it gets loaded with an IMAGE flag to represent that it's a
memory map of an executable file. But when this memory page is allocated normally using
VirtualAlloc, it gets allocated with a PRIVATE flag to show that it is allocated for data: