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
   
![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/1b62a645-93da-40a8-bae2-34bc63a209c5)

3.	The given ciphertext is provided.
   
![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/02cd6320-37b2-41e2-b95b-83d7a624c243)

5.	Use any chatbot to obtain the decryption function. In this case, I am using ChatGPT to retrieve the decryption function corresponding to the provided encryption function.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/f6100a1b-42e4-432b-9341-9e1caca31537)

6.	Here, we are prompted to input the key. The key is the parameter used by the encryption function to encrypt the plaintext.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/b197161f-98ef-4c9c-be8f-23f50eece36f)
 
7.	To decrypt, we need to enter a key. Since the key is not explicitly given, but through code analysis, we deduce that the key falls within the range of 1-10. Therefore, we can try all these key options.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/12e3c05d-99a9-42ee-bd49-783de02c3211)

8. In this case we can observe that 3 is not the valid key, as the ouput is not readable. 

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/24bebec3-f0ed-426c-bd36-e8bfad7238e5)

9. Eventually, the decrypted output makes sense when the key is set to 4, and that's the flag.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/501fea7a-47b7-494a-a1e4-8c72694cd21f)


 




