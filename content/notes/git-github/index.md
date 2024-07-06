
---
numbering: true
title: Git and Github
keywords: Git, GitHub, MarkDown, HTML
paper: A3
class: report
ShowToc: true
---

## New Repo
```
git init
```
to create new repo in directory.

## Commit Proccess

### Add new files

```
git add .
```
To stage all files in directory.

### Commit changes locally
```
git commit -m "Commit message here"
```
Create new commit with message.

### Push changes to remote
```
git push origin <branch name>
```
To push to remote named 'origin' 
and the branch name.

## Add Remote

(for github)

+ Create new repository on github.com
+ ensure that repository is set up
locally
+ stage and add a commit
+ make sure local repo is on correct
branch e.g. :

```
git branch -M main
```
+ add remote branch
e.g. for ssh:

```
git remote add origin git@github.com:Stephen-Zulauf/notes.git
```

or for http:

```
git remote add origin https://github.com/Stephen-Zulauf/notes.git
```

## Add SSH Auth

See [add ssh to git and github](../ssh)
gdlink:
[[ssh]]
