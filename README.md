# EX.-NO-1-D-IMPLEMENTATION-OF-VIGENERE-CIPHER

## AIM:
  To implement the Vigenere Cipher substitution technique using C program.
  
## ALGORITHM:
  STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
  
  STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
 
  STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
  
  STEP-4: The keyword and the plain text is read from the user.
  
  STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
  
  STEP-6: Pick the first letter of the plain text and that of the keyword as the row  indices and column indices respectively.
  
  STEP-7: The junction character where these two meet forms the cipher character.
  
  STEP-8: Repeat the above steps to generate the entire cipher text.
  
## PROGRAM:
        #include <stdio.h>
        #include <string.h>
        #include <ctype.h>
        
        
        void encryptVigenere(char text[], char key[], char result[]) {
            int textLen = strlen(text);
            int keyLen = strlen(key);
            int i, j = 0;
        
            for (i = 0; i < textLen; i++) {
                char c = text[i];
        
                if (isalpha(c)) {
                    char base = isupper(c) ? 'A' : 'a';
                    char keyBase = isupper(key[j % keyLen]) ? 'A' : 'a';
        
                    result[i] = ((c - base) + (key[j % keyLen] - keyBase)) % 26 + base;
                    j++; 
                } else {
                    result[i] = c; 
                }
            }
            result[textLen] = '\0';
        }
        
        int main() {
            char plaintext[100], key[100], encrypted[100];
        
            fgets(plaintext, sizeof(plaintext), stdin);
            plaintext[strcspn(plaintext, "\n")] = '\0'; 
            printf("Enter plaintext: %s\n",plaintext);
            fgets(key, sizeof(key), stdin);
            key[strcspn(key, "\n")] = '\0';
            printf("Enter key:%s",key);
            encryptVigenere(plaintext, key, encrypted);
            printf("\nEncrypted Text: %s\n", encrypted);
        
            return 0;
        }

## OUTPUT:
<img width="620" height="284" alt="image" src="https://github.com/user-attachments/assets/a296a1de-b0c1-42fc-ad6f-ab13b053d1f5" />

## RESULT:
  Thus the Vigenere Cipher substitution technique had been implemented successfully.
