# Archives

## Overview

Compressed files and archives are commonly used in Linux to reduce storage space, transfer files efficiently and create backups. Linux administrators work with archive formats on a daily basis when installing software, managing backups or inspecting downloaded files.

During my Linux learning journey, I became familiar with archive utilities while solving OverTheWire Bandit challenges, where several levels required identifying unknown file formats, extracting multiple layers of compressed files and understanding the difference between archives and compression.

This module documents the concepts and practical exercises I learned through personal Linux practice, OverTheWire Bandit, AWS EC2 and building this Linux SysAdmin Lab.

## Learning Objectives

After completing this module I was able to:

* Identify compressed files using Linux utilities.
* Understand the difference between archiving and compression.
* Create and extract archive files.
* Work with common Linux compression formats.
* Inspect unknown files before extracting them.
* Handle nested compressed files during troubleshooting.

## Key Concepts

### Archive vs Compression

Although these concepts are often used together, they are different.

An archive combines multiple files into a single file, while compression reduces the size of data.

The `tar` utility creates archives, whereas tools such as `gzip`, `bzip2` and `xz` compress data.

---

### Identifying File Types

Before extracting an unknown file, it is important to determine its format.

The command most commonly used is:

```bash
file
```

This became one of the most useful commands during the OverTheWire Bandit challenges.

---

### Working with Archives

Linux provides several utilities for creating and extracting archives.

The most common commands include:

```bash
tar
gzip
gunzip
zip
unzip
```

---

### Why It Matters

Archive management is a fundamental skill for Linux administrators.

It is frequently required when creating backups, restoring systems, downloading software packages, transferring files and analyzing unknown data.

Understanding archive formats also improves troubleshooting skills when working with unfamiliar files.

## Related Topics

* Filesystem
* Bash
* Text Processing
* Backup Strategies
* Linux Administration

## Learning Sources

* OverTheWire Bandit
* Linux Upskill Challenge
* AWS EC2 Ubuntu Server
* Personal Linux virtual machines
* GNU tar Documentation

## Interview Notes

* What is the difference between an archive and a compressed file?
* What does the `tar` command do?
* Why should you inspect a file before extracting it?
* Which compression formats are commonly used in Linux?
* When would you use `gzip` instead of `zip`?