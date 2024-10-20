Themida is a very complicated packer with many features. Most of the features
are anti-debugging and anti-analysis, which make it a very secure packer
that’s difficult to unpack and analyze.
Themida contains features that prevent analysis with VMware, debuggers,
and Process Monitor (procmon). Themida also has a kernel component,
which makes it much more difficult to analyze. Code running in the
kernel has very few restrictions, and analysis code generally runs in user
space, and is therefore subject to more restrictions
run the entire time that the original program is running.
Some automated tools are designed to unpack Themida files, but their
success varies based on the version of Themida and the settings used when
the program was packed. Themida has so many features and settings that it is
impossible to find a single unpacking strategy that will always work.
If automated tools don’t work, another great strategy is to use ProcDump
to dump the process from memory without debugging.