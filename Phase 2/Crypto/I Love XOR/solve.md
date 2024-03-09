# Cryptography Challenge Writeup: I Love XOR

Author: DarkCipher

---

## Introduction

In this challenge, our team member encrypted two image files using XOR, despite warnings against its use in encryption practices. The challenge was to crack these XORed files and retrieve the hidden information. The key hint provided was that both files were XORed using the same key.

- **Title**: I Love XOR
- **Flag Format**: CSL{flag}

---

## XOR Encryption

Our team member encrypted two image files using XOR encryption, making it challenging to retrieve the original images without the key. However, since the hint suggested that both files were XORed with the same key, it simplified our approach.

---

## Cracking the XOR Files

To crack the XOR files, we used the xortool, a tool specifically designed for XOR encryption.

### Steps:

1. Used xortool to combine the two XORed files into one raw data file.
   
   ```bash
   xortool-xor -f nascon.xor -f ctf.xor > file.data
2. Opened the raw data file in GIMP, adjusting the settings to ensure proper interpretation of the image.

3. Adjusted the width of the image and ajust offeset. In this case offset was default but width was needed to set 1200 and ensured the color format was set to RGB.

4. Examined the image and noticed that the flag was visible but inverted.

5. Inverted the image using GIMP's transformation tools.

6. After flipping the image vertically, we successfully retrieved the flag:

**CSL{*}**
