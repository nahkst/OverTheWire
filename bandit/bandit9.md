# Bandit Level 9 - Level 10

In this level you are tasked with finding a unique string of characters inside a "data.txt" file. 
This can be achieved by running the command: 

```bash
sort data.txt | uniq -u
```

Which sorts all of the duplicated lines of text together, and then pipes the result to the "uniq"
command. Finally removing all the duplicates using the flag "-u" and outputting the result. 

