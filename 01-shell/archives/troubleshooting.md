# Troubleshooting

## Issue 1 - Unable to read a file

### Problem

The file displayed unreadable characters.

### Diagnosis

The file was compressed rather than plain text.

### Solution

Inspect the file using `file` before opening or extracting it.

---

## Issue 2 - Wrong extraction utility

### Problem

The extraction command failed.

### Diagnosis

The archive format was different from the expected one.

### Solution

Determine the file type first, then choose the appropriate extraction utility.

---

## Issue 3 - tar extracted nothing

### Problem

No files appeared after running `tar`.

### Diagnosis

Incorrect extraction options or wrong archive format.

### Solution

Verify the archive type using `file` before extracting it.

---

## Issue 4 - Confusing archives with compressed files

### Problem

Expected `tar` to reduce the file size.

### Diagnosis

`tar` archives files but does not compress them unless compression options are used.

### Solution

Combine `tar` with `gzip` when creating compressed archives.

---

## Issue 5 - Multiple compressed layers

### Problem

The extracted file was still unreadable.

### Diagnosis

The file contained additional compression layers.

### Solution

Repeat the inspection process using `file` after each extraction step until reaching the final content.

---

## Lessons Learned

* Always inspect unknown files before extracting them.
* Understand the difference between archives and compression.
* Use the correct extraction utility for each format.
* Multiple compression layers require repeated inspection.
* Archive management is an essential Linux administration skill.