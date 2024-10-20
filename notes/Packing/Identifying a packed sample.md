**PE tool static signatures:** Open file in DetectItEasy

**Evaluating PE section names:**
packed files can contain specific section names, such as UPX0, .aspack, .stub

**Stub execution signs**: 
The following signs are an
indication that this is happening:
The entry point is not pointing to the first section (it would mostly be pointing to one of the last two sections) and this section's memory permission is EXECUTE (in
the section's characteristics)
The first section's memory permission will be mostly READWRITE

**Small import table:** Only enough to unpack the file, the rest are loaded dynamically