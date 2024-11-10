![[Pasted image 20240915124144.png]]

![[Pasted image 20240915124308.png]]

![[Pasted image 20240915124410.png]]

![[Pasted image 20240915124617.png]]

`CMP` subtracts the operands and sets the flags. Namely, it sets the zero flag if the difference is zero (operands are equal).

`TEST` sets the zero flag, `ZF`, when the result of the AND operation is zero. If two operands are equal, their bitwise AND is zero when both are zero. `TEST` also sets the sign flag, `SF`, when the most significant bit is set in the result, and the parity flag, `PF`, when the number of set bits is even.