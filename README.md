# RSA-Decryption-with-Pollard-s-p-1-Algorithm-in-Python
In this exercise, it will be implemented RSA decryption using Pollard's p-1 algorithm to factor a given RSA modulus n. The goal is to recover the plaintext message from the ciphertext c. Pollard's p-1 is a factorization algorithm that attempts to find nontrivial factors of n and, subsequently, use these factors to decrypt the ciphertext. Also it will be implemented functions to compute the modular inverse and apply the RSA decryption formula.

Pollard's p-1 Algorithm:
This is a factorization method that tries to find a factor p of n. It is particularly effective when one of the prime factors of n is smooth (i.e., has small prime factors).
The algorithm iteratively raises a to increasing powers mod n and computes the GCD of a-1 and n. If a nontrivial factor is found, it can be used to break the RSA encryption.

Extended GCD and Modular Inverse:
The extended_gcd() function is used to compute the GCD of two numbers along with the coefficients for Bézout's identity.
The mod_inverse() function computes the modular inverse of e modulo phi (Euler's totient function of n), which is crucial for the decryption step in RSA.

RSA Decryption:
Once the factor p is found, the other factor q is calculated as n // p.
The decryption exponent d is computed using the modular inverse of e with respect to phi = (p-1)*(q-1).
The ciphertext c is decrypted using the formula m = c^d mod n, and the decrypted message is converted back to a readable format using long_to_bytes().


