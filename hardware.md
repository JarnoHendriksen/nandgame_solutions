# Hardware

-   [Logic gates](#logic-gates)
    -   [Nand](#nand-gate)
    -   [Invert](#inverter)
    -   [And](#and-gate)
    -   [Or](#or-gate)
    -   [Xor](#xor-gate)
-   [Arithmetics](#arithmetics)
    -   [Half Adder](#half-adder)
    -   [Full Adder](#full-adder)
    -   [Multi-Bit Adder](#multi-bit-adder)
    -   [Increment](#increment)
    -   [Subtraction](#subtraction)
    -   [Equal to Zero](#equal-zero)
    -   [Less than Zero](#less-zero)
-   [Switching](#switching)
    -   [Selector](#selector)
    -   [Switch](#switch)

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

<a name="half-adder"></a>

### Half Adder

![Half adder containing four NAND gates and an inverter. The NAND gates are arranged like an XOR gate. The output of this is used for the low bit. The output of gate 1 is inverted, and used for the high bit.](Solutions/Hardware/Arithmetics/HalfAdder.png)

<a name="full-adder"></a>

### Full Adder

![Full adder](Solutions/Hardware/Arithmetics/FullAdder.png)

<a name="multi-bit-adder"></a>

### Multi-bit Adder

![Multi-bit adder](Solutions/Hardware/Arithmetics/MultiBitAdder.png)

<a name="increment"></a>

### Increment

![Increment](Solutions/Hardware/Arithmetics/Increment.png)

<a name="subtraction"></a>

### Subtraction

![Subtraction](Solutions/Hardware/Arithmetics/Subtraction.png)

<a name="equal-zero"></a>

### Equal to Zero

![](Solutions/Hardware/Arithmetics/EqualToZero.png)

<a name="less-zero"></a>

### Less than Zero

![](Solutions/Hardware/Arithmetics/LessThanZero.png)

<a name="switching"></a>

## Switching

<a name="selector"></a>

### Selector

![](Solutions/Hardware/Switching/Selector.png)

<a name="switch"></a>

### Switch

![](Solutions/Hardware/Switching/Switch.png)
