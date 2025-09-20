# Software

Low level: [Machine code](#machine-code) - [Assembly Language](#assembly) - [Assembler Program](#assembler)

## Low level

<a name="machine-code"></a>

### Machine code

| A   | ci  | -   | -   | \*  | -   | u   | op1 | op0 | zx  | sw  | a   | d   | \*a | lt  | eq  | gt  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 1   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1   | 0   | 0   | 1   | 0   | 0   | 0   | 0   |
| 1   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1   | 0   |
| 2   | 1   | 0   | 0   | 0   | 0   | 1   | 0   | 1   | 0   | 0   | 0   | 1   | 0   | 0   | 0   | 0   |
| 3   | 1   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1   | 1   | 1   |

<a name="assembly"></a>

### Assembly Language

#### Destination

| Opcode      | a   | d   | \*a |
| ----------- | --- | --- | --- |
| (blank)     | 0   | 0   | 0   |
| A =         | 1   | 0   | 0   |
| D =         | 0   | 1   | 0   |
| \*A =       | 0   | 0   | 1   |
| A, D =      | 1   | 1   | 0   |
| D, \*A =    | 0   | 1   | 1   |
| A, D, \*A = | 1   | 1   | 1   |

#### Calculation

| Opcode | u   | op1 | op0 | zx  | sw  |
| ------ | --- | --- | --- | --- | --- |
| D+A    | 1   | 0   | 0   | 0   | 0   |
| D-A    | 1   | 1   | 0   | 0   | 0   |
| A-D    | 1   | 1   | 0   | 0   | 1   |
| D+1    | 1   | 0   | 1   | 0   | 0   |
| A+1    | 1   | 0   | 1   | 0   | 1   |
| D-1    | 1   | 1   | 1   | 0   | 0   |
| A-1    | 1   | 1   | 1   | 0   | 1   |
| -D     | 1   | 1   | 0   | 1   | 1   |
| -A     | 1   | 1   | 0   | 1   | 0   |
| -1     | 1   | 1   | 1   | 1   | 0   |
| 1      | 1   | 0   | 1   | 1   | 0   |
| D      | 1   | 0   | 0   | 1   | 1   |
| A      | 1   | 0   | 0   | 1   | 0   |
| D&A    | 0   | 0   | 0   | 0   | 0   |
| D\|A   | 0   | 0   | 1   | 0   | 0   |
| ~D     | 0   | 1   | 1   | 0   | 0   |
| ~A     | 0   | 1   | 1   | 0   | 1   |
| 0      | 0   | 0   | 0   | 1   | 0   |

#### Jump-Condition

| Opcode  | lt  | eq  | gt  |
| ------- | --- | --- | --- |
| (blank) | 0   | 0   | 0   |
| ; JLT   | 1   | 0   | 0   |
| ; JEQ   | 0   | 1   | 0   |
| ; JGT   | 0   | 0   | 1   |
| ; JLE   | 1   | 1   | 0   |
| ; JGE   | 0   | 1   | 1   |
| ; JMP   | 1   | 1   | 1   |

<a name="assembler"></a>

### Assembler Program

```Python
# Set the value at the lamp's
# address to 1 to turn bit 0 on
A = 0x7FFF
*A = 1

# Set the value to 2 to turn
# bit 0 off, and bit 1 on
*A = *A + 1

# Jump to the first instruction
# to make the program loop indefinitely
A = 0
JMP
```
