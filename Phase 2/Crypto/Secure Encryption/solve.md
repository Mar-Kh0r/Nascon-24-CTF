# Cryptography Challenge Writeup: Secure Encryption

Author: DarkCipher

---

## Introduction

During our Nascon preparation, our team was concerned about implementing a secure encryption algorithm. The Security team introduced a new technique to safeguard our systems. However, when the technical team tested it, none of us could decrypt the message provided by the Security team. This writeup documents our efforts to decrypt the message and understand the encryption process.

- **Cipher**: 4e1d6c22c577af24b772eade7f4aee
- **Flag format**: CSL{SecretMessage}

---

## Decryption Process

The Security team provided us with a cipher that none of us could decrypt. The message seemed to be encrypted using an unknown technique. There was a hint that this command  was encrypted using a linux utility. So on finding we came  accross a utiltiy xxd.


## Understanding XXD and its Usage

To understand the encryption process, let's first examine the usage of the `xxd` command. `xxd` is a command-line utility that converts binary data into a hexadecimal representation and vice versa.

### Encrypting the Message

The Security team encrypted the message using the following command:

```bash
echo -n message | base64 -d | xxd -p
```

- echo -n msg: Prints the message without a newline.
- base64 -d: Decodes the base64-encoded message.
- xxd -p: Converts the decoded message into hexadecimal format.

### Decrypting the Message

To decrypt the cipher, we need to reverse the process. Here's the command provided by the Security team:

```bash
echo 4e1d6c22c577af24b772eade7f4aee | xxd -r -p | base64
```
This will decrypt the code and will return the flag

**CSL{*}**

## Alternative Method

Another thing can be done for this challenge

We can use cyberchef to decrypt it but it will not get detected automatically. But a similar case for this challenege is available on internet so using that we can use **HEX to PEM** to decrypt it
*https://gchq.github.io/CyberChef/#recipe=Hex_to_PEM('CERTIFICATE')&input=NGUxOGFjMjJjNGUxNzkyYmE5ZGViNGI3NzJiZGQzMTY1ZTA2*
  
