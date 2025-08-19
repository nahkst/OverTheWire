# Bandit Level 19 - Level 20 

In this level, the home directory contains a file called `bandit20-do`.

```
ls -l
```

Reveals that the binary exists and has the setuid flag set, this means
that the binary bandit20-do will run a command as if it were bandit20.
Regardless of who is running the command. 

Allowing you to read the next password with: 

```
./bandit20-do cat /etc/bandit_pass/bandit20 
```

Password revealed.
