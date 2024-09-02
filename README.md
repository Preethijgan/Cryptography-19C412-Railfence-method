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
```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main() {
    int i, j, len, rails, count;
    char str[1000];
    int code[100][1000]; 

    printf("Enter a Secret Message: ");
    fgets(str, sizeof(str), stdin);  
    str[strcspn(str, "\n")] = '\0'; 

    len = strlen(str);

    printf("Enter number of rails: ");
    scanf("%d", &rails);

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

    return 0;
}


```


## OUTPUT:
![Screenshot 2024-09-02 075132](https://github.com/user-attachments/assets/ad61b820-6c56-4a4e-9f4a-97ceef4bdba2)



## RESULT:
The program is executed successfully
