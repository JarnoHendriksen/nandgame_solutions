# Software

Low level: [Machine code](#machine-code) - [Assembly Language](#assembly) - [Assembler Program](#assembler)  
Stack machine: [Init stack](#init-stack) - [Push D](#push-d) - [Pop D](#pop-d) - [Pop A](#pop-a) - [Push Value](#push-value) - [Push Static](#push-static) - [Pop Static](#pop-static) - [Push Memory](#push-memory) - [Pop Memory](#pop-memory)  
Jumps: [Goto](#goto) - [If-goto](#if-goto)  
Function calls: [Call](#call) - [Function](#function) - [Return](#return) - [Push argument](#push-argument) - [Pop argument](#pop-argument) - [add](#add) - [sub](#sub) - [negate](#negate) - [getChar](#getchar) - [putChar](#putchar)

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

## Stack machine

### Shared constants

These constants are accessible in all subsequent software levels.

| Name | Number |
| ---- | ------ |
| SP   | 0      |
| ARGS | 1      |
| LOCS | 2      |
| RVAL | 6      |
| TEMP | 10     |

<a name="init-stack"></a>

### Init stack

```Python
# Store the value 255
# (hex 100) in register D
A = 0x100
D = A

# Store the content of D in RAM,
# at the address given by SP (0)
A = SP
*A = D
```

<a name="push-d"></a>

### Push D

```Python
# Get the current location of the stack pointer
# (i.e. the value stored at address SP)
A = SP
A = *A
*A = D

# Increment the stack pointer
A = SP
D = *A
*A = D+1
```

<a name="pop-d"></a>

### Pop D

```Python
# Decrement the stack pointer
A = SP
D = *A - 1
*A = D

# Store the value at the current
# position of the stack pointer in D
A = SP
A = *A
D = *A
```

<a name="pop-a"></a>

### Pop A

```Python
# Store the old value of D on stack
push.D

# Decrease stack pointer by 2
A = SP
D = *A - 1
*A = D
A = SP
D = *A - 1
*A = D

# Restore D by getting the value at SP+1
A = SP
D = *A
A = D + 1
D = *A

# Store the value at SP in A
# (w/o touching D)
A = SP
A = *A
A = *A
```

<a name="push-value"></a>

### Push Value

```Python
A = value
D = A
push.D
```

<a name="push-static"></a>

### Push Static

```Python
A = address
D = *A
push.D
```

<a name="pop-static"></a>

### Pop Static

```Python
pop.D
A = address
*A = D
```

<a name="push-memory"></a>

### Push Memory

```Python
pop.A
D = *A
push.D
```

<a name="pop-memory"></a>

### Pop Memory

```Python
pop.D
pop.A
*A = D
```

## Jumps

<a name="goto"></a>

### Goto

```Python
A = label
JMP
```

<a name="if-goto"></a>

### If-goto

```Python
pop.D
A = label
D; JNE
```

## Function calls

<a name="call"></a>

### Call

```Python
# push args and locs
push.static ARGS
push.static LOCS

# push the address of the instruction
# right after the jump to the function
A = restore
D = A
push.D

# Calculate the new address of ARGS (SP - argCount - 3)
A = 0
D = *A
A = argumentCount
D = D-A
A = 3
D = D-A

# Store the address of the first argument in ARGS
A = ARGS
*A = D

# Jump to the function address
A = functionName
JMP

label restore:
# Store ARGS temporarily at address 10 (0xa)
A = ARGS
D = *A
A = TEMP
*A = D

# restore locals
pop.static LOCS

# restore args
pop.static ARGS

# set SP to previous args value
A = TEMP
D = *A
A = SP
*A = D

# push the return value on stack
push.static RVAL
```

<a name="function"></a>

### Function

```Python
label functionName:

# set LOCS to SP
A = SP
D = *A
A = LOCS
*A = D

# allocate space on stack for local storage
A = SP
D = *A
A = localsCount
D = D+A
A = SP
*A = D
```

<a name="return"></a>

### Return

```Python
# Pop the return value off the stack into RVAL
pop.static RVAL

# Set SP back to the value of LOCS
A = LOCS
D = *A
A = SP
*A = D

# Pop the return address off the stack and jump to it
pop.A
JMP
```

<a name="push-argument"></a>

### Push argument

```Python
# Calculate ARGS+index and store in register D
A = ARGS
D = *A
A = index
D = D+A

# Read from the address calculated above,
# and push it onto the stack
A = D
D = *A

push.D
```

<a name="pop-argument"></a>

### Pop argument

```Python
# Pop stack value into TEMP
pop.static TEMP

# Get the address of ARGS
A = ARGS
D = *A

# Add index to ARGS
A = index
D = D+A

# Push the new address onto the stack
push.D

# Push the value in TEMP onto stack
push.static TEMP

# Pop value and address from stack and move into address
pop.memory
```

<a name="add"></a>

### Add

```Python
function add 0
    # Push the arguments onto the stack
    push.argument 0
    push.argument 1

    # Pop the second argument into D,
    # and the first argument into A
    pop.D
    pop.A

    # Add the values and push onto the stack
    D = D+A

    push.D
return
```

<a name="sub"></a>

### Sub

```Python
function sub 0
    # Push the arguments onto the stack
    push.argument 0
    push.argument 1

    # Pop the second argument into D,
    # and the first argument into A
    pop.D
    pop.A

    # Subtract 1st arg from 2nd arg
    D = A-D

    push.D
return
```

<a name="negate"></a>

### Negate

```Python
function negate 0
    # Push the argument onto the stack
    push.argument 0

    # Pop the argument into D
    pop.D

    # Negate the value and push onto the stack
    D = -D

    push.D
return
```

<a name="getchar"></a>

### getChar

```Python
function getChar 0
    # Wait for key value to become non-zero
    label waitNZ:
    # Push the key value onto the stack
    push.static 0x6000
    # If key pressed (is non-zero), jump out of the loop
    if.goto store
    # Else, continue looping
    A = waitNZ
    D; JMP

    label store:
    # Store key value in TEMP memory address
    A = 0x6000
    D = *A
    A = TEMP
    *A = D

    # Wait for key to be 0 again
    label waitZ:
    push.static 0x6000
    if.goto waitZ
    # If key is 0, push the key code onto stack
    push.static TEMP
return
```

<a name="putchar"></a>

### putChar

```Python
function putChar 0
    # Push the destination address
    # and key value (argument) onto the stack
    push.value 0x6002
    push.argument 0

    # Pop both, and store the value at the given address
    pop.memory
return
```
