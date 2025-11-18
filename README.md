# EX-NO-7-Implement-DES-Encryption

## Aim:

To use the Data Encryption Standard (DES) algorithm for a practical application, such as securing sensitive data transmission in financial transactions.

## ALGORITHM:

1. DES is based on a symmetric key encryption technique that encrypts data in 64-bit blocks.
2. DES uses a Feistel network structure with 16 rounds of processing for encryption.
3. DES has a 64-bit key, but only 56 bits are used for encryption (the remaining 8 bits are for parity).
4. DES applies initial and final permutations along with 16 rounds of substitution and permutation transformations to produce ciphertext.

## Program:

```
#include <stdio.h>
#include <string.h>

void xor_enc(char *msg,char *key,char *out,int n){
    int k=strlen(key);
    for(int i=0;i<n;i++) out[i]=msg[i]^key[i%k];
    out[n]=0;
}

void xor_dec(char *enc,char *key,char *out,int n){ xor_enc(enc,key,out,n); }

int main(){
    char msg[100],key[100],enc[100],dec[100];
    printf("***** XOR Encryption/Decryption *****\n");
    printf("Enter message: "); fgets(msg,sizeof msg,stdin); msg[strcspn(msg,"\n")]=0;
    printf("Enter key: "); fgets(key,sizeof key,stdin); key[strcspn(key,"\n")]=0;
    int n=strlen(msg);
    xor_enc(msg,key,enc,n);
    printf("Original: %s\nEncrypted(hex): ",msg);
    for(int i=0;i<n;i++) printf("%02X ",(unsigned char)enc[i]);
    printf("\n");
    xor_dec(enc,key,dec,n);
    printf("Decrypted: %s\n",dec);
}

```

## Output:

<img width="703" height="336" alt="Screenshot 2025-11-18 181307" src="https://github.com/user-attachments/assets/8e71df73-c1a3-4500-9415-199f41a04989" />

## Result:
  The program is executed successfully

