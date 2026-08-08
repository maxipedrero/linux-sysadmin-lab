# DNS Commands

Quick reference for common DNS troubleshooting and diagnostic commands in Linux.

## Basic Resolution

### `host`

Perform a simple DNS lookup:

```bash
host github.com
```

Useful for quickly checking whether a hostname resolves.

---

### `nslookup`

Query a DNS server:

```bash
nslookup github.com
```

Query a specific DNS server:

```bash
nslookup github.com 1.1.1.1
```

---

### `dig`

Perform a detailed DNS query:

```bash
dig github.com
```

`dig` is particularly useful for troubleshooting because it provides detailed information about the query and response.

---

## Query Specific Record Types

### A — IPv4

```bash
dig github.com A
```

### AAAA — IPv6

```bash
dig github.com AAAA
```

### MX — Mail servers

```bash
dig github.com MX
```

### NS — Name servers

```bash
dig github.com NS
```

### CNAME — Aliases

```bash
dig github.com CNAME
```

### SOA — Start of Authority

```bash
dig github.com SOA
```

---

## Query a Specific DNS Server

Google DNS:

```bash
dig github.com @8.8.8.8
```

Cloudflare DNS:

```bash
dig github.com @1.1.1.1
```

This is useful for comparing DNS responses and isolating resolver-related problems.

---

## Reverse DNS

Perform a reverse lookup from an IP address:

```bash
dig -x 8.8.8.8
```

This queries a PTR record.

---

## Inspect Local DNS Configuration

View the resolver configuration:

```bash
cat /etc/resolv.conf
```

On systems using `systemd-resolved`:

```bash
resolvectl status
```

---

## Useful `dig` Options

Short answer:

```bash
dig +short github.com
```

Query a specific record:

```bash
dig github.com A
```

Query a specific DNS server:

```bash
dig github.com @1.1.1.1
```

Reverse lookup:

```bash
dig -x 8.8.8.8
```

Trace the DNS resolution process:

```bash
dig +trace github.com
```

---

## Common Troubleshooting Commands

Check IP connectivity:

```bash
ping 8.8.8.8
```

Check hostname resolution:

```bash
ping github.com
```

Check DNS resolution:

```bash
dig github.com
```

Check configured DNS servers:

```bash
cat /etc/resolv.conf
```

Check `systemd-resolved`:

```bash
resolvectl status
```

Test another resolver:

```bash
dig github.com @8.8.8.8
```

---

## Quick Reference

| Command                | Purpose                        |
| ---------------------- | ------------------------------ |
| `host domain`          | Simple DNS lookup              |
| `nslookup domain`      | DNS lookup                     |
| `dig domain`           | Detailed DNS query             |
| `dig domain A`         | Query IPv4                     |
| `dig domain AAAA`      | Query IPv6                     |
| `dig domain MX`        | Query mail servers             |
| `dig domain NS`        | Query name servers             |
| `dig domain CNAME`     | Query aliases                  |
| `dig domain SOA`       | Query zone authority           |
| `dig -x IP`            | Reverse DNS lookup             |
| `dig +short domain`    | Short result                   |
| `dig +trace domain`    | Trace DNS resolution           |
| `resolvectl status`    | Inspect DNS configuration      |
| `cat /etc/resolv.conf` | View resolver configuration    |
| `ping IP`              | Test IP connectivity           |
| `ping domain`          | Test resolution + connectivity |

---

## Troubleshooting Principle

When troubleshooting DNS, avoid jumping directly to conclusions.

A useful sequence is:

```text
Connectivity
     ↓
DNS Resolution
     ↓
DNS Configuration
     ↓
Specific Resolver
     ↓
Application / Service
```

The goal is to identify **where the failure occurs** before attempting to fix it.