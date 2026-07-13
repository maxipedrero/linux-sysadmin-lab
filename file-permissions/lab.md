# Lab - Linux File Permissions

## Objective

Practice inspecting and modifying file permissions using common Linux administration commands.

## Environment

* Operating System: Ubuntu Server
* Shell: Bash

## Tasks Performed

### 1. Created a test directory

```bash
mkdir permissions-lab
cd permissions-lab
```

### 2. Created test files

```bash
touch notes.txt
touch script.sh
```

Checked the default permissions:

```bash
ls -l
```

Observed that newly created files did not have execute permissions.

---

### 3. Granted execute permission to a script

```bash
chmod +x script.sh
```

Verified the result:

```bash
ls -l
```

The execute bit (`x`) was now present.

---

### 4. Changed permissions using numeric notation

```bash
chmod 644 notes.txt
chmod 755 script.sh
```

Compared both permission sets using `ls -l`.

---

### 5. Changed file ownership

```bash
sudo chown myuser:myuser notes.txt
```

Verified ownership:

```bash
ls -l
```

---

## Result

Successfully practiced:

* Reading file permissions
* Modifying permissions with `chmod`
* Understanding numeric permission notation
* Changing file ownership
* Verifying changes using `ls -l`

## Notes

Understanding file permissions is essential before working with services such as SSH, Nginx, Apache or shared directories because incorrect permissions often prevent services from working correctly.