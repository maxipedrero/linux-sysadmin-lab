# Troubleshooting

This document contains real permission-related issues encountered while learning Linux system administration.

---

## Issue #1 - Script could not be executed

### Problem

While trying to execute a shell script, Linux returned:

```text
Permission denied
```

### Diagnosis

Checked the file permissions:

```bash
ls -l script.sh
```

The execute permission (`x`) was missing.

### Solution

Granted execute permission to the script:

```bash
chmod +x script.sh
```

### Lesson Learned

Files created with `touch` are not executable by default. Always verify permissions before assuming a script is broken.

---

## Issue #2 - Understanding the output of `ls -l`

### Problem

At first, the output of:

```bash
ls -l
```

looked confusing.

Example:

```text
-rwxr-x---
```

It was difficult to understand which permissions belonged to the owner, the group and other users.

### Diagnosis

Broke the permission string into sections and learned the meaning of each character.

### Solution

Practiced interpreting permission bits during OverTheWire Bandit exercises until reading them became natural.

### Lesson Learned

Being able to quickly interpret `ls -l` is one of the most useful troubleshooting skills in Linux.

---

## Issue #3 - Forgetting to verify permissions first

### Problem

While troubleshooting Linux, it was easy to assume a command or application was failing for another reason.

### Diagnosis

Instead of checking permissions first, time was spent investigating unrelated causes.

### Solution

Adopted a habit of verifying permissions before continuing troubleshooting.

Useful commands:

```bash
ls -l
stat filename
```

### Lesson Learned

Checking file ownership and permissions is often one of the first diagnostic steps in Linux administration.
