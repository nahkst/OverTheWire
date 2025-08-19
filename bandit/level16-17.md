# Bandit Level 16 - Level 17

In this level you are required to scan ports 31000 - 32000 to find the open SSL port with a service
attached to it. The others that pop up simply echo your input back to you. There is one port however, 
that when you pass in the password for the current level it will return an SSH key for bandit 17.

```bash
nmap -p 31000-32000 --open -sV localhost
```

Which revealed a set of five open ports with services. Port 31790 stood out because it returned 
"invalid password. please enter the correct password". Thus it was the service I was looking for. 

I then used: 

```bash
echo "CURRENT_PASSWORD" | openssl s_client -connect localhost:31790
```

Obviously where "CURRENT_PASSWORD" is, I had the real password. ( I haven't added it here for reasons )
To enter the password and recieved an SSH key. I then saved this SSH key to my computer in a temporary file.
Followed by proper permissions. 

```bash
chmod 400 bandit17.key
```
After this I used this key to login to bandit 17 with

```bash
ssh -i bandit17.key bandit17@bandit.labs.overthewire.org -p 2220
```

En Voila 
