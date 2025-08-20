# Bandit Level 29 - Level 30

The funny thing is, that this happens all the time in development. 
API keys, secrets, sensitive information. It all sometimes finds it's way onto a repo.
This level is no different. You try the initial,

`cat README` 

And that reveals: 

```bash
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
```
"- password: <no passwords in production!>" This is the hint. This tells me that there's
possibly more than one branch. So after a quick: 

`git branch -r`

You will see the following: 

```bash
  origin/HEAD -> origin/master
  origin/dev
  origin/master
  origin/sploits-dev
```

Suspicions confirmed. Even better there is a "dev" branch. So we should run: 

```bash
git checkout dev
cat README
```

Hey! There it is. The password for the level. 

You wouldn't believe how many times this actually happens.
