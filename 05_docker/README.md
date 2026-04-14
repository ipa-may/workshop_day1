# Docker Commands

Simple Docker commands you will use often.

## Check Docker

```bash
docker --version
```

Shows the installed Docker version.

## Pull an Image

```bash
docker pull ubuntu:22.04
```

Downloads an image from Docker Hub.

## List Images

```bash
docker images
```

Shows all images stored on your computer.

## Run a Container

```bash
docker run -it ubuntu:22.04
```

Starts a container and opens an interactive terminal.

## Run a Container with a Name

```bash
docker run -it --name my_container ubuntu:22.04
```

Starts a container and gives it a simple name.

## List Running Containers

```bash
docker ps
```

Shows containers that are currently running.

## List All Containers

```bash
docker ps -a
```

Shows running and stopped containers.

## Start a Stopped Container

```bash
docker start my_container
```

Starts an existing stopped container.

## Open a Shell in a Running Container

```bash
docker exec -it my_container bash
```

Opens a terminal inside a running container.

## Stop a Container

```bash
docker stop my_container
```

Stops a running container.

## Remove a Container

```bash
docker rm my_container
```

Deletes a stopped container.

## Remove an Image

```bash
docker rmi ubuntu:22.04
```

Deletes an image from your computer.

## Build an Image from a Dockerfile

```bash
docker build -t my_image .
```

Builds an image from the Dockerfile in the current folder.

## Docker Compose

Docker Compose is used to start and manage multiple containers together with one configuration file, usually called `docker-compose.yml` or `compose.yml`.

### Start Services

```bash
docker compose up
```

Starts all services defined in the compose file.

### Start Services in Background

```bash
docker compose up -d
```

Starts all services in detached mode, so the terminal stays free.

### Stop Services

```bash
docker compose down
```

Stops and removes the containers created by Docker Compose.

### Show Running Services

```bash
docker compose ps
```

Shows the containers started by Docker Compose.

### View Logs

```bash
docker compose logs
```

Shows log output from the services.

### Rebuild and Start

```bash
docker compose up --build
```

Builds images again if needed and then starts the services.

