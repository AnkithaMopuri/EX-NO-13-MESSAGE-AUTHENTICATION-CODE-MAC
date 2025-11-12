# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC
# Name:Mopuri Ankitha
# Register Number:212223040117
## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

## Program:
```
#include <stdio.h>
#include <string.h>

void computeMAC(char *key, char *message, char *mac) {
    unsigned long hash = 5381;
    char combined[1000];
    strcpy(combined, key);
    strcat(combined, message);

    for (int i = 0; combined[i] != '\0'; i++)
        hash = ((hash << 5) + hash) + combined[i]; 

    sprintf(mac, "%lx", hash);
}

int main() {
    char key[100], message[500], mac[100];

    printf("Enter Secret Key: ");
    scanf("%s", key);
    printf("Enter Message: ");
    scanf("%s", message);

    computeMAC(key, message, mac);

    printf("\nGenerated MAC: %s\n", mac);
    return 0;
}

```


## Output:
<img width="439" height="213" alt="image" src="https://github.com/user-attachments/assets/fce1cd19-4df3-4054-a8d4-3b0ab3523a2e" />

## Result:
The program is executed successfully.
