# File Permissions

## Overview

Linux controls access to files and directories through a permission system.

Every file has three permission sets:

- Owner
- Group
- Others

Each set defines whether a user can:

- Read (r)
- Write (w)
- Execute (x)

Understanding file permissions is essential for Linux administration because they determine who can access, modify, or execute files.

---

## Viewing Permissions

Display permissions using:

```bash
ls -l
```

Example:

```text
-rwxr-x--- 1 max users 2048 Jul 10 script.sh
```

Breakdown:

```
-rwxr-x---
│ │ │
│ │ └── Others
│ └──── Group
└────── Owner
```

---

## Permission Values

| Value | Permission |
|-------|------------|
| 4 | Read |
| 2 | Write |
| 1 | Execute |

Common examples:

755

644

700

600

---

## Changing Permissions

```bash
chmod 755 script.sh
```

```bash
chmod +x script.sh
```

Recursive:

```bash
chmod -R 755 project/
```

---

## Changing Ownership

```bash
chown user file
```

Change owner and group:

```bash
chown user:developers project/
```

---

## Changing Group

```bash
chgrp developers project/
```

---

## Useful Commands

ls -l

chmod

chown

chgrp

umask

getfacl

setfacl

stat

---

## What I Practiced
Reading Linux permissions
Modifying permissions with chmod
Changing ownership
Understanding numeric permission values
Giving execution permission to Bash scripts
Solving Permission denied errors
Managing permissions while completing OverTheWire Bandit exercises
Applying permissions when working with SSH keys