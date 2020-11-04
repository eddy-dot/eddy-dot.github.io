---
title: "Basic Linux Tutorial"
date: 2020-11-01T21:57:40+08:00
categories:
  - Blog
tags:
  - Linux
  - Permissions
  - Security
---

[SOURCE CODE](https://github.com/eddy-dot/Linux-Tutorial)

| Command           | Description                                            | 
|-------------------|--------------------------------------------------------|
| cd                |used to navigate through directories, and home directory|
| cd ..             |navigates one directory behind the current path         | 
| cd <directoryname>|navigates inside a directory                            |
| ls -la            |lists directories and files in the current path         |
| cd /              |navigates to the root path                              |
| whoami            |shows the user we are currently using                   |

## Permisions

    Files and directories interacts with 3 types of actors:
-   **Owner** of the file/directory
-   Member of a **Group**
-   And **Other**, which is not the owner NOR a member of the group

Each actor can perform 3 actions:

|Action | Symbol| 
|-------|-------|
|Read   | **r** |
|Write  | **w** |
|Execute| **x** |

Combination of the actions with number:

|Number | Symbol| 
|-------|-------|
|   0   |  ---  |
|   1   |  --x  |
|   2   |  -w-  |
|   3   |  -wx  |
|   4   |  r--  |
|   5   |  r-x  |
|   6   |  rw-  |
|   7   |  rwx  |

```bash
    cd                  #let's go to the homw directory
    mkdir practice      #create a directory
    cd practice         #go inside the directory
    touch file1.txt     #create txt file
    touch file2.cpp     #create c++ file
    touch file3.cs      #create c# file
```
    Let's check the file permissions

```bash
    ls -la
```    
    Let's change those permissions

```bash
    chmod 777 file1.txt
    chmod 741 file2.cpp
    chmod 400 file3.cs
    ls -la
```
-    file1.txt has all the permissions, on real life this should be avoid because of high security treat of the server.
-   file2.cpp has a common permission pattern
-   file3.cs has a very strict security permission, used when files are too exposed like a web server to the internet

## Groups
    We can see in the listing of the files that there is a part where we see the username we are currently using tow times, separated by a semicolon, the fact is that the username in the left side of the semicolon i the user and the name on the right side of the semicolon corresponds to a groupname. When a user is created a group with the same name is created by default, and hen we are creating files and directories out user and group are assigned to them by default.

    Let's create a new group a new user:

```bash
    sudo useradd myusername
    groupadd mygroup
```
    Let's assign the user and group we just created to the files we just created
```bash
    chown myusername:mygroup file1.txt
    chown myusername:mygroup file2.cpp
    chown myusername:myusername file3.cs
```

## Sudo

    There is a super user called root, that has permissions to do everythin in the system. There is a group called sudo, and it's member can perform root action by typing sudo before the command
```bash
    sudo su         #we can become root
```
## Resources

```bash
    df -h         #disk partitions
    top           #current cpu usage
    vmstat        #current memory usage
    free          #current memory usage              
```
## Networking
```bash
    ping <ip address or domain name>    #check ip adress availability
    ifconfig                            #current network interface configuration