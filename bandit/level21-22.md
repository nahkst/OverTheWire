# Bandit Level 21 - Level 22

This level was interesting. The password is stored in a tmp file that is consistently
updated by a cron job. First you need to find the cron job that is updating this file.

Looking inside /etc/cron.d/ you can see a file aptly named cronjob_bandit22.sh which
also has reading priviledges. You can discover this running: 

```bash
ls -l /etc/cron.d
```

Which will reveal all of the cronjobs. So because it's most likely that the password
for level 22 has something to do with the cron job named: cronjob_bandit22.sh I ran this:

```bash
cat cronjob_bandit22.sh
```

To see what sort of shell script is running. The script is inside the directory /usr/bin/
and is being run every few minutes or so. So with a quick

```bash
ls -l /usr/bin
```

We can see that this script is also readble. A quick `cat` on the file reveals that it does 
two things. It chmods a file to 644 making it world readable. And secondly it dumps the password
from /bandit_pass/bandit22 into a temporary file. So using that temporary file name we can do

```bash
cat /tmp/TEMPORARY_FILE_NAME
```

I've left this name out purposefully. As with all of the other explanations I've done. I'm not
here to reveal the answer. It's to showcase my problem solving ability. 

