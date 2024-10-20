**Shared Files**
Shared files are special files with names that start with \\serverName\share or \\?\serverName\share. They access directories or files in a shared folder stored on a network. The \\?\ prefix tells the OS to disable all string parsing, and it
allows access to longer filenames.

**Files Accessible via Namespaces**
Additional files are accessible via namespaces within the OS. Namespaces can be thought of as a fixed number of folders, each storing different types
of objects. The lowest level namespace is the NT namespace with the prefix \.
The NT namespace has access to all devices, and all other namespaces exist within the NT namespace

Another example is malware usage of \\Device\\PhysicalMemory in order to access physical memory directly

Device\\ PhysicalDisk1

**Alternate Data Streams**
The Alternate Data Streams (ADS) feature allows additional data to be added to an existing file within NTFS, essentially adding one file to another

ADS data is named according to the convention normalFile.txt:Stream:$DATA,
which allows a program to read and write to a stream
