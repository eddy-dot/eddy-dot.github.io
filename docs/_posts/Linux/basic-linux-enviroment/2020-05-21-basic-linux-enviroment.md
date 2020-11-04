---
weight: 1
title: "Setting up a basic Linux enviroment"
date: 2020-05-21T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Eddy Valverde"
authorLink: "https://dits.technology"
description: "This article shows the a basic settup of a Linux Enviroment."
resources:
- name: "featured-image"
  src: "featured-image.jpg"

tags: ["Linux", "Git", "Docker", "Ubuntu", "Visual Code"]
categories: ["Tutorial"]

lightgallery: true
---

This article shows the a basic settup of a Linux Enviroment.

<!--more-->
## 1. Install Ubuntu
Follow [this](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview) instructions
## 2. Install Visual Code
### a. Download the .deb installer from [here](https://code.visualstudio.com/)
### b. Install the .deb file    

```bash
sudo dpkg -i ~/Downloads/code_XXXXXXXX.deb
```
## 3. Install git

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install git
```

## 2. Install Docker
### a. Install docker engine, follow the instructions [here](https://docs.docker.com/engine/install)
### b. Install docker-compose, follow the instructions [here](https://docs.docker.com/compose/install/)

## 3. Install Postgres

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
```

