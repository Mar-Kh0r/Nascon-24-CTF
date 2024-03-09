# Cryptography Challenge Writeup: Crash The Hash

Author: DarkCipher

---

## Introduction

Our data servers recently faced an attempted breach, but our team managed to thwart the attack, preserving all our data. We obtained a hash associated with the perpetrator's account, which we suspect could lead us to a crucial password. Additionally, we acquired an image from the intruder's system. This writeup details our analysis and efforts to crack the hash, as well as insights from the image related to the individual, Jamal.

- **Title**: Crash The Hash
- **Type**: Hard
- **Flag Format**: CSL{type_plaintext}

---

## Hash Details

- **Hash**: `$2a$04$br3E2dcYMacuD.xXoejoPeMx26ruKt0irg34CBRVBlNJVkAKAFqXK`
- **Type of Hash**: bcrypt (Identified By online Tool Hash Analyzer)
- *https://www.tunnelsup.com/hash-analyzer/*

---

## Image Analysis

Upon inspecting the image, we extracted metadata using Exiftool, which revealed the username 'coolboyjamal' from the author name. Further investigation led us to an Instagram account belonging to Jamal.

Upon inspecting profile each post had a topic so from description of challenge we knew that we have to gather important words.Jamal's Instagram posts contained significant words and locations in the descriptions:

- Dubai
- Italy
- Japan
- Birthdate: 2842005
- Pakistan
- Biryani

---

## Generating Wordlist
From a hint we knew that after doing OSINT we have to make a wordlist. There are many tools for that but i perefered writing my own python code for that. So basically I combined 3 words at a time with all possible date combinations.

## Cracking the Hash

To crack the hash, we created a Python script that generated combinations of the significant words and the birthdate. We used these combinations with tools like John the Ripper or Hashcat to attempt to find the password associated with the hash.

### Python Script:

```python
from itertools import permutations

def generate_combinations(words, num_str):
    word_combinations = permutations(words, 3)
    all_word_combinations = [''.join(combo) for combo in word_combinations]
    num_combinations = permutations(num_str, len(num_str))
    all_num_combinations = [''.join(combo) for combo in num_combinations]
    combined_results = [word_combo + num_combo for word_combo in all_word_combinations for num_combo in all_num_combinations]
    return combined_results

def write_to_file(results, filename):
    with open(filename, 'w') as file:
        for result in results:
            file.write(result + '\n')

def main():
    words = ["dubai", "rawalpindi", "biryani", "japan", "pakistan", "italy"]
    date_numbers = "2842005"
    all_combinations = generate_combinations(words, date_numbers)
    write_to_file(all_combinations, 'wordlist.txt')

if __name__ == "__main__":
    main()
````

## Obtaining Flag

- Now finally we have a wordlist and a hash. SO we can use hashcat or johntheripper to get our final value
- **john --format=bcrypt --wordlist=wordlist.txt hash.txt**
- OR
- **hashcat -m 3200 hash wordlist.txt**

- It will return the flag after cracking hash sucessfuly. As this was only a 4 rounds bycrypt hash only took a few minutes to crack.

- **CSL{*}**
