Native

**Invoke-Expression (iex):** This executes a statement provided as
an argument
**Invoke-Command (icm):** This is often used with the -ScriptBlock argument to achieve pretty much the same
functionality as Invoke-Expression
**Invoke-WebRequest (iwr):** This sends a web request; for example, it could send a request to interact with the C&C
**ConvertTo-SecureString:** This is commonly used for decrypting an embedded script

.NET

**\[System.Net.WebClient\] class:** 

**DownloadString**: Download a string and store it in memory
**DownloadData**: download the payload as a Byte array
**DownloadFile**: Download a file to disk

Each of these methods has its Async versions with the corresponding name suffixes (like DownloadStringAsync)

**The \[System.Net.WebRequest\],**
**\[System.Net.HttpWebRequest\],**
**\[System.Net.FileWebRequest\],**
**and \[System.Net.FtpWebRequest\] classes:**

Create (also CreateDefault and CreateHttp): creates a web request to the server
GetResponse: This sends a request and gets the response. Versions with the Async suffix and the Begin and
End prefixes are also available for asynchronous operations (such as BeginGetResponse or GetResponseAsync)
GetRequestStream: This returns a stream for writing data to the internet resource. Versions with the Async suffix and the Begin and End prefixes are available

**The \[System.Net.Http.HttpClient\] class**
GetAsync, GetStringAsync, GetStreamAsync, GetByteArrayAsync, PostAsync, and PutAsync. Multiple options for http requests

The \[System.IO.Compression.DeflateStream\] and
\[System.IO.Compression.GZipStream\] classes are commonly
employed to decompress the embedded shellcode after decoding itbusing the base64 algorithm
usually used with a
\[System.IO.Compression.CompressionMode\]::Decompress parameter as an argument for an \[System.IO.StreamReader\]

The \[System.Convert\] class:
FromBase64String : Decrypt base64-encoded
strings

