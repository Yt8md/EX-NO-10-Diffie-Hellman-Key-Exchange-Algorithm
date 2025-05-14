# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:

```
#include <math.h>
#include <stdio.h>

long long int power(long long int a, long long int b, long long int P) {
    if (b == 1)
        return a;
    else
        return (((long long int)pow(a, b)) % P);
}

int main() {
    long long int P, G, x, a, y, b, ka, kb;
    printf("\n***** Diffie-Hellman Key Exchange Algorithm *****\n\n");
    printf("Enter the value of P: ");
    scanf("%lld", &P);
    printf("The value of P: %lld\n", P);
    printf("Enter the value of G (Primitive root of P): ");
    scanf("%lld", &G); 
    printf("The value of G: %lld\n\n", G);
    a = 4;
    printf("The private key a for Alice: %lld\n", a);
    x = power(G, a, P); 
    b = 3; 
    printf("The private key b for Bob: %lld\n\n", b);
    y = power(G, b, P);
    ka = power(y, a, P); 
    kb = power(x, b, P); 

    printf("Secret key for the Alice is: %lld\n", ka);
    printf("Secret key for the Bob is: %lld\n", kb);

    return 0;
}
```


## Output:

![Screenshot 2025-05-08 081825](https://github.com/user-attachments/assets/937c890e-2818-48c6-bce3-123988af9aa4)


## Result:
  The program is executed successfully

