# Overview
cpu_top integrates all CPU components
-Program Counter
-Instruction Register
-ALU
-ROM
-Control Unit(FSM)

It implements a Fetch-Decode-Execute instruction cycle

# Inputs and Outputs
Signal   |   Width  |  Description
clk      |     1    | System Clock
rst_n    |     1    | Active-low reset
out_port |   8-bit  | CPU Output

# Internal Registers

Register   |   Purpose
PC         | Holds next instruction address
IR         | Stores fetched instruction
ACC        | Accumulator
ZF         | Zero flag
STATE      | FSM Current state

# CPU Execution Flow
-Fetch
Reads instruction from ROM
Stores in IR
Increment PC

-Decode
Decode opcode
Decide execution path

-Execute
ALU operation
Branch decision
Output write

# Control Unit(FSM)
implemented using a Moore-style FSM
States
-FETCH
-DECODE
-EXEC_ALU
-EXEC_BR
-EXEC_OUT

# Verilog concepts used
