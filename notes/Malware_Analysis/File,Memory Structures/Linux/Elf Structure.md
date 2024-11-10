Supports 32 and 64 bit address sizes
Supports Endianness

**e_ident:** This is a set of bytes responsible for ELF identification. Not required and ==can only give a clue on target OS==
**e_type:** defines the type of the file
**e_machine:** specifies target platform
**e_entry:** Entry point of the sample
**e_phoff**: Offset of the program header, give the system enough information to load the file to
memory when creating the process
**e_shoff**: offset of the section header, section header contains information about each section, which includes its name, type, attributes, virtual address, offset, and size

makes sense to pay
attention to the code section (usually,this is .text), as well as the section containing strings
(such as .rodata) as they can give plenty of information about malware's purposes