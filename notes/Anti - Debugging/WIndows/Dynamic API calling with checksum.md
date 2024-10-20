For a malware author to implement this trick, they need to pre-calculate a checksum for this API name and push this value as an argument to a function that scans export tables of different libraries and searching for an API by this checksum.

![[Pasted image 20240821000451.png]]