---
weight: 1
title: "Postgres Tutorial"
date: 2020-07-11T21:57:40+08:00
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

# Basic Postgres Commands

## 1. Login in postgres (Linux)

```bash
sudo su - postgres
psql
```

## 2. Create database, and give access to a new user

```sql
CREATE DATABASE mydb;
CREATE USER myuser WITH ENCRYPTED PASSWORD 'mypass';
GRANT ALL PRIVILEGES ON DATABASE mydb TO myuser;
```

## 3. Create Table

```sql
\c mydb as myuser

CREATE TABLE accounts (
    user_id serial PRIMARY KEY,
    username VARCHAR ( 50 ) UNIQUE NOT NULL,
    password VARCHAR ( 50 ) NOT NULL,
    email VARCHAR ( 255 ) UNIQUE NOT NULL,
    created_on TIMESTAMP NOT NULL,
        last_login TIMESTAMP 
);

CREATE TABLE mytable (user_id INT PRIMARY KEY);

```

## 4. Remove all data from a table    

```sql
TRUNCATE FROM mytable;
```

## 5. Remove a line from a table

```sql
DELETE FROM mytable WHERE user_id = 1;
```

## 6. Difference between TRUNCATE and DELETE

>TRUNCATE is and efficient way to remove all data from a table(Uses less server’s resources), while DELETE delete data one by one.


## List available databases

```sql
\l
```

## List Tablespaces

```sql
\db
```

## Quit postgres

```sql
\q
```

## Switch connection to a new database

```sql
\c 
```

## List available tables

```sql
\dt
```

## List available schema

```sql
\dn
```

## List available functions

```sql
\df
```

## List available views

```sql
\dv
```

## List users and roles

```sql
\du
```

## Display command history

```sql
\s
```

## Execute psql commands from a file

```sql
\i filename
```

## get help psql commands

```sql
\?
```

