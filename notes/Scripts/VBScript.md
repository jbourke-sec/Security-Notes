**WScript.Shell:** This gives access to multiple system-wide operations

==RegRead/RegDelete/RegWrite==: These interact with the Windows
registry
==Run==: This is used to run an application

**Shell.Application**: This allows more system-related functionality, as follows:

==GetSystemInformation==: This acquires various system information
==ServiceStart==: This starts a service
==ServiceStop==: This stops a service
==ShellExecute==: This runs a script or an application

**Scripting.FileSystemObject:** This gives access to filesystem operations

Among native methods, the following can be used to execute expressions and statements:
**Eval:** This evaluates an expression and returns a result value. It interprets the = operator as a comparison rather than an assignment.
**Execute:** This executes a group of statements separated by colons or line breaks in the local scope.
**ExecuteGlobal:** This is the same as Execute, but for the global scope. It is commonly used by attackers to execute decoded blocks.

it is relatively straightforward to work with Windows Management
Instrumentation (WMI) using VBScript

With the help of the WbemScripting.SWbemLocator object and its ConnectServer method in order to access "root\\cimv2":

![[Pasted image 20240904234643.png]]

Through the winmgmts: moniker:
![[Pasted image 20240904234740.png]]