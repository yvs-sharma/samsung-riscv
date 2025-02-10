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
  
The task focuses on exploring C and RISC-V labs to compile C programs using both the GCC and RISC-V compilers.</summary>

### C Lab

We start by creating a file in the chosen directory using a simple editor like Leafpad. After writing the program to calculate the sum of numbers from 1 to n, save the file, close the editor, and compile it using GCC. Once compiled, you can run the program to see the output.

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

Optimization levels in GCC improve code performance and size to varying degrees. -O0 applies no optimization, suitable for debugging. -O1 offers basic optimizations, making code faster and smaller without significantly increasing compilation time, striking a balance between performance and simplicity. -Ofast prioritizes speed over strict compliance with standards, ideal for performance-critical tasks but requires thorough testing to avoid unexpected issues. Testing is crucial, as higher optimizations may complicate debugging or affect precision in critical calculations.

### Description of the commands used while execution:

**C lab**

1. cd: Changes the current working directory in a command-line interface.
2. leafpad: A simple and lightweight graphical text editor for Linux systems.
3. gcc: Performs the compilation step to build a program.
4. ./a.out: It will execute the file that was created with the compile.

**RISC-V lab**

1. -mabi=lp64: Specifies the ABI (Application Binary Interface) for RISC-V, indicating the use of the LP64 model, which uses 64-bit long integers and pointers.
2. -march=rv64i: Specifies the target architecture for RISC-V. rv64i indicates a 64-bit RISC-V processor using the base integer instruction set (I).
3. riscv-objdump: A tool that displays assembly instructions from a compiled RISC-V binary file. It helps in debugging and understanding compiled code.
4. -Ofast: An aggressive optimization level in GCC that prioritizes performance over strict standards compliance. It enables high-speed optimizations, but some may deviate from strict IEEE or ISO standards.
5. -O1: Enables basic optimizations in GCC that improve performance without significantly increasing compilation time.
</details>

----------------------------------------------------------------------------------------------------------------------------

<details>
<summary><b>TASK 4:</b> 
  
The task focuses on exploring C and RISC-V labs to compile C programs using both the GCC and RISC-V compilers.</summary>

### C Lab

We start by creating a file in the chosen directory using a simple editor like Leafpad. After writing the program to calculate the sum of numbers from 1 to n, save the file, close the editor, and compile it using GCC. Once compiled, you can run the program to see the output.

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

Optimization levels in GCC improve code performance and size to varying degrees. -O0 applies no optimization, suitable for debugging. -O1 offers basic optimizations, making code faster and smaller without significantly increasing compilation time, striking a balance between performance and simplicity. -Ofast prioritizes speed over strict compliance with standards, ideal for performance-critical tasks but requires thorough testing to avoid unexpected issues. Testing is crucial, as higher optimizations may complicate debugging or affect precision in critical calculations.

### Description of the commands used while execution:

**C lab**

1. cd: Changes the current working directory in a command-line interface.
2. leafpad: A simple and lightweight graphical text editor for Linux systems.
3. gcc: Performs the compilation step to build a program.
4. ./a.out: It will execute the file that was created with the compile.

**RISC-V lab**

1. -mabi=lp64: Specifies the ABI (Application Binary Interface) for RISC-V, indicating the use of the LP64 model, which uses 64-bit long integers and pointers.
2. -march=rv64i: Specifies the target architecture for RISC-V. rv64i indicates a 64-bit RISC-V processor using the base integer instruction set (I).
3. riscv-objdump: A tool that displays assembly instructions from a compiled RISC-V binary file. It helps in debugging and understanding compiled code.
4. -Ofast: An aggressive optimization level in GCC that prioritizes performance over strict standards compliance. It enables high-speed optimizations, but some may deviate from strict IEEE or ISO standards.
5. -O1: Enables basic optimizations in GCC that improve performance without significantly increasing compilation time.
</details>

----------------------------------------------------------------------------------------------------------------------------




