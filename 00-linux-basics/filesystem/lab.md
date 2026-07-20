# Hands-on Lab

## Objective

Explore the Linux filesystem hierarchy and identify the purpose of the most important system directories.

## Environment

Ubuntu Server running on AWS EC2.

---

## Exercise 1 — Display the current directory

```bash
pwd
```

Observation:

Verified the current working directory before navigating through the system.

---

## Exercise 2 — Explore the root directory

```bash
cd /
ls
```

Observation:

Listed the main directories that make up the Linux filesystem.

---

## Exercise 3 — Explore configuration files

```bash
cd /etc
ls
```

Observation:

Observed configuration files for networking, SSH, users, services and many installed applications.

---

## Exercise 4 — Explore system logs

```bash
cd /var/log
ls
```

Observation:

Identified where Linux stores system log files used for troubleshooting.

---

## Exercise 5 — Explore user directories

```bash
cd /home
ls
```

Observation:

Verified that each regular user has a personal directory.

---

## Exercise 6 — Explore mounted filesystems

```bash
cd /mnt
ls
```

Observation:

Verified that mounted storage devices can appear under this directory.
