# Docker Commands

Quick reference for the Docker commands used during the fundamentals labs.

## Images

List local images:

```bash
docker images
```

Pull an image:

```bash
docker pull <image>
```

Run a container from an image:

```bash
docker run <image>
```

---

## Containers

List running containers:

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

Start a stopped container:

```bash
docker start <container>
```

Stop a running container:

```bash
docker stop <container>
```

Remove a container:

```bash
docker rm <container>
```

---

## Interactive Containers

Run a container interactively:

```bash
docker run -it ubuntu:24.04 bash
```

The flags mean:

```text
-i → Keep STDIN open
-t → Allocate a pseudo-terminal
```

---

## Detached Containers

Run a container in the background:

```bash
docker run -d <image>
```

Example:

```bash
docker run -d --name mi-nginx nginx
```

---

## Execute Commands in a Running Container

Open Bash inside a running container:

```bash
docker exec -it <container> bash
```

Run a single command:

```bash
docker exec <container> ps aux
```

---

## Attach to a Container

Attach to the container's main process:

```bash
docker attach <container>
```

### `exec` vs `attach`

```text
docker attach
    ↓
Connects to the main process

docker exec
    ↓
Starts a new process
```

---

## Logs

View container logs:

```bash
docker logs <container>
```

Follow logs in real time:

```bash
docker logs -f <container>
```

---

## Port Publishing

Publish a container port on the host:

```bash
docker run -p <host-port>:<container-port> <image>
```

Example:

```bash
docker run -d --name mi-nginx -p 8080:80 nginx
```

This means:

```text
Host port 8080
       ↓
Container port 80
```

The service can then be accessed through:

```text
http://localhost:8080
```

---

## Inspect Containers

Inspect detailed container configuration:

```bash
docker inspect <container>
```

This can provide information about:

* Network configuration.
* Mounts.
* Environment variables.
* Container configuration.
* IP addresses.

---

## Container Networking

Enter a Linux container:

```bash
docker exec -it <container> bash
```

Then inspect network interfaces:

```bash
ip a
```

---

## Container Processes

Inside a Linux container:

```bash
ps aux
```

or:

```bash
ps -ef
```

---

## Useful Nginx Example

Create an Nginx container:

```bash
docker run -d --name mi-nginx -p 8080:80 nginx
```

Check its status:

```bash
docker ps
```

View logs:

```bash
docker logs mi-nginx
```

Open:

```text
http://localhost:8080
```

Stop the container:

```bash
docker stop mi-nginx
```

Remove it:

```bash
docker rm mi-nginx
```

---

## Quick Reference

| Command          | Purpose                              |
| ---------------- | ------------------------------------ |
| `docker images`  | List local images                    |
| `docker pull`    | Download an image                    |
| `docker run`     | Create and start a container         |
| `docker ps`      | List running containers              |
| `docker ps -a`   | List all containers                  |
| `docker start`   | Start a stopped container            |
| `docker stop`    | Stop a running container             |
| `docker rm`      | Remove a container                   |
| `docker exec`    | Run a process inside a container     |
| `docker attach`  | Attach to the main container process |
| `docker logs`    | View container logs                  |
| `docker inspect` | Inspect container configuration      |
| `docker images`  | List local images                    |

---

## Common Workflow

A basic Docker workflow:

```text
1. Find or pull an image
        ↓
2. Create and run a container
        ↓
3. Inspect the container
        ↓
4. Interact with the container
        ↓
5. Check logs
        ↓
6. Stop or remove the container
```
