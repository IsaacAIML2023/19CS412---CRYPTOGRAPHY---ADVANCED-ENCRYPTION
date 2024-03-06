 ## IMPLEMENTATION OF RSA
 # AIM :
 To write a C program to implement the RSA encryption algorithm.

## ALGORITHM:
STEP-1: Select two co-prime numbers as p and q.

STEP-2: Compute n as the product of p and q.

STEP-3: Compute (p-1)*(q-1) and store it in z.

STEP-4: Select a random prime number e that is less than that of z.

STEP-5: Compute the private key, d as e *
mod-1
(z).

STEP-6: The cipher text is computed as messagee *

STEP-7: Decryption is done as cipherdmod n.

## PROGRAM:
```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
// Function to calculate greatest common divisor (GCD)
int gcd(int a, int b) {
if (b == 0)
return a;
return gcd(b, a % b);
}
// Function to generate RSA keys
void generateRSAKeys(int *n, int *e, int *d) {
// Choose two prime numbers (p and q)
int p;
int q;
printf("enter two prime numbers:");
scanf("%d %d",&p,&q);
// Calculate n = p * q
*n = p * q;
// Calculate Euler's totient function (φ(n))
int phi = (p - 1) * (q - 1);
// Choose a public exponent (e) such that 1 < e < φ(n) and gcd(e, φ(n)) = 1
*e = 5; // You can choose a different value for e, typically a prime number
// Calculate the private exponent (d) such that (d * e) % φ(n) = 1
*d = 0;
while ((*d * *e) % phi != 1) {
(*d)++;
}
}
// Function to perform modular exponentiation (base^exponent % modulus)
int modExp(int base, int exponent, int modulus) {
int result = 1;
while (exponent > 0) {
if (exponent % 2 == 1) {
result = (result * base) % modulus;
}
base = (base * base) % modulus;
exponent /= 2;
}
return result;
}
// Function to encrypt a message using the public key
int encrypt(int message, int publicKey, int modulus) {
return modExp(message, publicKey, modulus);
}
// Function to decrypt a message using the private key
int decrypt(int ciphertext, int privateKey, int modulus) {
return modExp(ciphertext, privateKey, modulus);
}
int main() {
int n, e, d;
int plaintext;
printf("enter plaintext:");
scanf("%d",&plaintext);
generateRSAKeys(&n, &e, &d);
printf("Original message: %d\n", plaintext);
int ciphertext = encrypt(plaintext, e, n);
printf("Encrypted message: %d\n", ciphertext);
int decryptedMessage = decrypt(ciphertext, d, n);
printf("Decrypted message: %d\n", decryptedMessage);
return 0;
}
```
## OUTPUT:
![Screenshot 2024-03-05 113517](https://github.com/AlluguriSrikrishnateja/19CS412---CRYPTOGRAPHY---ADVANCED-ENCRYPTION/assets/118343892/b96f8704-db74-4fb0-835d-078d58644625)


## RESULT :

Thus the C program to implement RSA encryption technique had been
implemented successfully





## IMPLEMENTATION OF DIFFIE HELLMAN KEY EXCHANGE ALGORITHM

## AIM:

To implement the Diffie-Hellman Key Exchange algorithm using C language.


## ALGORITHM:

STEP-1: Both Alice and Bob shares the same public keys g and p.

STEP-2: Alice selects a random public key a.

STEP-3: Alice computes his secret key A as g
a mod p.

STEP-4: Then Alice sends A to Bob.


STEP-5: Similarly Bob also selects a public key b and computes his secret
key as B and sends the same back to Alice.


STEP-6: Now both of them compute their common secret key as the other
one’s secret key power of a mod p.

## PROGRAM: 

```
#include <math.h>
#include <stdio.h>
// Power function to return value of a ^ b mod P
long long int power(long long int a, long long int b,
long long int P)
{
if (b == 1)
return a;
else
return (((long long int)pow(a, b)) % P);
}
int main()
{
long long int P, G, x, a, y, b, ka, kb;
// Both the persons will be agreed upon the
// public keys G and P
printf("Enter the value of P:");
scanf("%lld",&P); // A prime number P is taken
printf("The value of P : %lld\n", P);
printf("Enter the value of G:");
scanf("%lld",&G); // A primitive root for P, G is taken
printf("The value of G : %lld\n\n", G);
// Alice will choose the private key a
a = 4; // a is the chosen private key
printf("The private key a for Alice : %lld\n", a);
x = power(G, a, P); // gets the generated key
// Bob will choose the private key b
b = 3; // b is the chosen private key
printf("The private key b for Bob : %lld\n\n", b);
y = power(G, b, P); // gets the generated key
// Generating the secret key after the exchange
// of keys
ka = power(y, a, P); // Secret key for Alice
kb = power(x, b, P); // Secret key for Bob
printf("Secret key for the Alice is : %lld\n", ka);
printf("Secret Key for the Bob is : %lld\n", kb);
return 0;
}
```
## OUTPUT:

<img width="342" alt="image" src="https://github.com/AlluguriSrikrishnateja/19CS412---CRYPTOGRAPHY---ADVANCED-ENCRYPTION/assets/118343892/a3f5b0fa-ef81-4215-9521-2a16c87cef68">


## RESULT: 

Thus the Diffie-Hellman key exchange algorithm had been successfully
implemented using C.





## IMPLEMENTATION OF DES ALGORITHM

## AIM:
To write a program to implement Data Encryption Standard (DES)

## ALGORITHM :

STEP-1: Read the 64-bit plain text.

STEP-2: Split it into two 32-bit blocks and store it in two different arrays.

STEP-3: Perform XOR operation between these two arrays.

STEP-4: The output obtained is stored as the second 32-bit sequence and the
original second 32-bit sequence forms the first part.

STEP-5: Thus the encrypted 64-bit cipher text is obtained in this way. Repeat the
same process for the remaining plain text characters.

### PROGRAM :

```
from cryptography.fernet import Fernet
message = input()
key = Fernet.generate_key()
fernet = Fernet(key)
encMessage = fernet.encrypt(message.encode())
print("original string: ", message)
print("encrypted string: ", encMessage)

decMessage = fernet.decrypt(encMessage).decode()
 
print("decrypted string: ", decMessage)
```
## OUTPUT:

<img width="756" alt="image" src="https://github.com/AlluguriSrikrishnateja/19CS412---CRYPTOGRAPHY---ADVANCED-ENCRYPTION/assets/118343892/23e74c08-7cea-4381-b9fe-97e247b17470">

## RESULT:

Thus the data encryption standard algorithm had been implemented
successfully.

