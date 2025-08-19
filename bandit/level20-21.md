# Bandit Level 20- Level 21

This level is the first real hacking section I think I've come across.
You need to act as the service that the binary './suconnect' talks to. 
This is because you can supply it with any port, there's no specificity.

So I started a service using:

```bash
echo -n PASSOWRD_FOR_BANDIT20 | nc -l -p 1234 &
```

This started a "function" that ran on port 1234. When queried it would return
the password for bandit20. Which is exactly what ./suconnect needs to recieve
in order to compare it to the text file it uses and ultimately return the next levels password. 

```bash
./suconnect 1234
```

Returned the password for the next level. 
