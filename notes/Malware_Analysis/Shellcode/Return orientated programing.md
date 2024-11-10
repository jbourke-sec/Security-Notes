
SetProcessDEPPolicy and NtSetInformationProcess APIs to disable DEP.

The trick here is to use the Import Address Table (IAT) of a module to get the address of any of these APIs

attacker can redirect the execution to the beginning of this API.

the attacker places all the arguments that are required for each of these
APIs, followed by a return to the API they want to execute

VirtualProtect to set shellcode memory location permissions to execute
