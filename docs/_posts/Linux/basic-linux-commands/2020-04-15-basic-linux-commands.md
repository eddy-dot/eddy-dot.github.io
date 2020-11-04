---
weight: 1
title: "Linux Commands"
date: 2020-04-15T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Eddy Valverde"
authorLink: "https://dits.technology"
description: "This article shows the basic commands for Linux server administration."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Linux", "Bash", "Terminal"]
categories: ["Tutorial"]

lightgallery: true
---

# Basic Linux Commands

```bash
vmstat 5 5
```

>show cpu usage id(idle), 5 times, 5 seconds of difference one another

<br />

```bash
top
```

>show current memory and cpu usage, and open applications with its resource consuming percentage.

<br />

```bash
 history
 ```
>shows the commands typed y the current user

<br />

```bash
cd
```

>navigates in linux directories

<br />

```bash
ls -la [optional path]
```

>lists files in the current path or the specified path

<br />

```bash
mkdir directoryname
```

>mkdir command creates a new directory in the specified directory

<br />

```bash
chown username:groupname file
```

>changes file’s ownership and group

<br />

```bash
chmod 777 file
```

>changes permissions of a file, the order of the number represent (owner, group, other) and each number represents rwx(read, write, execute)

<br />

```bash
df -h
```

>shows the usage of the server’s Filesystems

<br />

```bash
touch filename.extension
```

>creates a file

<br />

```bash
usermod -aG groupname username
```

>add user to a group

<br />

```bash
usermod -aG sudo username
```

>add user to sudoers file

<br />

```bash
sudo su username
```

>login in the system as the specified username

<br />