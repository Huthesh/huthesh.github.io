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
1. Creates a new branch with the name given
2. Commits the changes in current branch to new branch
3. Stash the changes in current branch
