==Can hide malware presence==
Hook Process32First and Next, removing it from results
File listing APIs such as FindFirstFileA and FindNextFileA
Registry enumerations calls like RegQueryInfoKey and RegEnumKeyEx

Stealing data from outbound comms like banking trojans
InternetConnectA, HttpSendRequestA, InternetReadFile
ws2_32.dll
Firefox API calls like PR_Read, PR_Write, PR_Close.


