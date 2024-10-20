Starting the program:
Creating the process data structures: Windows then creates the process data structure in the kernel (which is called EProcess)
Initialize the virtual memory: Then, Windows creates the process, virtual
memory and its representation of the physical memory and saves it inside the EProcess structure, creates the PEB structure with all necessary information, and then loads the main two DLLs that Windows applications will always need,
which are ntdll.dll and kernel32.dll
Loading the PE file: After that, Windows starts loading the PE file (which we will explain next), loading all the required third-party libraries (DLLs), including
all DLLs these libraries require, and makes sure to find the required APIs from these libraries and save their addresses in the import table
