# Bandit Level 13 - Level 14 

This one is quite straight-forward. The level gives you a private ssh key which you need to use to access
the next level. Bandit14 has the correct privileges in order for you to read the password found at 

"/etc/bandit_pass/bandit14" 

This means that you have ssh from bandit13 into bandit14 using this private key. 

```bash
ssh ./sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

This gives access to the next machine, and here you run the command. 

```bash
cat /etc/bandit_pass/bandit14
```

To reveal the password.

