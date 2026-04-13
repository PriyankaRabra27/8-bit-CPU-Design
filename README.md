# 8 bit CPU design in Verilog

A simple **8-bit accumulator-based CPU** design in **Verilog HDL to demonstrate the fundamentals of processor architecture, including the **fetch-decode-execute cycle**, **ALU operations**, **program counter control**, **instruction decoding**, and **branching**.

## Overview
This project implements a basic 8-bit CPU with a small custom instruction set. The design is modular and includes seperate Verilog modules for **ALU**, **ROM**, **CPU top module**, alond with a **testbench** for simulation.
The CPU is controlled using a **finite state machine** and executes instructions stored in ROM. It supports arithematic, logic, output and branch operations.

## Features
- 8-bit accumulator-based CPU.
- 16-bit instruction format
- FSM-based control unit
- Seperate ALU and ROM modules
- Supports Arithematic and logic instructions
- Supoorts conditional and unconditional branching
- Verified through simulation using testbench

## Architecture
Following are the main blocks in CPU:-
- **Program Counter** -holds the address of next instruction
- **Instruction Register** - stores the current instruction
- **Accumulator** - main working register
- **Zero Flag** - indicates whether ALU result is 0
- **ROM** - stores the instruction program
- **ALU** - performs arithematic and logic operations.
- **Output port** - stores the value sent by the 'OUT' instructions.

## Instruction format
Each instruction is **16 bits wide**:
- `IR[15:12]` → Opcode
- `IR[11:8]`  → Reserved
- `IR[7:0]`   → Immediate data / branch address

## Supported Instructions

| Opcode | Instruction | Description |
|--------|-------------|-------------|
| `0x0` | NOP  | No operation |
| `0x1` | LOAD | Load immediate value into ACC |
| `0x2` | ADD  | Add immediate value to ACC |
| `0x3` | SUB  | Subtract immediate value from ACC |
| `0x4` | AND  | Bitwise AND with ACC |
| `0x5` | OR   | Bitwise OR with ACC |
| `0x6` | JMP  | Unconditional jump |
| `0x7` | JZ   | Jump if Zero Flag is set |
| `0x8` | OUT  | Send ACC to output port |

## FSM Operation

The CPU operates using the following states:

- **FETCH** – fetch instruction from ROM using PC and load it into IR
- **DECODE** – decode opcode and determine instruction type
- **EXEC_ALU** – execute arithmetic/logic instruction
- **EXEC_BR** – execute branch instruction (`JMP` / `JZ`)
- **EXEC_OUT** – update output port with ACC value

## Project Structure

```text
8-bit-CPU-Design/
├── ALU/
├── CPU_top_module/
├── ROM/
├── simulation/
├── testbench/
├── LICENSE
└── README.md
