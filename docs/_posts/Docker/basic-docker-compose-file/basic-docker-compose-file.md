---
weight: 1
title: "Basic Docker Compose File"
date: 2020-02-13T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Eddy Valverde"
authorLink: "https://dits.technology"
description: "This article shows the basic commands for Linux server administration."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Database", "Postgres"]
categories: ["Tutorial"]

lightgallery: true
---

<!--more-->
```docker
version: '2.2'                  #version of docker-compose 2.2

volumes:                        #In this section volumes are specified
  wordpress:
  db:
networks:                       #In this section networks are specified
  backend:    
  proxy:    

services:                       #Specifies the containers that are going to e used

  wordpress:
    image: wordpress            #Indicates the image that is going to be used
    restart: always
    ports:                      #ports open in the image are going to be mapped in the computer
      - 8080:80                 # "pc's ip":"container's ip"
    environment:                #continer's enviroment variables are specified here
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: exampleuser
      WORDPRESS_DB_PASSWORD: examplepass
      WORDPRESS_DB_NAME: exampledb
    volumes:                    #containers data is mapped outside the container, using volumes, in order
      - wordpress:/var/www/html
    mem_reservation: 512M       #indicates the memory reservation in MegaBytes of the container
    mem_limit: 1024M            #indicates the memory limit in MegaBytes of the container
    cpus: 0.3                   #indicates the cpu allocation of the continer
    networks:                   #Indicates what networks already declared in lne 6
        - backend
        - proxy

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_DATABASE: exampledb
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
      MYSQL_RANDOM_ROOT_PASSWORD: '1'
    volumes:
      - db:/var/lib/mysql
    mem_reservation: 512M
    mem_limit: 1024M
    cpus: 0.3
    networks:
        - backend        
```
