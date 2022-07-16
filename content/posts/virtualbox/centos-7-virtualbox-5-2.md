---
title: "CentOS 7 VirtualBox 5.2 Error"
description: "Error in CentOS after updating VirtualBox to 5.2"
date: 2017-10-25
menu:
  sidebar:
    name: "CentOS 7 VirtualBox 5.2 Error"
    identifier: centos-7-virtualbox-5.2-error
    parent: virtualbox
---

## Issue

A recent linux kernel update (3.10.0-693.2.2.el7.x86_64) caused the VirtualBox Guest Additions 5.2 in my CentOS7 box to break.

Error message:

```sh
/tmp/vbox.0/hgsmi_base.c: In function ‘hgsmi_send_caps_info’:
/tmp/vbox.0/hgsmi_base.c:99:2: error: implicit declaration of function ‘AssertRC’ [-Werror=implicit-function-declaration]
  AssertRC(p->rc);^M
  ^
cc1: some warnings being treated as errors
make[2]: *** [/tmp/vbox.0/hgsmi_base.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxvideo] Error 2
```

More information is in this [virtualbox thread](https://forums.virtualbox.org/viewtopic.php?f=1&t=85080)

[virtualbox ticket](https://www.virtualbox.org/ticket/17163)

## Resolution

An updated VirtualBox Guest Additions installer which contains the fix can now be downloaded from the [virtualbox website](https://www.virtualbox.org/wiki/Downloads).
