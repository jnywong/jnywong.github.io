---
title: "VSCode for Remote Development"
date: 2023-07-26
date-format: long
author: "Jenny Wong"
venue:
  title: "Baskerville Remote Drop-In"
---

## Visual Studio Code

VSCode is an editor made by Microsoft for Windows, Linux and macOS.

Feature-rich compared to Vi, nano, etc., with extensions for

- Git
- linting
- intelligent code completion
- Remote Development
- and more!

Install Visual Studio Code [here](https://code.visualstudio.com/).

---

## SSH

Secure Shell (SSH) is a network communication protocol that allows two computers to communicate, e.g. your laptop and Baskerville.

*Pre-requisite:* For VSCode Remote Development to work, you need an SSH Client installed.

| OS | Instructions |
| -- | -- |
| Windows 10+ | Install the [Windows OpenSSH Client](https://learn.microsoft.com/windows-server/administration/openssh/openssh_install_firstuse) |
| Earlier Windows | Install [Git for Windows](https://git-scm.com/download/win) |
| macOS | Comes pre-installed |
| Debian/Ubuntu | Run `sudo apt-get install openssh-client`|
| RHEL/Fedora/CentOS | Run `sudo yum install openssh-clients`|

---

## Install Remote - SSH Extension

:::{iframe} https://www.youtube.com/embed/cc0jlKC0bGQ?si=T4MnuYTZzDLqqCEV
:width: 100%
:::

---

## Add New SSH Host

:::{iframe} https://www.youtube.com/embed/4ev1KdKLC5A?si=YHKI7L61z7KMTWde
:width: 100%
:::

---

## Close Remote Connection

:::{iframe} https://www.youtube.com/embed/Y_9BFnhFRzI?si=vcq4pOsVBbQ9r0__
:width: 100%
:::

---

## Install Remote Explorer

:::{iframe} https://www.youtube.com/embed/-pWhznkkjtM?si=hvqU2Un0rtFlCElV
:width: 100%
:::

---

## Port Forwarding

You might want to run an application on Baskerville that launches a server remotely and view it on your local browser.

Port forwarding is a way to redirect the remote application's server address and port to your local browser.

Run this command on your **local machine**

```bash
ssh -N -L <local_port>:bask-pg0XXXuXXX:<remote_port> baskerville
```

where 

- `bask-pg0XXXuXXX` is the nodename of the Baskerville **compute node** you are running the remote application
- `<local_port>` is any number from 0 to 65353 (that's not already in use)
- `<remote_port>` is the port number your remote application is using (usually able to manually define this)

---

## Port Forwarding - Tensorboard

:::{iframe} https://www.youtube.com/embed/_sHpwUwX5wo?si=apBVe2ffiahXOa1M
:width: 100%
:::

---

## tmux

Using `tmux` on Baskerville allows you to create interactive jobs that you can detach from. If you get disconnected from the cluster, for example by putting your laptop to sleep, your resource allocation on Baskerville will be terminated and your job killed.

You can avoid this with `tmux`, where you can detach gracefully from a session Baskerville and `tmux` will continue your session in the background until you come back.

*Baskerville is a shared resource. Please don't leave your job idle, and remember to `scancel` your job when you are finished.*

---

## Interactive Job without tmux

:::{iframe} https://www.youtube.com/embed/iRk-RbAbOvA?si=lK2J4CEWA0uHzB0S
:width: 100%
:::

---

## Interactive Job with tmux

:::{iframe} https://www.youtube.com/embed/ufSwCbo7HQs?si=afmB94YAIbe9j3eo
:width: 100%
:::

---

## Summary

- **VSCode** is a powerful, feature-rich text editor
- VSCode Extensions can aid remote development on Baskerville HPC clusters, such as
  - **Remote - SSH**
  - **Remote explorer**
- **Port forward** to view remote applications in your local web browser
- `tmux` keeps your terminal session alive when your connection to the cluster drops

---

## Useful resources

- [docs.baskerville.ac.uk](https://docs.baskerville.ac.uk)
- [apps.baskerville.ac.uk](https://apps.baskerville.ac.uk)
- [admin.baskerville.ac.uk](https://admin.baskerville.ac.uk)
- [portal.baskerville.ac.uk](https://portal.baskerville.ac.uk)
- [Baskerville HPC GitHub](https://github.com/baskerville-hpc)
- Email us at [baskerville-tier2-support@contacts.bham.ac.uk](mailto:baskerville-tier2-support@contacts.bham.ac.uk)
