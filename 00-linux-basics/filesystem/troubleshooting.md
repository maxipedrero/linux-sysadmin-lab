# Troubleshooting

## Issue

Could not find a configuration file.

### Diagnosis

I was looking in the wrong directory.

### Solution

Learn the purpose of the main Linux directories and use commands like `find`, `locate` or `which` to locate files.

---

## Issue

Modified the wrong file.

### Diagnosis

I confused configuration directories with user directories.

### Solution

Always verify the current directory using `pwd` before editing files.

---

## Issue

Permission denied while accessing a system directory.

### Diagnosis

Some directories contain files that require administrative privileges.

### Solution

Use `sudo` only when administrative access is required.

---

## Issue

Forgot where mounted storage was located.

### Diagnosis

Mounted filesystems are commonly available under `/mnt`.

### Solution

Check mounted filesystems using `mount`, `findmnt` or inspect `/mnt`.