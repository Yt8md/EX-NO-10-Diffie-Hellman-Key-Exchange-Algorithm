## EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm
## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm

1. **Objective**  
   Diffie-Hellman Key Exchange allows two parties to securely generate a shared secret key over an insecure communication channel.

2. **Public Parameters Initialization**  
   - Choose a large prime number `p`.  
   - Choose a primitive root modulo `p`, denoted as `g`.  
   - Both `p` and `g` are public and known to both parties.

3. **Private Key Selection**  
   - Alice selects a private key `a`.  
   - Bob selects a private key `b`.

4. **Public Key Computation**  
   - Alice computes `A = g^a mod p` and sends it to Bob.  
   - Bob computes `B = g^b mod p` and sends it to Alice.

5. **Shared Secret Key Computation**  
   - Alice computes the secret key as `K = B^a mod p`.  
   - Bob computes the secret key as `K = A^b mod p`.  
   - Both values of `K` will be the same, and this becomes the shared secret.

6. **Security Note**  
   - The security of this algorithm relies on the difficulty of solving the **Discrete Logarithm Problem**.  
   - Even if an attacker knows the values of `p`, `g`, `A`, and `B`, it is computationally infeasible to compute `a`, `b`, or `K`.


## Program:
```
#include <stdio.h>


long long int mod_exp(long long int base, long long int exp, long long int mod) {
    long long int result = 1;
    while (exp > 0) {
        // If exp is odd, multiply base with result
        if (exp % 2 == 1)
            result = (result * base) % mod;

        // Now exp must be even, so divide by 2 and square the base
        exp = exp >> 1; // equivalent to exp = exp / 2
        base = (base * base) % mod;
    }
    return result;
}

int main() {
    long long int P, G, a, b, x, y, ka, kb;

    printf("\n********* Diffie-Hellman Key Exchange Algorithm **********\n\n");

    // Step 1: Agree on public values P (prime number) and G (primitive root)
    printf("Enter a prime number P: ");
    scanf("%lld", &P); // A prime number P is taken
    printf("The value of P: %lld\n", P);

    printf("Enter a primitive root G for P: ");
    scanf("%lld", &G); // A primitive root G is taken
    printf("The value of G: %lld\n\n", G);

    // Step 2: Alice selects a private key a
    printf("Enter the private key for Alice (a): ");
    scanf("%lld", &a);
    x = mod_exp(G, a, P); // Alice's public key x = G^a % P
    printf("The public key for Alice (x = G^a mod P): %lld\n", x);

    // Step 3: Bob selects a private key b
    printf("Enter the private key for Bob (b): ");
    scanf("%lld", &b);
    y = mod_exp(G, b, P); // Bob's public key y = G^b % P
    printf("The public key for Bob (y = G^b mod P): %lld\n\n", y);

    // Step 4: Exchange public keys and generate the shared secret key
    ka = mod_exp(y, a, P); // Alice computes the shared key ka = y^a % P
    kb = mod_exp(x, b, P); // Bob computes the shared key kb = x^b % P

    // Step 5: Display the shared secret keys (ka and kb should be equal)
    printf("Shared secret key for Alice (ka = y^a mod P): %lld\n", ka);
    printf("Shared secret key for Bob (kb = x^b mod P): %lld\n", kb);

    if (ka == kb) {
        printf("\nDiffie-Hellman Key Exchange successful. Both parties share the same key.\n");
    } else {
        printf("\nError: The keys for Alice and Bob do not match.\n");
    }

    return 0;
}
```
## Output:

![image](https://github.com/user-attachments/assets/7c1d831b-5583-470d-875d-2ad1d400a63d)


## Result:
  The program is executed successfully

