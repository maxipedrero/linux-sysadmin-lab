# DNS Troubleshooting

## Overview

DNS problems can often look like general network or application failures. The goal of troubleshooting is to determine whether the problem is related to DNS resolution, network connectivity, or the application itself.

A useful troubleshooting approach is to test each layer separately.

---

## 1. Check Network Connectivity

First, test connectivity using an IP address instead of a hostname:

```bash
ping 8.8.8.8
```

If this works, the system has basic network connectivity.

If it fails, investigate the network connection before troubleshooting DNS.

---

## 2. Check DNS Resolution

Test whether a hostname can be resolved:

```bash
ping google.com
```

or:

```bash
dig google.com
```

If an IP address works but the hostname cannot be resolved, DNS becomes a primary suspect.

---

## 3. Check the Configured DNS Server

Inspect the local DNS configuration:

```bash
cat /etc/resolv.conf
```

On systems using `systemd-resolved`:

```bash
resolvectl status
```

Look for the configured DNS servers and verify that they are reachable.

---

## 4. Test a Specific DNS Resolver

To determine whether the problem is related to the local DNS resolver, query another DNS server directly:

```bash
dig google.com @8.8.8.8
```

and:

```bash
dig google.com @1.1.1.1
```

If the external resolvers return a valid response while the local resolver does not, the problem may be related to the local DNS configuration, router, or network provider.

---

## 5. Check Different Record Types

A domain can have multiple types of DNS records.

Examples:

```bash
dig example.com A
dig example.com AAAA
dig example.com MX
dig example.com NS
dig example.com SOA
```

This helps determine whether the problem affects a specific record type.

For example, a website may have an `A` record but no `AAAA` record.

---

## 6. Check for NXDOMAIN

A response such as:

```text
status: NXDOMAIN
```

means that the requested domain name does not exist according to the DNS server.

Possible causes include:

* Typographical errors.
* Incorrect hostname.
* Missing DNS record.
* Incorrect DNS zone configuration.

Example:

```bash
dig githb.com
```

---

## 7. Check the DNS Query Time

`dig` reports the query time:

```text
Query time: 21 msec
```

A very high query time may indicate DNS performance problems, although query latency can vary depending on the resolver, network conditions, caching, and the DNS infrastructure involved.

DNS resolution should be investigated separately from the performance of the application itself.

---

## 8. Check DNS Cache and TTL

DNS responses can be cached according to their TTL.

Check the TTL using:

```bash
dig example.com
```

Example:

```text
example.com.    300    IN    A    192.0.2.10
```

A recently changed DNS record may not be visible immediately because intermediate resolvers can still have the previous response cached.

---

## 9. Example: SSH Works by IP but Not Hostname

Suppose:

```bash
ssh user@192.0.2.10
```

works, but:

```bash
ssh user@server.example.com
```

fails.

A useful troubleshooting sequence is:

```bash
dig server.example.com
```

Then check:

```bash
cat /etc/resolv.conf
```

and test another resolver:

```bash
dig server.example.com @1.1.1.1
```

If the IP connection works but DNS resolution fails, the problem is likely related to DNS rather than SSH itself.

---

## 10. Example: `apt update` Cannot Resolve a Host

An error such as:

```text
Temporary failure resolving 'archive.ubuntu.com'
```

can indicate a DNS resolution problem.

Troubleshooting:

```bash
ping 8.8.8.8
```

```bash
dig archive.ubuntu.com
```

```bash
cat /etc/resolv.conf
```

If necessary, test an external resolver:

```bash
dig archive.ubuntu.com @1.1.1.1
```

This helps distinguish between:

* Network connectivity problems.
* Local DNS configuration problems.
* Resolver problems.
* Repository or application problems.

---

## DNS Troubleshooting Workflow

A simple workflow to remember:

```text
1. Can I reach an IP?
        |
        +-- No → Troubleshoot network connectivity
        |
        +-- Yes
             |
2. Can I resolve a hostname?
        |
        +-- No → Troubleshoot DNS
        |
        +-- Yes
             |
3. Does the application work?
        |
        +-- No → Investigate application/service
        |
        +-- Yes → Problem solved
```

The key principle is to **isolate the problem instead of assuming that every connection failure is a DNS problem**.