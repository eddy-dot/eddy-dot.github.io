---
toc: true
title: "Docker Tutorial: Deploying a Blog"
date: 2020-05-15T21:57:40+08:00
categories:
  - Blog
  - Video
tags:
  - DevOps
  - Virtualization
  - Docker
---

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/K8bkz3PfvlM/0.jpg)](https://www.youtube.com/watch?v=K8bkz3PfvlM)

<br/>

[SOURCE CODE](https://github.com/eddy-dot/docker-tutorial)

## What is docker? Why is it important to use it?
Docker provides the ability to package and run an application in a loosely isolated environment called a container. That coil be a windows or linux environment.
Because Docker containers encapsulate everything an application needs to run (and only those things), they allow applications to be shuttled easily between environments. Any host with the Docker runtime installed—be it a developer's laptop or a public cloud instance—can run a Docker container. So the “It works on my machine” days are gone.

## What to install?
Docker desktop
Visual studio code

<br/>
## Basic Docker Cheatsheet:

| Command   			 	        | Description                                  						                  |
|-----------------------------------|-------------------------------------------------------------------------------------|
| docker pull <image>:<tag>     	|Pull an image or a repository from a registry						                  |
| docker run <image>:<tag>      	|Run a command in a new container                     					              |
| docker ps    		 	            |List containers             									                      |
| docker rm <container id>:<tag>    |Remove one or more containers               							              |
| docker images       			    |List images                                   						                  |
| docker image rm <image id>:<tag> 	|Remove one or more images                   							              |
| docker volume ls  			    |List volumes      										                              |
| docker volume rm <volume id>      |Remove one or more volumes    								                          |
| docker network ls    		        | docker network ls                      							                  |
| docker network rm <network id>    |docker network rm   										                          |
| docker stats      			    |Display a live stream of container(s) resource usage statistics   				      |
| docker-compose up      		    | Builds, (re)creates, starts, and attaches to containers for a service.			  |
| docker-compose down      		    | Stops containers and removes containers, networks, volumes, and images created by up|

<br/>



<br/>
## Example with hello-world, explain where it comes from(dockerhub)
If you Know the OOP, so an image is like a class an a container is an object. You can create multiple containers from an image, and you can create an image based on another image.
```bash
docker pull hello-world
```
We pull from dockerhub the image
```bash
docker images
```
We check that we have only one image, lets create a container with that image
```bash
docker run hello-world
```
Now a container ran, and printed the hello world message in the console
```bash
docker ps
```
We can see that a container is running, but we dont need it, we want to remove it
```bash
docker rm <Container id> 
docker ps
```
Now the container is gone

Where did the hello-world image come from?
Go to docker-hub.com, which is a docker registry, go to explore, search hello-world, get inside, go to tags, show latest
Images are downloaded from docker registries(private servers can be set up for hosting private images). Images have version control using tags, when no tag is used the “latest” tag is downloaded by default, but it is no recommended because the “latest” tagegd images are constantly updating so dependency issues might appear. Lets add tagged hello-world 
Image.
```bash
docker pull hello-world:linux
```
Lets run the tagged image
```bash
docker run hello-world:linux
```
Lets remove it
```bash
docker rm <Container id> 
docker ps
```
Now the container is gone

## Make another example with ghost

Now lets create a more complex app <br />
Go to docker-hub.com, go to explore, search ghost, get inside, go to docker compose example <br />
We are now going to use an app called ghost, but it needs a mysql database. As this configuration is a little bit complex its better to write a docker-compose file. <br />
Go to Files, Documents, Repositories, create directory docker-tutorial, open visual studio code here, now go to terminal, add terminal. create directory example1, create a file named docker-compose.yml inside example1 and paste the text you just copied.
```bash
cd example-1
Docker-compose up -d
```
Now go to a web browser and go to http://localhost:8080 <br />
As you can see the is the app running <br />
Lets go back to the docker-compose file <br />
The file starts starts with a version tag, that defines the docker-compose version
Then there is another  tag called services, where the containers are declared, lets say that a service is a container, for now.
Inside each service (ghost:db) there is a tag called image, where the image of the container is defined. <br />
One important tag is ports, maps the container port to localhost port in this order "localhost_port:container_port", the db service doesnt need it because ghost container can listen to it through an internal network that connects the services by default.

```bash
Docker network ls
```
You can see the default network here

Lets add another service to docker-compose
```bash
Docker-compose down
```




## Make another example with ghost+admin
Create a new directory, name it example-2, copy the docker-compose.yml of example 1 into example2, and edit it. Add adminer service to it.
Go to docker-hub.com, go to explore, search adminer, get inside, go to docker compose example and copy adminer service
Update the just copied service and update 8080 for 8081
```bash
Cd ..
Cd example-2
Docker-compose up -d
```
Now go to a web browser and go to http://localhost:8080
As you can see the is the app running
Now go to a web browser and go to http://localhost:8081
Adminer is a tool to administrate the database, lets get in with root credentials
Host: the name of the service
User: root
Password: example

Navigate through databases

What if my app  need a custom db?
```bash
Docker-compose down
```
## Make another example with ghost+admin+ custom database
Create a directory, name it db-init
Inside it create a file named a.sql and add the following
```sql
CREATE DATABASE testdb;
```
Create a b.sql and add the following
```sql
USE testdb;
 
CREATE TABLE authors (id INT, name VARCHAR(20), email VARCHAR(20));
```
Create a b.sql file and add the following
```sql
USE testdb;
 
INSERT INTO authors (id,name,email) VALUES(1,"Vivek","xuz@abc.com");
 
INSERT INTO authors (id,name,email) VALUES(2,"Priya","p@gmail.com");
 
INSERT INTO authors (id,name,email) VALUES(3,"Tom","tom@yahoo.com");
```
Now go to the dockerfile, inside the db service add
```docker-compose
volumes:
     - ./db-init:/docker-entrypoint-initdb.d
```
It will map the the files in db-init inside the container directory  docker-entrypoint-initdb.d, and the db will execute the file in alphabetic number.

Now lets run it again
```bash
Docker-compose up -d
```
Now go to a web browser and go to http://localhost:8081
Go inside the database
Look for testdb
Check data


## Make another example with ghost+adminer+ custom database + networks + volumes + cpu limits
### Persist data
Persist database data: THis is necessary when services restart but the app need to persist the data.

Add a tag before services called volumes, then map a volume called mysqlvolume, then go to volumes section of db service and add -mysqlvolume:/var/lib/mysql

### Complex Networks setting

Separate networks: for security reasons web apps like ghost and adminer should face the internet, so they are connected to the front-end network, but the database should not face the internet, so it should be isolated from internet.

Add a tag before services called networks, and add -backend and frontend.
Then map both networks on adminer and ghost, and backend in db.

### Resource reservation
Now we can also set a limit for resource usage 
```docker-compose
mem_reservation: 718M
   em_limit: 1024M
   cpus: 0.4
```
Mem_reservation is for memory reservation in megabytes
Em_limit limit for memory usage in megabytes
Cpus: cpu usage limit
For ghost:
```docker-compose
     mem_reservation: 521M
     em_limit: 718M
     cpus: 0.4
```
For db
```docker-compose
mem_reservation: 718M
   em_limit: 1024M
   cpus: 0.4
```
For adminer:
```docker-compose
mem_reservation: 128M
   em_limit: 256M
   cpus: 0.1
```

Now lets see it running
```bash
Docker-compose up -d

Docker volume ls
```
We can see the volume we described in the docker-compose file
```bash
Docker network ls
```
We can see the networks we described in the docker-compose file
```bash
Docker status
```
We can see the resources consumed by each container declared in the docker compose file
## How to containerize my app? (Node js app example in VIsual Studio code)

### What to install?
Npm
### Steps

Visual studio code has an awesome feature lets use it

First lets create an app, an api, that says hello world

Then we install docker in visual studio code

Shift + P in Visual studio code,s then create docker file

Build docker

#### How to host it remotely

Go to hub.docker.com, create account, create repository
```bash

docker tag local-image:tagname new-repo:tagname
docker push new-repo:tagname
```
Now lets go to hub.docker.com

We can see that the image has a tag that we just pushed from our computer
Now everyone could docker pull eddydot/testrepo:test and run my app from any computer with internet access.
