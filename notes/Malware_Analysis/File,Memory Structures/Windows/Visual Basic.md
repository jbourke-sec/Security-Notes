atlook like standard MZ-PE executables. They can be
easily recognized by a unique imported DLL, MSVBVM60.DLL

At the entry point of a sample, we can expect to see a call to the ThunRTMain (MSVBVM60.100) runtime function

The Thun here is a reference to the original project's name, BASIC Thunder. This function
receives a pointer to the following structure

![[Pasted image 20240901132557.png]]

Now, let's take a look at the ProjectInfo structure:

![[Pasted image 20240901132707.png]]

![[Pasted image 20240901132737.png]]
**NativeCode.** This field can be used to figure out whether the sample is compiled as p-code or native code.

**P-code:** In this case, the main imported DLL will be MSVBVM60.DLL, which
provides access to all the necessary VB functions:

**Native code:** In addition to MSVBVM60.DLL, there will also be the typical system
DLLs such as kernel32.dll and the corresponding import functions:
