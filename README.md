# EX No. 14 : HASH ALGORITHM

#### Name : Prajin S
#### Register Number : 212223230151

## AIM:
To implement HASH ALGORITHM

## ALGORITHM:

### Step 01:
Hash Algorithm is used to convert input data (message) into a fixed-size string, typically a hash value, which uniquely represents the original data.

### Step 02: Initialization
   - Choose a hash function \( H \) (e.g., SHA-256, MD5, etc.).
   - The message \( M \) to be hashed is input.

### Step 03: Message Preprocessing
   - Break the message \( M \) into fixed-size blocks. If necessary, pad the message to make it compatible with the block size required by the hash function.
   - For example, in SHA-256, the message is padded to ensure that its length is a multiple of 512 bits.

### Step 04: Hash Calculation
   - Process the message block by block, applying the hash function \( H \) iteratively to produce an intermediate hash value.
   - For SHA-256, each block is processed through a series of logical operations, bitwise manipulations, and modular additions.

### Step 05: Output
   - After all blocks are processed, the final hash value (digest) is produced, which is a fixed-size output (e.g., 256-bit for SHA-256).
   - The resulting hash is unique to the input message, meaning even a small change in the message will result in a completely different hash.

### Step 06: Security
The strength of the hash algorithm lies in its collision resistance, ensuring that it is computationally infeasible to find two different messages that produce the same hash value.


## Program:
```C
#include <stdio.h>
#include <string.h>

void computeSimpleHash(const char *message, unsigned char *hash)
{
    unsigned char temp = 0;
    for (int i = 0; message[i] != '\0'; i++)
    {
        temp = temp ^ message[i];
        temp += message[i];
    }
    *hash = temp;
}

int main()
{
    char message[256];
    unsigned char hash;
    char receivedHash[3];

    printf("Enter the message: ");
    scanf("%255[^\n]", message);

    computeSimpleHash(message, &hash);
    printf("Computed Hash (in hex): %02x\n", hash);

    printf("Enter the received hash (in hex, 2 digits): ");
    scanf("%2s", receivedHash);

    unsigned int receivedHashValue;
    if (sscanf(receivedHash, "%x", &receivedHashValue) != 1)
    {
        printf("Invalid hash input.\n");
        return 1;
    }

    if (hash == receivedHashValue)
    {
        printf("Hash verification successful. Message is unchanged.\n");
    }
    else
    {
        printf("Hash verification failed. Message has been altered.\n");
    }

    return 0;
}
```

## Output:
Enter the message: prajinwriteshash

Computed Hash (in hex): 24

Enter the received hash (in hex, 2 digits): 24

Hash verification successful. Message is unchanged.

![Screenshot 2025-05-17 165914](https://github.com/user-attachments/assets/3ccd5813-fe6a-4fcb-b8ff-954fd55de90f)

![Screenshot 2025-05-17 165844](https://github.com/user-attachments/assets/e2df533d-1a2e-4974-b636-e6b8d33aa64e)


## Result:
The program is executed successfully and results are verified as well.
