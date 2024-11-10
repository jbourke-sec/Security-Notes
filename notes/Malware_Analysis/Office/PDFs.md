A PDF is a tree file that consists of objects that implement one of eight data types:

- **Null object.** 
- **Boolean values.** 
- **Numbers.** 
- **Names:** These values can be recognized by a forward slash at the beginning.
- **Strings:** Surrounded by double parentheses.
- **Arrays:** Enclosed within square brackets.
- **Dictionaries:** In this case, double curly brackets are used.
- **Streams**: These are the main data storage blocks, and they support binary data. Streams can be compressed in order to reduce the size of the associated data.

PDF documents start with the %PDF signature, followed by the format version number

**xref:** This is used to mark the cross-reference table, contains offsets of all indirect objects
**obj/endobj:** These keywords define indirect objects.
**stream/endstream:** This can be used to define streams.
**trailer:** This defines the trailer dictionary at the end of the file

**Entries**
**/ObjStm:** The object stream, a complex data type that can be used
to store multiple objects. Usually, it is accompanied by several
other entries, such as /N defining the number of embedded objects
and /First, which defines the offset of the first object inside it.
The first line of the stream defines the numbers and offsets of
embedded objects, all separated by spaces.
**/Action:** Describes the action to perform. There are different types
of them, for example:
**/Launch:** Defines the launch action to execute an application specified using the /F value. Optionally, separate parameters can be provided using a separate entry, for example, /Win for Windows
**/URI:** Defines the URI action to resolve a URI specified.
**/JavaScript:** Executes a specified piece of JavaScript:
**/JS:** Defines a text string or a stream
containing a JavaScript block that
should be executed once the action
(rendition or JavaScript) triggers.
**/Rendition:** Can be used to execute the JavaScript as well. The same /JS name can be used to specify it.
**/SubmitForm:** Sends data to the specified address.
The URL is provided in the /F entry, and might be used in phishing documents.
**/EmbeddedFiles:** Can be used to store an auxiliary file, for
example, a malicious payload.
**/Catalog:** The root of the object hierarchy; defines references to
other objects.
**/Names:** An optional document name dictionary. Allows you to refer to some objects by names rather
than by references, for example, using /JavaScript
or /EmbeddedFiles mappings.
**/OpenAction:** Specifies the destination to display
(generally, this isn't relevant for malware analysis purposes) or an action to perform once the document is opened (see the previous list).
**/AA:** Additional actions associated with trigger events.

**/Filter:** This entry defines the decoding filter(s) to be applied to the associated stream so that the data becomes readable. /FFilter can be used in the stream's external file. For some of them, optional parameters can be specified using /DecodeParms (or /FDecodeParms, respectively). Multiple filters can be
cascaded if necessary. There are two main categories of filters: compression filters and ASCII filters. 
Here are some examples that are commonly used in malware:
/**FlateDecode**: Probably the most common way to compress text
and binary data, this utilizes the zlib/deflate algorithm
**/LZWDecode**: In this case, the LZW compression algorithm is used
instead
**/RunLengthDecode**: Here, the data is encoded using the Run-
Length Encoding (RLE) algorithm
**/ASCIIHexDecode:** Data is encoded using hexadecimal
representation in ASCII
**/ASCII85Decode:** Another way to encode binary data, in this case
using ASCII85 (also known as Base85) encoding
**/Encrypt:** An entry in the file trailer dictionary that specifies that this document
is password protected. The entries in the corresponding object specify the way this is done:
**/O:** This entry defines the owner-encrypted document. Generally,
it is used for DRM purposes.
**/U:** Associated with the so-called user-encrypted document, it is
usually done for confidentiality. Malware authors may use it to
bypass security checks and then give the victim a password to
open it.
It is worth mentioning that in the modern specification, it is possible to replace parts of
these names (or even the whole name) with \#XX hexadecimal representations, so /URI can
become /#55RI or even /#55#52#49.