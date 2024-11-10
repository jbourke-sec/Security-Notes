
The Microsoft Component Object Model (COM) is an interface standard that makes it possible for different software components to call each other’s code without knowledge of specifics about each other

COM is implemented as a client/server framework. The clients are the programs that are making use of COM objects,

Each thread that uses COM must call the OleInitialize or CoInitializeEx
function at least once prior to calling any other COM library function

COM objects are accessed via their globally unique identifiers (GUIDs) known as class identifiers (CLSIDs) and interface identifiers (IIDs).

The CoCreateInstance function is used to get access to COM functionality.

COM Server Malware
Some malware implements a malicious COM server, which is subsequently used by other applications

Malware that implements a COM server is usually easy to detect because it exports several functions, including DllCanUnloadNow, DllGetClassObject,
DllInstall, DllRegisterServer, and DllUnregisterServer, which all must be exported by COM servers.