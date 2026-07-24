# HILL CIPHER

## EX. NO: 3

## AIM

To write a C program to implement the Hill Cipher substitution technique.

---

# DESCRIPTION

The Hill Cipher is a polygraphic substitution cipher based on linear algebra. Each letter is represented by a number modulo 26 using the following mapping:

| Letter | Value |
|--------|------:|
| A | 0 |
| B | 1 |
| C | 2 |
| ... | ... |
| Z | 25 |

To encrypt a message, the plaintext is divided into blocks of fixed length (here, 3 letters). Each block is converted into its numerical equivalent and multiplied by an invertible **3 × 3 key matrix**. The resulting values are reduced modulo 26 to produce the ciphertext.

For decryption, the ciphertext block is multiplied by the inverse of the key matrix (modulo 26), which recovers the original plaintext.

---

# ALGORITHM

**Step 1:** Read the plaintext from the user.

**Step 2:** Convert each character of the plaintext into its corresponding numerical value (A = 0, B = 1, ..., Z = 25).

**Step 3:** Arrange the plaintext values as a column matrix of order **3 × 1**.

**Step 4:** Multiply the plaintext matrix with the **3 × 3 encryption key matrix**.

**Step 5:** Apply modulo 26 to each resulting value.

**Step 6:** Convert the numerical values back into characters to obtain the ciphertext.

**Step 7:** Multiply the ciphertext matrix with the inverse key matrix.

**Step 8:** Apply modulo 26 and convert the numerical values back into characters to obtain the original plaintext.

---

# PROGRAM

```c
#include <stdio.h>
#include <string.h>

int main()
{
    int key[3][3], p[100], c[100];
    char msg[100];
    int i, j, k, len, sum;

    printf("Enter Plain Text: ");
    scanf("%s", msg);

    printf("Enter 3x3 Key Matrix:\n");
    for(i = 0; i < 3; i++)
        for(j = 0; j < 3; j++)
            scanf("%d", &key[i][j]);

    len = strlen(msg);

    while(len % 3 != 0)
        msg[len++] = 'X';
    msg[len] = '\0';

    for(i = 0; i < len; i++)
        p[i] = msg[i] - 'A';

    for(k = 0; k < len; k += 3)
    {
        for(i = 0; i < 3; i++)
        {
            sum = 0;
            for(j = 0; j < 3; j++)
                sum += key[i][j] * p[k + j];

            c[k + i] = sum % 26;
        }
    }

    printf("Cipher Text: ");
    for(i = 0; i < len; i++)
        printf("%c", c[i] + 'A');

    return 0;
}
```

---

# OUTPUT


<img width="1850" height="854" alt="image" src="https://github.com/user-attachments/assets/10390fd2-c7a3-4b10-aeee-e02e2340cc66" />



# RESULT

Thus, the C program to implement the **Hill Cipher** encryption and decryption technique was successfully executed, and the corresponding ciphertext and original plaintext were obtained.
