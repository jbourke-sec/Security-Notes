Windows allows logon scripts to be run whenever a specific user or group of users log into a system. This is done via adding a path to a script to the `HKCU\Environment\UserInitMprLogonScript` Registry key

Depending on the access configuration of the logon scripts, either local credentials or an administrator account may be necessary