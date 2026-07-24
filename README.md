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
#include <ctype.h>

int main()
{
    unsigned int a[3][3] = {
        {6, 24, 1},
        {13, 16, 10},
        {20, 17, 15}
    };

    unsigned int b[3][3] = {
        {8, 5, 10},
        {21, 8, 21},
        {21, 12, 8}
    };

    unsigned int c[3], d[3];
    char msg[4];
    int i, j, t;

    printf("Enter plain text (3 letters): ");
    scanf("%3s", msg);

    if (strlen(msg) != 3)
    {
        printf("Error: The plain text must be exactly 3 letters.\n");
        return 1;
    }

    printf("Plain Text in Numeric Form: ");

    for (i = 0; i < 3; i++)
    {
        msg[i] = toupper(msg[i]);
        c[i] = msg[i] - 'A';
        printf("%u ", c[i]);
    }

    for (i = 0; i < 3; i++)
    {
        t = 0;

        for (j = 0; j < 3; j++)
        {
            t += a[i][j] * c[j];
        }

        d[i] = t % 26;
    }

    printf("\nEncrypted Cipher Text: ");

    for (i = 0; i < 3; i++)
    {
        printf("%c", d[i] + 'A');
    }

    for (i = 0; i < 3; i++)
    {
        t = 0;

        for (j = 0; j < 3; j++)
        {
            t += b[i][j] * d[j];
        }

        c[i] = t % 26;
    }

    printf("\nDecrypted Plain Text: ");

    for (i = 0; i < 3; i++)
    {
        printf("%c", c[i] + 'A');
    }

    printf("\n");

    return 0;
}
```

---

# OUTPUT

<img width="1850" height="850" alt="image" src="https://github.com/user-attachments/assets/51cf27d4-4949-4773-8ea4-61d0094704ba" />



# RESULT

Thus, the C program to implement the **Hill Cipher** encryption and decryption technique was successfully executed, and the corresponding ciphertext and original plaintext were obtained.
