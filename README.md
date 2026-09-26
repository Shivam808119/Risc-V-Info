
# 🧠 RISC-V-Info

## 📖 About This Repository

This repository contains my notes and learning from studying **RISC-V architecture**.

I am learning RISC-V from the basics, starting with processors and instruction execution, and moving toward registers, memory, execution models, and the RISC-V Instruction Set Architecture.

## 🎯 What I Am Learning

- Processor fundamentals
- Instruction execution
- Processor performance
- Binary and bit-level operations
- Signed and unsigned numbers
- RISC-V registers
- Register allocation
- Memory hierarchy
- Virtual memory
- Address translation
- Cache and memory access patterns
- In-order execution
- Out-of-order execution
- VLIW
- Dataflow processors
- Vector processors
- RISC-V Instruction Set Architecture

---

# 📚 Chapter 1 — Processor Fundamentals

## 1.1 Your Daily Life and Processors

We are using processors in daily life in many ways, like:

1. 📱 Clicking a picture from the phone
2. 🚀 App launch
3. 📸 Capture
4. 🚗 Running a car and many more things
5. 📷 Camera activation (by using the ISP, a dedicated processor)

---

## 1.2 Why Understanding Processors Matters

We need to care about processors because they are used everywhere in our daily life:

1. 🚗 Car
2. 🏠 Home
3. 💻 Workspace
4. 🌆 Public space and everywhere


## 1.3 The Technology Hierarchy


            TECHNOLOGY HIERARCHY

┌──────────────────────────────────────────────┐
│ Floor 10 → Applications                     │
│             Instagram, WhatsApp, Games      │
├──────────────────────────────────────────────┤
│ Floor 9  → Programming Languages             │
│             Java, Python, JavaScript         │
├──────────────────────────────────────────────┤
│ Floor 8  → Operating Systems                 │
│             Android, iOS, Windows, Linux    │
├──────────────────────────────────────────────┤
│ Floor 7  → Software Libraries                │
│             Graphics, Networking, Database  │
├──────────────────────────────────────────────┤
│ Floor 6  → Compilers and Interpreters        │
├──────────────────────────────────────────────┤
│ Floor 5  → Assembly Language                 │
│             RISC-V defines this level        │
├──────────────────────────────────────────────┤
│ Floor 4  → Processor Architecture            │
│             RISC-V specification             │
├──────────────────────────────────────────────┤
│ Floor 3  → Digital Logic Design              │
│             Gates, Flip-flops, ALUs          │
├──────────────────────────────────────────────┤
│ Floor 2  → Transistors and Electronic        │
│             Circuits                         │
├──────────────────────────────────────────────┤
│ Floor 1  → Silicon Manufacturing and Physics │
└──────────────────────────────────────────────┘

⚙️ Chapter 2 — Understanding Processors
2.1 Processor

ISA stands for Instruction Set Architecture.

A processor performs a set of instructions in a fast and efficient way.

CPU is called the brain of the computer.

It only performs the instructions that we provide to it based on the conditions.

2.2 The Instruction Execution Cycle of the Processor
        ┌─────────┐
        │  FETCH  │
        └────┬────┘
             ↓
        ┌─────────┐
        │ DECODE  │
        └────┬────┘
             ↓
        ┌─────────┐
        │ EXECUTE │
        └────┬────┘
             ↓
        ┌──────────┐
        │ WRITEBACK│
        └────┬─────┘
             ↓
        ┌─────────┐
        │ REPEAT  │
        └────┬────┘
             ↓
      Next Instruction
FETCH → The processor first gets the next instruction from memory.
DECODE → Understand the instruction and what it means.
EXECUTE → Perform the instruction.
WRITEBACK → Write the result to the required destination.
REPEAT → Move to the next instruction.
2.3 Processor Performance Metrics

The main performance metrics are:

⏱️ Clock Speed
🔢 Instructions Per Cycle (IPC)
⚡ Efficiency
1. Clock Speed

Clock speed tells how many clock cycles a processor can perform per second.

Frequency	Cycles per Second	Typical Usage
1 MHz	1 million	Early microcontrollers (1970s)
100 MHz	100 million	Basic embedded systems
1 GHz	1 billion	Smartphones, tablets
3 GHz	3 billion	Desktop computers
2. IPC

IPC tells us how many instructions can be performed by a clock cycle.


3. Performance
Performance
    =
Clock Speed × Instructions Per Cycle × Efficiency
🔢 Chapter 3 — Binary and Digital Foundations
3.1 Binary and Voltage

It represents only two voltage states because this is:

Fast
Power efficient
Reliable
Speed
0 → Low Voltage
1 → High Voltage
3.3 Bit-Level Operations

Bit-level operations are similar to logic gates.

The main operations are:

Bitwise AND
Bitwise OR
Bitwise XOR
Bitwise AND
1 AND 1 = 1
1 AND 0 = 0
0 AND 1 = 0
0 AND 0 = 0

Example:

  1011
& 1101
------
  1001
Bitwise OR
1 OR 1 = 1
1 OR 0 = 1
0 OR 1 = 1
0 OR 0 = 0

Example:

  1011
| 1101
------
  1111
Bitwise XOR
1 XOR 1 = 0
1 XOR 0 = 1
0 XOR 1 = 1
0 XOR 0 = 0

Example:

  1011
^ 1101
------
  0110
3.3.2 Signed and Unsigned Numbers
🔵 Unsigned Numbers

Use all bits for magnitude.

8-bit unsigned: 0 to 255
16-bit unsigned: 0 to 65,535
32-bit unsigned: 0 to 4,294,967,295
🔴 Signed Numbers
8-bit signed: -128 to +127
16-bit signed: -32,768 to +32,767
32-bit signed: -2,147,483,648 to +2,147,483,647
Two's Complement

How two's complement is used to represent a negative number:

Positive Number
      ↓
Invert All Bits
      ↓
     Add 1
      ↓
Negative Number
🧮 Chapter 4 — Registers
4.1 Registers: The Processor's Workspace

A register is a very small storage inside the processor.

Registers are important because they are very close to the CPU and can be accessed fast.

Each 32-bit register consists of 32 flip-flops (memory cells).

Bit 31                              Bit 0
  ↓                                   ↓
┌──────────────────────────────────────┐
│              32 Bits                 │
└──────────────────────────────────────┘
  ↑                                   ↑
 MSB                                 LSB
Bit 31 = MSB (Most Significant Bit)
Bit 0 = LSB (Least Significant Bit)
4.2 RISC-V Register Set

RISC-V has 32 general-purpose registers:

x0 → x31

plus special registers.

Register x0 is hardwired to always contain zero.

Why is x0 useful?
Set a register to zero
Copy a register
Ignore a result
Nothing useful changes
Register Table
Register	Name	Main Purpose
x0	zero	Always 0
x1	ra	Return address
x2	sp	Stack pointer
x3	gp	Global pointer
x4	tp	Thread pointer
x5–x7	t0–t2	Temporary values
x8	s0/fp	Saved register / frame pointer
x9	s1	Saved register
x10–x11	a0–a1	Arguments / return values
x12–x17	a2–a7	Function arguments
x18–x27	s2–s11	Saved registers
x28–x31	t3–t6	Temporary values
Easy Way to Remember
x0       → permanent 0
x1 (ra)  → where to return
x2 (sp)  → where the stack currently is
a0-a7    → function inputs/outputs
t0-t6    → temporary workspace
s0-s11   → values that must be preserved

s0, s1, and s2 are callee-saved registers.

4.2.3 Function Structure
┌──────────────────────────┐
│ Prologue                 │
│ Prepare & Save           │
└────────────┬─────────────┘
             ↓
┌──────────────────────────┐
│ Function Body            │
│ Do the Work              │
└────────────┬─────────────┘
             ↓
┌──────────────────────────┐
│ Epilogue                 │
│ Restore & Clean Up       │
└────────────┬─────────────┘
             ↓
            ret
             ↓
      Go Back to Caller
4.3 Register Allocation

Register allocation means deciding which registers will hold which values during a calculation.

We can store the value in the desired register according to the calculation.

💾 Chapter 5 — Memory Systems
5.1 The Memory Hierarchy

Computer memory is organised on the basis of:

Size
Speed
Cost
Level	Typical Size	Speed	Main Purpose
CPU Registers	32 × 32-bit	0.1 ns	Currently active data
L1 Cache	32–64 KB	1–2 ns	Recently used instructions/data
L2 Cache	256 KB–1 MB	5–10 ns	Less recently used data
L3 Cache	8–32 MB	20–50 ns	Shared cache between cores
Main Memory (RAM)	4–32 GB	50–100 ns	Program storage
SSD	256 GB–4 TB	0.1–1 ms	Long-term file storage
Hard Drive	1–10 TB	5–10 ms	Bulk storage
Memory Hierarchy
        FAST
         ↑
    Registers
         ↓
      L1 Cache
         ↓
      L2 Cache
         ↓
      L3 Cache
         ↓
        RAM
         ↓
        SSD
         ↓
     Hard Drive
         ↓
        SLOW

This hierarchy exists because some memory is expensive and some is much cheaper.

Solution

We can use costly memory for better performance and slower, cheaper memory for data storage so the computer can be more budget-friendly.

5.2.1 Virtual Memory

Virtual memory is a technique where the OS uses part of the storage (SSD/HDD) as extra memory when RAM is not enough.

5.2.2 Address Translation
MMU

MMU = Memory Management Unit

The MMU translates virtual addresses into physical addresses.

TLB

The MMU first checks the:

TLB = Translation Lookaside Buffer

Think of the TLB as a small cache of recent address translations.

Address Translation Flow
        Virtual Address
               ↓
              MMU
               ↓
              TLB
           ↙       ↘
       Found       Not Found
         ↓             ↓
Physical Address   Page Table
                       ↓
                 Physical Address
5.3.1 Memory Access Patterns and Performance
🟢 Cache-Friendly

Accesses nearby memory sequentially → good spatial locality → fewer cache misses → faster.

array[0] → array[1] → array[2] → array[3]
🔴 Cache-Unfriendly

Accesses distant memory locations → poor spatial locality → more cache misses → slower.

array[0] → array[64] → array[128] → array[192]
⚙️ Chapter 6 — Processor Execution Models
6.1 In-Order Execution

In-order execution means instructions are executed in the same order as they appear in the program.

Example
1 → 2 → 3 → 4

If one instruction is slow, later instructions may have to wait (stall).

Advantages
Simple hardware
Lower power
Predictable
Easier to debug
Lower cost
Disadvantages
Slower when instructions stall
Cannot fully use instruction-level parallelism
6.2 Out-of-Order Execution

Out-of-order execution means the processor executes ready/independent instructions early instead of strictly following program order.

Example

Program order:

1 → 2 (slow) → 3 → 4

Processor can execute:

1 → 2 → 4 → 3
Advantages
Higher performance
Better use of execution units
Hides memory delays
Uses instruction-level parallelism
Disadvantages
Complex hardware
Higher power consumption
Higher cost
Less predictable execution time
Vulnerable to speculative-execution attacks
6.2.2 Out-of-Order Implementation Details
Instruction Queue → Holds multiple instructions.
Reservation Stations → Hold instructions waiting for their operands.
Reorder Buffer (ROB) → Makes sure instructions complete in program order.
Register Renaming → Removes false dependencies.
VLIW — Very Long Instruction Word

VLIW = Very Long Instruction Word

Moves instruction scheduling from hardware → compiler.
One instruction word can contain multiple independent operations.
Compiler ensures there are no data dependencies between operations executed together.
Advantages
Simpler hardware
Lower power
Compiler can optimize globally
Predictable execution
Disadvantages
Requires sophisticated compiler
Poor code density due to possible NOPs
Difficult with cache misses
Not compatible with existing software
6.3 Specialized Execution Models
6.3.1 Dataflow Processors
Execute an instruction when its required data/operands are ready.
They don't strictly follow program order.
Main idea: Data Ready → Execute
Independent instructions can execute without waiting for each other.
Example
1. A = 10 + 20
2. B = 50 × 2
3. C = A + B

Instructions 1 and 2 are independent:

       ┌── 1 → A ──┐
Start ─┤            ├→ 3 → C
       └── 2 → B ──┘
Key Idea
Data Ready → Execute
6.3.2 Vector Processors
Perform the same operation on multiple data elements simultaneously.
Useful for arrays and other data-parallel work.
Scalar = one element at a time.
Vector = multiple elements together.
Example
A = [1, 2, 3, 4]
B = [10, 20, 30, 40]

A + B
  ↓
C = [11, 22, 33, 44]
Scalar
1 + 10
2 + 20
3 + 30
4 + 40
Vector
[1, 2, 3, 4] + [10, 20, 30, 40]
              ↓
         [11, 22, 33, 44]

The PDF's 1000-element example describes scalar processing as taking 1000+ cycles, while vector processing is shown as taking 10–100 cycles depending on vector width.

RISC-V's V extension is specifically designed for data-parallel/vector execution.

🚀 Chapter 7 — RISC-V Instruction Set Architecture

