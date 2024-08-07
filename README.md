<details>
  <summary>TASK 1</summary>
The First task was to install the necessary softwares like virtual box , Risc-v tool and run a C program that counts 1 to N 
insttaling virtual box
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/80faafdc-45e1-4534-816b-0f105889e7eb)
Installing Ubuntu
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/3ca8366d-6633-4fde-bb3a-f74f2781582f)
C Code and output 
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/a02725f3-4de9-489c-a951-284bc18fcffa)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/aa608163-ab2f-4ab8-9500-af0936fc68b4)
</details>
<details>
  <summary>TASK 2</summary>
The provided C program is a simple implementation of an Automated  Vending Machine with change . The program offers the different juices and balance .

  ```
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
```
CODE BREAK DOWN 


Main function 
```
int main() {
  // Define drink prices (adjust as needed)
  float coke_price = 1.00;
  float juice_price = 1.50;

  // Variables for user input and calculations
  int choice, inserted_money = 0;
  float change;

  // Welcome message
  printf("Welcome to the Vending Machine!\n");
```
LOOP FUNCTION 
```
 while (inserted_money < (choice == 1 ? coke_price : juice_price)) {
          printf("Insert money (minimum $%.2f): ", (choice == 1 ? coke_price : juice_price) - inserted_money);
          scanf("%d", &inserted_money);
        }
```
        
        CODE IN LEAFPAD 
![c program in leafpad](https://github.com/sahana09012004/TASK-1-/assets/150324046/80828039-3426-4e9e-bd41-62d0f498ca2f)


![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/9d589350-c651-4d7a-b5be-fef8af054cd2)

</details>
<details>
  <summary>TASK 3</summary>
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

</details>
<details>
  <summary>TASK 4</summary>
Identify various RISC-V instruction type (R, I, S, B, U, J) and exact 32-bit instruction code in the instruction type format for below RISC-V instructions.


INSTRUCTIONS:

```
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

```

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
    funct7 (7 bits)_: 0000000.

    
   rs2 (5 bits)_: 00100.

   
   rs1 (5 bits)_: 00001.

   
   funct3 (3 bits)_: 100.

   
   rd (5 bits)_: 01000.

   
   opcode (7 bits)_: 0110011.

   
   32-bit binary patterns_:

   
            0000000 00100 00001 100 01000 0110011.




2.I-Type (Immediate) Instructions:

In the RISC-V architecture, I-type instructions are mostly used for operations using instantaneous values, which are constants that are integrated into the instruction itself. These instructions can load data from memory, carry out arithmetic operations, and apply instantaneous values to different types of calculations. They play a crucial role in streamlining code that often has to employ constants, allowing for effective data manipulation without the need for extra load instructions.

I-type instructions improve efficiency and code density by eliminating the need for many instructions to complete a single job, therefore streamlining processes. Because load instructions enable data to be retrieved directly into registers from memory, they are also essential for efficient memory access. All things considered, I-Type instructions greatly increase the RISC-V instruction's adaptability and efficiency.

   Purpose_: Used for operations involving a constant (immediate) value and for load instructions.
   Format_: 31     20 19  15 14  12 11   7 6 0.
              immediate rs1 funct3 rd   opcode.
   opcode_: Operation code.
   
   rs1_: Source register.
   
   rd_: Destination register.
   
   funct3: Function field.
   
   immediate_: 12-bit immediate value.
   
   Efficiency_:*Combines a register and an immediate value, reducing the need for additional instructions to load constants.
                 *Immediate values are embedded within the instruction, allowing quick access and reducing memory usage.
                 
   Flexibility_:*Useful for arithmetic operations with constants and for load  instructions.
           *Supports operations like immediate addition, bit shifts, and load from memory.

  
  
  ADDI r12, r3, 5
    immediate (12 bits)_: 000000000101.

    
   rs1 (5 bits)_: 00011.

   
   funct3 (3 bits)_: 000.

   
   rd (5 bits)_: 01100.

   
   opcode (7 bits)_: 0010011.

   
   32-bit binary patterns_:

   
            000000000101 00011 000 01100 0010011.
  
  
  
  
  
3.S-Type (Store) Instructions:

S-type instructions are used for storing data from a register to memory. The immediate value is split between two fields for encoding purposes. S-Type instructions in RISC-V are primarily used for storing data from a register to memory. These instructions are essential for memory operations where data needs to be written to a specific memory address.

The S-Type instructions work by taking the contents of a source register and storing it at a memory address computed from a base register plus an immediate offset. This immediate offset allows for flexible addressing modes, enabling access to different memory locations relative to the base address.

The typical operations in this category include SW (Store Word), SH (Store Halfword), and SB (Store Byte), which store 32-bit, 16-bit, and 8-bit values, respectively. S-type instructions play a crucial role in efficient data handling and manipulation, ensuring that the CPU can interact with memory effectively for various computational tasks and real-world applications.


SW r3, r1, 4
  immediate (12 bits)_: 000000000100 (split as 7 and 5 bits).

  
  rs2 (5 bits)_: 00011.

  
  rs1 (5 bits)_: 00001.

  
  funct3 (3 bits)_: 010.

  
  opcode (7 bits)_: 0100011.

  
  32-bit binary patterns_:

  
           0000000 00011 00001 010 00010 0100011.
  
  
  
  
  
  
  32-bit binary patterns:

ADD  r1, r2, r3_: 00000000001100010000000010110011.

    SUB  r3, r1, r2_: 01000000001000001000000110110011.

  AND  r2, r1, r3_: 00000000001100001111000010010011.

   OR   r8, r2, r5_: 00000000010100010110000100010011.

   XOR  r8, r1, r4_: 00000000010000001100000100010011.

  SLT  r10, r2, r4_: 00000000010000010101000101010011.
  
  ADDI r12, r3, 5_: 00000000010100010000001100010011.
  
  SW   r3, r1, 4_: 00000000001100001010001000110011.
  
  SRL  r16, r11, r2_: 00000000001001011101000000110011.
  
  BNE  r0, r1, 20_: 00000000001000000000100101100011.
  
  BEQ  r0, r0, 15_: 00000000000000000000011111100011.
  
  LW   r13, r11, 2_: 00000000001001011010001100100011.
  
  SLL  r15, r11, r2_: 00000000001001011000001111010011.
  
These binary patterns represent the 32-bit encoded instructions for each of the specified RISC-V instructions.
</details>

<details>
  <summary>TASK 5</summary>
RISC-V Core Verilog netlist and Testbench for Functional simulation
I have developed a set of commands and achieved the desired output for my project. This was accomplished by referece above and the key sources, which provided valuable guidance and examples. These references were in understanding the required techniques and applying them effectively in my implementation.
In this task we will obtain the waveform for RISC-V using Verilog Code and Verilog Testbench

![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/1fca4a0f-1840-412b-82dc-4e2690a33a1a)



OUTPUT 
1. ADD (r1,r2,r3)
   ![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/e2128b27-0ba9-42b8-89ac-1436e4210d73)
2. SUB (r3,r1,r2)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/011df5bf-8775-41b3-94cb-4368c363e460)
3.OR (r8,r2,r5)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/74e7c14d-e34b-4687-a3b6-55e647bce44a)
4.XOR (r8,r1,r4)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/7f93c126-7f67-40cd-8244-759709b464f4)
5.BEQ (r0,r0,15)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/4c9ce01b-fe2e-4084-8611-0413d558e862)
6.SLL (r15,r11,r2)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/748ad86f-08e2-4daa-82a6-b6ecd57178b3)
7.BNE (r0,r1,20)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/19f53256-5bbf-49a3-8ddd-3b3aee0b415a)
8.GTKWAVE WINDOW
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/baf78d7f-735d-42e3-a38f-b9754e382ed8)

</details>
<details>
  <summary>TASK 6</summary>
Using the VSDsquadron mini board, the Vending Machine project simulates the operation of vending machines. LEDs are used to show the machine's various states and operations, and push buttons are used to input coins of various denominations into this system. The project manages the coin inputs and provides change in accordance by implementing a state machine in C, making it an interactive and educational project for learning embedded systems and state machine design.

<br><em>COMPONENTS FOR VENDING MACHINE </em>

1.VSDsquadron Mini Board

2.Buttons

3.LEDs

4.Breadboard

5.Connecting Wires

6.Coin dispenser module

Corresponding Pins 
VCC- 5V pin 
GND - GND pin 
LED-GPIO pins

PROGRAM 

```
#include "stm32f10x.h" // Include the STM32F10x standard peripheral library      
#include <stdio.h>      
#include <stdbool.h>    

// Define states    
typedef enum {    
    S0,  // Initial state
    S5,  // State after 5 cents coin inserted    
    S10, // State after 10 cents coin inserted    
    S20, // State after 20 cents coin inserted    
    S50  // State after 50 cents coin inserted    
} State;    

// Function prototypes    
void vending_machine(State *state, int coin, bool *nw_pa, bool *ret5, bool *ret10, bool *ret20);    
void GPIO_Config(void);    
int read_coin(void);    
void update_outputs(bool nw_pa, bool ret5, bool ret10, bool ret20);    

// Function to handle state transitions and actions    
void vending_machine(State *state, int coin, bool *nw_pa, bool *ret5, bool *ret10, bool *ret20) {    
    *nw_pa = false;
    *ret5 = false;    
    *ret10 = false;    
    *ret20 = false;  

    switch (*state) {    
        case S0:    
            if (coin == 1) *state = S5;    
            else if (coin == 2) *state = S10;    
            else if (coin == 3) *state = S20;    
            else if (coin == 4) *state = S50;    
            break;
        case S5:    
            *nw_pa = true;    
            if (coin >= 2) *ret5 = true;    
            if (coin >= 3) *ret10 = true;    
            if (coin == 4) *ret20 = true;    
            break;    
        case S10:    
            *nw_pa = true;    
            if (coin >= 3) *ret10 = true;    
            if (coin == 4) *ret20 = true;    
            break;    
        case S20:    
            *nw_pa = true;    
            if (coin == 4) *ret20 = true;    
            break;    
        case S50:    
            *nw_pa = true;    
            break;    
        default:    
            *state = S0;    
            break;    
    }
}

// Configure GPIO pins for input (coin buttons) and output (indicators)
void GPIO_Config(void) {    
    GPIO_InitTypeDef GPIO_InitStructure;    

    // Enable clock for Port D    
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE);    

    // Configure GPIOs for input (coin buttons)    
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_3 | GPIO_Pin_4 | GPIO_Pin_5 | GPIO_Pin_6;    
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU; // Input with pull-up    
    GPIO_Init(GPIOD, &GPIO_InitStructure);

    // Configure GPIOs for output (indicators)    
    GPIO_InitStructure.GPIO_Pin = GPIO_Pin_0 | GPIO_Pin_1 | GPIO_Pin_2;    
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP; // Push-pull output    
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;    
    GPIO_Init(GPIOD, &GPIO_InitStructure);    
}

// Read the coin inserted (1, 2, 3, or 4 for 5c, 10c, 20c, 50c)    
int read_coin(void) {    
    if (!GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_3)) return 1;    
    if (!GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_4)) return 2;    
    if (!GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_5)) return 3;    
    if (!GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_6)) return 4;    
    return 0;    
}    
    
// Update GPIO outputs based on vending machine state    
void update_outputs(bool nw_pa, bool ret5, bool ret10, bool ret20) {    
    if (nw_pa) {    
        GPIO_SetBits(GPIOD, GPIO_Pin_0); // Set NW_PA output pin    
    } else {    
        GPIO_ResetBits(GPIOD, GPIO_Pin_0); // Reset NW_PA output pin    
    }    

    if (ret5) {    
        GPIO_SetBits(GPIOD, GPIO_Pin_1); // Set RET_5 output pin    
    } else {    
        GPIO_ResetBits(GPIOD, GPIO_Pin_1); // Reset RET_5 output pin    
    }    

    if (ret10) {    
        GPIO_SetBits(GPIOD, GPIO_Pin_2); // Set RET_10 output pin    
    } else {    
        GPIO_ResetBits(GPIOD, GPIO_Pin_2); // Reset RET_10 output pin    
    }    
}    

int main(void) {    
    State state = S0;    
    bool nw_pa = false, ret5 = false, ret10 = false, ret20 = false;    
    int coin;    

    // Initialize GPIO and configure peripherals    
    GPIO_Config();    

    while (1) {    
        coin = read_coin();    

        if (coin != 0) {    
            vending_machine(&state, coin, &nw_pa, &ret5, &ret10, &ret20);    
            update_outputs(nw_pa, ret5, ret10, ret20);    
            
            // Delay to debounce and ensure stable button readings    
            for (int i = 0; i < 100000; ++i) {    
                __NOP();    
            }      
        }    
    }    
}

```  
</details>

## PIN DIAGRAM

```
-------------------------------------------
| Pin | Function             | Connection  |
-------------------------------------------
| VCC | Power Supply         | 5V          |
| GND | Ground               | Ground      |
| D0  | Motor 1 Control      | Motor Driver|
| D1  | Motor 2 Control      | Motor Driver|
| D2  | Motor 3 Control      | Motor Driver|
| D3  | Motor 4 Control      | Motor Driver|
| D4  | Coin Acceptor Signal | Coin Acceptor|
| D5  | Bill Acceptor Signal | Bill Acceptor|
| D6  | Product Sensor 1     | Sensor      |
| D7  | Product Sensor 2     | Sensor      |
| D8  | Product Sensor 3     | Sensor      |
| D9  | Product Sensor 4     | Sensor      |
| D10 | Keypad Row 1         | Keypad      |
| D11 | Keypad Row 2         | Keypad      |
| D12 | Keypad Row 3         | Keypad      |
| D13 | Keypad Row 4         | Keypad      |
| TX  | Transmit Pin         | Serial Device|
| RX  | Receive Pin          | Serial Device|
| SDA | I2C Data Pin         | I2C Device  |
| SCL | I2C Clock Pin        | I2C Device  |
| A0  | Display Control 1    | Display     |
| A1  | Display Control 2    | Display     |
| A2  | Display Control 3    | Display     |
| A3  | Display Control 4    | Display     |
| PWM1| PWM Pin 1            | Motor Driver|
| PWM2| PWM Pin 2            | Motor Driver|

```  
PROJECT DEMONSTRATION :
https://drive.google.com/file/d/1eSQ_JeUjuP-3Olc6P18xBKogo6NMC45I/view?usp=drivesdk
