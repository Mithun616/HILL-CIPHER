# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:
### Step 1:

Design of Hill Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 
ALGORITHM DESCRIPTION:
The Hill cipher is a substitution cipher invented by Lester S. Hill in 1929. Each letter is represented by a number modulo 26. To encrypt a message, each block of n letters is multiplied by an invertible n × n matrix, again modulus 26.
To decrypt the message, each block is multiplied by the inverse of the matrix used for encryption. The matrix used for encryption is the cipher key, and it should be chosen randomly from the set of invertible n × n matrices (modulo 26).
The cipher can, be adapted to an alphabet with any number of letters. All arithmetic just needs to be done modulo the number of letters instead of modulo 26.


## PROGRAM:

~~~
import numpy as np

def mod_inverse(matrix, modulus):
    det = int(round(np.linalg.det(matrix)))
    det_inv = pow(det, -1, modulus)
    matrix_inv = det_inv * np.round(det * np.linalg.inv(matrix)).astype(int) % modulus
    return matrix_inv

def text_to_numbers(text):
    return [ord(char) - ord('A') for char in text.upper() if char.isalpha()]

def numbers_to_text(numbers):
    return ''.join(chr(num + ord('A')) for num in numbers)

def encrypt(text, key):
    text_nums = text_to_numbers(text)
    while len(text_nums) % len(key) != 0:
        text_nums.append(ord('X') - ord('A'))
    text_matrix = np.array(text_nums).reshape(-1, len(key))
    encrypted_matrix = (np.dot(text_matrix, key) % 26).flatten()
    return numbers_to_text(encrypted_matrix)

def decrypt(ciphertext, key):
    key_inv = mod_inverse(key, 26)
    cipher_nums = text_to_numbers(ciphertext)
    cipher_matrix = np.array(cipher_nums).reshape(-1, len(key))
    decrypted_matrix = (np.dot(cipher_matrix, key_inv) % 26).flatten()
    return numbers_to_text(decrypted_matrix)

key_matrix = np.array([[1, 2, 1], [2, 3, 2], [2, 2, 1]])
plaintext = "SECURITYLABORATORY"
ciphertext = encrypt(plaintext, key_matrix)
decrypted_text = decrypt(ciphertext, key_matrix)

print("Key Matrix:\n", key_matrix)
print("Plaintext:", plaintext)
print("Ciphertext:", ciphertext)
print("Decrypted Text:", decrypted_text)
~~~

## OUTPUT:
OUTPUT:
Simulating Hill Cipher

![Screenshot 2025-03-19 091421](https://github.com/user-attachments/assets/3856fb98-ce30-4d47-bf9b-8e4268488f28)

Input Message : SecurityLaboratory
Padded Message : SECURITYLABORATORY Encrypted Message : EACSDKLCAEFQDUKSXU Decrypted Message : SECURITYLABORATORY

## RESULT:
The program is executed successfully
