

````markdown
# 🧠 RISC-V-Info
````

## 📖 About This Repository

This repository contains my notes and learning from studying **RISC-V architecture**.

I am learning RISC-V from the basics, starting with processors and instruction execution, and moving toward registers, memory, processor execution models, and the RISC-V Instruction Set Architecture.

These notes contain the concepts I have learned, along with examples and diagrams that helped me understand them.

---

# 1. 🌐 Introduction to Processors

## 1.1 Processors in Daily Life

We use processors in many parts of our daily life.

| Example | What the Processor Does |
|---|---|
| 📱 Taking a picture | Processes the camera input and image |
| 📱 App launch | Helps load and execute the application |
| 📸 Camera activation | ISP processes camera data |
| 🚗 Cars | Controls different systems |
| 🏠 Home | Used in routers, appliances, security systems, etc. |
| 💻 Workspace | Computers, printers, security systems |
| 🌆 Public spaces | Traffic lights, payment systems, displays, etc. |

### Camera Example

When we take a picture, different processors can be involved.

```text
Touch Input
     ↓
Camera Application
     ↓
Camera Sensor
     ↓
ISP
     ↓
Image Processing
     ↓
Storage
     ↓
Display


**ISP = Image Signal Processor**

It is a dedicated processor used for processing camera data.

---

## 1.2 Why Understanding Processors Matters

Processors are everywhere in our daily life.

| Place           | Examples                                                 |
| --------------- | -------------------------------------------------------- |
| 🚗 Car          | Engine control, safety systems, infotainment, navigation |
| 🏠 Home         | Thermostat, router, appliances, security                 |
| 💻 Workspace    | Computers, printers, security badges, elevators          |
| 🌆 Public Space | Traffic lights, payment systems, surveillance, displays  |

---

# 2. 🏗️ The Technology Hierarchy

Technology can be understood as different layers where each layer depends on the layers below it.

| Floor | Technology Layer                    | Examples                       |
| ----: | ----------------------------------- | ------------------------------ |
|    10 | Applications                        | Instagram, WhatsApp, Games     |
|     9 | Programming Languages               | Python, Java, JavaScript       |
|     8 | Operating Systems                   | Android, iOS, Windows, Linux   |
|     7 | Software Libraries                  | Graphics, Networking, Database |
|     6 | Compilers and Interpreters          | Convert/execute programs       |
|     5 | Assembly Language                   | RISC-V defines this level      |
|     4 | Processor Architecture              | RISC-V specification           |
|     3 | Digital Logic Design                | Gates, Flip-flops, ALUs        |
|     2 | Transistors and Electronic Circuits | Electronic implementation      |
|     1 | Silicon Manufacturing and Physics   | Physical foundation            |

### RISC-V Position

```text
Applications
     ↑
Programming Languages
     ↑
Operating Systems
     ↑
Software Libraries
     ↑
Compilers / Interpreters
     ↑
Assembly Language       ← RISC-V
     ↑
Processor Architecture  ← RISC-V
     ↑
Digital Logic
     ↑
Transistors
     ↑
Silicon / Physics
```

RISC-V defines the **processor architecture and instruction set level**, providing a foundation for the software layers above it.

---

# 3. 🧠 What Is a Processor?

## ISA

**ISA = Instruction Set Architecture**

The ISA defines the instructions that a processor understands.

## Processor

A processor performs a set of instructions in a fast and efficient way.

The CPU is often called the **brain of the computer**.

A processor performs the instructions provided to it according to the conditions of the program.

### What a Processor Can Do

| Capability      | Meaning                                    |
| --------------- | ------------------------------------------ |
| Arithmetic      | Add, subtract, multiply, divide            |
| Logic           | AND, OR, NOT operations                    |
| Comparison      | Compare values                             |
| Memory Access   | Read/write data                            |
| Decision Making | Choose the next instruction                |
| Input/Output    | Communicate with other parts of the system |

### What a Processor Cannot Do Directly

A processor does not directly:

* Understand human language
* See or hear
* Learn or adapt
* Create content

These require software, sensors, algorithms, and other system components.

---

# 4. 🔄 Instruction Execution Cycle

Every processor repeatedly goes through a basic instruction execution cycle.

```text
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
```

| Stage         | What Happens                          |
| ------------- | ------------------------------------- |
| **FETCH**     | Get the next instruction from memory  |
| **DECODE**    | Understand what the instruction means |
| **EXECUTE**   | Perform the required operation        |
| **WRITEBACK** | Store the result                      |
| **REPEAT**    | Move to the next instruction          |

---

## Example: Adding Two Numbers

```asm
add x3, x1, x2
```

Meaning:

```text
x3 = x1 + x2
```

### Instruction

```text
00000000001000001000000110110011
```

### Decode

| Field           | Value     | Meaning             |
| --------------- | --------- | ------------------- |
| Opcode          | `0110011` | R-type arithmetic   |
| rd              | `00011`   | Destination = x3    |
| rs1             | `00001`   | First operand = x1  |
| rs2             | `00010`   | Second operand = x2 |
| funct7 + funct3 | —         | ADD operation       |

### Execute

Suppose:

```text
x1 = 15
x2 = 7
```

Then:

```text
15 + 7 = 22
```

### Writeback

```text
x3 = 22
```

---

# 5. ⚡ Processor Performance

The main processor performance metrics are:

| Metric          | Meaning                                       |
| --------------- | --------------------------------------------- |
| **Clock Speed** | Number of clock cycles per second             |
| **IPC**         | Instructions performed per clock cycle        |
| **Efficiency**  | How effectively the processor uses its cycles |

---

## 5.1 Clock Speed

Clock speed tells us how many clock cycles a processor can perform per second.

| Frequency | Cycles per Second | Typical Usage          |
| --------- | ----------------: | ---------------------- |
| `1 MHz`   |         1 million | Early microcontrollers |
| `100 MHz` |       100 million | Basic embedded systems |
| `1 GHz`   |         1 billion | Smartphones, tablets   |
| `3 GHz`   |         3 billion | Desktop computers      |

> Higher clock speed does not always mean better performance. A processor with a lower clock speed can perform better if it uses its cycles more efficiently.

---

## 5.2 IPC

**IPC = Instructions Per Cycle**

IPC tells us how many instructions can be performed in one clock cycle.

---

## 5.3 Performance Formula

```text
Performance
    =
Clock Speed × Instructions Per Cycle × Efficiency
```

---

# 6. 🔢 Binary and Digital Representation

Computers represent information using binary.

```text
0 → Low voltage
1 → High voltage
```

Using two voltage states provides:

* Fast operation
* Power efficiency
* Reliability
* Good speed

---

# 7. 🔀 Bit-Level Operations

Bit-level operations are similar to logic-gate operations.

The main bitwise operations are:

| Operation   | Symbol |
| ----------- | ------ |
| Bitwise AND | `&`    |
| Bitwise OR  | `\|`   |
| Bitwise XOR | `^`    |

---

## 7.1 Bitwise AND

```text
1 AND 1 = 1
1 AND 0 = 0
0 AND 1 = 0
0 AND 0 = 0
```

Example:

```text
  1011
& 1101
------
  1001
```

---

## 7.2 Bitwise OR

```text
1 OR 1 = 1
1 OR 0 = 1
0 OR 1 = 1
0 OR 0 = 0
```

Example:

```text
  1011
| 1101
------
  1111
```

---

## 7.3 Bitwise XOR

```text
1 XOR 1 = 0
1 XOR 0 = 1
0 XOR 1 = 1
0 XOR 0 = 0
```

Example:

```text
  1011
^ 1101
------
  0110
```

---

# 8. 🔢 Signed and Unsigned Numbers

## Unsigned Numbers

Unsigned numbers use all bits to represent the magnitude.

| Size   | Range                |
| ------ | -------------------- |
| 8-bit  | `0 to 255`           |
| 16-bit | `0 to 65,535`        |
| 32-bit | `0 to 4,294,967,295` |

---

## Signed Numbers

Signed numbers use two's complement representation.

| Size   | Range                              |
| ------ | ---------------------------------- |
| 8-bit  | `-128 to +127`                     |
| 16-bit | `-32,768 to +32,767`               |
| 32-bit | `-2,147,483,648 to +2,147,483,647` |

---

## Two's Complement

Two's complement is used to represent negative numbers.

```text
Positive Number
       ↓
 Invert all bits
       ↓
     Add 1
       ↓
Negative Number
```

### Example: -5 in 8-bit

```text
Step 1: Positive 5

00000101

Step 2: Invert all bits

11111010

Step 3: Add 1

11111010
+      1
--------
11111011

11111011 = -5
```

---

# 9. 🧮 Registers — The Processor's Workspace

A register is a very small storage location inside the processor.

Registers are important because they are very close to the CPU and can be accessed very quickly.

Each 32-bit register consists of **32 flip-flops (memory cells)**.

```text
Bit 31                              Bit 0
  ↓                                   ↓

┌──────────────────────────────────────┐
│              32 Bits                 │
└──────────────────────────────────────┘

  ↑                                   ↑
 MSB                                 LSB
```

| Term | Meaning               |
| ---- | --------------------- |
| MSB  | Most Significant Bit  |
| LSB  | Least Significant Bit |

```text
Bit 31 = MSB
Bit 0  = LSB
```

---

# 10. 🧩 RISC-V Register Set

RISC-V has **32 general-purpose registers**:

```text
x0 → x31
```

plus special registers.

## Register x0

Register `x0` is hardwired to always contain zero.

It is useful for:

1. Setting a register to zero
2. Copying a register
3. Ignoring a result
4. Performing operations where a zero value is needed

---

## RISC-V Registers

| Register  | Name     | Main Purpose                   |
| --------- | -------- | ------------------------------ |
| `x0`      | `zero`   | Always `0`                     |
| `x1`      | `ra`     | Return address                 |
| `x2`      | `sp`     | Stack pointer                  |
| `x3`      | `gp`     | Global pointer                 |
| `x4`      | `tp`     | Thread pointer                 |
| `x5–x7`   | `t0–t2`  | Temporary values               |
| `x8`      | `s0/fp`  | Saved register / frame pointer |
| `x9`      | `s1`     | Saved register                 |
| `x10–x11` | `a0–a1`  | Arguments / return values      |
| `x12–x17` | `a2–a7`  | Function arguments             |
| `x18–x27` | `s2–s11` | Saved registers                |
| `x28–x31` | `t3–t6`  | Temporary values               |

---

## Easy Way to Remember

| Register Group | Main Idea                     |
| -------------- | ----------------------------- |
| `x0`           | Permanent `0`                 |
| `x1 (ra)`      | Where to return               |
| `x2 (sp)`      | Stack location                |
| `a0–a7`        | Function inputs/outputs       |
| `t0–t6`        | Temporary workspace           |
| `s0–s11`       | Values that must be preserved |

`s0`, `s1`, and `s2` are callee-saved registers.

---

# 11. 📞 Function Structure

A function generally has three main parts:

```text
┌──────────────────────────┐
│        Prologue          │
│      Prepare & Save      │
└────────────┬─────────────┘
             ↓
┌──────────────────────────┐
│      Function Body       │
│        Do the Work       │
└────────────┬─────────────┘
             ↓
┌──────────────────────────┐
│         Epilogue         │
│     Restore & Clean Up   │
└────────────┬─────────────┘
             ↓
            ret
             ↓
       Go Back to Caller
```

| Part              | Purpose                                       |
| ----------------- | --------------------------------------------- |
| **Prologue**      | Prepare the function and save required values |
| **Function Body** | Perform the actual work                       |
| **Epilogue**      | Restore saved values and clean up             |
| `ret`             | Return to the caller                          |

---

# 12. 🧠 Register Allocation

Register allocation means deciding which registers will hold which values during a calculation.

The goal is to store values in the desired registers while performing the calculation.

---

# 13. 💾 Memory Hierarchy

Computer memory is organized based on:

* Size
* Speed
* Cost

| Level                 |  Typical Size |       Speed | Main Purpose                    |
| --------------------- | ------------: | ----------: | ------------------------------- |
| **CPU Registers**     | `32 × 32-bit` |    `0.1 ns` | Currently active data           |
| **L1 Cache**          |    `32–64 KB` |    `1–2 ns` | Recently used instructions/data |
| **L2 Cache**          | `256 KB–1 MB` |   `5–10 ns` | Less recently used data         |
| **L3 Cache**          |     `8–32 MB` |  `20–50 ns` | Shared cache between cores      |
| **Main Memory (RAM)** |     `4–32 GB` | `50–100 ns` | Program storage                 |
| **SSD**               | `256 GB–4 TB` |  `0.1–1 ms` | Long-term file storage          |
| **Hard Drive**        |     `1–10 TB` |   `5–10 ms` | Bulk storage                    |

---

## Memory Hierarchy

```text
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
```

---

## Why Does This Hierarchy Exist?

The basic trade-off is:

```text
Fast Memory
    ↓
More Expensive
    ↓
Smaller Capacity

Slow Memory
    ↓
Cheaper
    ↓
Larger Capacity
```

The solution is to use:

* Small amounts of fast memory for active data
* Larger amounts of slower memory for less active data

This helps create a computer that balances **performance, capacity, and cost**.

---

# 14. 🧠 Virtual Memory

Virtual memory is a technique where the operating system uses part of storage, such as an SSD/HDD, as extra memory when RAM is not enough.

---

# 15. 🔄 Address Translation

## MMU

**MMU = Memory Management Unit**

The MMU translates:

```text
Virtual Address → Physical Address
```

---

## TLB

**TLB = Translation Lookaside Buffer**

The TLB is a small cache that stores recently used address translations.

The CPU/MMU checks the TLB for a recent translation.

---

## Address Translation Flow

```text
              Virtual Address
                     ↓
                    MMU
                     ↓
                    TLB
                 ↙      ↘
             Found     Not Found
               ↓           ↓
       Physical Address  Page Table
                             ↓
                     Physical Address
```

---

# 16. 💨 Memory Access Patterns

## Cache-Friendly Code

Cache-friendly code accesses nearby memory sequentially.

This provides good spatial locality, fewer cache misses, and faster execution.

```text
array[0]
   ↓
array[1]
   ↓
array[2]
   ↓
array[3]
```

### Example

```text
array[0] → array[1] → array[2] → array[3]
```

---

## Cache-Unfriendly Code

Cache-unfriendly code accesses distant memory locations.

This can cause poor spatial locality, more cache misses, and slower execution.

```text
array[0] → array[64] → array[128] → array[192]
```

### Simple Comparison

| Access Pattern  | Cache Behaviour  | Performance |
| --------------- | ---------------- | ----------- |
| Sequential      | Cache-friendly   | Faster      |
| Distant/strided | Cache-unfriendly | Slower      |

---

# 17. ⚙️ Processor Execution Models

## 17.1 In-Order Execution

In-order execution means instructions are executed in the same order as they appear in the program.

```text
1 → 2 → 3 → 4
```

If one instruction is slow, later instructions may have to wait.

This is called a **stall**.

### Advantages

| Advantage             |
| --------------------- |
| Simple hardware       |
| Lower power           |
| Predictable execution |
| Easier to debug       |
| Lower cost            |

### Disadvantages

| Disadvantage                                    |
| ----------------------------------------------- |
| Performance can be limited by slow instructions |
| Cannot fully use instruction-level parallelism  |
| Can stall on memory access or long operations   |

---

# 18. 🚀 Out-of-Order Execution

Out-of-order execution allows the processor to execute ready or independent instructions early instead of strictly following program order.

### Example

Program order:

```text
1 → 2 (slow) → 3 → 4
```

Possible execution order:

```text
1 → 2 → 4 → 3
```

Instruction `4` is independent, so it can execute before instruction `3` is ready.

---

## Advantages

| Advantage                          |
| ---------------------------------- |
| Higher performance                 |
| Better use of execution units      |
| Can hide memory delays             |
| Uses instruction-level parallelism |

## Disadvantages

| Disadvantage                                |
| ------------------------------------------- |
| Complex hardware                            |
| Higher power consumption                    |
| Higher cost                                 |
| Less predictable execution time             |
| Vulnerable to speculative-execution attacks |

---

# 19. 🔧 Out-of-Order Implementation

Important components include:

| Component                | Purpose                                           |
| ------------------------ | ------------------------------------------------- |
| **Instruction Queue**    | Holds multiple instructions                       |
| **Reservation Stations** | Hold instructions waiting for operands            |
| **Reorder Buffer (ROB)** | Makes sure instructions complete in program order |
| **Register Renaming**    | Removes false dependencies                        |

---

# 20. 📦 VLIW

**VLIW = Very Long Instruction Word**

VLIW moves instruction scheduling from hardware to the compiler.

```text
Traditional:
Hardware → Schedules Instructions

VLIW:
Compiler → Schedules Instructions
```

One instruction word can contain multiple independent operations.

The compiler ensures that there are no data dependencies between operations executed together.

---

## VLIW Advantages

* Simpler hardware
* Lower power
* Compiler can optimize globally
* Predictable execution

## VLIW Disadvantages

* Requires a sophisticated compiler
* Poor code density due to possible NOPs
* Difficult with cache misses
* Not compatible with existing software

---

# 21. 🔗 Specialized Execution Models

## 21.1 Dataflow Processors

A dataflow processor executes an instruction when its required data or operands are ready.

It does not strictly follow program order.

### Main Idea

```text
Data Ready
    ↓
Execute
```

Independent instructions can execute without waiting for each other.

### Example

```text
1. A = 10 + 20
2. B = 50 × 2
3. C = A + B
```

Instructions `1` and `2` are independent.

```text
       ┌── 1 → A ──┐
Start ─┤            ├→ 3 → C
       └── 2 → B ──┘
```

### Key Idea

```text
Data Ready → Execute
```

---

# 22. 🧮 Vector Processors

Vector processors perform the same operation on multiple data elements simultaneously.

They are useful for:

* Arrays
* Data-parallel operations
* Processing many similar values

### Scalar vs Vector

| Type       | Meaning                    |
| ---------- | -------------------------- |
| **Scalar** | One element at a time      |
| **Vector** | Multiple elements together |

---

## Example

```text
A = [1, 2, 3, 4]

B = [10, 20, 30, 40]

A + B
   ↓
C = [11, 22, 33, 44]
```

### Scalar Processing

```text
1 + 10
2 + 20
3 + 30
4 + 40
```

### Vector Processing

```text
[1, 2, 3, 4] + [10, 20, 30, 40]
                ↓
           [11, 22, 33, 44]
```

The tutorial's 1000-element example describes scalar processing as taking **1000+ cycles**, while vector processing is shown as taking **10–100 cycles depending on vector width**.

RISC-V's **V extension** is designed for data-parallel/vector execution.


# 23. 🧩 RISC-V Instruction Set Architecture

