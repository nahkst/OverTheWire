# Bandit Level 4 - Level 5

Level 4 is really quite simple with a little knowledge of a for loops. 

The password is hidden in one of the "human-readable" files inside the ./inhere folder. 

You could the manually do `cat "./--file..."` for every file but this is tedious.

Now because the files are named: "--file..." this means that you cannot simply use `cat *` 
which would normally reveal the contents of every file in the folder. 

So you would have to use `cat -- *`. 

Another alternative is to use a for-loop.

```bash
for f in *; do cat -- "$f"; done
```

by using "--" in this expression we are telling cat "everything after this filename:
