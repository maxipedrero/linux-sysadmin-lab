# SSH

## Overview

Secure Shell (SSH) is one of the most important tools for Linux system administrators. It provides a secure way to access remote machines, transfer files and authenticate users over an encrypted connection.

Throughout my Linux learning journey, SSH became an essential tool while working with AWS EC2 instances, authenticating with GitHub using SSH keys and managing remote Linux servers from the terminal.

This module documents the concepts, commands and practical exercises I learned through personal Linux practice, OverTheWire Bandit, AWS EC2 and building this Linux SysAdmin Lab.

## Learning Objectives

After completing this module I was able to:

* Understand the purpose of SSH.
* Connect securely to remote Linux servers.
* Generate SSH key pairs.
* Understand the difference between public and private keys.
* Configure GitHub authentication using SSH.
* Understand the purpose of the `~/.ssh` directory.
* Verify SSH connectivity.
* Troubleshoot common SSH authentication issues.

## Key Concepts

### What is SSH?

SSH (Secure Shell) is a secure protocol used to remotely access Linux systems through an encrypted connection.

Unlike older protocols such as Telnet, SSH encrypts all communication between the client and the server.

---

### SSH Authentication

SSH supports different authentication methods.

The two most common are:

* Password authentication
* Public key authentication

For most Linux administration tasks, public key authentication is the preferred and more secure option.

---

### Public and Private Keys

An SSH key pair consists of:

**Private Key**

Stored locally and never shared.

Example:

```text
~/.ssh/id_ed25519
```

**Public Key**

Can be shared safely with remote systems.

Example:

```text
~/.ssh/id_ed25519.pub
```

The public key is installed on the remote server (or GitHub), while the private key remains only on the local machine.

---

### The ~/.ssh Directory

The `.ssh` directory stores SSH configuration files and keys.

Common files include:

```text
id_ed25519
id_ed25519.pub
known_hosts
config
authorized_keys
```

Each file has a specific purpose in SSH authentication and host verification.

---

### Host Verification

The first time an SSH connection is established, the client verifies the identity of the remote host.

If the host is trusted, its fingerprint is stored in:

```text
~/.ssh/known_hosts
```

This helps prevent man-in-the-middle attacks.

---

### SSH and GitHub

GitHub no longer supports password authentication for Git operations.

Instead, SSH keys allow secure authentication without entering a username and password for every push or pull operation.

---

### SSH and AWS EC2

SSH is the standard method for accessing Linux virtual machines running on AWS EC2.

The connection is typically established using a private key:

```bash
ssh -i my-key.pem ubuntu@<public-ip>
```

---

## Why It Matters

SSH is one of the most frequently used tools by Linux administrators.

It enables secure remote administration, cloud management, Git workflows, file transfers and automation.

Understanding SSH is a fundamental requirement for working with Linux servers.

## Related Topics

* TCP/IP
* Git
* AWS EC2
* Linux Security
* Public Key Cryptography

## Learning Sources

* OverTheWire Bandit
* Linux Upskill Challenge
* AWS EC2 Ubuntu Server
* GitHub SSH Authentication
* Personal Linux virtual machines

## Interview Notes

* What is SSH?
* Why is SSH more secure than Telnet?
* What is the difference between a public and a private key?
* What is the purpose of the `known_hosts` file?
* What is stored inside the `.ssh` directory?
* Why does GitHub recommend SSH authentication?
* How do you connect to an EC2 instance using SSH?