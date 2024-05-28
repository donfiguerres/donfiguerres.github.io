---
title: "Tmux Settings"
description: "Tmux settings"
date: 2024-05-28T22:40:00+08:00
hero: images/pexels-nemuel-sereti-6424586.jpg
menu:
  sidebar:
    name: "Tmux Settings"
    identifier: tmux-settings
    parent: software-development
---

Saving here a copy of tmux settings so it's easy to set it up in a new machine.


```
set -g mouse on

# vi keybindings
set-window-option -g mode-keys vi
bind-key -T copy-mode-vi v send -X begin-selection
bind-key -T copy-mode-vi V send -X select-line
bind-key -T copy-mode-vi y send -X copy-pipe-and-cancel 'xclip -in -selection clipboard'

# required by neovim checkhealth
set -g default-terminal "tmux-256color"
set-option -sa terminal-features ',xterm-256color:RGB'
set-option -sg escape-time 10
set-option -g focus-events on
```
