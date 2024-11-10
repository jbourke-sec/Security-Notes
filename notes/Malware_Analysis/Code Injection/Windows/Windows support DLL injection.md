***HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows***
***NT\CurrentVersion\Windows\AppInit_DLLs***

The libraries specified here are loaded
together with every process that loads user32.dll
requires DLLs to be signed and it's disabled by default for Windows 8 and
beyond
still can be misused by setting
the RequireSignedAppInit_DLLs value to False and LoadAppInit_DLLs value to
True

***HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session***
***Manager\AppCertDlls***

The libraries in this registry entry are loaded in each process that calls at least one of the
following functions:

CreateProcess
CreateProcessAsUser
CreateProcessWithLogonW
CreateProcessWithTokenW
WinExec

requires
administrative privileges since HKEY_LOCAL_MACHINE is not writable for normal users

***HKEY_CURRENT_USER\Software\Classes\<AppName>\shellex\ContextMenuHandlers***

This path loads a shell extension (a DLL file) in order to add additional features to the main
Windows shell (explorer.exe).

can be easily created and modified without any
administrative privileges.

**Winlogon Notify**
Malware authors can hook malware to a particular Winlogon event, such as logon, logoff, startup, shutdown, and lock screen



