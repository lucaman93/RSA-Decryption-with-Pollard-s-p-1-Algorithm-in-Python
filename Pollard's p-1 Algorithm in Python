import math
from Crypto.Util.number import long_to_bytes

def pollards_p_1(n, B):
    a = 2
    for i in range(2, B):
        a = pow(a, i, n)
        d = math.gcd(a - 1, n)
        if 1 < d < n:
            return d
    return None

def extended_gcd(a, b):
    if a == 0:
        return b, 0, 1
    else:
        gcd, x, y = extended_gcd(b % a, a)
        return gcd, y - (b // a) * x, x

def mod_inverse(a, m):
    gcd, x, _ = extended_gcd(a, m)
    if gcd != 1:
        raise Exception('Modular inverse does not exist')
    else:
        return x % m

# Given RSA parameters
n = 0x...  # Replace with actual hexadecimal value
e = 0x...  # Replace with actual hexadecimal value
c = 0x...  # Replace with actual hexadecimal value

# Try to factor n using Pollard's p-1 algorithm
B = 1000000  # You might need to adjust this value
p = pollards_p_1(n, B)

if p:
    q = n // p
    phi = (p - 1) * (q - 1)
    d = mod_inverse(e, phi)
    
    # Decrypt the message
    m = pow(c, d, n)
    
    # Convert to bytes and then to string
    decrypted = long_to_bytes(m).decode('utf-8', errors='ignore')
    
    print(f"Factored n: p = {p}, q = {q}")
    print(f"Decrypted message: {decrypted}")
else:
    print("Failed to factor n. Try increasing B or using a different method.")
