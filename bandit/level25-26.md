# Bandit Level 25 - Level 26

This level and the next are linked. In a way you have to solve both of them at the same time.
I had no idea at first, but once you realise that the only way to get the ./bandit27-do script to 
run from bandit26 there is a way. 

The command to focus on here is the `more` command, and how to exploit it. 

When you log into bandit25 with SSH you are given a file ./bandit26-sshkey. This can be used
to access bandit26. However when you SSH in, you are immediately booted out. 
So how do we figure out what's going on here? Well, in the description it mentions that bandit26
is not using a normal shell (/bin/bash). It is using something custom. So after a quick
google search of how to check the shell. I found you can run: 

```bash
grep "^bandit26" /etc/passwd/
```

Which could translate to: 

```bash
/etc/passwd/ | grep bandit26
```

This revealed that the "shell" bandit 26 is using is at:

`bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext`

So let's read what this script "showtext" does: 

```bash
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh
export TERM=linux

exec more ~/text.txt
exit 0
```

Here's when I realised that it has to be something to do with the "more" command. Yet I couldn't
quite figure it out. I found out after searching online "more linux command exploit" and shortly after 
that I googled "escape rbash with more linux command". That the more command is exploitable because
it gives you access to vim/vi and in turn allows you to bypass rbash and run shell commands.

This gave me the solution but I needed to figure out how to get "more" to trigger. The solution to that
was really quite simple. And one of those "slap forehead" moments.

I was digging for a while and eventually stumbled upon it.

"To trigger the more command interactively, resizing the terminal window usually works in many terminals. 
Once more is open, you can press v to launch vi, which lets you run shell commands and escape the restricted shell."

I admit, this is the only time that I sought out the solution to this. I was upset, but I had figured about 90%
of the problem out on my own. This was acceptable to me.

Initially I started with: 

```vim
:e /etc/bandit_pass/bandit26
```

Which gave me access to the bandit26 password file. I copied that and saved it locally ( as I usually do ).

This is where 

[Bandit 27](./bandit26-27.md) comes in.
