Easiest way to handle embedded PowerShell encryption is through dynamic analysis in the PowerShell Integrated Scripting Environment (ISE).

In this case, the code to dump the decrypted string on a disk is being added straight after the decryption block. For this purpose, the Set-Content, Add-Content, and Out-File cmdlets, along with the pipe symbol (|) or classic > and >> input redirects, can be used:
powershell -c "$a='secret'; $a | set-content 'output.txt'"
Alternatively, the Write-Host cmdlet can be used to write the decrypted output to the console and then redirect it to a file.