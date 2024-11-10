**Common P code instructions**

**Data storage and movement:**
==LitStr/LitVarStr==: Initializes a string
LitI2/LitI4/...: Pushes an integer value to the stack (often
used to pass arguments)
==FMemLdI2/FMemLdRf/...:== Loads values of a particular type
(memory)
==Ary1StI2/Ary1StI4/...:== Puts values of a particular type into an
array
==Ary1LdI2/Ary1LdI4/...:== Loads values of a particular type from
an array
==FStI2/FStI4/...:== Puts a variable value into the stack
==FLdI2/FLdI4/...:== Loads a value into a variable from the stack
==FFreeStr:== Frees a string
==ConcatStr:== Concatenates a string
==NewIfNullPr:== Allocates space if null

**Arithmetic operations:**
==AddI2/AddI4/...==: Adding operation
==SubI2/SubI4/..==.: Subtraction operation
==MulI2/MulI4/...==: Multiplication operation
DivR8: Division operation
OrI4/XorI4/AndI4/NotI4/...: Logical operations
Comparison:
EqI2/EqI4/EqStr/...: Check if equal
NeI2/NeI4/NeStr/...: Check if not equal
GtI2/GtI4/...: Check if greater than
LeI2/LeI4/...: Check if less or equal than

**Control flow:**
==VCallHresult/VCallAd(VCallI4)/...==: Calls a function
==ImpAdCallI2/ImpAdCallI4/...==: Calls an import function (API)
==Branch/BranchF== - Branch/Branch if False: Branches when
the condition is me

Here are the most common abbreviations used in opcode names:

Ad: Address
Rf: Reference
Lit: Literal
Pr: Pointer
Imp: Import
Ld: Load
St: Store
C: Cast
DOC: Duplicate opcode