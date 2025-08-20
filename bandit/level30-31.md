# Bandit Level 30 - Level 31

This level was not so simple as the last few. It took a little while for me
to figure it out. It's to do with git tags. Now, I don't usually use these. 
They're forms of a special type of commit message. A "snapshot label"  as I've found they're
described online. I only stumbled on the answer to this by accident really. 

```bash
git tag -l
```

Revealed a tag called "secret":

```bash
git show secret
```

Will reveal the password. Though, it actually shows the commit content.
