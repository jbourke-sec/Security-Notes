PowerShell understands
even truncated arguments and the associated parameters as long as they are not ambiguous.

**NoProfile (often referred to as -NoP)**: This skips the loading of the PowerShell profile; it is useful as it is not affected by local settings.
**-NonInteractive (often referred to as -NonI**): This doesn't present an
interactive prompt; it is useful when the purpose is to execute specified
commands only.
**-ExecutionPolicy (often referred to as -Exec or -EP)**: This is often used with the Bypass argument to ignore settings that limit certain PowerShell
functionality. It can also be achieved by many other approaches; for example, by modifying PowerShell's ExecutionPolicy registry value.
**-WindowStyle (often referred to as -Win or -W):** This is usually used by
attackers with a Hidden (or 1) argument to hide the corresponding window for stealth purposes.
-**Command (often referred to as -C):** This executes a command provided in a command line.
**-EncodedCommand (often referred to as -Enc, -EC, or -E)**: This executes anencoded (base64) command provided in a command line