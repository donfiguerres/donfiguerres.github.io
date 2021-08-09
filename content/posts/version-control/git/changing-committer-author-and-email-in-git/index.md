---
title: "Changing Committer, Author, and Email in Git"
description: "Changing the "
date: 2021-08-10T00:12:25+08:00
hero: images/commit-logs.jpg
menu:
  sidebar:
    name: "Changing Committer, Author, and Email in Git"
    identifier: changing-committer-author-and-email-in-git
    parent: git
---


**NOTE**: to be updated

For local

git config --global user.name "you name"
git config --global user.email you@domain.com
git commit --amend --reset-author


Change in remote
git filter-branch -f --env-filter '
    GIT_AUTHOR_EMAIL="lyndonfiguerres@gmail.com"
    GIT_COMMITTER_EMAIL="lyndonfiguerres@gmail.com"
' HEAD


git log --pretty=format:"[%h] %cd - Committer: %cn (%ce), Author: %an (%ae)"

git update-ref -d refs/original/refs/heads/master

rm -rf .git/refs/original

git push --force --tags origin HEAD:master


source: https://stackoverflow.com/questions/750172/how-to-change-the-author-and-committer-name-and-e-mail-of-multiple-commits-in-gi/4903673