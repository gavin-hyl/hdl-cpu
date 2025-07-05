# Caltech-10 CPU

A complete 8-bit microprocessor implementation in ABEL (Advanced Boolean Expression Language).

## Overview

The Caltech-10 is a custom 8-bit CPU designed as a platform for learning computer architecture and digital systems design. This project implements a fully functional and tested processor with arithmetic, logic, control, and memory management capabilities.

## Architecture

### System Specifications
- **Data Width**: 8-bit data bus, 16-bit instruction words
- **Program Memory**: 13-bit address space (8KB)
- **Data Memory**: 8-bit address space (256 bytes)
- **Registers**: 8-bit Accumulator, X register, S register
- **Flags**: Carry, Overflow, Sign, Zero flags

### Memory Map
- **Program Address Bus**: 13 bits (0x0000 - 0x1FFF)
- **Data Address Bus**: 8 bits (0x00 - 0xFF)
- **I/O Support**: Memory-mapped I/O capability

## CPU Components

### 1. Arithmetic Logic Unit (ALU)
**File**: `ALU.abl`

The ALU performs all computational operations:
- **Arithmetic**: Addition, subtraction with carry/borrow
- **Logic**: AND, OR, XOR, NOT operations
- **Shift/Rotate**: Left/right shifts and rotates (arithmetic and logical)
- **Flag Management**: Automatic flag computation and conditional flag updates

### 2. Control Unit (CU)
**File**: `CU.abl`

The control unit orchestrates CPU operation:
- **Instruction Decoding**: 16-bit instruction register and decoder
- **State Machine**: Multi-cycle instruction support (CALL/RTS)
- **Control Signals**: Generates all control signals for other units
- **Conditional Execution**: Branch and conditional instruction support

### 3. Program Address Unit (PAU)
**File**: `PAU.abl`

Manages program flow and addressing:
- **Program Counter**: 13-bit PC with increment/hold capability
- **Jump Operations**: Direct and relative addressing modes
- **Subroutines**: Call and return stack operations
- **Address Generation**: Flexible program address computation

### 4. Data Access Unit (DAU)
**File**: `DAU.abl`

Handles data memory operations:
- **Addressing Modes**: Direct, indexed, and stack addressing
- **Register Management**: X and S register operations
- **Memory Interface**: Data address generation and register updates
- **Pre/Post Operations**: Increment/decrement addressing

### 5. CPU Template
**File**: `CPUTemplate.abl`

Top-level integration module:
- **Component Instantiation**: Connects all major units
- **Bus Management**: Handles data routing between components
- **I/O Interface**: External memory and I/O connections
- **Signal Routing**: Interconnects all control and data paths

## Key Features

### Instruction Set Architecture
- **Load/Store**: Memory and register operations
- **Arithmetic**: ADD, SUB with multiple addressing modes
- **Logic**: Bitwise operations (AND, OR, XOR, NOT)
- **Shift/Rotate**: Complete set of shift and rotate instructions
- **Branches**: Conditional and unconditional jumps
- **Subroutines**: CALL and RTS instructions
- **I/O**: Memory-mapped I/O operations

### Advanced Features
- **Multi-cycle Instructions**: Complex operations span multiple clock cycles
- **Flag Masking**: Selective flag updates for specific operations
- **Flexible Addressing**: Multiple addressing modes for versatile programming
- **Stack Operations**: Built-in stack pointer and operations
- **Interrupt Capability**: Flag register supports interrupt handling

## File Structure

```
caltech-ee10a/
├── README.md           # This file
├── CPUTemplate.abl     # Top-level CPU module
├── ALU.abl            # Arithmetic Logic Unit
├── CU.abl             # Control Unit
├── PAU.abl            # Program Address Unit
├── DAU.abl            # Data Access Unit
└── instructions.xlsx   # Instruction set documentation
```

## Technical Details

### Clock and Reset
- **Synchronous Design**: All operations synchronized to system clock
- **Active-Low Reset**: System reset initializes all registers and state
- **Pipeline Considerations**: Multi-cycle instructions properly handle timing

### Data Flow
1. **Instruction Fetch**: Program memory → Instruction Register
2. **Decode**: Control Unit generates all control signals
3. **Execute**: ALU/Memory operations performed
4. **Write-back**: Results stored in registers/memory

### Control Signals
The CPU uses extensive control signaling:
- **ALU Control**: Operation selection, flag management
- **Memory Control**: Read/write, address selection
- **Register Control**: Load/hold, multiplexer selection
- **Flow Control**: Jump conditions, state machine control

## Development Notes

This implementation demonstrates several important concepts:
- **Modular Design**: Each major component in separate files
- **Hierarchical Architecture**: Clear separation of concerns
- **Parameterized Components**: Flexible bit widths and configurations
- **Comprehensive Testing**: Full instruction set verification with 762 tests

---

*This project represents a significant undertaking in digital systems design, providing hands-on experience with all aspects of CPU architecture and implementation.* 
