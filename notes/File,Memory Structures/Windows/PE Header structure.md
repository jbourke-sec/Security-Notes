**MZ header**
Early in the MS-DOS era, Windows and DOS co-existed, and both had their executable files with the same extension, .exe

This program cannot be run in DOS mode

when a Windows application gets executed in the DOS environment,
the small DOS application at the start of it will get executed

**PE header**
![[Pasted image 20240817130047.png]]

Machine: This field represents the processor type
NumberOfSections: This value represents the number of sections that
follow the headers
TimeDateStamp: This is the exact date and time that this program was compiled
Characteristics: This value represents the type of the executable file

**Optional header**
Magic: This identifies the platform this PE file supports
ImageBase: This is the address where the program was designed to be loaded in the virtual memory
SectionAlignment: The size of each section and all headers' size should be aligned to this value while loaded in the memory
FileAlignment: The size of each section in the PE file
MajorSubsystemVersion: This represents the minimum Windows version to run the application,
SizeOfImage: This is the size of the whole application in memory
SizeOfHeaders: This is the size of all headers

**Data Directory**
The Data directory array points to the other optional headers that might be included in the executable and are not necessary included in every application.

Import table: This represents the code functions (or APIs) that this program doesn't include but wants to import from other executable files or libraries of code (or DLLs).
Export table: This represents the code functions (or APIs) that this program includes in its code and is willing to export and allow other applications to use, rather than rewrite them from scratch.
Resource table: This is always located at the start of the resource section and its purpose is to represent the packages' files with the program, such as icons, images, and others.
Relocation table: This is always located at the start of the relocation section and it's used to fix addresses in the code when the PE file is loaded to another place in memory.
TLS table: Thread Local Storage could be used to bypass debuggers

Section table
![[Pasted image 20240817141746.png]]

PointerToRawData: The pointer to the beginning of the section in the file on the hard disk (relatively to the start of the file). These types of addresses are called offsets.
Characteristics: Memory protection flags (EXECUTE, READ, or WRITE).

**PE+ (x64 PE)**
Very similar to the good old PE header with very few changes as follows:
ImageBase: It is 8 bytes instead of 4 bytes.
BaseOfData: This was removed from the Optional header.
Others: Some other fields, such as SizeOfHeapCommit, SizeOfHeapReserve, SizeOfStackReserve, and SizeOfStackCommit are now 8 bytes instead of 4 bytes.
Magic: This value changed from 0x10B (representing x86) to 0x20B
(representing x64).