# Bandit Level 10 - Level 11

It is required that you find the human-readable text inside the "data.txt" file. The passwor is prepended with 
"=" which should help to search for the correct string. 

However, while you can use "cat" to read the whole file, it is tricky to find the right answer. 

This is where "strings" comes in. Strings gives you the human-readable text inside a file. So the correct
way to find out the answer is by doing: 

```bash
strings data.txt
```

which then displays the password for the next level. As you scroll down you will see it.
