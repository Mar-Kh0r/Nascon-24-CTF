# Investigation Report: Back from Holidays

Author: DarkCipher

---

## Introduction

Mr. Hamza has returned from his vacations, only to find that our systems have been compromised by a dangerous virus. Our team, while analyzing the virus, discovered alarming plans by attackers from America, Washington. These attackers are collaborating with a notorious organization, posing a severe threat to our systems and potentially causing massive destruction. Our mission is to thwart their plans at all costs.

We intercepted a suspicious message from the attackers' system, containing clues about their next meeting location. This writeup details our investigation process and the discovery of the meeting location and hotel contact information.

- **Flag Format**: CSL{Hotelname_Phonenumber}

---

## Investigation Details

### Clue Analysis

The intercepted message hinted at a meeting location in Washington, USA. The message mentioned a restaurant where "queen sits to watch snowy court."

### Searching for Snowy Courts

On Web, we conducted a search for "Snowy Courts" in Washington, which led us to Snows Court NW.

### Locating the Meeting Point

Upon further investigation on google maps, we discovered Queen Annes Ln NW, located adjacent to Snows Ct NW. In the vicinity, we identified The Rivers Inn on google maps, and adjacent to it, the Matera hotel (closest hotel).

### Retrieving Contact Information

By accessing the Matera hotel's details, we retrieved the contact number: +12023015401.

---

## Conclusion

Our investigation into the intercepted message led us to the Matera hotel, where the attackers plan to meet. By obtaining the hotel's contact information, we are better equipped to take necessary actions to prevent the meeting and thwart their malicious plans.

The flag for this challenge is:

**CSL{*}**

