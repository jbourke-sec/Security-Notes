**Privileges required:** root

Adversaries can establish persistence by adding a malicious binary path or shell commands to `rc.local`, `rc.common`, and other RC scripts specific to the Unix-like distribution

Executes on reboot of the system


especially effective for lightweight Unix-like distributions using the root user as default, such as IoT or embedded systems

Several Unix-like systems have moved to Systemd and deprecated the use of RC scripts. This is now a deprecated mechanism in macOS in favor of Launchd