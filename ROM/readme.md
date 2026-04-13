# Overview
The ROM stores the program executed by CPU.
Each memory location contains a **16-bit instruction**.

## Inputs and Outputs

| Signal | Width | Description |
|--------|------:|-------------|
| `addr` | 8-bit | Address input from the Program Counter (PC) |
| `data` | 16-bit | Instruction output from ROM |

## Current Program Stored in ROM

| Address | Instruction |
|--------:|-------------|
| `0x00` | `LOAD 1` |
| `0x01` | `OUT` |
| `0x02` | `ADD 1` |
| `0x03` | `OUT` |
| `0x04` | `JMP 1` |


## Logical Concept

ROM is implemented using a `case` statement.
For each address, a fixed 16-bit instruction is returned.

During the **FETCH** state, the CPU uses the Program Counter to provide the ROM address, and the corresponding instruction is read from ROM and loaded into the Instruction Register.

## Verilog Concepts used

- always@(*) for combinational memory
- case(addr) for address decoding
- Constant instruction encoding using concatenation

## Why ROM instead of RAM
- Program does not change during execution
- Simpler and synthesizable
- Ideal for small CPUs and learning architecture
- It is suitable for storing a fixed demo program.

