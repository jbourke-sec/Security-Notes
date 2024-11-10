Of the Windows network options, malware most commonly uses Berkeley compatible sockets, functionality that is almost identical on Windows and UNIX systems.
Berkeley compatible sockets’ network functionality in Windows is implemented in the Winsock libraries, primarily in ws2_32.dll

![[Pasted image 20240913004800.png]]

**The WinINet API**
In addition to the Winsock API, there is a higher-level API called the WinINet API.

InternetOpen is used to initialize a connection to the Internet.
InternetOpenUrl is used to connect to a URL
InternetReadFile works much like the ReadFile function, allowing the program
to read the data from a file downloaded from the Internet.