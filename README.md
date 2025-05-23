# Ex-4 Rail-Fence-Program
# NAME:POOJASRI L
# REG.NO:212223220076

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>
void encrypt(char str[], int rails);
void decrypt(char str[], int rails);
int main() {
 int rails;
 char str[1000];
 printf("Enter a message: ");
 fgets(str, sizeof(str), stdin);
 str[strcspn(str, "\n")] = '\0';
 printf("Enter number of rails: ");
 scanf("%d", &rails);
 getchar();
 encrypt(str, rails);
 decrypt(str, rails);
 return 0;
}
void encrypt(char str[], int rails) {
 int len = strlen(str);
 char rail[rails][len];
 for (int i = 0; i < rails; i++)
 for (int j = 0; j < len; j++)
 rail[i][j] = '\n';
 int row = 0, down = 1;
 for (int i = 0; i < len; i++) {
 rail[row][i] = str[i];
 if (row == rails - 1)
 down = 0;
 else if (row == 0)
 down = 1;
 row += down ? 1 : -1;
 }
 printf("Encrypted message: ");
 for (int i = 0; i < rails; i++)
 for (int j = 0; j < len; j++)
 if (rail[i][j] != '\n')
 printf("%c", rail[i][j]);
 printf("\n");
}
void decrypt(char str[], int rails) {
 int len = strlen(str);
 char rail[rails][len];
 for (int i = 0; i < rails; i++)
 for (int j = 0; j < len; j++)
 rail[i][j] = '\n';
 int row = 0, down = 1;
 for (int i = 0; i < len; i++) {
 rail[row][i] = '*';
 if (row == rails - 1)
 down = 0;
 else if (row == 0)
 down = 1;
 row += down ? 1 : -1;
 }
 int index = 0;
 for (int i = 0; i < rails; i++)
 for (int j = 0; j < len; j++)
 if (rail[i][j] == '*' && index < len)
 rail[i][j] = str[index++];
 printf("Decrypted message: ");
 row = 0, down = 1;
 for (int i = 0; i < len; i++) {
 printf("%c", rail[row][i]);
 if (row == rails - 1)
 down = 0;
 else if (row == 0)
 down = 1;
 row += down ? 1 : -1;
 }
 printf("\n");
}
```
# OUTPUT
![image](https://github.com/user-attachments/assets/a4eab23a-ee42-412c-9bab-7e9e5348b123)


# RESULT
The program is executed successfully
