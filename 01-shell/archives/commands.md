# Commands Reference

## File Inspection

```bash
file
```

Identifies the format of an unknown file.

---

## Archive Management

```bash
tar
```

Creates and extracts archive files.

---

## Compression

```bash
gzip
gunzip

bzip2
bunzip2

xz
unxz
```

Compresses and decompresses files using different algorithms.

---

## ZIP Archives

```bash
zip
unzip
```

Creates and extracts ZIP archives.

---

## Useful Examples

```bash
file data

tar -cf backup.tar project/

tar -xf backup.tar

tar -czf backup.tar.gz project/

tar -xzf backup.tar.gz

gzip notes.txt

gunzip notes.txt.gz
```