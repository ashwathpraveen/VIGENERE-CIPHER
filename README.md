# VIGENERE-CIPHER
## EX. NO: 4
```
REG N0: 212224220012
NAME: ASHWATH P
```
## IMPLEMETATION OF VIGENERE CIPHER
 
## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>
void vigenereEncrypt(char plaintext[], char key[], char ciphertext[]) {
 int i, j;
 int pLen = strlen(plaintext);
 int kLen = strlen(key);

 for (i = 0, j = 0; i < pLen; i++) {
 char p = toupper(plaintext[i]);
 char k = toupper(key[j % kLen]);

 if (p >= 'A' && p <= 'Z') {
 ciphertext[i] = ((p - 'A') + (k - 'A')) % 26 + 'A';
 j++;
 } else {
 ciphertext[i] = plaintext[i];
 }
 }
 ciphertext[pLen] = '\0';
}
void vigenereDecrypt(char ciphertext[], char key[], char plaintext[]) {
 int i, j;
 int cLen = strlen(ciphertext);
 int kLen = strlen(key);

 for (i = 0, j = 0; i < cLen; i++) {
 char c = toupper(ciphertext[i]);
 char k = toupper(key[j % kLen]);

 if (c >= 'A' && c <= 'Z') {
 plaintext[i] = ((c - 'A') - (k - 'A') + 26) % 26 + 'A';
 j++;
 } else {
 plaintext[i] = ciphertext[i];
 }
 }
 plaintext[cLen] = '\0';
}

int main() {
 char plaintext[100], key[100], ciphertext[100], decrypted[100];

 printf("Enter plaintext: ");
 scanf("%s", plaintext);

 printf("Enter key: ");
 scanf("%s", key);

vigenereEncrypt(plaintext, key, ciphertext);
printf("Encrypted text: %s\n", ciphertext);
vigenereDecrypt(ciphertext, key, decrypted);
printf("Decrypted text: %s\n", decrypted);
return 0;
}
```

## OUTPUT
<img width="804" height="351" alt="image" src="https://github.com/user-attachments/assets/d974d403-7829-4352-8103-94faddf31eda" />

## RESULT
