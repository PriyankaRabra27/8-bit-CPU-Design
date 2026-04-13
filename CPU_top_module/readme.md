## Overview
The `cpu_top` module is the main module of the CPU.  
It connects the **ROM**, **ALU**, and internal registers, and controls the overall instruction execution flow.

This module is responsible for:
- fetching instructions from ROM
- decoding the instruction opcode
- controlling ALU operations
- executing branch and output instructions
- updating registers such as **PC**, **IR**, **ACC**, and **ZF**

## Inputs and Outputs

| Signal     | Width | Description |
|------------|------:|-------------|
| `clk`      | 1-bit | System clock |
| `rst_n`    | 1-bit | Active-low reset |
| `out_port` | 8-bit | Output port of the CPU |

## Internal Registers

| Register | Width | Description |
|----------|------:|-------------|
| `pc`     | 8-bit | Program Counter, stores address of next instruction |
| `ir`     | 16-bit | Instruction Register, stores current instruction |
| `acc`    | 8-bit | Accumulator, main working register |
| `zf`     | 1-bit | Zero Flag, set when ALU result is zero |
| `state`  | 3-bit | Current FSM state |
| `next_state` | 3-bit | Next FSM state |

## Functional Role
The `cpu_top` module coordinates the complete **fetch-decode-execute cycle** of the CPU.

### 1. Fetch
- ROM is addressed using `pc`
- instruction is loaded into `ir`
- `pc` is incremented

### 2. Decode
- opcode is extracted from `ir[15:12]`
- immediate value or branch address is extracted from `ir[7:0]`
- next execution state is selected based on opcode

### 3. Execute
Depending on the instruction:
- ALU instructions update `acc` and `zf`
- branch instructions update `pc`
- `OUT` instruction updates `out_port`

## FSM States

| State | Description |
|-------|-------------|
| `S_FETCH`    | Fetch instruction from ROM and increment PC |
| `S_DECODE`   | Decode opcode and choose execution path |
| `S_EXEC_ALU` | Execute ALU instruction and update ACC/ZF |
| `S_EXEC_BR`  | Execute branch instruction (`JMP` / `JZ`) |
| `S_EXEC_OUT` | Copy ACC value to output port |

## Instruction Decoding
The instruction stored in `ir` is divided as follows:

- `ir[15:12]` → Opcode
- `ir[11:8]`  → Reserved
- `ir[7:0]`   → Immediate value / branch address

The opcode determines whether the CPU will execute:
- an ALU instruction
- a branch instruction
- an output instruction
- or a NOP

## ALU Coordination
The CPU generates the control signal `alu_sel` based on the opcode.  
This control signal selects the required ALU operation such as:
- `LOAD`
- `ADD`
- `SUB`
- `AND`
- `OR`

The ALU takes:
- `acc` as input `a`
- `imm` as input `b`

and produces:
- `alu_y` as result
- `alu_z` as zero flag output

These are used to update `acc` and `zf` during `S_EXEC_ALU`.

## Branch Execution
Branch instructions are handled in the `S_EXEC_BR` state.

- `JMP` loads `pc` with the target address unconditionally
- `JZ` loads `pc` with the target address only if `zf = 1`

This allows the CPU to change the normal sequential program flow.

## Verilog Concepts Used
- sequential logic using `always @(posedge clk)`
- combinational next-state logic using `always @(*)`
- FSM implementation using state encoding
- opcode decoding using bit slicing
- module instantiation for ROM and ALU
- non-blocking assignments for register updates
- case statements for control logic

## Why This Module Is Important
The `cpu_top` module acts as the central coordinator of the CPU.  
It combines both:
- **control logic**, which decides what operation should happen
- **datapath behavior**, which updates registers and moves data

This module is the core of the processor design.
