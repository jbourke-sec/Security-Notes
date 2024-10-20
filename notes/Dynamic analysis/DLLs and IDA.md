Load it to IDA as any other executable

**Choose debugger**
Local Win32 debugger for 32-bit Windows

Remote Windows debugger with
the win64_remote64.exe application for 64-bit Windows

Set the full path of rundll32.exe (or regsvr32.exe for COM DLL

COM DLL recognised by recognized by DllRegisterServer/DllUnregisterServeror the DllInstall

Set the full path to the DLL to the Parameters field

**For a typical DLL** that's loaded using
rundll32.exe, append either a name or a hash followed by the ordinal (for
example, #1) of the export function you want to debug

**For Control Panel (CPL) DLLs** that can be recognized by the CPlApplet export, the shell32.dll,Control_RunDLL argument can be specified before the path to the analyzed DLL instead

**For the COM DLLs**
full path should be prepended with
the /u argument in case
the DllUnregisterServer export needs
to be debugged. For a DllInstall
export, a combination of /n
/i[:cmdline] arguments should be used instead

**In case the DLL is a service DLL**
You need to properly debug ServiceMain