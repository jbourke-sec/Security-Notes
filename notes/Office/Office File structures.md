**CFB**
Byte order (2 bytes): Always 0xFFFE representing little-endian order
Sector shift (2 bytes): The FAT sector size as a power of 2, 0x0009 for major version 3 (2^9 = 512 bytes) or 0x000C for major version 4 (2^12 = 4,096 bytes)
Number of FAT sectors (4 bytes): Number of FAT sectors
First directory sector location (4 bytes): Represents the starting sector number for the directory stream
First DIFAT sector location (4 bytes): Starting sector number for the DIFAT data
Number of DIFAT sectors (4 bytes): Stores a number of DIFAT sectors
DIFAT (436 bytes): An array of integers (4 bytes each) representing the first 109 Locations of FAT sectors
File Allocation Table (FAT): Main space allocator, an array of sector numbers grouped into FAT sectors to comprise a chain
Mini FAT: Allocator for the mini stream and small user-defined data

For each sector in a chain, the ID of the next sector is stored up until the last one that contains the ENDOFCHAIN (0xFFFFFFFE) value

**Double-Indirect File Allocation Table (DIFAT):** Stores the locations of FAT
sectors
Directory: Stores metadata for storage and stream objects

stream and storage objects are used in a similar way to files and directories in typical
filesystems.

olebrowse: A pretty basic GUI tool that allows you to browse CFB
documents
oledir: Displays directory entries within CFB files
olemap: Shows all sectors present in the document, including the
header
oleobj: Allows you to extract embedded objects from CFB files
**Rich text format**
human-readable in usual text editors

Control words:  special commands that may have certain states represented by a number. Prepended with \\

\\rtfN: The starting control word that can be found at the
beginning

Delimiters: Mark the end of an RTF control word, space, non alphanumeric symbols, A digit with an optional hyphen (to specify minus)
Control symbols: Consist of a backslash, followed by a non-alphabetic character.
Treated in pretty much the same way as control words.
Groups: Consist of text and control words or symbols specifying associated attributes, all surrounded by curly brackets.

**Office open XML format**
associated with newer Microsoft Office products and is implemented in files with extensions that end with x, such as .docx

all information is stored in Open Packaging Convention (OPC) packages

Content_Types.xml: This file can be found in any document and stores
MIME type information

docProps: Contains several XML files describing certain properties associated with the document

<document_type_specific_directory>: This directory contains the actual
document data

Word - document.xml
Excel - Workbook,xml
PP - presentation.xml
