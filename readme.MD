# 📦 **Docker Overview**

## 🐳 What is Docker?

- **Virtualization software** that simplifies development and deployment.
- Packages applications with all necessary **dependencies, configurations, system tools,** and **runtime** into a **container** (a standardized unit for software).
- **Portable artifact**: easily shared and distributed.

---

## 🛠️ Development Process

### 🔄 Before Containers

- Each developer needed to **manually install and configure** all services on their local machine.
- Sharing projects required teammates to **install all dependencies** manually.
- Managing multiple services was cumbersome.

### 🏗️ With Containers

- Docker provides an **isolated environment** with all required services inside.
- Start services with a **single command** that works on any OS.
- Simplifies running **different versions** of the same app without conflicts.

---

## 🚀 Deployment Process

### ❌ Without Containers

- Developers had to provide **detailed setup instructions** for each service to the deployment team.

### ✔️ With Containers

- Developers create a **Dockerfile** with all dependencies.
- Deployment teams simply run this file to deploy the application.

---

## 🆚 Docker vs Virtual Machines

### ⚙️ Understanding OS Layers

1. **Application Layer** (User interaction)
2. **Kernel Layer** (Middleman between user and hardware)
3. **Hardware**

### 🔍 Key Differences

| **Feature**       | **Docker**             | **Virtual Machines**   |
| ----------------- | ---------------------- | ---------------------- |
| **Image Size**    | Couple of **MB**       | Couple of **GB**       |
| **Startup Time**  | **Seconds**            | **Minutes**            |
| **Compatibility** | **Linux distros** only | **All OS**             |
| **Kernel**        | Uses **host's kernel** | Has its **own kernel** |

### 🤔 Why Docker Needs Linux

- Docker uses the **Linux kernel**. To run it on Windows, a **Linux kernel** is required.

---

## 🖥️ Docker Desktop

- Enables Docker on **any OS** using a **hypervisor layer** and a lightweight Linux distro.

---

## 🏗️ Docker Components

### 🖼️ Docker Images

- An **executable application artifact**.
- Contains **source code, dependencies,** and **OS layer**.
- Supports **environment variables, directories,** and **files**.

### 📦 Docker Containers

- **Running instances** of Docker images.
- Can run **multiple containers** from a single image.

### 🗂️ Docker Registries

- **Storage and distribution system** for Docker images.
- Popular registry: **Docker Hub** (hosts official images for Redis, MongoDB, etc.).

### 🏷️ Image Versioning

- Each version has its own image, available on **Docker Hub**.

---

## 🌐 Accessing Docker Containers

### 🔒 Isolated Network

- Containers run in an **isolated network** by default.

### 🔗 Port Binding

- Makes services available to the **outside world** by exposing container ports to the host.
- Only **one service** can run per port.

```bash
docker run -d -p {exposedPort}:{containerPort} {name}:{tag}
```

**_docker run_** creates a new container everytime. It doesn't re-use previous container. If you have run 'docker run' multiple time then you would have multiple container on your computer

### 🗂️ Docker Registry vs Repository

| **Term**              | **Description**                                                                   |
| --------------------- | --------------------------------------------------------------------------------- |
| **Docker Registry**   | A service providing **storage** and a collection of **repositories**.             |
| **Docker Repository** | A collection of **related images** with the same name but different **versions**. |

---

### 🏗️ Structure of Docker file

- Dockerfiles start from a parent image or 'base image'
- It's a docker image that your image is based on. You choose the base image, depending on which tools you need to have available. For example a JS project needs Node.

#### Commands:

```bash
    FROM
```

- Dockerfiles must begin with a FROM instruction
- Build this image from the specified image

```bash
    RUN
```

- will execute any command in a shell inside the container environment

```bash
    COPY
```

- copies files or directories from <src> and adds them to the filesystem of the container at the path <dest>. Basically takes all your file of your application and add them to your container.

```bash
    WORKDIR
```

- sets the working directory for all following commands
- like changing into a directory: 'cd'

```bash
    CMD
```

- the instruction that is to be executed when a docker container starts
- there can only be one 'CMD' instruction in a dockerfile

---

### 🗂️ Docker Layers

- Remember: A docker image consists of layers
- Each instruction in the dockerfile creates one layer
- These layers are stacked and each one is a delta of the changes from the previous layer.

---

### 🛠️ Docker Commands

| **Command**                                                   | **Description**                                                                             |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `docker images`                                               | Lists **all Docker images**.                                                                |
| `docker ps`                                                   | Lists **running containers**.                                                               |
| `docker pull {name}:{tag}`                                    | Pulls an image from Docker Hub. If no **tag** is specified, pulls the **latest** version.   |
| `docker run {name}:{tag}`                                     | Runs a container from the specified **image** and **tag**.                                  |
| `docker run -d {name}:{tag}`                                  | Runs a container in the **background**. Can also use `--detach` instead of `-d`.            |
| `docker logs {containerId}`                                   | Displays **logs** of a container, even if it’s running in the background.                   |
| `docker stop {container}`                                     | Stops one or more **running containers** by ID.                                             |
| `docker run -d -p {exposedPort}:{containerPort} {name}:{tag}` | **Port binding**: Exposes container port to host port. Can use `--publish` instead of `-p`. |
| `docker ps -a`                                                | Lists **all containers** (running or stopped).                                              |
| `docker start {containerId}`                                  | Starts an **existing container** instead of creating a new one.                             |
| `--name`                                                      | Specifies a **custom name** for a container when using `docker run`.                        |
| `docker build -t {name}:{tag} .`                              | **Builds an image** from a Dockerfile with a specified **name** and **tag**.                |
