# Bandit Level 11 - Level 12

ROT13. A variation of the famous caesar cipher. ROT13 works by "rotating" a given letter 13 times in the alphabet. 
The trick here is to decrypt the data.txt file using "tr" but first you have to pipe the output from "cat"

```bash
cat data.txt | tr "N-ZA-Mn-za-m" "A-Za-z"
```

Where "N-ZA-Mn-za-m" describes the ROT13 letters and to switch them to "A-Za-z".
