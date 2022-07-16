---
title: "Git Connection Errors During Cloning"
description: "Various errors in git like 'fatal: fetch-pack: invalid index-pack output' when cloning a big repo."
date: 2022-01-14T17:18:36+08:00
hero: images/git-error.png
menu:
  sidebar:
    name: "Git Connection Errors During Cloning"
    identifier: git-connection-errors-during-cloning
    parent: git
---

I got these errors recently when I was trying to clone one of our repos.
Unstable network connection or network infrastructure may have caused this so
as a workaround, you can clone the repo "bit-by-bit".

```sh
$ git clone ssh://git@your.host.com/yourrepo.git
Cloning into 'projectdir'...
    ...
remote: Enumerating objects: 26639, done.
remote: Counting objects: 100% (269/269), done.
remote: Compressing objects: 100% (152/152), done.
client_loop: send disconnect: Connection reset by peer6 MiB/s
fetch-pack: unexpected disconnect while reading sideband packet
fatal: fetch-pack: invalid index-pack output
```

```sh
$ git clone ssh://git@your.host.com/yourrepo.git
Cloning into 'projectdir'...
    ...
remote: Enumerating objects: 26639, done.
remote: Counting objects: 100% (269/269), done.
remote: Compressing objects: 100% (152/152), done.
client_loop: send disconnect: Connection reset by peer9 MiB/s
fatal: early EOF
fatal: fetch-pack: invalid index-pack outputing sideband packet
```

## Workaround

The workaround is to checkout the repo bit-by-bit.

### Disable Compression

Not sure how this exactly helps but some users in the stackoverflow reference
claim that this actually fixed their error. No harm in trying. You will enable
it again in the succeeding steps.

```sh
git config --global core.compression 0
```

### Clone the Repo

Now, clone the repo using a depth of 1.

```sh
git clone --depth 1 <repo_URI>
```

example:

```sh
git clone --depth 1 ssh://git@your.host.com/yourrepo.git
```

### Enable Compression

Set compression back to default.

```sh
git config --global --unset core.compression
```

### Retrieve the Rest of the Repo

Try to retrieve the other commits.

```sh
git fetch --unshallow
```

Then try to fetch all branches. Note that in the command below, it is assumed
that the remote repository is named 'origin'. You should change it to the name
of your remote repository if otherwise.

```sh
git config remote.origin.fetch +refs/heads/*:refs/remotes/origin/*
git fetch --all
```

References:

- <https://stackoverflow.com/questions/21277806/fatal-early-eof-fatal-index-pack-failed>
- <https://stackoverflow.com/questions/20338500/git-repository-lost-its-remote-branches>
- <https://stackoverflow.com/questions/11868447/how-can-i-remove-an-entry-in-global-configuration-with-git-config>
