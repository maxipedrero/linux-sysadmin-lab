# Users and Groups

## Overview

Linux is a multi-user operating system where every file, process, and service runs under a specific user account. Understanding how users and groups work is fundamental for managing permissions, securing systems, and administering Linux servers.

This module documents the concepts and practical exercises I completed while learning Linux user and group management.

## Learning Objectives

After completing this module I was able to:

* Understand the difference between users and groups.
* Identify the current user and group membership.
* Create and manage users.
* Create and manage groups.
* Add and remove users from groups.
* Understand the purpose of `/etc/passwd`, `/etc/group`, and `/etc/shadow`.
* Switch between users using `su`.
* Execute administrative tasks using `sudo`.
* Understand how users and groups relate to Linux file permissions.

## Key Concepts

### Users

Each person or service running on a Linux system is represented by a user account.

Examples include:

* Regular users
* The root user
* System users created for services

### Groups

Groups simplify permission management by allowing multiple users to share access to files and resources.

A user can belong to one primary group and multiple supplementary groups.

### Important Files

* `/etc/passwd`
* `/etc/group`
* `/etc/shadow`

Each file stores different information related to authentication and account management.

## Why It Matters

Understanding users and groups is essential for:

* Managing file permissions
* Configuring SSH access
* Using sudo safely
* Running system services
* Administering Linux servers

## Related Topics

* File Permissions
* SSH
* Sudo
* Linux Filesystem

## Learning Sources

* OverTheWire Bandit
* Personal Linux virtual machines
* AWS EC2 Ubuntu instances
* Official Linux documentation