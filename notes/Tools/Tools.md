**Autoruns by Sysinternals**
allow you to see whether any sensitive registry entries have been exploited for malicious use on
the current system
**x64_dbg:** This is a debugger for x86 and x64 executables with a very similar (if not identical) interface to OllyDbg. It's also an open source debugger: Use for dynamic analysis and memory dumping
**Scylla**: Rebuilds IAT for dumped executable
**XORSearch:** searches inside ciphertext by using a given plain text sample to search for. It doesn't only cover xor—it also covers other algorithms, including bit shifting
**funcap** appears to be
extremely handy as it allows you to record arguments that have been passed to
functions during the execution process and keep them in comments once it's
done
**Volatility:** there is a command called malfind. This command finds hidden and injected
code inside a process (or the entire system)
we can dump all memory images inside this process using the vaddump command
For injected PE files, we can dump them to disk (and reconstruct their headers and sections
back, but not import tables) using dlldump
One command lists the loaded
modules from the PEB information (from user mode), which is dlllist,
lists all loaded modules from EPROCESS kernel object information (kernel mode), which is
ldrmodules.
Any mismatch in the results between both commands could represent a
hollow process injection due to unlinking of memory spaces
When the application module is not linked to its PE file, possible process hollowing
When the application module appears in the dlllist results and not at all in the ldrmodules results, it represents that the process is hollowed out and that the malware is possibly loaded at another address. The malfind command could help us to find the new address
When the application appears in both commands' results and linked with the PE filename of the application, but there's a mismatch of the module address, could indicate possible injection with PEB tampering plugin called ***HollowFind*** that combines all of these commands.
we can use a Volatility command
called apihooks for API hooking
**Sysinternals tool called ProcDump**
This will dump the whole process and its memory. If you only want the process image, you can use -mm to create a Mini process image
**procmon:** is an advanced monitoring tool for Windows
that provides a way to monitor certain registry, file system, network, process, and thread activity
**Regshot:** is an open source registry comparison tool that allows you to take and compare two registry snapshots.
**Wireshark:** Wireshark is an open source sniffer, a packet capture tool that intercepts and logs network traffic. To use Wireshark to view the contents of a TCP session, right-click any TCP packet and select Follow TCP Stream

**olebrowse:** A pretty basic GUI tool that allows you to browse CFB
documents
**oledir**: Displays directory entries within CFB files
**olemap**: Shows all sectors present in the document, including the
header
oledump: This powerful tool gives a valuable insight into streams that are
present in the document and features dumping and decompression options as
well
**rtldump**: Another tool from the same author, this time aiming to facilitate the analysis of RTF documents

rtfdump -s stream number to drill into a stream
-H Decode hexadecimal

**pyxswf:** to detect, extract and analyze Flash objects (SWF) that may be embedded in files such as MS Office documents (e.g. Word, Excel) and RTF
**OfficeMalScanner**: Features several heuristics to search for and analyze
shellcode entries, as well as encrypted MZ-PE files
**officedissector**: a parser library written in Python that was designed for the security
analysis of OOXML files—can be used for automating certain tasks.
**OleVBA** - VBA Macros
**ExifTool** is a program for reading, writing, and manipulating image, audio, video, and PDF Metadata

**Kernel**

**WinDbg:** This is an irreplaceable tool when we are talking about debugging the kernel-mode code on Windows. Officially supported by Microsoft, this tool features multiple commands and extensions that aim to make the analysis as straightforward as possible
?: This is used to display regular commands.
**DriverView:** This is a tool developed by NirSoft; it allows you to quickly get a
list of loaded drivers and their location in memory
**DebugView**: This is a Sysinternals tool that allows you to monitor the debugging
output from both the user and kernel modes
**WinObj**: This is another useful tool from Sysinternals that can present a list of
various system objects relevant to kernel-mode debugging, such as devices and
drivers

**Shellcode**
use a debugger for the targeted
architecture and platform (such as OllyDbg for 32-bit Windows) by copying the hexadecimal representation of the shellcode and using the binary paste option
**Libemu:** Emulator
**Pokas x86 Emulator**: Emulator
**shellcode2exe.py**: Convert shellcode to executable
**scdbg:** analyse shellcpde

**Microsoft Word**

**oletools:** A unique set of several powerful tools that allow an analyst to analyze all common documents associated with Microsoft Office products, for example:
**olebrowse:** A pretty basic GUI tool that allows you to browse CFB
documents
**oledir:** Displays directory entries within CFB files
**olemap:** Shows all sectors present in the document, including the
header
**oleobj:** extract embedded objects from CFB files
**rtfobj:** same for RTF documents
oledump: This powerful tool gives a valuable insight into streams that are
present in the document and features dumping and decompression options as
well 
**rtfdump:** analysis of RTF documents
**OfficeMalScanner:** Features several heuristics to search for and analyze
shellcode entries, as well as encrypted MZ-PE files
**msodde tool:** (part of oletools) Useful for DDE Auto exploitation
**oledump:** can be used to extract and
analyze VBA macros


**.NET**

**Dnspy**: it's a decompiler that allows you to debug and patch the app
**main function:** right-click on the program (from the sidebar) and
choose Go To Entry Point

More meaningful method names
Edit Method or clicking Alt + Enter and changing the name of the method. After that, you need to save the module and reload it

You can modify the entry point code and add a call to the decryption function to decrypt strings

**de4dot:** de4dot.exe \<sample\>
This will rename all the obfuscated name

You can then decrypt the strings dynamically using the following command:
de4dot \<sample\> --strtyp delegate --strtok \<decryption method
ID\>

**Visual Basic**

**P-Code**
VB decompiler can be used to get access to its internals. The Lite
version is free and provides access to the p-code disassembly
Can also be used as a decompiler for dynamic debugging, only the code that has to be traced needs to be created
When this isnt available to debugging use the WKTVBDE project
**P32Dasm** tool that allows you to obtain p-code listings in a
few clicks

**Native-Code**
Most static/dynamic PE tools do the job
**IDA vb.idc script:** automatically marks up most of the important structures, as well as the
corresponding pointers

**decode-vbe.py**: Decode VBE to VBS



**Java**

**Ghidra**: This reverse-engineering toolkit supports multiple file formats and instruction sets, including Java bytecode
**Procyon:** Another powerful decompiler, this is able to process Java files, raw
bytecode, and bytecode Abstract Syntax Tree (AST).
**d4j:** A Java decompiler built on top of the Procyon project.

Dealing with anti-reverse engineering solutions

many variants of malware use either cracked versions or demo and
leaked licences of commercial obfuscators

**Java Deobfuscator**: A versatile
project that supports a decent amount of commercial protectors
**JMD:** A Java bytecode analysis and deobfuscation tool that is able to remove obfuscation implemented by multiple well-known protectors
**Java DeObfuscator (JDO):** A general-purpose deobfuscator that implements several universal techniques, such as renaming obfuscated values to be unique
and indicative to their data type
**jrename:** Another universal deobfuscator that specializes in renaming values in order to make the code more readable

**PowerShell**

**PowerShell Integrated Scripting Environment (ISE):** Easiest way to handle embedded PowerShell encryption is through dynamic analysis

**JavaScript**
**jsbeautifier:** Basic unpacking and deobfuscation

**Chrome or Firefox developer tools:** generic dynamic analysis

**Malzilla:** Deobfuscation

**ExtractScripts**: Extract scripts from HTML files.



