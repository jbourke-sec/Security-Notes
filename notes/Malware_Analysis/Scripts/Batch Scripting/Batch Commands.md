This set of commands provides the most fundamental functionality and
is embedded into the interpreter itself. This means that the commands don't have their own executable files

**call:** This command executes functionality from the current batch
file or another batch file
**cd**: This command changes the current directory
**copy:** This command copies filesystem objects to a new location
**del/erase**: These commands delete existing files (not directories)
**dir**: This command lists filesystem objects
**move:** This command moves filesystem objects to another location
**rd/rmdir:** These commands delete directories (not files)
ren/rename: These commands change the names of the filesystem
objects
**start:** This command executes a program or opens a file
according to its extension

External: These are tools that are provided as independent executable programs and can be found in a system directory.

**at:** This schedules a program to execute at a certain time.
**attrib:** This displays or changes the filesystem object attributes;
for example, the system, read-only, or hidden attributes.
**cacls:** This displays or changes the Access Control List (ACL).
find: This searches for particular filesystem objects; for example,
by filename, by path, or by extension.
format: This formats a disk overwriting (or destroying) the
previous content.
**ipconfig:** This displays and renews the network configuration for
the local machine.
**net**: This is a multifunctional tool that supports various network
operations, including user (net user) and remote resource (net
share) administration.
**ping:** This tool checks the connectivity to remote resources by
using ICMP packets. It can also be used to establish a subvert
network channel and exfiltrate data.
robocopy and xcopy: These tools copy filesystem objects to
another location.
**rundll32:** This loads the DLL; here, exports by name and by
ordinals are both supported.
**sc:** This communicates with Service Control Manager and
manages Windows services including creating, stopping, and
changing operations.
**schtasks:** This is a more powerful version of the at tool; it works
by scheduling programs to start at a particular time. This is
essentially a console alternative to Windows Task Scheduler, and it
supports local and remote machines.

**Common tools to download/decode payloads**

bitadmin
certutil
regsvr32
mshta
wmic

**Obfuscation**
Substrings
Variable replacement
long random variable names
meaningless characters like pairs of double quotes, carats



