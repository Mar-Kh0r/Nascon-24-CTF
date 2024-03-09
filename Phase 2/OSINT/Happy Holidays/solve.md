# Investigation Report: Happy Holidays

Author: DarkCipher <br>
Type: Easy

---

## Introduction

Mr. Hamza, the head of our security department, went on vacation without providing details about an important virus that has affected our system. We urgently need information about this virus, but Mr. Hamza is unreachable. However, his voice mail provided a clue directing us to contact his assistant, Haris Rauf, at harisofficial19@gmail.com. Our objective is to identify the name and type of the virus and obtain its hash for further analysis.

- **Flag Format**: CSL{executablename_md5hash}

---

## Investigation Details

### Contacting Haris Rauf

Following the instructions in Mr. Hamza's voice mail, we reached out to Haris Rauf via email at harisofficial19@gmail.com.

### Obtaining New Username

Upon contacting Haris, we received a response indicating a new username, "harishacker19."

### Investigating the Username

We searched for "harishacker19" on name checking websites, which revealed that the username is prevalent on various platforms, including GitHub.

### Analyzing GitHub Repository

Upon visiting the GitHub repository associated with the username "harishacker19," we found a collection of ransomware-related files.

### Extracting Details

Within the repository, we discovered a file named "details.txt," which directed us to a Medium blog for further information.

### Hash Analysis

On the Medium blog, under the "Case Study" section, we found a hash: 
- **Hash**: 86e0eac8c5ce70c4b839ef18af5231b5f92e292b81e440193cdbdc7ed108049f

### Virus Identification

Using the hash, we conducted a search on VirusTotal, revealing the details of the virus:
- **Name**: VapeHacksLoader.exe
- **MD5 Hash**: c850f942ccf6e45230169cc4bd9eb5c8

---
The flag for this challenge is:
**CSL{*}**

