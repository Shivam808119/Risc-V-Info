# Risc-V-Info
What i learned about Risc V i write it there

Question:   how we do conncet logic gate to Risc -V


question :
RISC-V assembly
      ↓
Binary instruction
      ↓
Electrical signals
      ↓
Digital logic
      ↓
ALU / registers
      ↓
Result



unable to understood this 

We are using the daily life processor in many ways like 
1. clicking the picture from the phone 
2. App launch
3. capture
4. running a car and many more things
5. Cammera activation (By using the ISP a dedicated processor for that )


we need to care about the processor because it used everywhere in our daily life 
1. car
2. home
3. workspace
4. public space and everywhere



The Technology Hierarchy

Floor 10: Applications (Instagram, WhatsApp, Games)
Floor 9: Programming Languages (Java, Python, JavaScript)
Floor 8: Operating Systems (Android, iOS, Windows, Linux)
Floor 7: Software Libraries (Graphics, Networking, Database)
Floor 6: Compilers and Interpreters
Floor 5: Assembly Language RISC-V defines this level
Floor 4: Processor Architecture RISC-V specification
Floor 3: Digital Logic Design (Gates, Flip-flops, ALUs)
Floor 2: Transistors and Electronic Circuits
Floor 1: Silicon Manufacturing and Physics



ISA stands for Instruction Set Architecture.

**Processor**

Processor that perform the set of instructions in fast and efficient way 
Cpu is called the brain of the computer 


it only perform the instruction that we provide to it on some conditions 

The Instruction Execution Cycle of the processor 

FETCH →   The processor first needs to get the next instruction from memory.
DECODE  → undertand the instruction what does it mean 
EXECUTE → perform the instruction 
WRITEBACK → write back the instruction in the  memory 
REPEAT  → Move to the next instruction

**Processor Performance Metrics**


1.Clock Speed
2.Instructions Per Cycle (IPC)
3. Efficiency



1. Clock speed tell the how many a clock cycle a processor can perform per second

   Frequency Cycles per Second Typical Usage
   
1 MHz     1 million     Early microcontrollers (1970s)
100 MHz   100 million   Basic embedded systems
1 GHz     1 billion     Smartphones, tablets
3 GHz     3 billion     Desktop computers


2. IPC  tell us how many instaruction can be performed by a clock cycle

3. Performance =    Clock Speed × Instructions Per Cycle × Efficiency



it represent  only 2 voltage only because  this is 

1. fast
2. power efficeint
3. realibilty
4. speed

**Bit level Operations **

Bit level operation is similier to the gates also 

like :
1. Bitwise AND
2. Bitwise OR
3. Bitwise X-OR



Unsigned Numbers: Use all bits for magnitude
• 8-bit unsigned: 0 to 255
• 16-bit unsigned: 0 to 65,535
• 32-bit unsigned: 0 to 4,294,967,295


Signed Numbers:
• 8-bit signed: -128 to +127
• 16-bit signed: -32,768 to +32,767
• 32-bit signed: -2,147,483,648 to +2,147,483,647

How they use the two's completement to convert the positive number in the negative 

Positive number  → Invert all bits  → Add 1  → Negative number  

**Registers: The Processor's Workspace**


Register is a very small storage insde the processor 


register are imprtant beause they are very close to CPU 
and can be accessed fast 


Each 32-bit register consists of 32 flip-flops (memory cells).
Bit 31 = MSB (Most Significant Bit)
Bit 0 = LSB (Least Significant Bit)


**RISC-V Register Set**

RISC-V has 32 general-purpose registers (x0-x31) plus special registers.

Register x0 is hardwired to always contain zero.
0x register is useful because 

1. Set a register to zero
2. Copy a register
3. Ignore a result
4. Nothing useful changes



| Registers | Name   | Main purpose                   |
| --------- | ------ | ------------------------------ |
| x0        | zero   | Always 0                       |
| x1        | ra     | Return address                 |
| x2        | sp     | Stack pointer                  |
| x3        | gp     | Global pointer                 |
| x4        | tp     | Thread pointer                 |
| x5–x7     | t0–t2  | Temporary values               |
| x8        | s0/fp  | Saved register / frame pointer |
| x9        | s1     | Saved register                 |
| x10–x11   | a0–a1  | Arguments / return values      |
| x12–x17   | a2–a7  | Function arguments             |
| x18–x27   | s2–s11 | Saved registers                |
| x28–x31   | t3–t6  | Temporary values               |



x0       → permanent 0
x1 (ra)  → where to return
x2 (sp)  → where the stack currently is
a0-a7    → function inputs/outputs
t0-t6    → temporary workspace
s0-s11   → values that must be preserved


 s0, s1, and s2 are callee-saved registers


Prologue → Prepare & Save
     ↓
Function Body → Do the Work
     ↓
Epilogue → Restore & Clean Up
     ↓
ret → Go Back to Caller


Register allocation means deciding which registers will hold which values during a calculation.
we can store the value in the deisred register we want to store 

**The Memory Hierarchy**

Computer memory is organised on the bacis of there size speed cost 

| Level                 | Typical Size |     Speed | Main Purpose                    |
| --------------------- | -----------: | --------: | ------------------------------- |
| **CPU Registers**     |  32 × 32-bit |    0.1 ns | Currently active data           |
| **L1 Cache**          |     32–64 KB |    1–2 ns | Recently used instructions/data |
| **L2 Cache**          |  256 KB–1 MB |   5–10 ns | Less recently used data         |
| **L3 Cache**          |      8–32 MB |  20–50 ns | Shared cache between cores      |
| **Main Memory (RAM)** |      4–32 GB | 50–100 ns | Program storage                 |
| **SSD**               |  256 GB–4 TB |  0.1–1 ms | Long-term file storage          |
| **Hard Drive**        |      1–10 TB |   5–10 ms | Bulk storage                    |


This Hierarchy is exists because some memory is expensive and some is very cheaper 
Solution : Then the best solution of this is we can use the Costly memeory for more and better perfromage and the solwer and cheap mempry for data storage that it  can be the buget freindly computer become 



Virtual memory is a technique where the OS uses part of the storage (SSD/HDD) as extra memory when RAM is not enough.

**Address Translation**

MMU - Memory management Unit 

The MMU translates virtual addresses into physical addresses

The MMU first checks the:
TLB = Translation Lookaside Buffer
Think of the TLB as a small cache of recent address translations.


























