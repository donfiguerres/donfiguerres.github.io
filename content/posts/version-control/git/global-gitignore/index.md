---
title: "Global gitignore File"
description: "How to ignore files globally for the user in Git."
date: 2022-07-01T23:15:00+08:00
hero: images/steps-screenshot.png
menu:
  sidebar:
    name: "Global gitignore File"
    identifier: global-gitignore-file
    parent: git
---

When working with a version control system, you normally have files that are
not ignored in some projects but you would like to ignore in globally in your
workstation environment. The ways to do that are listed below.


## Option 1: The git/ignore file in the home directory

The user's ignore file is mentioned briefly in the
[Git documentation](https://git-scm.com/docs/gitignore#_synopsis). You can add
here your ignore rules the same way as you do it with your project .gitignore
rules.

> ***NOTE:*** This file will not exist by default so you have to manually create
it.

__*nix__

```bash
~/.config/git/ignore
```

__Windows__

```cmd
%USERPROFILE%\git\ignore
```


## Option 2: Using core.excludesFile

The core.excludesFile option is metioned in the
[Git documentation](https://git-scm.com/docs/gitignore#_cofiguration).

Follow the commands below to set-up your global gitignore file.

> ***NOTE:*** You can use any file name and path you want but I've used
`.gitignore` in the user's home directory the examples below to make it
consistent with typical preferences.


__*nix__

```bash
git config --global core.excludesFile '~/.gitignore'
```

__Windows cmd__


```cmd
git config --global core.excludesFile "%USERPROFILE%\.gitignore"
```

__Windows PowerShell__

```powershell
git config --global core.excludesFile "$Env:USERPROFILE\.gitignore"
```

## References
- https://stackoverflow.com/questions/7335420/global-git-ignore/