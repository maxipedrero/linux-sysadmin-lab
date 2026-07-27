# Commands Reference

## Key Management

```bash
ssh-keygen
ssh-agent
ssh-add
```

Generate and manage SSH key pairs.

---

## Remote Connections

```bash
ssh
```

Connect to remote Linux systems securely.

---

## Display Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

Display the public key before copying it to GitHub or another server.

---

## SSH Directory

```bash
ls -la ~/.ssh
```

List SSH configuration files and keys.

---

## Repository Configuration

```bash
git remote -v

git remote set-url origin git@github.com:username/repository.git
```

Display or update the Git remote URL.

---

## Connectivity Test

```bash
ssh -T git@github.com
```

Verify SSH authentication with GitHub.

---

## AWS EC2

```bash
ssh -i my-key.pem ubuntu@<public-ip>
```

Connect to an EC2 instance using a private key.

---

## Useful Examples

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"

eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_ed25519

cat ~/.ssh/id_ed25519.pub

ls -la ~/.ssh

git remote -v

ssh -T git@github.com

ssh -i my-key.pem ubuntu@<public-ip>
```