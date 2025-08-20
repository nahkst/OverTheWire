# Bandit Level 23 - Level 24

This is the first level where you have to think outside the box a bit. The
task is to get the cron job to execute a file in a folder that you don't have access to. 
You need to create this file, and somehow get it into this folder. 

I started with checking out the script: 

```bash
cat /usr/bin/cronjob_bandit24
```

Which showed me something like this:

```bash
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

If you break down how this script works; it iterates through each file in this specific folder
"/var/spool/bandit24/foo", executes the file and the deletes the script. 
This happens every minute or so. 

I found out that there doesn't exist a folder called "/var/spool/bandit23/foo" which meant that,
I couldn't simply create a file at this location. And because I was connected to bandit23 I didn't
directly have permission for bandit24. 

This required a different approach. So i created a temporary folder under /tmp/something. Inside
this temporary folder I created a file called "tmp.sh" which I wrote the following:

```bash
#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/something/tmppass
```

I then gave this script permissions for anyone to execute using `chmod 777 tmp.sh`. I copied this file
into the folder "/var/spool/bandit24/foo" successfuly, and then waiting about a minute for a new file to
appear inside my temporary folder "something". 

This was successful and I finally used: 

```bash
cat ./tmppass
```

Which then revealed the password.

I initially tried to create a symlink to the folder, connecting /tmp/something to /var/spool/bandit24/foo
but when I used `cp` to copy the file to the /bandit24/foo folder. It actually worked to my surprise. 
I am not sure if this was supposed to happen. I dont think it should have because bandit23 isn't suppsed 
to have had access to that specific folder. Anyhow, it worked.

After that it was just a matter of time before the password was saved to the file `tmppass`.


* I also have a feeling that the method for the previous level will work on this level too. By changing
* the $myname to "bandit24" and getting cronjob to print the password to a temporary file.
