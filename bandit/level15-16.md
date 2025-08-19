# Bandit Level 15 - Level 16

In this level you are tasked with doing the same thing as level 14 - 15.
The key difference being that you need to use an SSL connection to do this. 

Openssl is the command that should be used to achieve this because it grants the user SSL
over the connection with s_client. It "wraps" the connection with a secure layer.

```bash
openssl s_client -connect localhost:30001
```

This spits a bunch of text back at you and waits for an input when it's done. 

If you input the current level's password you will get "Correct" followed by the password 
for the next level.
