Rootkit samples are usually drivers that implement the traditional MZ-PE structure

any tool (excluding user-mode debuggers such as OllyDbg)
supporting them should handle rootkits without any major problems

Once the sample is open, the first step is to track down the DriverObject, which is
provided as the first argument of the main function (through the stack for 32-bit systems
and through the rcx register for 64-bit systems)

it is worth checking whether any completion routine is specified using
the IoSetCompletionRoutine API.

we need to search for the presence of instructions that allow us to disable security measures such as the previously mentioned write protection, which involves using the CR0 register.

Are there any devices malware attaches to? Is there any process or filename mentioned there?