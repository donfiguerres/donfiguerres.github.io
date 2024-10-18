---
title: "Common Tools for Software Development"
description: "Common Tools for Software Development"
date: 2022-06-23T23:34:00+08:00
hero: images/pexels-nemuel-sereti-6424586.jpg
menu:
  sidebar:
    name: "Common Tools for Software Development"
    identifier: common-tools
    parent: software-development
---

List of tools that I've used throughout my development career that you might
find useful too. I use this list when setting up a new VM or workstation.

## Browser

- [Google Chrome](https://www.google.com/chrome)
  - It's most people's default browser although Edge has a better performance in
  Windows.
- [Brave Browser](https://brave.com)
  - I use this personally for browsing.
  - It has a lot of default privacy features.
  - Can be used to test if a website will continue to function if all the
  security and privacy features are enabled.
- [Firfox](https://www.mozilla.org/)
  - Has cool privacy features and containerization feature.

## Package Manager

- [Homebrew](https://brew.sh/)
  - Homebrew initially started as a MacOS package manager but is now available
  for Linux distros. It's a good package manager if you want to always have
  the latest version of the software you need. Otherwise, it's hard to keep
  older versions as the philosophy of Homebrew is to only maintain the latest
  versions.

## Editor

- [VSCode](https://code.visualstudio.com)
  - Basically an editor on steroids.
  - Can function as an IDE through extensions.
  - List of extensions
    - Vim by vscodevim
    - C/C++ Extension Pack by Microsoft
    - CMake by twxs
    - Python by Microsoft
    - C# by Microsoft
    - Extension Pack for Java by Microsoft
    - Intellicode by Microsoft
    - GitLense by GitKraken
    - Git History by Don Jayamanne
    - Remote - SSH and Remote - WSL by Microsoft
- [Notepad++](https://notepad-plus-plus.org)
  - Handy windows notepad editor.

- [neovim](https://neovim.io/)
  - This is a very extensible successor to vim. The are a lot of plug ins
  available to give it the IDE experience. I'm currently using
  [LazyVim](https://www.lazyvim.org/) setup. I keep my current configuration
  [here](https://github.com/donfiguerres/donfiguerres-neovim-config).

## IDE

- [Intellij](https://www.jetbrains.com/idea)
  - Probably the best IDE for Java development.
- [Eclipse](https://www.eclipse.org)
  - Not the best IDE but I'm keeping it here since there are limitations in the
  community edition of Intellij.

## File Explorer

- [Multi Commander](http://multicommander.com)
  - Far Manager alternative.
  - Useful when opening a lot of directories simultaneously.

## Process Manager and Monitoring

- [Process Explorer](https://docs.microsoft.com/en-us/sysinternals/downloads/process-explorer)
  - A superuser alternative to Task Manager.
- [Process Hacker](https://processhacker.sourceforge.io/)
  - A much more modern alternative to Process Explorer.
  - Note: This tool has been flagged recently as malware by antivirus softwares
  because malicious actors have used it in some attacks.
- [htop](https://htop.dev/)
  - A great process manager for Linux.
  - A modern alternative to top.

## Terminal and Terminal Emulator

- [PuTTY](https://www.putty.org)
  - Remote connection to *nix and IBM i machines.
  - WSL can basically replace this tool but I'm keeping it here just in case.
- [WinSCP](https://winscp.net)
  - File explorer to a remote machine.
- [tmux](https://github.com/tmux/tmux/)
  - Tmux is a terminal multiplexer that helps you to manage multiple terminal
  sessions.

## Remote Desktop

- [mRemoteNG](https://mremoteng.org)
- Remote desktop connection manager where you can connect to multiple remote
  desktops and the connections are arranged via tabs.
- [VcXsrv](https://sourceforge.net/projects/vcxsrv)
  - X11 Window server
  - More actively developed than Xming.

## Virtualization

- [VirtualBox](www.virtualbox.org)
  - For hosting virtual machines

## Containerization

- [Docker](https://www.docker.com)
  - Modern day containerization.

## Version Control

- [Git](https://git-scm.com)
  - Need I say more? Even this website version controlled with Git.
  - Follow [this guide](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-git)
  for setting up in WSL especially for credential management.

## API Platform

- [Postman](https://www.postman.com/)
  - Postman is described in its website as "an API platform for building and using APIs".
    It is something I often use for testing REST API endpoints. Currently, it
    can also support websockets.

## LDAP Browser

- [JXplorer](http://jxplorer.org)
  - Free LDAP Browser

## Database

- [SQL Developer](https://www.oracle.com/database/technologies/appdev/sqldeveloper-landing.html)
  - No longer bundled with Oracle database starting from version 19.
- [IBM Data Studio](https://www.ibm.com/ph-en/products/ibm-data-studio)
  - DB2 development studio

## IBM

- [IBM i Access - Client Solutions](https://www.ibm.com/support/pages/ibm-i-access-client-solutions)
  - 5250 terminal (green screen) emulator is handy when connecting to IBM i
  machines.

## Meeting Tools

Developing software requires a lot of collaboration so minimizing noise coming
into your microphone is also essential.

- [Real-time Noise Suppression Plugin](https://github.com/werman/noise-suppression-for-voice)
  - This is a noise suppression plugin that filters out non-voice sound from
  your microphone. I currently use it as a plugin for [Equalizer APO](https://sourceforge.net/projects/equalizerapo/)
  which is an equalizer application for Windows.
