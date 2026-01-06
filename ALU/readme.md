# Overview

ALU is the core component of CPU. It performs arithematic and logical operations on 8-bit data based on a control signal provided by Control Unit.

# Inputs and Outputs

Signal   |   Width   |  Description
a          8-bit       Accumulator input
b          8-bit       Immediate value
sel        3-bit       ALU operation select
y          8-bit       ALU result
z          1-bit       Zero flag(1 if result is 0)

# Operations

sel    |   operation
000      Pass B(LOAD)
001      ADD
010      SUB
011      AND
100      OR

# Logical Concept
ALU uses a MUX-like Case statements to select an operation.
The result is stored in y.
The zero flag z is asserted when y == 0, enabling conditional branching(JZ).

# Verilog Concepts used

always@(*) for combinational logic
Case statements for operation selection
Continuous assignment for zero flag
