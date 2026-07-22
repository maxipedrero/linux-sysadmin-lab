# Hands-on Lab

## Objective

Practice Linux pipes and redirections through scenarios inspired by OverTheWire Bandit, personal Linux practice, and everyday system administration tasks.

**Environment**

* Ubuntu Server (AWS EC2)
* Ubuntu Virtual Machine
* OverTheWire Bandit

---

## Scenario 1 - Creating configuration files from the terminal

### Objective

Create configuration files without opening a text editor.

### Commands Used

```bash
cat > .gitignore <<EOF
# macOS
.DS_Store

# VS Code
.vscode/

# Python
__pycache__/
*.pyc
EOF
```

### Observation

Learned how output redirection can generate configuration files directly from the command line.

---

## Scenario 2 - Redirecting command output to a file

### Objective

Save command output for later inspection.

### Commands Used

```bash
ls -la > files.txt

cat files.txt
```

### Observation

Practiced redirecting standard output into a file and verifying the generated content.

---

## Scenario 3 - Appending information to an existing file

### Objective

Add new information without replacing existing content.

### Commands Used

```bash
echo "Linux SysAdmin Lab" > notes.txt

echo "Learning Pipes and Redirections" >> notes.txt

cat notes.txt
```

### Observation

Understood the difference between overwriting (`>`) and appending (`>>`) output.

---

## Scenario 4 - Connecting commands with pipes

### Objective

Process command output without creating temporary files.

### Commands Used

```bash
history | tail

ls -la | less
```

### Observation

Learned how pipes connect commands, allowing the output of one command to become the input of another.

---

## Scenario 5 - Filtering command output

### Objective

Locate relevant information within large outputs.

### Commands Used

```bash
history | grep git

find . -name "*.md" | sort
```

### Observation

Practiced combining multiple commands to filter and organize information efficiently.

---

## Scenario 6 - Counting search results

### Objective

Count the number of matching files.

### Commands Used

```bash
find . -name "*.md" | wc -l
```

### Observation

Learned how command pipelines simplify repetitive administrative tasks.

---

## Skills Practiced

* Output redirection
* Appending data
* Command pipelines
* Searching for information
* Filtering command output
* Saving command results
* Working efficiently from the command line