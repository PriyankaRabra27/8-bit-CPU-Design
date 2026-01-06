# Overview
The ROM stores the program executed by CPU.
Each memory location contains a 16-bit instruction.

# Inputs and Outputs

Signal   |   Width   |  Description
addr     | 8-bit     | Program Counter
data     | 16-bit    | Instruction Output

# Logical Concept

ROM is implemented using a case statement.
For each address, a fixed instruction is returned.
The CPU reads one instruction per clock cycle during FETCH.

# Verilog Concepts used

always@(*) for combinational memory
case(addr) for address decoding
Constant instruction encoding

# Why ROM instead of RAM

Program does not change during execution
Simpler and synthesizable
Ideal for small CPUs and learning architecture

