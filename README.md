# EX.-NO-1-E-IMPLEMENTATION-OF-RAIL-FENCE-ROW-COLUMN-TRANSFORMATION-TECHNIQUE

## AIM:
  To write a C program to implement the rail fence transposition technique.
  
## ALGORITHM:

STEP-1: Read the Plain text.

STEP-2: Arrange the plain text in row columnar matrix format.

STEP-3: Now read the keyword depending on the number of columns of the plain text.

STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.

STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

## PROGRAM:
        #include <stdio.h>
        #include <string.h>
        
        void encryptRailFence(char *text, int key, char *cipher)
        {
            int len = strlen(text);
            int k = 0;
        
            for (int row = 0; row < key; row++) {
                int step1 = (key - row - 1) * 2;
                int step2 = row * 2;
                int pos = row;
        
                int toggle = 0; 
        
                while (pos < len) {
                    cipher[k++] = text[pos];
        
                    if (row == 0)
                        pos += (key - 1) * 2;
                    else if (row == key - 1)
                        pos += (key - 1) * 2;
                    else {
                        if (toggle == 0) {
                            pos += step1;
                            toggle = 1;
                        } else {
                            pos += step2;
                            toggle = 0;
                        }
                    }
                }
            }
            cipher[k] = '\0';
        }
        
        int main()
        {
            char text[100], cipher[100];
            int key;
        
            scanf("%[^\n]", text);
            
            printf("Enter text: %s\n",text);
            
            scanf("%d", &key);
            
            printf("Enter key (number of rails): %d",key);
            
            encryptRailFence(text, key, cipher);
            
            printf("\nEncrypted text: %s\n", cipher);
        
            return 0;
        }

## OUTPUT:
<img width="613" height="271" alt="image" src="https://github.com/user-attachments/assets/07d51fe6-c37a-43b3-9f04-6088e26064ed" />

## RESULT:
  Thus the rail fence algorithm had been executed successfully.
