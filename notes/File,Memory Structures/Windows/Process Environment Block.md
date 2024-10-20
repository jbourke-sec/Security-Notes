typedef struct _PEB { BYTE Reserved1[2]; BYTE BeingDebugged; BYTE Reserved2[1]; PVOID Reserved3[2]; PPEB_LDR_DATA Ldr; PRTL_USER_PROCESS_PARAMETERS ProcessParameters; PVOID Reserved4[3]; PVOID AtlThunkSListPtr; PVOID Reserved5; ULONG Reserved6; PVOID Reserved7; ULONG Reserved8; ULONG AtlThunkSListPtr32; PVOID Reserved9[45]; BYTE Reserved10[96]; PPS_POST_PROCESS_INIT_ROUTINE PostProcessInitRoutine; BYTE Reserved11[128]; PVOID Reserved12[1]; ULONG SessionId; } PEB, *PPEB;

`Ldr`

A pointer to a [PEB_LDR_DATA](https://learn.microsoft.com/en-us/windows/desktop/api/winternl/ns-winternl-peb_ldr_data) structure that contains information about the loaded modules for the process.

`ProcessParameters`

A pointer to an [RTL_USER_PROCESS_PARAMETERS](https://learn.microsoft.com/en-us/windows/desktop/api/winternl/ns-winternl-rtl_user_process_parameters) structure that contains process parameter information such as the command line.

