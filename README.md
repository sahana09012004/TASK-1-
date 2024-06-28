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
SPIKE Simulation 
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/c91baf0b-1a80-46cc-9fe4-f248b2b0ea86)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/b709256c-b0a8-49c6-b2ab-c373178fe03f)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/e296e5a5-4830-4148-96e4-beab579d0cc5)


OUTPUT IN RISC-V
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/bf1f5c46-44e0-44e5-a1d7-b9052d71cbee)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/6f9d35cd-7d44-4283-a1d4-8f48d4efd2bc)
![image](https://github.com/sahana09012004/TASK-1-/assets/150324046/40a2c21e-e6fe-4d29-88e8-4ec0d1a69e46)


Hence the output in both spike and RISC-V is verfied.



