# Bandit Level 26 - Level 27

This level continues from level 25; after exiting SSH I realised:
When you try to login to 26 with the password, it immediately logs you out. 

So I did what I knew to do now, only differently. 

I resized the window and SSH'd into bandit26, which triggered more again.
Now because previously I had found out you could trick "more" into running shell commands via vi.
I had the idea to trick the system into running a legitimate bash shell. 
So then I accessed Vi inside more and wrote the following: 

```bash
:shell sh=/bin/bash/
:sh
```

Which placed me straight into running bandit26 in a proper shell. Then I had to check what 
files I had in the home directory.

```bash
ls
./bandit27-do ./text.txt
```

Well that's handily placed. There was an executable called "./bandit27-do" to which I wrote:

```bash
./bandit27-do cat /etc/bandit_pass/bandit27
```

This revealed the password for the next level. What was tricky at first turned out to solve two levels at once.
