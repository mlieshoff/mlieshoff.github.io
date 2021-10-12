---
layout: post
title: (Git) Global ignore file
---

```
~/.gitignore_global
```

```
*.bak
*/tmp/*
```

```
~/.gitconfig
```

```
[core]
    excludesfile = /home/<USER>/.gitignore_global
    autocrlf = input
[user]
    name = <USER>
    email = <USER>
[push]
    default = current
```
