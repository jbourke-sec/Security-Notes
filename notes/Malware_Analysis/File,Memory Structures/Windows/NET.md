
Based on PE Structure

The .NET structure starts with a PE header that has the last entry in the data directory pointing to .NET's special CLR header

**.NET COR20 header**
starts after 8 bytes of the .text section contains basic information
about the .NET file

**cb:** Represents the size of the header (always 0x48) **MajorRuntimeVersion and MinorRuntimeVersion**: Always with values of 2 and 5 (even with runtime 4)
**Metadata address and size:** Contains all the CLR streams

**EntryPointToken (or RVA):** Represents the entry point and contains 2 values (0x6000012)

**0x06**: Represents the sixth table in the first stream Methods
**0x12 (18)**: Represents the method ID in the methods table, points to the metadata structure that contains all the information about classes,
methods, strings

**Identifying a .NET **

Imports only one API
==_CorExeMain== from mscoree.dll

using a PEiD or CFF Explorer that
includes signatures covering .NET

**Metadata streams**


**#~:** This stream contains all the tables that store information about classes, namespaces (classes containers), events, methods, attributes, and so on. Each
table has a unique ID (for example, the Methods table has an ID of 0x6).

**\#Strings:** This stream includes all the strings that are used in the #~ section. This includes the methods' names, classes' names, and so on. The structure of this stream is the following: each item starts with its length, followed by the string, and then the next item length followed by the string, and so on.

**\#US:** This stream is similar to the \#Strings stream, but it contains the strings that are used by the application itself

