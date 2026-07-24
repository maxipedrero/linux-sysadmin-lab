# Troubleshooting

## Issue 1 - grep returned no results

### Problem

The expected text was not found.

### Diagnosis

The search was case-sensitive or the text did not exist.

### Solution

Verify the spelling or use case-insensitive searches.

Example:

```bash
grep -i linux README.md
```

---

## Issue 2 - uniq did not remove duplicate lines

### Problem

Duplicate entries remained after using `uniq`.

### Diagnosis

The input was not sorted before running the command.

### Solution

Sort the data first.

Example:

```bash
sort users.txt | uniq
```

---

## Issue 3 - Unknown file contents

### Problem

The file contained unreadable characters.

### Diagnosis

The file was binary or encoded.

### Solution

Inspect it before opening.

Example:

```bash
file data

strings data
```

---

## Issue 4 - Too much output to inspect manually

### Problem

The command produced hundreds of lines.

### Diagnosis

Reading the complete output was inefficient.

### Solution

Filter or limit the output.

Example:

```bash
grep

head

tail
```

---

## Issue 5 - Counted the wrong information

### Problem

The command returned unexpected numbers.

### Diagnosis

The wrong `wc` option was used.

### Solution

Review the available options.

Example:

```bash
wc -l

wc -w

wc -c
```

---

## Issue 6 - Searching the wrong file

### Problem

The command completed successfully but the expected information was missing.

### Diagnosis

The wrong file or directory was inspected.

### Solution

Verify the location before searching.

Example:

```bash
pwd

find .
```

---

## Lessons Learned

* Search before reading entire files.
* Sort data before removing duplicates.
* Identify unknown files before opening them.
* Filter large outputs whenever possible.
* Combine text processing with pipes to simplify administration tasks.