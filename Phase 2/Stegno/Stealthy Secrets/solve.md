# Cryptography Challenge Writeup: Stealthy Secrets

Author: DarkCipher <br>
Type: Hard

---

## Introduction

An intriguing image surfaced within our team's files, accompanied by a cryptic voice note. Our team member suggested it holds something special, yet we've been unable to unravel its secrets. With layers of encryption woven into its pixels, the image challenges even the most seasoned codebreakers. Will you dare to venture into the realm of "Stealthy Secrets" and unearth the elusive flag concealed within?

- **Flag Format**: CSL{flag}

---

## Decrypting the Image

### Morse Code Decryption

The image contained a hidden message encoded in Morse code. Upon decoding, it revealed the passphrase: `NASCONISVERYAMAZING`.

### Steganography

As we had the filename `NasconIsCapatalized` so this was a hint.Utilizing the passphrase `NASCONisveryamazing`, we successfully unlocked the steganographically hidden content within the image. You can use any tool but i prefered steghide. <br>
*steghide extract -sF nascon.jpeg*

### Unveiling Hidden Content

Within the unlocked file, we encountered a combination of Base64 encoding and a Vigenère cipher.

### Deciphering the Clues

#### Base64 Decoding

We decoded the Base64-encoded message, revealing a hint encoded within.

#### Hint Unraveling

Applying a ROT13 cipher to the decoded hint provided us with guidance, indicating that a Vigenère cipher was in use and the key was embedded within and hint said that key is infront of our eyes.So upon trying different available text I tried the file name.

### Obtaining the Key

The key for the Vigenère cipher was identified as "cyp," derived from the filename.

### Decrypting the Flag

Using the "cyp" key, we successfully deciphered the Vigenère-encrypted text, revealing the elusive flag:
**CSL{*}**

