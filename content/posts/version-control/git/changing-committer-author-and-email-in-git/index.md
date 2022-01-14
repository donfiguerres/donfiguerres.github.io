---
title: "Changing Committer, Author, and Email in Git"
description: "Changing the Committer, Author, and Email in Git"
date: 2021-08-10T00:12:25+08:00
hero: images/commit-logs.jpg
menu:
  sidebar:
    name: "Changing Committer, Author, and Email in Git"
    identifier: changing-committer-author-and-email-in-git
    parent: git
---

I recently observed in my GitHub profile that most of my commits are not
shown in my contribution activity. After doing a quick search, I found that the
problem because my email in my commits do not match the email associated with
my GitHub account.

## Changing Commits in the Remote Repository

You need to use the filter-branch command to change the emails and names.

```sh
git filter-branch -f --env-filter '
    GIT_AUTHOR_NAME="yourname";
    GIT_AUTHOR_EMAIL="youremaill@host.com"
    GIT_COMMITTER_NAME="yourname";
    GIT_COMMITTER_EMAIL="youremail@host.com"
' HEAD
```

The command above changes the email and name for all of the commits. If you're
working on a shared repository, you need to use an if statement to change only
your commits.

```sh
git filter-branch -f --env-filter '
if [ "$GIT_AUTHOR_NAME" = "oldname" ];
then
    GIT_AUTHOR_NAME="newname";
    GIT_AUTHOR_EMAIL="newemail@host.com"
fi
if [ "$GIT_COMMITTER_NAME" = "oldname" ];
then
    GIT_COMMITTER_NAME="newname";
    GIT_COMMITTER_EMAIL="newemail@host.com"
fi
' HEAD
```

After executing the command. You'll have a backup history named original.
Delete it with this command.

```sh
git update-ref -d refs/original/refs/heads/master
```

Then remove the directory.
```
rm -rf .git/refs/original
```

After performing the steps above, you can check if the author and committer name
and email were changed using the log command.

```sh
git log --pretty=format:"[%h] %cd - Committer: %cn (%ce), Author: %an (%ae)"
```

To push your changes to the remote repository.
```
git push --force --tags origin HEAD:master
```

After pushing your changes, you can now verify your commit logs in the remote
repository. If you're on GitHub, the author avatar should match your GitHub
profile picture. Your commit should also now be shown in your contributions.

> **NOTE**: Note that `.git/logs` will still have logs that contain your old
name and email.


## Changing Local Commits

If in case you still haven't pushed your commits, then you can still use --amend
option in commit to correct your name and email.

```sh
git config --global user.name "yourname"
git config --global user.email youremail@host.com
git commit --amend --reset-author
```

## Refrences
source: https://stackoverflow.com/questions/750172/how-to-change-the-author-and-committer-name-and-e-mail-of-multiple-commits-in-gi/4903673