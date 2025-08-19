# Bandit Level 22 - Level 23

Cron jobs seem to be the following suit for the last level and this one. 
Basically you need to be able to read the script and tell what it does. 
This one in particular takes the name "bandit22" from `whoami` and creates a target folder: 

```bash
myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
```

This reveals that the target directory is a md5 hashed value. With white space removed. 
This is because md5 usually will hash something in the format: 

```
3f76e1e8b5d2e8a1a7f2c8e2a5d9f1b2  -
```

The command cut -d ' ' -f 1 removes the whitespace by splitting the string at the space and returning the first part.

What is easy is that you can simply run this script with:

```bash
/usr/bin/cronjob_bandit23.sh
```

Which will output that the password has been saved to a tmp file. 
Copy the value for the tmp file and do:

```bash
cat /tmp/VALUE_TO_TMP_FILE
```

Right, so now that I've explained this part. I need to now explain the next step.

Because you are logged in as "bandit22" when running this script. The hashed string will be for bandit22. This means
that we have to trick the system into created a hashed string for bandit23. I did this by doing: 

```bash
myname="bandit23"
echo I am $myname | md5sum
```

Which returned a hashed value, I copied that and used `cat` to print out the value from the temporary
file called 


```bash
cat /tmp/VALUE_TO_TMP_FILE
```

Hey presto! You've got your password.
