# Hands-on Lab

## Objective

Practice archive creation, extraction and file inspection through scenarios inspired by OverTheWire Bandit and everyday Linux administration tasks.

**Environment**

* Ubuntu Server (AWS EC2)
* Ubuntu Virtual Machine
* OverTheWire Bandit

---

## Scenario 1 - Identifying an unknown file

### Objective

Determine the type of a file before attempting to open or extract it.

### Commands Used

```bash
file data
```

### Observation

Learned to inspect unknown files before deciding which extraction utility to use. This approach became essential while solving several OverTheWire Bandit levels.

---

## Scenario 2 - Compressing a file with gzip

### Objective

Reduce the size of a file.

### Commands Used

```bash
gzip notes.txt
gunzip notes.txt.gz
```

### Observation

Practiced compressing and restoring files using the most common Linux compression utility.

---

## Scenario 3 - Creating a tar archive

### Objective

Bundle multiple files into a single archive.

### Commands Used

```bash
tar -cf backup.tar project/
```

### Observation

Learned that `tar` creates an archive without compressing it by default.

---

## Scenario 4 - Extracting an archive

### Objective

Restore archived files.

### Commands Used

```bash
tar -xf backup.tar
```

### Observation

Extracted archived content while preserving the original directory structure.

---

## Scenario 5 - Working with compressed archives

### Objective

Create and extract compressed tar archives.

### Commands Used

```bash
tar -czf backup.tar.gz project/

tar -xzf backup.tar.gz
```

### Observation

Understood how `tar` and `gzip` are commonly combined to create compressed backups.

---

## Scenario 6 - Multiple compression layers

### Objective

Inspect and extract nested compressed files.

### Commands Used

```bash
file
gzip
gunzip
bzip2
bunzip2
tar
```

### Observation

Practiced identifying different compression formats before extracting them, inspired by one of the most challenging OverTheWire Bandit exercises.

---

## Skills Practiced

* File inspection
* Archive creation
* Archive extraction
* Compression
* Backup fundamentals
* Troubleshooting unknown files