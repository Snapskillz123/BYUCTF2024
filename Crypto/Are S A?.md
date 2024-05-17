# Are S A?

Using the values of n,e and c given in the question, using the regular RSA encryption technique it didn't work. I then used factordb and found that n was prime, so i ran a different program such that n was prime.

from Crypto.Util.number import inverse, long_to_bytes, bytes_to_long
from sympy import isprime

def rsa_decrypt(n, e, c):
    if not isprime(n):
        raise ValueError("n must be a prime number.")

    # Compute φ(n) for a prime n
    phi_n = n - 1

    # Compute the modular inverse of e
    d = inverse(e, phi_n)

    # Decrypt the ciphertext
    plaintext_int = pow(c, d, n)
    plaintext = long_to_bytes(plaintext_int)
    
    return plaintext

# Given values (replace these with your actual values)
n = 32416190071  # Example value for a prime n (replace with actual value)
e = 65537        # Example value for e (standard value)
c = 21888242871839275222246405745257275088548364400416034343698204186575808495617  # Example ciphertext (replace with actual value)

# Decrypt the message
decrypted_message = rsa_decrypt(n, e, c)
print("Decrypted message:", decrypted_message.decode('utf-8'))


After running the program i got the required flag.

  # Flag

  byuctf{d1d_s0m3_rs4_stuff...m1ght_d3l3t3_l4t3r}
