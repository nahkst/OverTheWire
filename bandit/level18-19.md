# Bandit Level 18 - Level 19

This level demonstrates how to bypass restrictions caused by modified shell
startup scripts. You are told that someone has modified the .bashrc file 
so that every time you log in, you are immediately logged out.

You are also told that the password is stored in a file in the 'home' directory, therefore making
it easy to obtain with a simple command. ( basically handing you the solution )

Thankfully SSH allows you to send a command remotely. Simply by appending the command to the end of 
the request to the login request. SSH will then run the command on the server as if it was run locally. 

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```

Is what I ran to get the password. The server asked the current levels password ( which I had )
and the presto. It ran the command I sent remotely and gave me the password for the next level. 
