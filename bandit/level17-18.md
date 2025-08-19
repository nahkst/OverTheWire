# Bandit Level 18 - Level 19

The password for level 18 is stored in the passwords.new file, and is the only line that
is different from passwords.old. 

This puzzle is really quite easy to solve with knowledge of the "diff" command. Which tells the
immediate difference between two files. 

```bash
diff passwords.old passwords.new
```

This reveals the line where the passwords changed. The latter being the new password and therefore
the password for level 19. 
