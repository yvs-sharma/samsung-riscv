# Samsung-riscv
This program, guided by Kunal Ghosh Sir, focuses on RISC-V architecture and leverages open-source tools to teach VLSI chip design and RISC-V concepts.

## Basic Details:

**Name:** Sumukha Sharma Y V

**College:** Vidyavardhaka College of Engineering

**Email ID:** yvssharma007@gmail.com

**GitHub Profile:** [yvs-sharma](https://github.com/yvs-sharma)

**Linkedin Profile:** [Sumukha Sharma YV](https://www.linkedin.com/in/sumukha-sharma-yv-71213925a)

----------------------------------------------------------------------------------------------------------------------------

<details>
<summary><b>TASK 1:</b> 
  
The goal is to work with C and RISC-V labs, compiling C programs using both the GCC and RISC-V compilers.</summary>

### C Lab

First, create a file in your preferred directory using a basic editor like Leafpad. Write a program that calculates the sum of numbers from 1 to n, then save and close the editor. Next, compile the file using GCC. After compilation, run the program to view the output.

 C Code to calculate 1 to n numbers
```
#include<stdio.h>
int main()
{
  int i, sum=0, n=90;
  for(i=0;i<=n;++i)
    {
      sum+=i;
    }
  printf("Sum of numbers from 1 to %d is %d\n",n,sum);
  return 0;
}
```

The commands used are
```
gcc sum.c
./a.out

```

![image](https://github.com/user-attachments/assets/1a105a81-3e54-4135-921b-540f58007c90)

### RISC-V lab

It involves viewing the code with the cat command to ensure it’s correct.

```
cat sum.c

```
Next, compile it using the RISC-V GCC compiler.

```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum.o sum.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum.o sum.c
```
![image](https://github.com/user-attachments/assets/732013ca-7b48-4408-ac36-01ef83bfc12b)

After compiling, use

```
riscv64-unknown-elf-objdump -d sum.o

```
to disassemble the code and examine its assembly language version. This provides a closer look at how the program works at the hardware level.

The Assembly language code is displayed.

Using O1
![image](https://github.com/user-attachments/assets/955d5f39-b1ea-4c34-9027-b7aa30410faa)

Using Ofast
![image](https://github.com/user-attachments/assets/4efc08b1-1f7f-4752-87dd-4f852f58bef6)

GCC optimization levels help enhance code performance and reduce size to different extents.

-O0: No optimization is applied, making it ideal for debugging.

-O1: Introduces basic optimizations, improving speed and reducing size without significantly increasing compilation time, offering a good balance.

-Ofast: Focuses purely on speed, disregarding strict standard compliance. It's great for performance-intensive tasks but requires careful testing to prevent unexpected behavior.

Since higher optimization levels can make debugging harder or impact precision in sensitive calculations, thorough testing is essential.

### Description of the commands used while execution:

**C Lab**

-leafpad – A simple and lightweight text editor for Linux.

-gcc – Compiles the program to create an executable file.

./a.out – Executes the compiled program.

cd – Switches the working directory in the command-line interface.

**RISC-V Lab**

-march=rv64i – Defines the target architecture for RISC-V, where rv64i represents a 64-bit processor with a base integer instruction set.

-O1 – Enables basic GCC optimizations that enhance performance without greatly increasing compilation time.

-mabi=lp64 – Specifies the Application Binary Interface (ABI) for RISC-V, using 64-bit long integers and pointers.

-Ofast – A high-performance optimization flag in GCC that prioritizes speed over strict standard compliance.

riscv-objdump – A tool that disassembles RISC-V binaries, aiding in debugging and understanding compiled code.

</details>

----------------------------------------------------------------------------------------------------------------------------

<details>
<summary><b>TASK 2:</b> 
  
Conducting SPIKE simulation and debugging C code using the interactive debugging mode in Spike.</summary>

First, create a file in the selected directory using a basic editor like Leafpad. Write the program to swap two numbers, then save and close the editor.

 C Code to swap 2 numbers
```
#include<stdio.h>
void main()
{
int a=10, b=5, temp;
printf("Numbers before swap: A=%d and B=%d\n",a,b);
temp=a;
a=b;
b=temp;
printf("Numbers after swap: A=%d and B=%d\n",a,b);
}
```

The code should be compiled and simulated using both the GCC and RISC-V compilers, ensuring that the same output is displayed on the terminal for both.

The commands used are :

For gcc , 
```
gcc swap.c
./a.out

```

For riscv compiler , 
```
spike pk swap.o
```

![image](https://github.com/user-attachments/assets/1a105a81-3e54-4135-921b-540f58007c90)

Object dump using O1 and Ofast

![image](https://github.com/user-attachments/assets/732013ca-7b48-4408-ac36-01ef83bfc12b)

Using Ofast

![image](https://github.com/user-attachments/assets/955d5f39-b1ea-4c34-9027-b7aa30410faa)

Using O1

Debug:

1. To open the object dump , 
```
riscv64-unknown-elf-objdump -d swap.o | less
```

2. To debug ,
 ```
   spike -d pk swap.o
 ```
![image](https://github.com/user-attachments/assets/4efc08b1-1f7f-4752-87dd-4f852f58bef6)


### Description of the commands used while execution:

- **spike**: This is a simulator for the RISC-V Instruction Set Architecture (ISA), commonly used to simulate and test RISC-V programs. It emulates a RISC-V processor, allowing programs to run in a controlled setting.  
- **-d**: This flag activates debug mode, enabling step-by-step execution of the program. It allows you to inspect registers, memory, and other details, which is helpful for identifying issues and analyzing program behavior.  
- **pk**: Stands for proxy kernel, which serves as a lightweight operating system for RISC-V. It manages system calls and aids in running programs within the simulated environment.

### Description of assembly level instructions:  

- **addi (Add Immediate)**
  
  Format: `addi rd, rs1, imm`
  
  Adds an immediate value (imm) to the value in register `rs1` and stores the result in register `rd`.
  

- **sd (Store Doubleword)**
  
  Format: `sd rs2, offset(rs1)`
   
  Stores a 64-bit value from register `rs2` into memory at the address calculated by `offset + rs1`.

- **lui (Load Upper Immediate)**
  
  Format: `lui rd, imm`

  Shifts the immediate value (imm) left by 12 bits and stores it in the upper portion of the destination register `rd`.

- **li (Load Immediate)**
  
  Format: `li rd, imm`
  
  Loads an immediate value (imm) directly into register `rd`.
</details>

----------------------------------------------------------------------------------------------------------------------------

<details>
<summary><b>TASK 3:</b> 
  
The objective is to examine each of the given instructions, classify them by their type (R-type, I-type, or J-type), and then convert them into their corresponding 32-bit machine codes.</summary>

### What is RISC-V?

RISC-V is an open-source instruction set architecture (ISA) that allows developers to create processors tailored to specific needs, without any licensing costs. Built on reduced instruction set computer (RISC) principles, it represents the fifth generation of processors based on this concept. As an open and free alternative, RISC-V provides flexibility and easy access for developers.

### Instruction Formats in RISC-V :

The instruction format of a processor determines how machine language instructions are organized for execution. In RISC-V, instructions are made up of fields that indicate where the data is located and what operations should be performed. RISC-V has six primary instruction formats:

  1. R-format
  2. I-format
  3. S-format
  4. B-format
  5. U-format
  6. J-format

Each format serves specific purposes in the processor's operation.

![image](https://github.com/user-attachments/assets/71043fcb-ff93-4b61-8b8b-4b56f55e2414)

### 1. **R-type Instruction**:
 
This format is used for operations that involve registers rather than memory. It is mainly used for arithmetic and logical operations.  

The 32-bit instruction is divided into six fields:
![image](https://github.com/user-attachments/assets/6f289d8a-2533-4459-90ed-c4d0f234a4a9)

1. **Opcode (7 bits)**: Specifies the instruction format and the operation to be performed.  

2. **rd (5 bits)**: Represents the destination register where the result of the operation will be stored.  

3. **func3 (3 bits)**: Determines the specific arithmetic or logical operation to be carried out.  

4. **rs1 (5 bits)**: The first source register that holds the input data for the operation.  

5. **rs2 (5 bits)**: The second source register used alongside `rs1` for the computation.  

6. **func7 (7 bits)**: Provides additional details about the operation, similar to `func3`.  

These fields work together to execute arithmetic and logical instructions using registers in the RISC-V architecture.

Example : add A,B,C

32-bit Instruction: 0000000 00011 00010 000 00001 0110011


### 2. **I-type Instruction**:

The "I" in I-type stands for Immediate, indicating that the operations use both registers and an immediate (constant) value, rather than memory locations. This instruction type is mainly used for immediate and load operations.

The 32-bit instruction is divided into five fields:

1. **Opcode (7 bits)**: Specifies the operation to be performed and the instruction format.  

2. **rd (5 bits)**: Represents the destination register where the result of the operation is stored.  

3. **func3 (3 bits)**: Determines the specific operation to be carried out, such as arithmetic or logical operations.  

4. **rs1 (5 bits)**: The source register containing one of the operands for the operation.  

5. **imm (12 bits)**: The immediate value, which is a constant used in the operation.

These fields together enable operations that involve both registers and immediate values in RISC-V.

![image](https://github.com/user-attachments/assets/572d92bc-8931-4bbc-a4de-4bcee6be5020)

Example : addi A,B,15

32-bit Instruction: 000000000101 00010 000 00001 0010011


### 3. **S-type Instruction**:
   
   The "S" stands for Store, indicating that this instruction type is used to store the value from a register into memory. It is primarily used for store operations.

The 32-bit instruction is divided into six fields:
![image](https://github.com/user-attachments/assets/6f658175-7621-414b-93a7-3043495603c3)

1. **Opcode (7 bits)**: Specifies the instruction format and the operation to be performed.  

2. **imm[11:5] (7 bits)**: The upper 7 bits of a 12-bit signed immediate value, located in bits [31:25] of the instruction.  

3. **rs2 (5 bits)**: The source register containing the value to be stored in memory.  

4. **rs1 (5 bits)**: The base register used to calculate the memory address.  

5. **func3 (3 bits)**: Specifies the width and type of the store operation (e.g., word, half-word, or byte).  

6. **imm[4:0] (5 bits)**: The lower 5 bits of the 12-bit signed immediate value, located in bits [11:7] of the instruction.  

Key Features of S-type:
- S-type instructions do not have an `rd` field because they do not store values in registers.
- The value to be stored is found in the `rs2` field, while the address is calculated using `rs1` and the immediate field.

Example: sw x1, 6(x2)  

32-bit Instruction: 0000000 00001 00010 010 01000 0100011


### 4. **B-type Instruction**:

   The "B" stands for Branching, indicating that this instruction is used for conditional branching based on certain conditions.

The 32-bit instruction is divided into eight fields:
![image](https://github.com/user-attachments/assets/8003f573-890a-4b4f-910b-16459a1e7c9b)

1. **Opcode (7 bits)**: Specifies the instruction format and the operation to be performed.  

2. **imm[12] (1 bit)**: The most significant bit of a 12-bit signed immediate, located in bit [31] of the instruction.  

3. **imm[10:5] (6 bits)**: The next 6 bits of the signed immediate, located in bits [25:30] of the instruction.  

4. **imm[4:1] (4 bits)**: The next 4 bits of the signed immediate, located in bits [11:8] of the instruction.  

5. **imm[11] (1 bit)**: The second most significant bit of the signed immediate, located in bit [7] of the instruction.  

6. **rs1 (5 bits)**: The first source register used in conditional operations.  

7. **rs2 (5 bits)**: The second source register used in conditional operations.  

8. **func3 (3 bits)**: Specifies the condition for branching (e.g., equal, not equal, less than).  

### Branching Logic:  
- If the condition specified by `func3` is true, the Program Counter (PC) is updated by adding the immediate value to the current PC.  
- If the condition is false, the PC is updated by adding 4 bytes to the current PC, moving to the next instruction.  

Word Alignment:  
- RV32 instructions are word-aligned, meaning the address must always be a multiple of 4 bytes.

Example: beq x1, x2, 16 

32-bit Instruction: 0000000 00001 00010 000 00010 1100011


### 5. **U-type Instruction**:

   In the RV32 architecture, each U-type instruction is 32 bits long. The "U" stands for Upper Immediate, as these instructions are used to transfer an immediate value into the upper portion of the destination register. They are mainly used for loading large constants into registers.

The 32-bit instruction is divided into three fields:
![image](https://github.com/user-attachments/assets/4eaa9a7d-3ca8-4b32-a017-b28c7b8c9efe)

1. **Opcode (7 bits)**: Specifies the instruction format and the operation to be performed.  

2. **rd (5 bits)**: The destination register where the immediate value is transferred.  

3. **Immediate (20 bits)**: A 20-bit immediate value that is placed in the upper portion of the destination register.  

Key Instructions in U-type:

- **LUI (Load Upper Immediate)**: Loads a 20-bit immediate value into the upper portion of the destination register.  

- **AUIPC (Add Upper Immediate to PC)**: Adds a 20-bit immediate value to the current Program Counter (PC) and stores the result in the destination register.

Example: lui x1, 0x12345  

32-bit Instruction: 00010010001101000101 00001 0110111



### 6. **J-type Instruction**:

   The "J" stands for Jump, indicating that this instruction format is used for jump-type operations, typically for branching to a specific memory location. J-type instructions are mainly used for implementing jumps and loops, allowing the program to branch to desired memory locations.

The 32-bit instruction is divided into six fields:
![image](https://github.com/user-attachments/assets/e0add552-671b-4240-bb4a-cebe14c59a1a)

1. **Opcode (7 bits)**: Specifies the instruction format and the operation to be performed.  

2. **rd (5 bits)**: The destination register used to store the return address in jump operations.  

3. **Immediate (20 bits)**: A 20-bit signed immediate value that represents the offset for the jump.  

Key Instruction in J-type:
- **JAL (Jump and Link)**: This instruction performs a jump to the target address specified by the immediate value and stores the return address (the next instruction's address) in the destination register (`rd`).

Example: jal x1, 2048 

32-bit Instruction: 000000000010 0000000000 00001 1101111
</details>

----------------------------------------------------------------------------------------------------------------------------

<details>
<summary><b>TASK 4:</b> 
  
To conduct a functional simulation of the provided RISC-V Core Verilog netlist and testbench.</summary>

**Note**: The Verilog code and testbench for the RISC-V processor have already been created.

### Step 1: Installation of iverilog and gtkwave

Use the following commands for installation:

1. For iverilog ,
` $ sudo apt install iverilog`

2. For gtkwave,
` $ sudo apt install gtkwave`

### Step 2: Creating files for verilog and testbench by following commands
`  $ gedit iiitb_rv32i.v`
` $ gedit iiitb_rv32i_tb.v`

### Step 3: To simulate and run the verilog code , 
`  $ iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v`
` $ ./iiitb_rv32i`

### Step 4: Command to see the simulation waveform ,
`  $ gtkwave iiitb_rv32i.vcd`

The gtkwave will be opened and the following window will appear.
![image](https://github.com/user-attachments/assets/17c33cea-da53-448e-a1bd-444a42554025)


### Step 5: Analysing output waveform

Some of the output waveforms are given here ,

**1. sub r7 , r1 , r2**
![sub](https://github.com/user-attachments/assets/f4828f86-c400-43d2-9f0e-2c8d799dd9e2)

Here , the subtraction of r2 from r1 happens and the result is stored in r7.


**2. add r6 , r1 , r2**
![add](https://github.com/user-attachments/assets/e74c7763-8243-4ac9-8813-d76c7b197823)

Here , the sum of r2 from r1 happens and the result is stored in r6.


**3. and r8 , r1 , r3**
![and](https://github.com/user-attachments/assets/b37ebca2-2c48-47fb-b31a-7f5505016061)

Here , bitwise AND is performed between r1 and r3 , the result is stored in r8.


**4. or r9 , r2 , r5**
![or](https://github.com/user-attachments/assets/73640edf-7b2b-439d-ab6d-77115fa937cc)

Here , bitwise OR is performed between r2 and r5 , the result is stored in r9.


**5. xor r10 , r1 , r4**
![xor](https://github.com/user-attachments/assets/191e8185-9413-435a-9356-25edb7e2f29c)

Here , bitwise XOR is performed between r1 and r4 , the result is stored in r10.


**6. addi r12 , r4 , 5**
![image](https://github.com/user-attachments/assets/820e90ca-f119-49ab-ad87-d668344aa01f)

Here , the immediate data 5 is added to the register r4 , the result is stored in r12.


**7. lw r13 , r1 , 2**
![lw](https://github.com/user-attachments/assets/a2016bd8-8770-470e-bcfe-d580e3c78c35)

Here , the word from memory address r1 + 2 is loaded into r13.


**8. beq r0 , r0 , 15**
![beq](https://github.com/user-attachments/assets/f97b95d4-079a-4eb3-ae74-9443fe4dc929)

Here , the Branching happens to PC + 15 if r0 == r0 (always true)

</details>

----------------------------------------------------------------------------------------------------------------------------




