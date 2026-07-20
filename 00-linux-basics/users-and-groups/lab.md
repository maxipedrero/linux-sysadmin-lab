# Hands-on Lab

## Objective

Learn how Linux manages users and groups through practical exercises.

## Environment

Ubuntu Server running on AWS EC2.

## Exercise 1 - Identify the current user

Command executed:

whoami

Result:

max

Observation:

This command displays the currently logged-in user.

---

## Exercise 2 - Display user identity

Command executed:

id

Result:

uid=1000(...)
gid=1000(...)

Observation:

This command shows the user's UID, primary group, and supplementary groups.