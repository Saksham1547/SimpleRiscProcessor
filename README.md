# SimpleRISC Processor

## Overview
This project implements a SimpleRISC Processor using Verilog. The processor is designed to execute a subset of RISC instructions and includes various modules for instruction fetching, decoding, execution, memory access, and write-back stages. The design is modular, making it easy to understand and extend.

## Project Structure
The project is organized into the following files and modules:

### Core Modules
- **SimpleRiscProcessor.v**: The top-level module that integrates all components of the processor.
- **ControlUnit.v**: Handles the control signals for the processor.
- **ALU.v**: Performs arithmetic and logical operations.
- **RegisterFile.v**: Implements the register file for the processor.
- **RegisterFilesAccess.v**: Handles access to register files.
- **InstructionMemory.v**: Stores the program instructions.
- **InstructionFetch.v**: Fetches instructions from memory.
- **DataMemory.v**: Handles data storage and retrieval.

### Supporting Modules
- **4BitMux.v**: A 4-bit multiplexer.
- **add.v** / **adder.v**: Modules for addition operations.
- **subtract.v** / **subtractor.v**: Modules for subtraction operations.
- **ALUBlock.v**: Encapsulates ALU functionality.
- **branchPC.v**: Handles branch target address calculation.
- **PC.v** / **PCPlus4.v**: Program counter module and increment logic.
- **mux.v** / **MUX03.v**: Multiplexer modules for data selection.
- **MemoryUnit.v** / **MemoryUnitToMux.v**: Handles memory operations.
- **immx_op1.v** / **immx_op2.v**: Immediate value extraction modules.
- **Immediate_Branch_Target.v**: Calculates branch target addresses.

### Testing Module
- **TestBench.v**: Contains the testbench for simulating and verifying the processor's functionality.

## How to Run

### 1. Compile the Project
Run the following command in PowerShell:
```
iverilog -o cpu_sim 4BitMux.v add.v adder.v ALU.v ALUBlock.v branchPC.v ControlUnit.v DataMemory.v Immediate_Branch_Target.v immx_op1.v immx_op2.v InstructionFetch.v InstructionMemory.v MemoryUnit.v MemoryUnitToMux.v mux.v MUX03.v PC.v PCPlus4.v RegisterFile.v RegisterFilesAccess.v SimpleRiscProcessor.v sub.v subtractor.v TestBench.v ToRegisterFile.v
```

### 2. Run the Simulation
The output file will be saved as "cpu_sim". Run the following command to simulate:
```
vvp cpu_sim
```

### 3. View Waveforms (Optional)
If you want to view the waveforms, you can use GTKWave:
```
gtkwave cpu.vcd
```

## Features
- Modular design for easy understanding and extension
- Implements a subset of RISC instructions
- Includes a testbench for simulation and verification
- Supports arithmetic operations, memory access, and branching
- Pipeline stages for improved performance

## Architecture
The SimpleRISC processor follows a classic RISC architecture with the following stages:
1. Instruction Fetch (IF)
2. Instruction Decode (ID)
3. Execute (EX)
4. Memory Access (MEM)
5. Write Back (WB)

## Instruction Set
The processor supports a subset of RISC instructions including:
- Arithmetic operations (add, subtract)
- Logical operations
- Memory operations (load, store)
- Branch operations

## Future Work
- Implementing additional instructions
- Adding pipeline hazard detection and resolution
- Performance optimizations
- Integration with I/O interfaces
