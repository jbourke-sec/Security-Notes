Permissions Required: Administrator

`/Library/StartupItems` isn’t guaranteed to exist on the system by default as it is deprceated in favor of Launch Daemons

A startup item is a directory whose executable and configuration property list (plist), `StartupParameters.plist`, reside in the top-level directory

An adversary can create the appropriate folders/files in the StartupItems directory to register their own persistence mechanism

