TASK 1 
The First task was to install the necessary softwares like virtual box , Risc-v tool and run a C program that counts 1 to N 
insttaling virtual box
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/80faafdc-45e1-4534-816b-0f105889e7eb)
Installing Ubuntu
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/3ca8366d-6633-4fde-bb3a-f74f2781582f)
C Code and output 
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/a02725f3-4de9-489c-a951-284bc18fcffa)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/aa608163-ab2f-4ab8-9500-af0936fc68b4)
TASK 2 
The provided C program is a simple implementation of an Automated  Vending Machine with change . The program offers the different juices and balance .
#include <stdio.h>

int main() {
  // Define drink prices (adjust as needed)
  float coke_price = 1.00;
  float juice_price = 1.50;

  // Variables for user input and calculations
  int choice, inserted_money = 0;
  float change;

  // Welcome message
  printf("Welcome to the Vending Machine!\n");

  while (1) {
    // Display menu
    printf("\nDrinks:\n");
    printf("1. Coke ($%.2f)\n", coke_price);
    printf("2. Juice ($%.2f)\n", juice_price);
    printf("3. Exit\n");
    printf("Enter your choice: ");
    scanf("%d", &choice);

    // Handle user selection
    switch (choice) {
      case 1:
      case 2:
        printf("You selected ");
        if (choice == 1) {
          printf("Coke ($%.2f).\n", coke_price);
        } else {
          printf("Juice ($%.2f).\n", juice_price);
        }

        // Loop for money insertion
        while (inserted_money < (choice == 1 ? coke_price : juice_price)) {
          printf("Insert money (minimum $%.2f): ", (choice == 1 ? coke_price : juice_price) - inserted_money);
          scanf("%d", &inserted_money);
        }

        // Calculate and display change
        change = inserted_money - (choice == 1 ? coke_price : juice_price);
        printf("Thank you! Please take your drink and your change ($%.2f).\n", change);
        inserted_money = 0; // Reset inserted money for next purchase
        break;
      case 3:
        printf("Thank you for using the Vending Machine!\n");
        return 0; // Exit loop
      default:
        printf("Invalid choice. Please try again.\n");
    }
  }

  return 0;
}
CODE BREAK DOWN 


Main function 
int main() {
  // Define drink prices (adjust as needed)
  float coke_price = 1.00;
  float juice_price = 1.50;

  // Variables for user input and calculations
  int choice, inserted_money = 0;
  float change;

  // Welcome message
  printf("Welcome to the Vending Machine!\n");
LOOP FUNCTION 
 while (inserted_money < (choice == 1 ? coke_price : juice_price)) {
          printf("Insert money (minimum $%.2f): ", (choice == 1 ? coke_price : juice_price) - inserted_money);
          scanf("%d", &inserted_money);
        }

        
        CODE IN LEAFPAD 
![c program in leafpad](https://github.com/sahana09012004/TASK-1-/assets/150324046/80828039-3426-4e9e-bd41-62d0f498ca2f)


![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/9d589350-c651-4d7a-b5be-fef8af054cd2)


TASK 3 
Verification with Optimization Levels:

Verify the program's behavior with two different levels of optimization:

-O1: This optimization level enables basic optimizations that improve performance without significantly increasing compilation time.

-Ofast: This level enables aggressive optimizations, potentially breaking strict standards compliance for maximum performance.

SPIKE Simulation 
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/c91baf0b-1a80-46cc-9fe4-f248b2b0ea86)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/b709256c-b0a8-49c6-b2ab-c373178fe03f)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/e296e5a5-4830-4148-96e4-beab579d0cc5)


OUTPUT IN RISC-V
debug command riscv64-unknown-elf-objdump -d ticketterminal.o |less

![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/bf1f5c46-44e0-44e5-a1d7-b9052d71cbee)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/6f9d35cd-7d44-4283-a1d4-8f48d4efd2bc)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/40a2c21e-e6fe-4d29-88e8-4ec0d1a69e46)


Hence the output in both spike and RISC-V is verfied.




TASK 4 
Identify various RISC-V instruction type (R, I, S, B, U, J) and exact 32-bit instruction code in the instruction type format for below RISC-V instructions.


INSTRUCTIONS:
     ADD r1, r2, r3
     
     SUB r3, r1, r2
     
     AND r2, r1, r3
     
     OR r8, r2, r5
     XOR r8, r1, r4
     SLT r10, r2, r4
     ADDI r12, r3, 5
     SW r3, r1, 4
     SRL r16, r11, r2
     BNE r0, r1, 20
     BEQ r0, r0, 15
     LW r13, r11, 2
     SLL r15, r11, r2
Upload the 32-bit pattern on Github.

RISC-V is an open standard Instruction Set Architecture (ISA) that uses a modular design, allowing for a simple and scalable instruction set. Here are the main instruction types in RISC-V:

1. R-Type (Register Type)  *_Purpose_: Used for arithmetic and logical operations.
  Format_: 31   25 24  20 19  15 14  12 11   7 6   0.
             funct7 rs2 rs1 funct3 rd   opcode.
   
  opcode_: Operation code, specifies the operation to be performed.
  
  rs1, rs2_: Source registers.
  
  rd_: Destination register.
  funct3, funct7_: Function fields, provide more specificity for the operation.
  Efficiency_:*Uses only registers, which are faster to access compared to memory.
                *Allows for complex arithmetic and logical operations without memory access overhead.

              
  Flexibility_:*Supports a wide range of operations (e.g., addition, subtraction, bitwise operations).
                 *Function fields (funct3, funct7) allow for many operations to be encoded in a compact format.
   ADD r1, r2, r3:
    funct7 (7 bits)_: 0000000.
    
   rs2 (5 bits)_: 00011.
   
   rs1 (5 bits)_: 00010.
   
   funct3 (3 bits)_: 000.
   
   rd (5 bits)_: 00001.
   opcode (7 bits)_: 0110011.
   32 bit binary patterns_:
           0000000 00011 00010 000 00001 0110011.




   XOR r8, r1, r4:
      *_funct7 (7 bits)_: 0000000.
   *_rs2 (5 bits)_: 00100.
   *_rs1 (5 bits)_: 00001.
   *_funct3 (3 bits)_: 100.
   *_rd (5 bits)_: 01000.
   *_opcode (7 bits)_: 0110011.
   *_32-bit binary patterns_:
            0000000 00100 00001 100 01000 0110011.




2.I-Type (Immediate) Instructions:

In the RISC-V architecture, I-type instructions are mostly used for operations using instantaneous values, which are constants that are integrated into the instruction itself. These instructions can load data from memory, carry out arithmetic operations, and apply instantaneous values to different types of calculations. They play a crucial role in streamlining code that often has to employ constants, allowing for effective data manipulation without the need for extra load instructions.

I-type instructions improve efficiency and code density by eliminating the need for many instructions to complete a single job, therefore streamlining processes. Because load instructions enable data to be retrieved directly into registers from memory, they are also essential for efficient memory access. All things considered, I-Type instructions greatly increase the RISC-V instruction's adaptability and efficiency.

   *_Purpose_: Used for operations involving a constant (immediate) value and for load instructions.
   *_Format_: 31     20 19  15 14  12 11   7 6 0.
              immediate rs1 funct3 rd   opcode.
   *_opcode_: Operation code.
   *_rs1_: Source register.
   *_rd_: Destination register.
   *_funct3: Function field.
   *_immediate_: 12-bit immediate value.
   *_Efficiency_:*Combines a register and an immediate value, reducing the need for additional instructions to load constants.
                 *Immediate values are embedded within the instruction, allowing quick access and reducing memory usage.
   *_Flexibility_:*Useful for arithmetic operations with constants and for load  instructions.
           *Supports operations like immediate addition, bit shifts, and load from memory.

  
  
  ADDI r12, r3, 5
     *_immediate (12 bits)_: 000000000101.
   *_rs1 (5 bits)_: 00011.
   *_funct3 (3 bits)_: 000.
   *_rd (5 bits)_: 01100.
   *_opcode (7 bits)_: 0010011.
   *_32-bit binary patterns_:
            000000000101 00011 000 01100 0010011.
  
  
  
  
  
3.S-Type (Store) Instructions:

S-type instructions are used for storing data from a register to memory. The immediate value is split between two fields for encoding purposes. S-Type instructions in RISC-V are primarily used for storing data from a register to memory. These instructions are essential for memory operations where data needs to be written to a specific memory address.

The S-Type instructions work by taking the contents of a source register and storing it at a memory address computed from a base register plus an immediate offset. This immediate offset allows for flexible addressing modes, enabling access to different memory locations relative to the base address.

The typical operations in this category include SW (Store Word), SH (Store Halfword), and SB (Store Byte), which store 32-bit, 16-bit, and 8-bit values, respectively. S-type instructions play a crucial role in efficient data handling and manipulation, ensuring that the CPU can interact with memory effectively for various computational tasks and real-world applications.
SW r3, r1, 4
  *_immediate (12 bits)_: 000000000100 (split as 7 and 5 bits).
  *_rs2 (5 bits)_: 00011.
  *_rs1 (5 bits)_: 00001.
  *_funct3 (3 bits)_: 010.
  *_opcode (7 bits)_: 0100011.
  *_32-bit binary patterns_:
           0000000 00011 00001 010 00010 0100011.
  
  
  
  
  
  
  32-bit binary patterns:
  *_ADD  r1, r2, r3_: 00000000001100010000000010110011.
  *_SUB  r3, r1, r2_: 01000000001000001000000110110011.
  *_AND  r2, r1, r3_: 00000000001100001111000010010011.
  *_OR   r8, r2, r5_: 00000000010100010110000100010011.
  *_XOR  r8, r1, r4_: 00000000010000001100000100010011.
  *_SLT  r10, r2, r4_: 00000000010000010101000101010011.
  *_ADDI r12, r3, 5_: 00000000010100010000001100010011.
  *_SW   r3, r1, 4_: 00000000001100001010001000110011.
  *_SRL  r16, r11, r2_: 00000000001001011101000000110011.
  *_BNE  r0, r1, 20_: 00000000001000000000100101100011.
  *_BEQ  r0, r0, 15_: 00000000000000000000011111100011.
  *_LW   r13, r11, 2_: 00000000001001011010001100100011.
  *_SLL  r15, r11, r2_: 00000000001001011000001111010011.
These binary patterns represent the 32-bit encoded instructions for each of the specified RISC-V instructions.


   



