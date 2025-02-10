# Samsung-riscv
This program, guided by Kunal Ghosh Sir, focuses on RISC-V architecture and leverages open-source tools to teach VLSI chip design and RISC-V concepts.
## Basic Details:

**Name:** Sumukha Sharma Y V

**College:** Vidyavardhaka College of Engineering

**Email ID:** yvssharma007@gmail.com

**GitHub Profile:** [yvs-sharma](https://github.com/yvs-sharma)

----------------------------------------------------------------------------------------------------------------------------

<details>
<summary><b>TASK 1:</b> 

The task involves learning from C-based and RISC-V-based lab videos and compiling C code using both GCC and RISC-V compilers. 
In the C-based lab, you start by creating a file in your chosen directory using a text editor like gedit.

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
After writing a simple program to calculate the sum of numbers from 1 to n, you save and close the file. Then, you use the GCC compiler to compile and run the code, which gives you the output.
The commands used are
```
gcc sum1ton.c
./a.out
```
![image](https://github.com/user-attachments/assets/be6a91ae-3a5e-45ec-bd1a-933c33bae4a0)

In the RISC-V lab, the process is a bit different since it uses the RISC-V GCC compiler. First, you check the code using the cat command to make sure everything looks good.
```
cat sum.c
```
Then, you compile the code using special RISC-V options like -mabi=lp64, which is for 64-bit systems, and -march=rv64i, which targets the 64-bit RISC-V architecture.
The commands used are as follows:
```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum.o sum.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum.o sum.c
```
![image](https://github.com/user-attachments/assets/f9372c88-e5ce-4d54-af81-6b45dd51bb83)

After compiling, you can generate the assembly language version of the code using the following command. 

```
riscv64-unknown-elf-objdump -d sum.o
```
This helps you dive deeper into the code and understand its structure, like where the main function is located.

The Assembly language code is displayed.


Using O1

![image](https://github.com/user-attachments/assets/94aa1555-d430-4123-ba52-5b3e7dfb8dfe)

Using Ofast

Different optimization levels are available to improve how your code runs. For example, -O1 makes the code faster and smaller without taking too much time to compile. On the other hand, -Ofast pushes the speed to the max but might not stick to strict rules, which is fine for performance-heavy tasks. Other levels include -O0 for no optimization, -O2 for smarter improvements, -O3 for top-notch performance, and -Os for keeping the code compact. While higher optimizations can make your program faster, they might also cause unexpected issues, so it’s important to test everything carefully, especially in more complicated setups.
