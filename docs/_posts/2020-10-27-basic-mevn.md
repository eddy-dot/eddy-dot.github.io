---
title: "MEVN app with JWT authentication"
date: 2020-05-15T21:57:40+08:00
categories:
  - Blog
  - Video
tags:
  - MongoDB
  - Node.js
  - Javascript
---

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/TEdbwVhHE54/0.jpg)](https://www.youtube.com/watch?v=TEdbwVhHE54)

<br/>

[SOURCE CODE](https://github.com/eddy-dot/mevn-jwt)

App was started with [mevn-cli](https://mevn.madlabs.xyz/) </br>
JWT was implemented with [this post!](https://www.freecodecamp.org/news/securing-node-js-restful-apis-with-json-web-tokens-9f811a92bb52/) </br>
Front end was implemented with [this post!](https://www.digitalocean.com/community/tutorials/handling-authentication-in-vue-using-vuex)

# How to deploy the app
-   It is necessary to have install Docker Desktop in your computer
-   If want to get started using docker check  [this video](https://youtu.be/K8bkz3PfvlM)
1.   Download or clone this repo on your computer, if you don't know how to use git you can start by with [this video](https://youtu.be/c4SXBSBHlGY)
2.   run the following command in this project folder (Powershell)

```bash
docker-compose up -d
```

3.  to stop the app run the following command in this project folder(Powershell) "omit the -v if you want to persist data"

```bash
docker-compose down -v
```