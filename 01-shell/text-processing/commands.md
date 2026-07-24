# Commands Reference

## Search

```bash
grep
```

Searches for text patterns inside files or command output.

---

## Display File Content

```bash
head
tail
less
cat
```

Displays all or part of a text file.

---

## Counting

```bash
wc
```

Counts lines, words and characters.

---

## Sorting

```bash
sort
uniq
```

Organizes text and removes duplicate lines.

---

## File Inspection

```bash
file
strings
```

Identifies unknown files and extracts readable text from binary files.

---

## Useful Examples

```bash
grep "root" /etc/passwd

grep -i linux README.md

head README.md

tail README.md

wc -l README.md

sort users.txt | uniq

file secret.txt

strings binaryfile

history | grep git
```
