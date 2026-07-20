## Issue

Permission denied while reading /etc/shadow

### Diagnosis

The file is only readable by the root user.

### Solution

Use sudo when administrative privileges are required.

---

## Issue

Changes to group membership did not apply immediately.

### Diagnosis

The current login session still uses the previous group list.

### Solution

Log out and log back in, or start a new shell session.