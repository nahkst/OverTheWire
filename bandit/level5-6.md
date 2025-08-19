# Bandit Level 5 -> Level 6

Level 5 presents the first actual challenge of this series. The goal is to find a specific file in multiple folders
that matches a certain criteria. 

"""
human-readable
1033 bytes in size
not executable
"""

In the beginning I tried to use some sort of loop over each file and display the size of the file and whether or not it is human-readable. 
Something like: 

```bash
for d in *; do ls -h -s "$d"; done
```

This does not work effectively. The reason is because ls -h -s "$d" lists the contents of a directory and shows the disk space allocated for each file, 
not the actual file size in bytes. That’s why it doesn’t help filter by 1033 bytes. This presented a problem. 

So I did some digging. 

I found out that I can use "find" with some criteria to filter each file if it doesn't match. This is because the file command matches more specifically
to the file's actual properties.

```bash
find ./inhere -type f ! -executable -size 1033c -exec cat {} \;
```

"-type f" is telling the function to only look for files
"! -executable" filters out any file that is an executable 
"-size 1033c" looks for a file that is strictly 1033 bytes.
"exec cat {} \" executes the cat function on the file when the criteria match

This is a broad scope, in the way that looking for this file might match multiple criteria. Though for this exercise it works fine. 
That is why using "cat" on the file found prints the password. In another case it might display more text than needed. 

