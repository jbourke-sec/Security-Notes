OpenSCManager Returns a handle to the service control manager, which is used for all subsequent service-related function calls. All code that will interact with services will call this function.
CreateService Adds a new service to the service control manager, and
allows the caller to specify whether the service will start automatically at
boot time or must be started manually.
StartService Starts a service, and is used only if the service is set to be
started manually.