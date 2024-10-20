**Sysenter hooking**
When sysenter is called the processor switches to kernel mode specifically to a address stored in Model Specific Register (MSR).

MSR 0x176 (IA32_SYSENTER_EIP):
MSR 0x175 (IA32_SYSENTER_ESP):
MSR 0x174 (IA32_SYSENTER_CS):

These registers can be read and modified using rdmsr and wrmsr assembly instructions

wrmsr takes the register ID in ecx and the value to write in the edx:eax pair

only one processor is being
hooked. This means that the attacker has to create multiple threads,

**SSDT Hooking**
When a user-mode application uses sysenter, as you saw in Figure 3, the application provides the function number or ID in the eax register. This value in eax is divided in the
following way:
![[Pasted image 20240827235838.png]]
bits 0-11: This is the System Service Number (SSN), which is the index of this function in the SSDT
bits 12-13: This is the Service Descriptor Table (SDT), which represents the SSDT number
KeServiceDescriptorTable is 0x00,
and KeServiceDescriptorTableShadow is 0x01)

KiServiceTable: This is the array of function addresses to represent each ID that is passed to eax before sysenter.

For malware to hook this table, it needs to get the KeServiceDescriptorTable

For malware to hook this table, it needs to get the KeServiceDescriptorTable that's
exported by ntoskrnl.exe, and then move to KiServiceTable and modify the function that it wants to hook. To be able to modify this table, it needs to disable the write protection

There are multiple ways to do this, and the most common way
is by modifying the CR0 register value and setting the write-protection bit to zero:

PUSH EBX
MOV EBX, CR0
OR EBX, 0x00010000
MOV CR0,EBX
POP EBX

Microsoft implemented multiple protections to stop SSDT hooking, such as PatchGuard

Since KeServiceDescriptorTable is not exported, malware families started to search for
functions that used this table in order to gain access to the addresses. One of the functions
they used was KiSystemServiceRepeat.

**Hooking SSDT functions**
similar to API hooking. In this case, malware gets the
function from the SSDT using the function ID and patches the first few bytes with jmp

**IRP hooking**
For any driver to be able to receive and handle IRP requests, it is necessary to create a
device object. This device can be attached to a chain of device drivers that process a specific
type of IRP request

Creating a device object is simple: the driver can simply call the IoCreateDevice API and
provide the flags corresponding to the device it wants to attach to.

For the rootkit to attach to a named device (for example, \\FileSystem\\fastfat, to
receive filesystem requests), it needs to get the device object for that named device. There
are multiple ways to do this, and one of them is to use the
undocumented ObReferenceObjectByName API.

Once the device object is found, the
rootkit can use the IoAttachDeviceToDeviceStack API to attach to its chain of drivers
and receive the IRP requests that are sent to it.

After executing the IoAttachDeviceToDeviceStack API, the driver will be added to the
top of the chain, which means that the rootkit driver will be the first driver to receive the
IRP requests. Then, it can pass requests along to the next driver using the IoCallDriver
API.

Additionally, the rootkit would be the last driver to modify the response of the IRP
request after setting a completion routine.

To copy these parameters to the next driver's stack, the rootkit can use the IoCopyCurrentIrpStackLocationToNext API.

Once all the parameters are copied for the next driver, malware can set the completion routine using IoSetCompletionRoutine, and then pass this request to the next driver
using IoCallDriver.

Once the last driver in the chain executes the IoCompleteRequest API, the completion
routines will be executed one by one