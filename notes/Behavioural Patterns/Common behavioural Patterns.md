Malware generally has the same needs across all platforms

It needs to get into the target system.
In many cases, it needs to achieve persistence in order to survive the reboot.
It may need to get a higher level of privileges, for example, to achieve the systemwide
persistence or to get access to the valuable data.
In many cases, it needs to communicate with the remote system (C&C) in order
to do the following:
1. Get commands
2. Get new configuration
3. Get self-updates, as well as additional payloads
4. Upload responses, collected information, and files of interest

Some malware families behave like worms, aiming to penetrate deeper into networks; lateral movement