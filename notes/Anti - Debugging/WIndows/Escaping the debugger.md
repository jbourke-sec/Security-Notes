Process injection/hollowing

**TLS callbacks**
Some malware families use Thread Local Storage (TLS) to ==execute code that initializes every thread== (which runs before the thread's actual code starts).

In a data directory block of the PE header, there is an entry for TLS. It is commonly stored in the ==\.tls section==

The ==AddressOfCallBacks== points to a null-terminated array (the last element is zero) of callback functions, which are to be called after each other, each time a thread is created

Set a BP for AddressOfCallBacks

**Windows events callbacks**
Callbacks are each called for a specific event like a
mouse click,

If you are single stepping
over the malware instructions, the callback would still be executed without you noticing

There are so many ways to set callback functions.

**RegisterClass API**: The RegisterClass API creates a window
class that can be used to create a window

The ==WNDCLASSA structure passed as an arg to RegisterClass== contains all the necessary information related to this window, including the icon, the cursor icon,
the style, and most importantly the callback function to receive window
events. The code looks as follows:

**SetWindowLong API**: 
you have the window handle (from ==EnumWindows== or ==FindWindow ==or other APIs), you can call the SetWindowLong API to change the
window callback function

**Prevention:** Set BPs for any function that can set a function along with Dynamic loading functions

