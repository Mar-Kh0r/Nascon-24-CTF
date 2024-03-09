# Cryptography Challenge Writeup: Easy Encryption

Author: OxSmoke

---

## Introduction

In this challenge, contestants were given a Python script and a ciphertext. Their task was to decrypt the ciphertext using the provided Python script, which served as the encryption function. To achieve decryption, participants needed to write a corresponding decryption function based on the provided encryption function.

- **Title**: Easy Encryption
- **Flag Format**: CSL{flag}
- **Note:** In this challenge, regex flags were employed, which might result in variations in the output.

---

# Decryption Process Steps: 

1.	The following is the provided encryption function.
   
![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/8365f2af-92a6-4f5a-817e-92268c43c9f1)


2.	The given ciphertext is provided.
   
![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/eb39f369-0ab9-426a-a484-dbe2416851a8)


3.	Use any chatbot to obtain the decryption function. In this case, I am using ChatGPT to retrieve the decryption function corresponding to the provided encryption function.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/f7cbcf42-9df5-42ff-a6e3-3d46958e8693)

### Python Script: Decryption Function

```python

import random

def decrypt(key, ciphertext):
    plaintext = ""
    current_position = 0

    i = 0
    while i < len(ciphertext):
        plaintext += ciphertext[i]

        random_chars_count = key + current_position
        i += random_chars_count + 1

        current_position += 1

    return plaintext



ciphertext = input("Enter a message to decrypt (ciphertext): ")
# Input key...
key = int(input("Input a key as a number between 1 and 10: "))
while not (1 <= key <= 10):
    print("Invalid key, try again!")
    key = int(input("Input a key as a number between 1 and 10: "))

decrypted_text = decrypt(key, ciphertext)
print("Decrypted Text:")
print(decrypted_text)


````


4.	Here, we are prompted to input the key. The key is the parameter used by the encryption function to encrypt the plaintext.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/a0e355e0-7ffd-4e04-9caf-ac3cc8a265e2)

 
5.	To decrypt, we need to enter a key. Since the key is not explicitly given, but through code analysis, we deduce that the key falls within the range of 1-10. Therefore, we can try all these key options.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/2dc499cb-98cd-4983-baee-7973d48db10e)


6. In this case we can observe that 3 is not the valid key, as the ouput is not readable. 

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/883a9685-5fb3-47ff-945b-647694b58045)


7. Eventually, the decrypted output makes sense when the key is set to 4, and that's the flag.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/20751028-6d8f-4e5f-ad4c-289191be164e)

