# Bandit Level 6 - Level 7

Alas, this level is not entirely different from the last save one thing. A bit more experience with the "find" command.

```bash
owned by user bandit7
owned by group bandit6
33 bytes in size
```

these are the criteria to be matched. So I started by pumping them into the find function: 

```bash
find . -user bandit7 -group bandit6 -size 33c -exec cat {} \;
```

This, of course, didn't work. The challenge was not going to give in that easily. 

So I tried something else, with a minor tweak. Let's check from the home directory. 

```bash
find ~ -user bandit7 -group bandit6 -size 33c -exec cat {} \;
```

Still nothing. So I changed the directory to go back to the parent directory.

I was met with every file pertaining to the bandit series. 

bandit1, bandit2, bandit3... and so on. 

This gave me an idea. I need to search through these folders to find the file that matches this description. 


```bash
find / -user bandit7 -group bandit6 -size 33c -exec cat {} \;
```
Changing from "." to "/" meant that I was now searching the entire system and not just the current directory.

This gave me a lot of permission errors. It made it hard to discover the right one. With a bit of scrolling you could see the password. 

I wanted to make it better, to print only the password. So I found: 


```bash
find . -user bandit7 -group bandit6 -size 33c 2>/dev/null -exec cat {} \;
```

 This worked a charm. There was the password.
