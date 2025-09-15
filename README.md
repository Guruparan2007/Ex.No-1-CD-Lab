# Ex. No : 1

# IMPLEMENTATION OF SYMBOL TABLE

# Register Number : 212224220030

# Date :08.08.25

# AIM:

To write a C program to implement a symbol table.

# ALGORITHM:

1. Start the program.
2. Get the input from the user with the terminating symbol ‘$’.
3. Allocate memory for the variable by dynamic memory allocation function.
4. If the next character of the symbol is an operator then only the memory is allocated.
5. While reading, the input symbol is inserted into symbol table along with its memory address.
6. The steps are repeated till ‘$’ is reached.
7. To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
8. Stop the program.

# PROGRAM:

```
#include <stdio.h>
#include <stdlib.h>   
#include <ctype.h>    
#include <string.h>

#define MAX_EXPRESSION_SIZE 100

int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    void *add[20];       
    char b[MAX_EXPRESSION_SIZE], d[20];  
    char c, srch;

    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0'; 
    n = i - 1;

    printf("\nGiven Expression: %s\n", b);

    printf("\nSymbol Table\n");
    printf("Symbol\tAddress\t\tType\n");

    for (j = 0; j <= n; j++) {
        c = b[j];
        if (isalpha((unsigned char)c)) {
            if (j == n || b[j + 1] == '+' || b[j + 1] == '-' || 
                b[j + 1] == '*' || b[j + 1] == '=' || b[j + 1] == '/') {
                
                void *p = malloc(sizeof(char));
                if (p == NULL) {
                    printf("Memory allocation failed\n");
                    return 1;
                }
                add[x] = p;
                d[x] = c;
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
        }
    }

    
    while ((c = getchar()) != '\n' && c != EOF);

    printf("\nThe symbol to be searched: ");
    srch = getchar();

    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("Symbol Found\n");
            printf("%c @ address %p\n", srch, add[i]);
            flag = 1;
            break;
        }
    }

    if (flag == 0) {
        printf("Symbol Not Found\n");
    }

 
    for (i = 0; i < x; i++) {
        free(add[i]);
    }

    return 0;
}

```

# OUTPUT:

symbol found:

<img width="548" height="479" alt="Screenshot 2025-08-26 083802" src="https://github.com/user-attachments/assets/d7811cc6-ac19-4530-9bf6-1101edfe48b3" />


symbol not found:

<img width="539" height="432" alt="Screenshot 2025-08-26 083326" src="https://github.com/user-attachments/assets/121b7f45-3f4c-4865-9fcf-37f4b2857ef7" />


# RESULT:

The program to implement a symbol table is executed and the output is verified.
