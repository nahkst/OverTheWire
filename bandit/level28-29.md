# Bandit Level 28 - Level 29

Another Git challenge. This one is not as simple as reading a README file.
Instead this one challenges you by checking out the previous logs. 

Now usually when you clone a repo, you look at what you're given. But you should also
look at the previous changes, at least to get a rough idea of how the project has evolved.

This is done by doing: 

`git log`

Which will show you the latest logs for the current repo.
In this case it also reveals that the password, was added and then removed from the README file.

`git show GIT_COMMIT_ID`

Will reveal which commit had the password. 
