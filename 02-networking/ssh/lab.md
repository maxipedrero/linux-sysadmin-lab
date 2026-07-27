# Hands-on Lab

## Objective

Practice SSH authentication, remote connections and key management through real-world scenarios inspired by GitHub authentication and AWS EC2 administration.

**Environment**

* Ubuntu Server (AWS EC2)
* macOS
* GitHub
* Personal Linux virtual machines

---

## Scenario 1 - Generate an SSH key pair

### Objective

Create a secure SSH key pair for authentication.

### Commands Used

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

### Observation

Learned how SSH generates a public and private key pair and why the private key should never be shared.

---

## Scenario 2 - Start the SSH agent

### Objective

Load SSH keys into memory.

### Commands Used

```bash
eval "$(ssh-agent -s)"
```

### Observation

Learned that the SSH agent manages private keys securely during a session.

---

## Scenario 3 - Add the private key

### Objective

Register the private key with the SSH agent.

### Commands Used

```bash
ssh-add ~/.ssh/id_ed25519
```

### Observation

Configured the SSH agent to authenticate automatically without repeatedly entering the key passphrase.

---

## Scenario 4 - Display the public key

### Objective

Copy the public key to GitHub.

### Commands Used

```bash
cat ~/.ssh/id_ed25519.pub
```

### Observation

Learned that only the public key is shared with remote services.

---

## Scenario 5 - Verify GitHub authentication

### Objective

Confirm that GitHub recognizes the SSH key.

### Commands Used

```bash
ssh -T git@github.com
```

### Observation

Successfully authenticated with GitHub using SSH keys instead of passwords.

---

## Scenario 6 - Connect to an AWS EC2 instance

### Objective

Access a remote Linux server.

### Commands Used

```bash
ssh -i my-key.pem ubuntu@<public-ip>
```

### Observation

Practiced remote Linux administration through a secure encrypted connection.

---

## Skills Practiced

* SSH authentication
* Public and private key management
* GitHub SSH configuration
* Remote Linux administration
* AWS EC2 connectivity
* SSH agent usage