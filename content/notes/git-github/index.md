---
title: "Git and Github"
date: 2024-07-11
# weight: 1
# aliases: ["/first"]
tags: ["Git", "GitHub", "Markdown", "HTML"]
categories: ["notes"]
author: "behoovah"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: true
comments: false
# description: "Desc Text."
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: false
ShowPostNavLinks: false
ShowWordCount: true
ShowRssButtonInSectionTermList: false
UseHugoToc: true
# cover:
  #  image: "<image path/url>" # image path/url
  #  alt: "<alt text>" # alt text
  #  caption: "<text>" # display caption under cover
  #  relative: false # when using page bundles set this to true
  #  hidden: true # only hide on current single page
# editPost:
  #  URL: "https://github.com/<path_to_repo>/content"
  #  Text: "Suggest Changes" # edit text
  #  appendFilePath: true # to append file path to Edit link
---

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

### Generate SSH key/pair

(on arch)

```
$ ssh-keygen
```

### Add Public key to github.com

public key will be in file ending in .pub

+ click on profile picture in upper
right corner
+ click settings in the menu
+ click SSH and GPG keys
+ click New ssh key
+ copy and paste the full text from the .pub file

---
