# Hands-on Lab

## Objective

Practice text processing commands through scenarios inspired by OverTheWire Bandit and everyday Linux administration tasks.

**Environment**

* Ubuntu Server (AWS EC2)
* Ubuntu Virtual Machine
* OverTheWire Bandit

---

## Scenario 1 - Searching for text inside files

### Objective

Locate specific information without reading the entire file.

### Commands Used

```bash
grep "password" README.md
```

### Observation

Learned how to search efficiently inside text files instead of inspecting them manually.

---

## Scenario 2 - Viewing only the beginning or end of a file

### Objective

Inspect large files more efficiently.

### Commands Used

```bash
head README.md

tail README.md
```

### Observation

Practiced viewing only the most relevant sections of large files.

---

## Scenario 3 - Counting information

### Objective

Determine the size of a file without reading it completely.

### Commands Used

```bash
wc README.md

wc -l README.md
```

### Observation

Learned how to count lines, words and characters quickly.

---

## Scenario 4 - Sorting and removing duplicates

### Objective

Organize text data before processing it.

### Commands Used

```bash
sort users.txt

sort users.txt | uniq
```

### Observation

Understood why sorting data before removing duplicates produces better results.

---

## Scenario 5 - Identifying unknown files

### Objective

Determine the type of a file before opening it.

### Commands Used

```bash
file data

strings data
```

### Observation

Practiced inspecting unknown files, a technique frequently required during OverTheWire Bandit challenges.

---

## Scenario 6 - Combining text processing with pipes

### Objective

Filter useful information from command output.

### Commands Used

```bash
history | grep git

find . -name "*.md" | wc -l
```

### Observation

Learned how combining multiple commands simplifies administrative tasks.

---

## Skills Practiced

* Searching text
* Inspecting files
* Counting information
* Sorting output
* Removing duplicates
* Identifying file types
* Combining commands with pipes