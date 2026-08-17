# Docker Fundamentals Lab

## Objective

Practice the basic Docker workflow:

```text
Image → Container → Process → Network → Application
```

The exercises below document the practical work performed while learning Docker fundamentals.

---

## 1. Verify Docker Installation

Run:

```bash
docker run hello-world
```

This verifies that Docker can download an image, create a container, run it, and display the container output.

Inspect available images:

```bash
docker images
```

---

## 2. Inspect Containers

List running containers:

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

The second command also shows containers that have already exited.

This demonstrates the difference between:

* Running containers.
* Stopped containers.

---

## 3. Run an Ubuntu Container

Create an interactive Ubuntu container:

```bash
docker run -it ubuntu:24.04 bash
```

Inside the container:

```bash
cat /etc/os-release
```

This verifies the Ubuntu environment running inside the container.

Create a directory:

```bash
mkdir /root/masi
```

This demonstrates that the container has its own writable filesystem.

---

## 4. Inspect Container Processes

Inside the container:

```bash
ps aux
```

or:

```bash
ps -ef
```

Observe the processes running inside the container.

This helps demonstrate process isolation between the container and the host.

---

## 5. Inspect Container Networking

Inside the Ubuntu container:

```bash
ip a
```

If `ip` is not available, install the required package:

```bash
apt update
apt install iproute2
```

The command displays the network interfaces available inside the container.

---

## 6. Inspect the Kernel

Inside the container:

```bash
uname -a
```

Observe the reported kernel information.

This demonstrates an important difference between containers and virtual machines: the container does not run an independent guest kernel.

---

## 7. Start and Attach to a Stopped Container

After stopping/exiting the container, list it:

```bash
docker ps -a
```

Start it again:

```bash
docker start <container>
```

Attach to its main process:

```bash
docker attach <container>
```

This demonstrates that a stopped container can be started again without creating a new container.

---

## 8. Execute a Command Inside a Running Container

Create a background container:

```bash
docker run -d --name test-container ubuntu:24.04 sleep 3600
```

Execute Bash inside it:

```bash
docker exec -it test-container bash
```

The important difference is that `docker exec` starts a new process inside an already running container.

---

## 9. Run Nginx

Create an Nginx container:

```bash
docker run -d --name mi-nginx -p 8080:80 nginx
```

Verify that it is running:

```bash
docker ps
```

The port mapping should show:

```text
8080 → 80
```

---

## 10. Access Nginx

Open the following address in a browser:

```text
http://localhost:8080
```

The default Nginx welcome page should be displayed.

The request flow is:

```text
Browser
   ↓
localhost:8080
   ↓
Docker host
   ↓
Container port 80
   ↓
Nginx
```

---

## 11. Inspect Nginx Logs

Run:

```bash
docker logs mi-nginx
```

Access the Nginx page again from the browser.

Run the command again and observe the HTTP request in the logs.

This demonstrates how containerized applications can expose useful operational information through container logs.

12. Understand Container Lifecycle

Practice the main container lifecycle commands:

docker ps
docker ps -a

docker stop <container>
docker start <container>

docker restart <container>

docker rm <container>

The lifecycle can be represented as:

Image
  ↓
docker run
  ↓
Created
  ↓
Running
  ↓
Stopped
  ↓
Removed

A stopped container can be started again, while removing it deletes the container itself.

13. Docker Compose

Docker Compose allows multiple services and their configuration to be defined in a YAML file.

A typical Compose project contains:

project/
├── compose.yml
└── ...

Example:

services:
  web:
    image: nginx
    ports:
      - "8080:80"

Start the services in the background:

docker compose up -d

The -d option runs the containers in detached mode, returning control of the terminal to the user.

Check running containers:

docker compose ps

View logs:

docker compose logs

Stop the services:

docker compose down
14. Understanding Compose Configuration

One of the main advantages of Compose is that the infrastructure configuration is stored in a file.

Instead of manually running:

docker run ...

multiple times, services, ports, networks, volumes and other configuration can be described in compose.yml.

The same configuration can then be recreated with:

docker compose up -d

This makes the environment easier to reproduce and maintain.

15. Docker Compose and Local AWS Simulation

Docker Compose also became relevant while exploring Floci, a local AWS simulator.

The idea is to run AWS-compatible services locally inside containers instead of interacting with real AWS resources.

This provides a useful environment for practicing AWS-related workflows while avoiding unnecessary cloud resources during experimentation.

The Compose file defines the services required by the local environment and allows them to be started together.

16. Practical Docker Workflow

The workflow learned throughout this module can be summarized as:

Search / Pull Image
       ↓
Create Container
       ↓
Start Application
       ↓
Publish Ports
       ↓
Inspect Processes
       ↓
Inspect Logs
       ↓
Troubleshoot
       ↓
Manage Lifecycle
       ↓
Define Environment with Compose