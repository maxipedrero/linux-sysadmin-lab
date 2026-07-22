# Commands Reference

## Pipes

```bash
|
```

Connects the output of one command to the input of another.

---

## Output Redirection

```bash
>
```

Redirects standard output to a file, replacing its contents if it already exists.

---

## Append Redirection

```bash
>>
```

Appends output to the end of a file without overwriting existing content.

---

## Input Redirection

```bash
<
```

Uses the contents of a file as the input for a command.

---

## Standard Error Redirection

```bash
2>
2>>
```

Redirects error messages to a file.

---

## Useful Commands

```bash
tee
grep
sort
wc
head
tail
less
cat
echo
```

---

## Examples

```bash
history | tail

history | grep git

find . -name "*.md" | sort

find . -name "*.md" | wc -l

echo "Linux" > notes.txt

echo "More notes" >> notes.txt

ls -la > files.txt

cat files.txt
```