---
title: Git stash
layout: default
description: huthesh.github.io
categories: [Git]
---
<ol class="breadcrumb">
  <li><a href="/Git">Git</a></li>
  <li class="active">Git stash</li>
</ol>

<div>
        {{ page.date | date: "%-d %B %Y" }}
</div>

## Stash a file while retaining other files



```
git add <file to retain>
git stash --keep-index
git reset
```

## Stash to branch


```
git stash branch <branch name>
```
This command will
<ol>
  <li>Creates a new branch with the name given</li>
  <li>Commits the changes in current branch to new branch</li>
  <li>Stash the changes in current branch</li>
</ol>


## Amend last commit message


```
git commit --amend -m "<Modified message>"
```

## Find Diff 

```
git diff local_branch origin/branch

git diff <<<<<<< Code diff unstaged files

git diff --staged <<<<<<< Code diff staged files or added files. 

git diff --name-only <<<<< Show only name of the files changed

git diff --name-status <<<<<<< Show file name and status

git diff --cached <<<<<< 

git diff HEAD <<<<<<<<< Both staged and unstaged 

git diff <branch> <<<<<<<<< diff of local and any branch (local or remote)

git diff --stat 
```

