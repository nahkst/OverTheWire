# Bandit Level 14 → Level 15

In this level you need to submit the current level’s password to localhost on port 30000.

First, I verified that the port was open by scanning with nmap:

```
nmap localhost
```

Sure enough, port 30000/tcp was open.

I then used netcat (nc) to connect and send the password:

```
nc localhost 30000
```

The connection prompted me for the password. After entering the Bandit14 password, I received the password for Level 15.
