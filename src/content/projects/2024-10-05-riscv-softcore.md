---
title: "RISC-V Softcore Processor"
description: "A custom 32-bit RISC-V compliant processor core implemented in Verilog with full ISA support and toolchain integration."
date: 2024-10-05
draft: false
tech: ["Verilog", "RISC-V", "Computer Architecture", "GCC Toolchain", "Simulation"]
github: "https://github.com/yourusername/riscv-softcore"
---

# RISC-V Softcore Processor

## Overview
This project implements a fully functional 32-bit RISC-V processor core supporting the RV32IMC instruction set. The core is synthesizable and has been tested on FPGA hardware with real applications running.

## Features
- RV32IMC ISA compliance (Integer, Multiply, Compressed)
- 5-stage pipelined architecture
- Branch prediction with 2-bit saturating counter
- Instruction and data caches (configurable size)
- Interrupt controller with nested interrupt support
- JTAG debug interface

## Architecture

### Pipeline Stages
1. **Instruction Fetch** - PC generation, instruction memory access
2. **Instruction Decode** - Register read, immediate generation
3. **Execute** - ALU operations, address calculation
4. **Memory** - Data memory access
5. **Writeback** - Result write to register file

### Key Modules
```verilog
module riscv_core (
    input wire clk,
    input wire reset,
    output wire [31:0] addr_o,
    inout wire [31:0] data_io,
    output wire we_o,
    output wire re_o
);
```

## Performance Metrics
- Maximum frequency: 100 MHz on Artix-7
- CPI: 1.2 average (with cache hits)
- Resource utilization:
  - LUTs: 4,500
  - FFs: 3,200
  - BRAM: 18 blocks

## Software Toolchain
- Custom GCC cross-compiler based on riscv64-unknown-elf-gcc
- Newlib C library port
- Bare-metal runtime with startup code
- Support for printf, malloc, and standard I/O

## Test Programs
The processor has been validated with:
- CoreMark benchmark (score: 185 @ 100MHz)
- Dhrystone benchmark
- Custom assembly test suites
- FreeRTOS port (in progress)

## Lessons Learned
- Hazard detection unit complexity
- Cache coherence challenges
- Importance of comprehensive testbenches

## Next Steps
- Add floating-point unit (RV32F)
- Implement AXI4 interface for SoC integration
- Port Zephyr RTOS
