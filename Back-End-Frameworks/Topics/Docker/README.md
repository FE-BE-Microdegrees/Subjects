# Docker: What It Is and What It Is Used For

![Docker](Docker.webp)

Image source: Dall-E by OpenAI

## Introduction

Docker is an open-source platform that allows developers and IT professionals to build, deploy, and manage applications in containers. Containers enable applications and their dependencies to run in an isolated environment, ensuring consistent and predictable behavior across all stages, from development to production.

- [Docker: What It Is and What It Is Used For](#docker-what-it-is-and-what-it-is-used-for)
  - [Introduction](#introduction)
  - [Learning Outcomes](#learning-outcomes)
  - [Key Concepts of Docker](#key-concepts-of-docker)
  - [How Docker Works](#how-docker-works)
    - [Containers vs Virtual Machines](#containers-vs-virtual-machines)
  - [Core Components of Docker](#core-components-of-docker)
    - [Docker Engine](#docker-engine)
    - [Docker Image](#docker-image)
    - [Docker Container](#docker-container)
    - [Docker Compose](#docker-compose)
  - [Docker Desktop](#docker-desktop)
    - [Installing and Setting Up Docker Desktop](#installing-and-setting-up-docker-desktop)
      - [Windows](#windows)
      - [macOS](#macos)
  - [Use Cases and Benefits of Docker](#use-cases-and-benefits-of-docker)
    - [Use Cases](#use-cases)
    - [Benefits](#benefits)
  - [References](#references)
  - [Review Questions or Exercises](#review-questions-or-exercises)

## Learning Outcomes

By the end of this chapter, learners should be able to:

- explain what Docker is and how it works;
- describe the differences between containers and virtual machines;
- name the core components of Docker and their functionality;
- outline the use cases and benefits of Docker;
- install Docker Desktop on their computer.

## Key Concepts of Docker

**Docker:** Docker is a platform that uses containerization technology to package applications and their dependencies into an isolated unit known as a container.

**Container:** A container is a lightweight, isolated environment that includes all the necessary files and dependencies to run an application. Containers share the same operating system kernel, making them more efficient than virtual machines.

**Docker Image:** A Docker image is a file that contains all the components necessary to run an application, including the code, frameworks, dependencies, and system tools. Images are read-only and are used to create containers.

**Docker Container:** A Docker container is a running instance of a Docker image that executes an application in an isolated environment. Containers are lightweight and start quickly.

**Dockerfile:** A Dockerfile is a text file that contains instructions for creating a Docker image. It defines the components and steps required to build the image.

**Docker Hub:** Docker Hub is a cloud-based repository where users can share, pull, and push Docker images.

## How Docker Works

Docker uses container technology that allows applications and their dependencies to be packaged, developed, and run in isolated environments. Containers run directly on the host operating system, sharing the same kernel, making them lighter and more efficient than traditional virtual machines.

### Containers vs Virtual Machines

Containers and virtual machines (VMs) are both isolated environments, but their principles of operation and use cases differ.

- **Containers:**

  - share the host operating system kernel;
  - are smaller and start faster;
  - provide better performance and efficiency;
  - are well-suited for microservices architectures and cloud-based applications.

- **Virtual Machines:**
  - run a full-fledged operating system with its kernel;
  - are larger and generally start slower;
  - provide complete isolation and security;
  - are suitable for running various operating systems on the same hardware.

## Core Components of Docker

### Docker Engine

Docker Engine is the primary component of Docker responsible for creating and running containers. It consists of three parts:

- **Server (Docker Daemon):** A service that manages the lifecycle of containers.
- **REST API:** An interface that allows communication with the Docker Daemon.
- **CLI (Command Line Interface):** A command-line tool that enables users to interact with Docker.

### Docker Image

A Docker image is an immutable template for an application and its dependencies used to create containers. Images are built using a Dockerfile.

Example Dockerfile:

```Dockerfile
# Start from a base image
FROM node:14

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Set the command to run the application
CMD ["node", "app.js"]
```

### Docker Container

A Docker container is a running instance of a Docker image. Containers are lightweight, isolated, and can be easily started, stopped, and removed.

Example of creating and running a container:

```bash
docker build -t my-node-app .
docker run -d -p 3000:3000 my-node-app
```

### Docker Compose

Docker Compose is a tool that allows you to define and manage multi-container applications. It uses a YAML configuration file, `docker-compose.yml`, to specify services, networks, and volumes.

Example of a `docker-compose.yml` file:

```yaml
version: "3"
services:
  web:
    image: my-node-app
    ports:
      - "3000:3000"
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
```

## Docker Desktop

Docker Desktop is a tool that provides an easy and user-friendly way to manage and develop Docker containers on Windows and macOS platforms. Docker Desktop integrates all the necessary tools, including Docker Engine, Docker CLI, Docker Compose, and Kubernetes, allowing developers to quickly start building and managing container-based applications.

For those unfamiliar with or unwilling to use command-line tools, Docker Desktop offers a simple graphical user interface for creating, running, and managing containers visually.

### Installing and Setting Up Docker Desktop

#### Windows

- Download the Docker Desktop installer from [Docker's official website](https://www.docker.com/products/docker-desktop).
- Run the installer and follow the instructions to install Docker Desktop.
- After the installation is complete, launch Docker Desktop and log in with your Docker Hub account (optional).

#### macOS

- Download the Docker Desktop DMG file from [Docker's official website](https://www.docker.com/products/docker-desktop).
- Open the DMG file and drag the Docker Desktop icon to the Applications folder.
- Launch Docker Desktop from the Applications folder and log in with your Docker Hub account (optional).

## Use Cases and Benefits of Docker

### Use Cases

- **Microservices Architecture:** Docker enables isolated and independent deployment of microservices.
- **Cloud-Based Applications:** Containers provide scalability and flexibility for cloud-based applications.
- **Development and Testing:** Docker allows for a consistent development and testing environment, reducing bugs and speeding up development cycles.
- **Modernizing Legacy Systems:** Docker helps containerize legacy systems and migrate them to more modern platforms.

### Benefits

- **Lighter and faster than virtual machines.**
- **Easy to install and manage.**
- **Scalability and portability.**
- **Consistent behavior across different environments.**
- **Strong ecosystem and large community.**

## References

- [Docker Official Documentation](https://docs.docker.com/)
- [Docker for Dummies by Earl Waud](https://www.amazon.com/Docker-Dummies-Earl-Waud/dp/1119564687)
- [Docker Hub](https://hub.docker.com/)
- [Learning Docker by Jeeva S. Chelladhurai](https://www.amazon.com/Learning-Docker-Jeeva-Chelladhurai/dp/1783984869)
- [Docker for Developers by Richard Bullington-McGuire](https://www.amazon.com/Docker-Developers-Richard-Bullington-McGuire/dp/1789617384)

## Review Questions or Exercises

- What is Docker and how does it differ from virtual machines?
- Explain the difference between Docker Image and Docker Container.
- Write a simple Dockerfile that creates an image for a Node.js application.
- What is Docker Compose and how does it help manage multi-container applications?