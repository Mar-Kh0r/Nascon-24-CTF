# Cryptography Challenge Writeup: Lottery Ticket

Author: OxSmoke

---

## Introduction

There are slot machines in a casino featuring 4 tags of 32 bits. We've successfully narrowed down a selection of tags to determine the winning lottery numbers. Moreover, we've identified the encryption function or mechanism employed to generate these lottery numbers.

---

## Challenge Statement

Embark on a thrilling cryptographic quest at our state-of-the-art casino! A mesmerizing slot machine awaits, adorned with enigmatic 32-bit binary tags that hold the key to a $25,000 lottery triumph. We've unraveled the elusive encryption algorithm that guards the path to victory. Your mission, should you choose to accept it, is to decipher the code and uncover the magical input that unlocks the grand prize. Are you ready to unravel the secrets and claim your fortune? The stakes are high, the challenge is real, and the jackpot awaits the master codebreaker!
- **Title**: Lottery Ticket
- **Flag Format**: CSL{?? _ ?? _ ?? _ ....}

---

## Decryption Process

In this challenge, the players were given two image files. The first file, named "testValues," contained the shortlisted values, while the second file, named "help," provided a diagram of Cipher Block Chaining (CBC).

---

## Understanding CBC and its Usage

In CBC mode, each block of plaintext is XORed with the previous ciphertext block before being encrypted. This way, each ciphertext block depends on all plaintext blocks processed up to that point.

## Steps: 

1.	The tags consist of a total of 32 bits, and the shortlisted values provided in the file are presented in 4 hexadecimal values.
   
3.	We can deduce that each hex value corresponds to 8 bits.
   
4.	The encryption function utilized is CBC, and the formula to crack CBC is determined as [C2 || (C1 xor Key2)].
   
5.	A hint for the player is also provided, indicating the formula to be used in breaking the CBC encryption.
   
6.	After identifying the formula, the provided test values are examined to identify those that hold true to the formula, potentially serving as the key to winning the lottery.

7.	While multiple values are provided, the following are the values through which the player will attain the winning lottery.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/c4bb8e85-6f75-4cb7-b138-08c03b86e824)

8.	Now, convert these values into binary and solve them according to the formula.
   
9.	First, convert **4A 56 78 9B** & **85 64 7E 92** into binary.
      - As the values are given in hexadecimal format use [CyberChef](https://gchq.github.io/CyberChef/) to convert it to 32 bits binary.
      - **Note**: Ensure that each number corresponds to an 8-bit binary, guaranteeing a 32-bit binary before performing the XOR operation.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/ede6b94d-d8a6-4c8a-9219-b3ba5fa937f3)

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/e613fe31-6a04-4554-aa8b-4a6816aea975)

9.	Perform the XOR operation (M1 XOR T2). 
      -	Use [XOR Cipher (dcode.fr)]( https://www.dcode.fr/xor-cipher) to perform xor operation.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/9ca37fab-89b0-4936-a1ac-1674eda7e876)

10.	Convert the value (xored value) into hexadecimal.

![image](https://github.com/TrojanNinja/Nascon-24-CTF/assets/122688432/ed475493-52b2-40a5-978e-5df4a2dcfe98)

11.	Finally, to complete the formula, concatenate M2 with the XORed answer.
      - [M2 || (M1 XOR T2)]

13.	**[M2 || (M1 XOR T2)]** = 88 98 6D 8F concat CF 32 06 09 ==> **88 98 6D 8F CF 32 06 09**
    
15.	Since the flag can't have spaces and adhering to the flag format, introduce underscores in place of spaces.
    Finally, here's the flag: **CSL{88_98_6D_8F_CF_32_06_09}**.



