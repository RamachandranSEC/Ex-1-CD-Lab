# Ex-1 IMPLEMENTATION-OF-SYMBOL-TABLE
## Name: KAVINRAJ.S
## Register No : 212223100019
# AIM:
## To write a C program to implement a symbol table.
# ALGORITHM:
1.	Start the program.
2.	Get the input from the user with the terminating symbol ‘$’.
3.	Allocate memory for the variable by dynamic memory allocation function.
4.	If the next character of the symbol is an operator then only the memory is allocated.
5.	While reading, the input symbol is inserted into symbol table along with its memory address.
6.	The steps are repeated till ‘$’ is reached.
7.	To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
8.	Stop the program. 
# PROGRAM:
```
#include <stdio.h> 
#include <ctype.h> 
#include <string.h> 
#include <stdlib.h>

#define MAX_EXPRESSION_SIZE 100

int main() {
    int i = 0, j = 0, x = 0, n, flag = 0; 
    void *add[5];
    char b[MAX_EXPRESSION_SIZE], d[15], c, srch;

    // Input the expression terminated by '$'
    printf("Enter the Expression terminated by $: ");
    while((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) { 
        b[i++] = c;
    }
    b[i] = '\0'; // Null-terminate the string
    n = i - 1;

    // Display the given expression
    printf("Given Expression: %s\n", b);

    // Symbol table heading
    printf("\nSymbol Table\n"); 
    printf("Symbol\taddr\ttype\n");

    // Build symbol table
    for(j = 0; j <= n; j++) { 
        c = b[j];
        if (isalpha((unsigned char)c)) { // Check if the character is a letter
            if (j == n) {
                void *p = malloc(sizeof(char)); 
                add[x] = p;
                d[x] = c; 
                printf("%c\t%p\tidentifier\n", c, p);
            } else {
                char ch = b[j + 1];
                if (ch == '+' || ch == '-' || ch == '*' || ch == '=') { 
                    void *p = malloc(sizeof(char));
                    add[x] = p;
                    d[x] = c; 
                    printf("%c\t%p\tidentifier\n", c, p); 
                    x++;
                }
            }
        }
    }

    // Search for a symbol
    printf("\nThe symbol to be searched: "); 
    getchar(); // To consume the newline character left by the previous input
    srch = getchar();
    
    for(i = 0; i <= x; i++) { 
        if (srch == d[i]) {
            printf("Symbol Found\n"); 
            printf("%c @ address %p\n", srch, add[i]); 
            flag = 1;
        }
    }

    if(flag == 0) {
        printf("Symbol Not Found\n");
    }

    // Free dynamically allocated memory
    for (i = 0; i <= x; i++) {
        free(add[i]);
    }

    return 0;
}
```
# OUTPUT:

![Screenshot 2024-10-17 144724](https://github.com/user-attachments/assets/b129e593-045e-4d55-9780-f0c2def769fa)


# RESULT:
The program to implement a symbol table is executed and the output is verified.

