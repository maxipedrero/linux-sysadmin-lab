# Troubleshooting

## Issue 1 - Unable to read a file with spaces in its name

### Problem

The command failed because the filename contained spaces.

### Diagnosis

Bash interpreted each space as a separator between different arguments.

### Solution

Wrap the filename in quotes or escape the spaces.

**Example**

```bash
cat "spaces in this filename"

cat spaces\ in\ this\ filename
```

---

## Issue 2 - Unable to access a file with special characters

### Problem

The shell could not interpret the filename correctly.

### Diagnosis

Some filenames begin with special characters or contain symbols that Bash interprets differently.

### Solution

Reference the file using the correct relative path or escape the special characters.

**Example**

```bash
cat ./-file07
```

---

## Issue 3 - Lost track of the current working directory

### Problem

After navigating through multiple directories it became difficult to determine the current location.

### Diagnosis

The current directory was never verified before continuing.

### Solution

Use `pwd` frequently to confirm the current working directory.

**Example**

```bash
pwd
```

---

## Issue 4 - Could not locate the required file

### Problem

The exact location of a file was unknown.

### Diagnosis

The filesystem had not been explored before attempting to open the file.

### Solution

Inspect the directory structure before assuming the file location.

**Example**

```bash
ls

find . -name "*.txt"
```

---

## Issue 5 - Permission denied while reading a file

### Problem

The current user did not have permission to access the file.

### Diagnosis

The file permissions restricted access to other users.

### Solution

Inspect permissions before attempting administrative actions.

**Example**

```bash
ls -l
```

---

## Issue 6 - Accidentally overwrote a file using output redirection

### Problem

A file was replaced after using the `>` operator.

### Diagnosis

The output redirection operator overwrites the destination file if it already exists.

### Solution

Verify the destination filename before redirecting output. Use `>>` when appending to an existing file.

**Example**

```bash
echo "Linux" > notes.txt

echo "More notes" >> notes.txt
```

---

## Issue 7 - GitHub rejected password authentication

### Problem

`git push` failed even though the correct GitHub password was provided.

### Diagnosis

GitHub no longer supports password authentication over HTTPS.

### Solution

Generate an SSH key pair, add the public key to GitHub and configure the repository to use the SSH remote URL.

---

## Lessons Learned

* Verify the current directory before modifying files.
* Inspect file permissions before assuming access.
* Explore the filesystem before searching for files.
* Understand how Bash interprets filenames.
* Prefer SSH authentication when working with GitHub.
* Review commands carefully before executing them.