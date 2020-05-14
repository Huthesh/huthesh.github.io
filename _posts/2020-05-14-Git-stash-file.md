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
