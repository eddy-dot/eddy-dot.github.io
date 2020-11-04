---
weight: 1
title: "Basic Docker Compose Commands"
date: 2020-01-12T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Eddy Valverde"
authorLink: "https://dits.technology"
description: "This article shows the basic commands for Linux server administration."
resources:
- name: "featured-image"
  src: "featured-image.jpg"

tags: ["Database", "Postgres"]
categories: ["Tutorial"]

lightgallery: true
---

```bash
docker-compose up -d
```

>Run the services in the docker-compose file in the current directory. The -d is to avoid logs inthe current terminal

```bash
docker-compose down --volumes
```

>Stop services in the services in the docker-compose file in the current directory. The option --volumes is to remove volumes associated to this docker-compose.yml