# Bandit Level 3 → Level 4

This level is a little trickier than previously faced. The file is hidden in a folder called `inhere`.  

It is easy to access this file by finding out what the file is called using:

```bash
ls -a ./inhere
```

Then you notice the file is aptly called ...Hiding-From-You. In order to access it easily, just use:

```bash
cat ./inhere/"...Hiding-From-You"
```

This will display the contents of the file.
