# Docker Guide

## Table of Contents
1. [Basic Docker Commands](#basic-docker-commands)
    - [Docker Start](#docker-start)
    - [Docker Pull](#docker-pull)
    - [Docker Run](#docker-run)
    - [Docker Stop](#docker-stop)
    - [Docker Remove](#docker-remove)
2. [Copying a JAR File to an Ubuntu Docker Container](#copying-a-jar-file-to-an-ubuntu-docker-container)
3. [Building Docker Images](#building-docker-images)
4. [Listing Containers](#listing-containers)
5. [Removing Images](#removing-images)
6. [Removing Dangling Volumes](#removing-dangling-volumes)
7. [Using Docker Volumes](#using-docker-volumes)
8. [Executing Commands in Running Containers](#executing-commands-in-running-containers)
9. [Cleaning Up Docker](#cleaning-up-docker)
---

## Basic Docker Commands
### Docker Start
- **Command**: `docker start <container_name_or_id>`
- **Usage**: Start an existing, stopped container.
### Docker Pull
- **Command**: `docker pull <image_name>`
- **Usage**: Download an image from Docker Hub or a Docker registry.
- **Example**: `docker pull ubuntu:latest`
### Docker Run
- **Command**: `docker run [OPTIONS] <image_name>`
- **Usage**: Create and start a new container from an image.
- **Example**: `docker run -it ubuntu:latest`
  - `-it` starts an interactive terminal session.
- **Common Options**:
  - `-d`: Run container in detached mode (in the background).
  - `-p <host_port>:<container_port>`: Map a port from the host to the container.
  - `--name <name>`: Assign a name to the container.
### Docker Stop
- **Command**: `docker stop <container_name_or_id>`
- **Usage**: Stop a running container.
### Docker Remove
- **Command**: `docker rm <container_name_or_id>`
- **Usage**: Remove a stopped container.
- **Note**: You must stop the container before removing it.
---



## Copying a JAR File to an Ubuntu Docker Container
### Method 1: Using Dockerfile
1. Create a `Dockerfile` to copy the JAR file into the container.
2. Example `Dockerfile`:
    ```Dockerfile
    # Use an official OpenJDK runtime as the base image
    FROM openjdk:11-jre-slim

    # Set the working directory
    WORKDIR /app

    # Copy the JAR file into the container
    COPY your-app.jar /app/your-app.jar

    # Run the JAR file
    CMD ["java", "-jar", "/app/your-app.jar"]
    ```
3. Build the Docker image:
    ```bash
    docker build -t my-java-app .
    ```
4. Run the Docker container:
    ```bash
    docker run -d --name java-container my-java-app
    ```
### Method 2: Using `docker cp`
- **Command**: `docker cp <host_file_path> <container_name_or_id>:<container_path>`
- **Usage**: Copy files or directories from the host to the container.
- **Example**:
    ```bash
    docker cp /path/to/your-app.jar java-container:/app/your-app.jar
    ```
- **Note**: You need to have the container running or at least created.

---




## Building Docker Images
- **Command**: `docker build -t <image_name> <path_to_dockerfile>`
- **Usage**: Build a new Docker image from a `Dockerfile`.
- **Example**:
    ```bash
    docker build -t my-custom-image .
    ```


## Listing Containers
- **Command**: `docker ps` or `docker ps -a`
- **Usage**: List all running containers (`docker ps`) or all containers (`docker ps -a`).

## Removing Images
- **Command**: `docker rmi <image_name_or_id>`
- **Usage**: Remove one or more images from the host.

## Removing Dangling Volumes
- **Command**: `docker volume prune`
- **Usage**: Remove all unused volumes to free up space.

## Using Docker Volumes
- **Command**: `docker run -v <host_path>:<container_path> <image_name>`
- **Usage**: Mount a directory from the host into the container.
- **Example**:
    ```bash
    docker run -v /host/data:/container/data ubuntu
    ```

## Executing Commands in Running Containers
- **Command**: `docker exec -it <container_name_or_id> <command>`
- **Usage**: Execute commands inside a running container.
- **Example**:
    ```bash
    docker exec -it java-container /bin/bash
    ```

## Cleaning Up Docker
- **Remove all stopped containers**:
    ```bash
    docker container prune
    ```
- **Remove all unused images**:
    ```bash
    docker image prune
    ```
- **Remove all unused data (images, containers, volumes, etc.)**:
    ```bash
    docker system prune
    ```

