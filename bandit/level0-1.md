# Bandit Level 1 → Level 2

Once you gain access to bandit1:

The password for level 2 is in a file called `"-"`.

This is a trick question because if you use `cat -` the hyphen (`"-"`) refers to STDIN/STDOUT, i.e., `/dev/stdin`, `/dev/stdout`.

This makes `"-"` a special character. So in order to open this file you need to explicitly state that it is a file using `./-`.

The answer being: `cat ./-`
