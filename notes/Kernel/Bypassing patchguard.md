PatchGuard code is ==changing its position in the kernel mode==
==from one update to another==, making it a moving target and breaking all the previous malware families that had been able to bypass it in the previous versions.

it's also ==possible to disable the driver signature enforcement==
option using the Command Prompt, as follows: ==bcdedit.exe /set testsigning on==

Requires ==admin privs and restart==

Another option that used to be available was to execute the ==bcdedit
/set nointegritychecks== on command, but, currently, this option is ==ignored on major==

==Disabling PatchGuard== using the Command Prompt
modern versions of Windows.
==bcdedit \/debug ON==
