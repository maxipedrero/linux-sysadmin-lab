# Troubleshooting

## Issue 1 - GitHub rejected username and password

### Problem

Git operations failed when using HTTPS authentication.

### Diagnosis

GitHub no longer supports password authentication for Git operations.

### Solution

Generate an SSH key pair, add the public key to GitHub and update the repository remote to use SSH.

---

## Issue 2 - Permission denied (publickey)

### Problem

SSH authentication failed.

### Diagnosis

The public key had not been added to the remote service or the wrong private key was being used.

### Solution

Verify that the correct public key is installed and that the SSH agent has loaded the corresponding private key.

---

## Issue 3 - The authenticity of host could not be established

### Problem

SSH displayed a warning before connecting.

### Diagnosis

The remote host had never been contacted before.

### Solution

Verify the host fingerprint and accept it only if it is trusted. The fingerprint will then be stored in the `known_hosts` file.

---

## Issue 4 - Successfully authenticated, but GitHub does not provide shell access

### Problem

The following message appeared after running:

```bash
ssh -T git@github.com
```

```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

### Diagnosis

This is the expected behavior.

### Solution

No action is required. The message confirms that SSH authentication is working correctly.

---

## Issue 5 - Repository continued asking for username and password

### Problem

Git still requested HTTPS credentials.

### Diagnosis

The repository remote was still configured to use HTTPS instead of SSH.

### Solution

Verify the remote configuration:

```bash
git remote -v
```

If necessary, update it to the SSH URL.

---

## Lessons Learned

* SSH keys provide secure authentication without passwords.
* Never share the private key.
* Always verify host fingerprints.
* GitHub authentication works through SSH keys rather than account passwords.
* Understanding SSH is essential for Linux system administration.