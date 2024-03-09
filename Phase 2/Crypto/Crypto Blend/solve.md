# Cryptography Challenge Writeup: Crypto Blend

Author: OxSmoke

---

## Introduction

In this challenge, participants were presented with a ciphertext and assigned the task of decrypting it. The primary objective was to deduce the encryption function employed for encrypting the ciphertext, drawing insights from clues provided in the problem statement. Additionally, hints were offered to guide players in identifying the specific cipher utilized for encryption.

---

## Challenge 

Unlock the secrets of this cipher challenge by delving into the fascinating world of modular arithmetic. The hidden key to unraveling the mystery lies in the fact that the encryption process relies on both multiplication and addition operations, creating a unique blend that echoes the distinctive traits of this cipher where GCD(25,17) = 1.

- **Title**: Crypto Blend
- **Flag Format**: CSL{flag}
- **Note:** In this challenge, regex flags were employed, which might result in variations in the output.

---

# Decryption Process Steps: 

---

### Hints

1. ![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/2a8bd4d9-c75f-455f-b212-737bea3479f4)
   
2. ![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/2ef85cb6-cb3f-4898-bde3-decebf4f1321)

---

The first hint suggests that the encryption algorithm used to encrypt the message is the Affine Cipher.

1.	Begin by researching the Affine Cipher to gain an understanding of its workings.
   
2.	Visit websites like dcode.fr or CyberChef to decrypt the ciphertext.
      - **Note:** Be aware that these sites typically have limits allowing only 26 characters.
        
3. The second hint suggests the use of 63 characters, and a playful reference to "Python is your best friend" implies that writing a Python script is the most straightforward way to decrypt the cipher.

4. Develop a Python script for decrypting the ciphertext using the Affine Cipher.

5. The Python script below is utilized for decryption. The ciphertext employed in the script is the one provided in the challenge.

### Python Script:

```python

allowed_characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789_'

def decrypt(cipher_text, a, b):
    mod_inverse_a = pow(a, -1, len(allowed_characters))
    plain_text = ""
    for char in cipher_text:
        if char in allowed_characters:
            plain_text += allowed_characters[mod_inverse_a * (allowed_characters.index(char) - b) % len(allowed_characters)]
        else:
            plain_text += char
    return plain_text


a = 25
b = 17
cipher_text = "zXL3YVHiITY3YVlkILWlv3uLvxu3IXLTV3VL9lVxu"
decrypted_message = decrypt(cipher_text, a, b)
print("Decrypted Message:", decrypted_message)
````

6. Finally, the flag is revealed:
   - CSL{The_crypt1c_crafteman_sends_the1r_regards}

