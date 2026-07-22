# Pipes & Redirections

## Overview

Pipes and redirections are fundamental features of the Linux shell that allow commands to work together efficiently. Instead of treating each command as an isolated tool, they make it possible to combine multiple commands into a single workflow.

Throughout my Linux learning journey, I began using redirections while creating configuration files, documenting labs, and managing project files directly from the terminal. Later, I learned how pipes simplify the process of filtering, sorting, and analyzing command output.

This module documents the concepts and practical examples I learned through personal Linux practice, OverTheWire Bandit, AWS EC2, and building this Linux SysAdmin Lab.

## Learning Objectives

After completing this module I was able to:

* Understand the purpose of pipes and output redirection.
* Redirect command output to files.
* Append information without overwriting existing content.
* Connect multiple commands using pipelines.
* Filter and inspect command output.
* Save command results for later analysis.

## Key Concepts

### Pipes (`|`)

A pipe sends the output of one command directly to another command.

Instead of creating temporary files, pipelines allow multiple commands to work together efficiently.

Example:

```bash
history | tail
```

---

### Output Redirection (`>`)

The `>` operator redirects the standard output of a command into a file.

If the destination file already exists, its contents are replaced.

Example:

```bash
echo "Linux SysAdmin Lab" > notes.txt
```

---

### Append Redirection (`>>`)

The `>>` operator appends output to the end of a file instead of replacing its contents.

Example:

```bash
echo "Second line" >> notes.txt
```

---

### Input Redirection (`<`)

The `<` operator sends the contents of a file as input to a command.

Although it is used less frequently during everyday administration, understanding input redirection is part of mastering the Linux shell.

---

### Standard Error Redirection (`2>`)

Linux separates normal command output from error messages.

Error output can be redirected independently for troubleshooting and scripting purposes.

---

### Why It Matters

Pipes and redirections are used constantly by Linux administrators.

They make it possible to inspect logs, filter information, save command output, automate repetitive tasks and troubleshoot systems more efficiently.

Understanding these concepts is an essential step toward shell scripting and advanced Linux administration.

## Related Topics

* Bash
* Text Processing
* Shell Scripting
* System Administration
* Log Analysis

## Learning Sources

* OverTheWire Bandit
* Linux Upskill Challenge
* AWS EC2 Ubuntu Server
* Personal Linux virtual machines
* Official Bash Documentation

## Interview Notes

* What is the purpose of a pipe in Linux?
* What is the difference between `>` and `>>`?
* What happens if the destination file already exists?
* What is standard output?
* What is standard error?
* Why are pipes considered one of the most powerful features of Unix?