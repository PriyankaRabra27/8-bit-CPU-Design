# 8-bit-CPU-Design

## Overview
This project implements a simple Accumulator-based 8-bit CPU designed from scratch using Verilog.
The project focuses on digital design fundamentals and Verilog HDL modeling, including combinational logic, sequential logic, finite state machines, and ROM-based program execution.
The CPU follows a simple fetch–decode–execute cycle and executes a small program stored in instruction ROM.
The design is modular, synthesizable, and suitable for simulation or FPGA demonstration.

## Features
- 8-bit data path
- 16 bit instruction format(opcode + imm/addr
- FSM based Control Unit
- ROM based program memory
- Synthesizable Verilog HDL
- Beginner friendly, modular design

## CPU Architecture
The CPU is Accumulator-based and consists of following main blocks:
- Program Counter(PC): holds address of next instruction
- Instruction ROM: stores program instruction
- Instruction Register(IR): holds fetched instruction
- Accumulator(ACC): primary working register
- ALU: arithmatic and logic unit
- Zero Flag(Z): set when ALU result is 0
- Output Register(OUT): drives external outputs
- Control Unit(FSM): controls fetch, decode, execute


## Learning Outcomes
- Understanding CPU Datapath and control
- FSM based control unit design
- Verilog HDL
- ROM based program execution and verification

