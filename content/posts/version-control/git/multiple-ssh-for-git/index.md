---
title: "Setting up multiple SSH keys in a single machine"
description: "How set multiple ssh keys in a single machine."
date: 2025-05-05T22:00:00+08:00
hero: images/steps-screenshot.png
menu:
  sidebar:
    name: "Global gitignore File"
    identifier: global-gitignore-file
    parent: git
---

This is helpful in order to authenticate using SSH keys in a single machine for multiple
accounts.

For example, you want to setup SSH keys in GitHub to authenticate for you work account
and another SSH key to authenticate for your personal account.

## Step 1: Generate SSH keys

```bash
ssh-keygen -t ed25519 -C "<your_email@example.com> <your organization name> <service>"

# Example
ssh-keygen -t ed25519 -C "myaccount@gmail.com MyOrg GitHub"
```

When asked for the file path of the key, make sure to add more context to the file name.
I usually use `encryption_service_org`.

```bash
# Example
~/.ssh/id_ed25519_github_myorg
```

## Step 2: Add SSH keys to your account

Copy the public key and add it to your account. There usually is a setting in your account
to add SSH keys.

For example, in GitHub, you can go to `Settings -> SSH and GPG keys -> New SSH key`.

## Step 3: Update your `~/.ssh/config` file

Open your `~/.ssh/config` file and add the following lines:

```
Host github-myorg
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519_github_myorg
  IdentitiesOnly yes
```

## Step 4: Update your `.gitconfig` file

Open your `~/.gitconfig` file and add `insteadOf` configurations to replace the URLs
with the configuration you've created in step 3.

For example

```ini
[url "ssh://git@github-myorg/myorg"]
        insteadOf = https://github.com/myorg
[url "ssh://git@github-myorg/myorg"]
        insteadOf = git@github.com:myorg
```

## References

- <https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent>
- <https://stackoverflow.com/questions/72650911/ssh-key-managment-for-multiple-git-accounts>
