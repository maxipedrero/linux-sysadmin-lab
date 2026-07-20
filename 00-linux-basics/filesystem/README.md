# Linux Filesystem

## Overview

The Linux filesystem follows a standardized directory structure where every directory has a specific purpose. Understanding this hierarchy is essential for system administration because configuration files, logs, applications, user data, and devices are all organized under a predictable layout.

This module documents the filesystem concepts I learned through Linux practice, AWS EC2 labs, OverTheWire Bandit challenges, and personal virtual machines.

## Learning Objectives

After completing this module I was able to:

* Navigate the Linux filesystem efficiently.
* Understand the purpose of the main system directories.
* Locate configuration files and log files.
* Distinguish between user data and system data.
* Understand where applications, services, and devices are represented.
* Use common filesystem navigation commands.
* Recognize the Linux Filesystem Hierarchy Standard (FHS).

## Important Directories

### /

The root directory is the top of the Linux filesystem. Every file and directory exists somewhere below it.

### /home

Contains personal directories for regular users.

### /root

Home directory of the root user.

### /etc

Stores system-wide configuration files.

Examples:

* SSH configuration
* Nginx configuration
* Apache configuration
* Network configuration

### /var

Contains data that changes while the system is running.

Examples include:

* System logs
* Cache
* Spool files

### /tmp

Temporary files used by applications.

### /usr

Contains most user applications and shared resources.

### /bin

Essential user commands required during system startup and recovery.

### /sbin

System administration commands, generally intended for privileged users.

### /dev

Represents hardware devices as files.

### /proc

Virtual filesystem containing information about running processes and the Linux kernel.

### /mnt

Common location used to temporarily mount filesystems and storage devices.

## Why It Matters

Understanding the filesystem hierarchy helps administrators:

* Locate configuration files quickly.
* Troubleshoot Linux systems.
* Configure services.
* Read logs.
* Manage storage devices.
* Work efficiently from the command line.

## Related Topics

* Navigation
* File Permissions
* Users and Groups
* SSH
* System Services
* Monitoring

## Learning Sources

* OverTheWire Bandit
* Linux Upskill Challenge
* AWS EC2 Ubuntu Server
* Personal Linux virtual machines
* Official Linux documentation