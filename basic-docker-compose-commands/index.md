# Basic Docker Compose Commands


```bash
docker-compose up -d
```

>Run the services in the docker-compose file in the current directory. The -d is to avoid logs inthe current terminal

```bash
docker-compose down --volumes
```

>Stop services in the services in the docker-compose file in the current directory. The option --volumes is to remove volumes associated to this docker-compose.yml
