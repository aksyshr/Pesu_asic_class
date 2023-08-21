# VLSI Physical Design for ASICs

## Objective

The objective of VLSI physical design for ASICs is to convert a logical RTL design into a physical layout suitable for fabrication. This process ensures the circuit's functionality aligns with design constraints, performance goals, and manufacturing standards.

## Skill Outcomes

Participants in this course will gain expertise in the following areas:

- **Architectural Design**: Understanding the overall structure and organization of integrated circuits.
- **RTL Design / Behavioral Modeling**: Creating a Register Transfer Level (RTL) description of a digital circuit's behavior.
- **Floorplanning**: The initial phase of physical design where the locations of major components are planned.
- **Placement**: Determining the precise locations of cells or modules on the chip.
- **Clock Tree Synthesis**: Building a clock distribution network to ensure synchronous operation.
- **Routing**: Establishing interconnections between different parts of the design.

## Installation

To get started with the VLSI Physical Design for ASICs workshop, follow these steps:

1. Download the `run.sh` script from the [GitHub repository](https://github.com/kunalg123/riscv_workshop_collaterals/blob/master/run.sh).

2. Open a terminal on your system.

3. Navigate to the directory where you downloaded the `run.sh` script. For example, if it's in your Downloads folder, use the following command:

    ```sh
    cd Downloads
    ```

4. Execute the script by running the following command:

    ```sh
    ./run.sh
    ```

This will initiate the installation process and set up the necessary environment for the workshop.

# Table of Contents

## DAY 1
  
## Introduction to RISC-V ISA and GNU Compiler Toolchain

### Introduction to Basic Keywords
- Introduction
- From Apps to Hardware
- Detail Description of Course Content

### Labwork for RISC-V Toolchain
- C Program
- RISC-V GCC Compiler and Disassemble
- Spike Simulation and Debug

### Integer Number Representation
- 64-bit Unsigned Numbers
- 64-bit Signed Numbers
- Labwork For Signed and Unsigned Numbers

## DAY 2

## Introduction to ABI and Basic Verification Flow

### Application Binary Interface
- Introduction to ABI
- Memory Allocation for Double Words
- Load, Add and Store Instructions

# VLSI Physical Design for ASICs
In the assembly file, we declared assembly functions with appropriate signatures that match the calling conventions of your platform.

### C Program - Sum of numbers from 1 to 9
```p4.c```
```c
#include <stdio.h>

extern int load(int x, int y);

int main()
{
  int result = 0;
  int count = 9;
  result = load(0x0, count+1);
  printf("Sum of numbers from 1 to 9 is %d\n", result);
}
```
### Assembly File 
```load.s```

```s
.section .text
.global load
.type load, @function

load:

add a4, a0, zero
add a2, a0, a1
add a3, a0, zero

loop:

add a4, a3, a4
addi a3, a3, 1
blt a3, a2, loop
add a0, a4, zero
ret
```
# Simulate C Program using Function Call

**Compilation:** To compile C code and Asseembly file use the command

```riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o p3.o p3.c load.s```

this would generate object file ```p3.o```

**Execution:** To execute the object file run the command

```spike pk p3.o```

![8](https://github.com/akshatva7/pes_asic_class/assets/135726741/55f2d630-e640-4633-81ae-4d4a14218977)

![Screenshot from 2023-08-20 22-01-13](https://github.com/akshatva7/pes_asic_class/assets/135726741/d20630e3-9bf5-4f96-a916-31655534aa09)

![Screenshot from 2023-08-20 22-01-35](https://github.com/akshatva7/pes_asic_class/assets/135726741/8861a8bc-256d-47da-93b4-7492a3a5a1ed)









