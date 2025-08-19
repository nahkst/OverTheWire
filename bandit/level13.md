# Bandit Level 13 - Level 14

Data.txt is a hex dump of a file that has been repeatedly compressed. In this level you have to
figure out how to decompress the file. I started by following the instructions on the page saying that
I should start a temporary folder. Inside this folder I copied the hex dumped file and renamed it to 
data.bin. 

I then could use "file" on this file to find out what was used to compress it. 

```bash
file data.bin
```

Revealed that the file was compressed using gzip. Which meant I should rename the file again to "data.gz".
After I had done this I was able to decompress the file using "gunzip". Which after running "file" on the new file
I discovered that bzip2 was used. Meaning I had to rename the file again to "data.bz2". So that I could use 
bunzip2 on the new file. 

A couple iterations later and I got a .tar file. This meant I had to use: 

```bash
tar -xf data6
```

To reveal another gzip compresed file. This was the case until finally a data8 reveled itself to be ASCII text.

This was the password. 

A simple procedure for something that initially looked complex.
