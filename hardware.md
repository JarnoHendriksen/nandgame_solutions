# Hardware

-   [Logic gates](#logic-gates)
    -   [Nand](#nand-gate)
    -   [Invert](#inverter)
    -   [And](#and-gate)
    -   [Or](#or-gate)
    -   [Xor](#xor-gate)
-   [Arithmetics](#arithmetics)

<a name="logic-gates"></a>

## Logic gates

<a name="nand-gate"></a>

### Nand

![NAND gate consisting of two default-on relays. The first relay takes the inputs A and B, and the second relay takes the output of the first one as control, and the constant 1 as input.](Solutions/Hardware/LogicGates/Nand.png)

<a name="inverter"></a>

### Invert

![Inverter consisting of a NAND gate, with both input terminals hooked up to the single input value.](Solutions/Hardware/LogicGates/Invert.png)

<a name="and-gate"></a>

### And

![AND gate consisting of a NAND gate followed by an inverter.](Solutions/Hardware/LogicGates/And.png)

<a name="or-gate"></a>

### Or

![OR gate consisting of a NAND gate, with both inputs inverted.](Solutions/Hardware/LogicGates/Or.png)

<a name="xor-gate"></a>

### Xor

![XOR gate consisting of 4 NAND gates. Gate 1 takes the inputs A and B. Gate 2 takes A and the output of gate 1. Gate 3 takes B and the output of gate 1. Gate 4 takes the outputs of gates 3 and 4.](Solutions/Hardware/LogicGates//Xor.png)

<a name="arithmetics"></a>

## Arithmetics

### Half Adder

![Half adder containing four NAND gates and an inverter. The NAND gates are arranged like an XOR gate. The output of this is used for the low bit. The output of gate 1 is inverted, and used for the high bit.](Solutions/Hardware/Arithmetics/HalfAdder.png)

### Full Adder

![Full adder](Solutions/Hardware/Arithmetics/FullAdder.png)

### Multi-bit Adder

![Multi-bit adder](Solutions/Hardware/Arithmetics/MultiBitAdder.png)

### Increment

![Increment](Solutions/Hardware/Arithmetics/Increment.png)

### Subtraction

![Subtraction](Solutions/Hardware/Arithmetics/Subtraction.png)

### Equal to Zero

![](Solutions/Hardware/Arithmetics/EqualToZero.png)

### Less than Zero

![](Solutions/Hardware/Arithmetics/LessThanZero.png)
