WinUpack is a packer with a GUI front end, designed for optimal compression, and not for security. 

There is a command-line version of this packer called UPack, and there are automated unpackers specific to UPack and WinUpack.

Although security isn’t its focus, WinUpack does include security measures that make it difficult to find the OEP, and render techniques such as searching for the tail jump or using OllyDump useless.

The best strategy for finding the OEP for a program packed with UPack is to set a breakpoint on GetProcAddress, and then single-step carefully over instructions looking for the loops that set the import resolution

A good way to doublecheck
is to examine the code around the OEP, which should look like ordinary code compared to the unpacking stub

Another strategy that works on UPack is to set a breakpoint on
GetModuleHandleA for GUI programs or GetCommandLineA for command-line programs

Sometimes WinUpack crashes OllyDbg by using a PE header that Olly-Dbg parses incorrectly.