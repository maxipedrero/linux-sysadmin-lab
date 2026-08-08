# Docker Fundamentals

## Overview

This module documents my introduction to **Docker** and containerization.

The goal was to understand the fundamental concepts behind containers and learn how to create, manage, inspect, and interact with Docker containers from the command line.

The exercises were performed on macOS using Docker Desktop.

---

## Learning Objectives

* Understand the difference between Docker images and containers.
* Create and run containers.
* Manage stopped and running containers.
* Interact with containers using Bash.
* Execute commands inside running containers.
* Inspect processes and network interfaces inside containers.
* Understand basic container networking.
* Publish container ports to the host.
* Run an Nginx web server inside a container.
* Inspect container logs.
* Understand how containers differ from virtual machines.

---

## Docker Images

A Docker **image** is a read-only template used to create containers.

For example:

```bash
docker run -it ubuntu:24.04 bash
```

uses the `ubuntu:24.04` image to create a new container.

Images can be listed with:

```bash
docker images
```

An image can be used to create multiple independent containers.

---

## Docker Containers

A **container** is a running or stopped instance created from a Docker image.

List running containers:

```bash
docker ps
```

List all containers, including stopped ones:

```bash
docker ps -a
```

A container has its own filesystem, processes, network interfaces, and isolated environment.

However, containers are not complete virtual machines and do not include their own kernel.

---

## Running an Interactive Container

An Ubuntu container can be started with:

```bash
docker run -it ubuntu:24.04 bash
```

The options mean:

* `-i` keeps standard input open.
* `-t` allocates a pseudo-terminal.
* `bash` starts a Bash shell inside the container.

Once inside the container, commands such as:

```bash
cat /etc/os-release
```

can be used to inspect the container's operating system environment.

---

## Managing Containers

Start a stopped container:

```bash
docker start <container>
```

Attach to its main process:

```bash
docker attach <container>
```

Execute a command inside a running container:

```bash
docker exec -it <container> bash
```

These commands serve different purposes.

`docker attach` connects to the container's main process, while `docker exec` starts a new process inside an already running container.

This distinction became particularly important when working with the Nginx container.

---

## Container Processes

Processes running inside a container can be inspected using standard Linux commands:

```bash
ps aux
```

or:

```bash
ps -ef
```

A container has its own process namespace, so the processes visible from inside the container are different from the processes normally visible from the host.

---

## Container Networking

Networking information can be inspected from inside a Linux container.

For example:

```bash
ip a
```

This can show the container's network interfaces and assigned IP addresses.

The container has its own network environment, but it still relies on the host's networking infrastructure to communicate outside the container.

---

## Containers vs Virtual Machines

One of the most important concepts learned in this module is that a container is **not a virtual machine**.

A virtual machine includes:

```text
Application
     ↓
Guest OS
     ↓
Guest Kernel
     ↓
Virtual Hardware
     ↓
Host
```

Containers instead share the underlying kernel provided by the host/container runtime environment:

```text
Application
     ↓
Container
     ↓
Container Runtime
     ↓
Host Kernel
```

This makes containers generally lighter and faster to start than traditional virtual machines.

During the lab, inspecting:

```bash
uname -a
```

from inside the Ubuntu container demonstrated that the container was using the kernel provided by the Docker environment rather than having an independent Ubuntu kernel.

---

## Running Nginx in Docker

A practical exercise was performed by running Nginx inside a container:

```bash
docker run -d --name mi-nginx -p 8080:80 nginx
```

This command:

* Downloads the `nginx` image if it is not available locally.
* Creates a container named `mi-nginx`.
* Runs it in detached mode.
* Publishes port `80` from the container on port `8080` of the host.

The application was then accessible through:

```text
http://localhost:8080
```

This demonstrated the basic relationship between a container port and a host port:

```text
Browser
   ↓
localhost:8080
   ↓
Host
   ↓
Container port 80
   ↓
Nginx
```

---

## Container Logs

Container logs can be viewed with:

```bash
docker logs mi-nginx
```

When accessing Nginx from a browser, the HTTP request appeared in the container logs.

This demonstrated that application-level activity inside a container can be inspected from the Docker host.