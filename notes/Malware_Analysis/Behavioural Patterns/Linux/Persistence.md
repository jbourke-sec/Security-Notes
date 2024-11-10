**Cron Job:** 
attacker adds a new entry
to crontab, malware will be executed again after the reboot and, apart from this, it may revive malware if it is killed

Crontab utility
/var/spool/cron/crontabs/

modify /etc/crontab or
place a script in /etc/cron.d/
or /etc/cron.hourly(requires elevated privileges)

**Services:** 

SysV-style init: Script needs to be placed in the /etc/init.d/ location.

can be invoked by using the symbolic link in the /etc/rc?.d/ location

to add malicious commands to the /etc/inittab file by defining runlevels
directly.

modify the /etc/rc.local
file that's executed after normal system services

**Upstart:** later replaced
by systemd

main location of the configuration files in this case is /etc/init

**systemd:** This system aims to replace System V, locatio for the configuration files this time is
/etc/systemd.

**Profile Configurations**

Malicious commands added to
user's ˜/.bash_profile (or ~/.bash_login and the older sh's ~/.profile files) or /.bashrc files

former is executed for
login shells

latter is for interactive non-login shells

Other shells have their own profile files, for example, zsh uses
the .zprofile file.

This approach requires no elevated privileges.

The
/etc/profile file can be used in the same way but, in this case, elevated
privileges are required

**Desktop autostart**

approach abuses autostart
configurations for X desktops. The malicious .desktop files are placed in
the ~/.config/autostart location. Another location for executing scripts this way is ~/.config/autostart-scripts.

**Actual file replacement**
modifies/replaces actual original programs that are run periodically. generally require elevated privileges

**SUID executables**
possible to misuse SUID executables (files executed with the owner's privileges)

allow the execution of virtually any command with escalated privileges using the -exec argument