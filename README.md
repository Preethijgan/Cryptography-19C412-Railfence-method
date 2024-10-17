# Rail Fence Cipher
Rail Fence Cipher using with different key values

## AIM:
To develop a simple C program to implement Rail Fence Cipher.

## DESIGN STEPS:
Step 1:
Design of Rail Fence Cipher algorithnm

Step 2:
Implementation using C or pyhton code

Step 3:
Testing algorithm with different key values. ALGORITHM DESCRIPTION: In the rail fence cipher, the plaintext is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

## PROGRAM:
```C
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

void encrypt(char str[], int rails);
void decrypt(char str[], int rails);

int main() {
    int choice, rails;
    char str[1000];

    printf("Enter a Message: ");
    fgets(str, sizeof(str), stdin);  
    str[strcspn(str, "\n")] = '\0'; 

    printf("Enter number of rails: ");
    scanf("%d", &rails);

    printf("Choose an option:\n1. Encrypt\n2. Decrypt\n");
    scanf("%d", &choice);

    if (choice == 1) {
        encrypt(str, rails);
    } else if (choice == 2) {
        decrypt(str, rails);
    } else {
        printf("Invalid choice.\n");
    }

    return 0;
}

void encrypt(char str[], int rails) {
    int i, j, len, count;
    int code[100][1000]; 

    len = strlen(str);

    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            code[i][j] = 0;
        }
    }

    count = 0;  
    j = 0;      

    while (j < len) {
        if (count % 2 == 0) {
            for (i = 0; i < rails && j < len; i++) {
                code[i][j] = (int)str[j]; 
                j++;
            }
        } else {
            for (i = rails - 2; i > 0 && j < len; i--) {
                code[i][j] = (int)str[j]; 
                j++;
            }
        }
        count++;
    }

    printf("\nEncrypted Message: ");
    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            if (code[i][j] != 0) {
                printf("%c", code[i][j]);
            }
        }
    }
    printf("\n");
}

void decrypt(char str[], int rails) {
    int i, j, len, count;
    int code[100][1000];
    char decrypted[1000];

    len = strlen(str);

    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            code[i][j] = 0;
        }
    }

    count = 0;
    j = 0;
    int index = 0;

    while (j < len) {
        if (count % 2 == 0) {
            for (i = 0; i < rails && j < len; i++) {
                code[i][j] = 1; 
                j++;
            }
        } else {
            for (i = rails - 2; i > 0 && j < len; i--) {
                code[i][j] = 1; 
                j++;
            }
        }
        count++;
    }

    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            if (code[i][j] == 1) {
                code[i][j] = (int)str[index++];
            }
        }
    }

    index = 0;
    j = 0;

    while (j < len) {
        if (count % 2 == 0) {
            for (i = 0; i < rails && j < len; i++) {
                decrypted[j] = (char)code[i][j];
                j++;
            }
        } else {
            for (i = rails - 2; i > 0 && j < len; i--) {
                decrypted[j] = (char)code[i][j];
                j++;
            }
        }
        count++;
    }
    decrypted[j] = '\0';

    printf("\nDecrypted Message: %s\n", decrypted);
}



```


## OUTPUT:
![Screenshot 2024-10-17 093518](https://github.com/user-attachments/assets/550a8eef-bfd3-4069-bf11-9fd46cde0972)
![Screenshot 2024-10-17 093604](https://github.com/user-attachments/assets/0d0fe0ae-3551-418e-aaa0-09de62d38c89)






## RESULT:
The program is executed successfully
