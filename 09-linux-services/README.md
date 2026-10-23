# 09 - Linux Services & systemd

## Overview

This module focuses on Linux service management using systemd, the system and service manager used by many modern Linux distributions, including Ubuntu.

The goal is to understand how services are started, stopped, monitored, configured, and troubleshot in a Linux environment.

This module follows a hands-on approach, combining theoretical concepts with practical exercises and controlled troubleshooting scenarios.

## Objectives

By completing this module, I aim to:

- Understand the role of systemd in Linux system administration.
- Inspect and manage services using `systemctl`.
- Understand service unit files and their main directives.
- Configure a service to start automatically at boot.
- Inspect service logs using `journalctl`.
- Diagnose common service startup failures.
- Document troubleshooting procedures and root causes.

## Topics Covered

- Introduction to systemd
- Service states and lifecycle
- Service management with `systemctl`
- Unit files and service configuration
- Service dependencies and startup behavior
- Logging and diagnostics with `journalctl`
- Troubleshooting failed services
- Practical administration scenarios

## Lab Environment

- **Operating System:** Ubuntu Linux
- **Service Manager:** systemd
- **Tools:** Bash, systemctl, journalctl
- **Permissions:** A user with `sudo` privileges

Commands and configurations will be tested in a controlled lab environment before being documented as verified.

## Repository Structure

```text
09-linux-services/
├── README.md
├── lab.md
├── troubleshooting.md
└── examples/
    └── hello-lab.service
```

## Learning Approach

Each exercise will include:

1. Objective and expected outcome
2. Concepts and commands
3. Practical implementation
4. Verification steps
5. Troubleshooting and lessons learned

## Status

In progress.

## Key Takeaway

Reliable service management is a core Linux system administration skill. Understanding how to inspect services, interpret logs, and identify root causes helps build the foundation for managing production systems and cloud infrastructure.
