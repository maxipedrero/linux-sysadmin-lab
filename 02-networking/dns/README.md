# DNS (Domain Name System)

## Overview

DNS (Domain Name System) is a fundamental service used to translate human-readable domain names into IP addresses.

For example:

```text
github.com → IP address
```

Instead of having to remember an IP address for every service, users and applications can work with domain names.

DNS is involved in many of the tasks performed by a system administrator, including accessing websites, connecting to remote servers, cloning Git repositories, downloading packages, and communicating with cloud services.

---

## Learning Objectives

In this module, I learned how DNS works and how Linux systems perform domain name resolution.

The main objectives were:

* Understand the purpose of DNS.
* Understand the basic DNS resolution process.
* Identify common DNS record types.
* Query DNS servers from Linux.
* Inspect local DNS configuration.
* Compare different DNS resolvers.
* Understand DNS caching and TTL.
* Troubleshoot common DNS-related connectivity problems.

---

## How DNS Resolution Works

When a user or application requests a domain such as:

```text
github.com
```

the system needs to determine which IP address corresponds to that domain.

A simplified view of the process is:

```text
Application
     |
     v
DNS Resolver
     |
     v
DNS Server
     |
     v
IP Address
     |
     v
Remote Server
```

The operating system sends a DNS query to the configured resolver. The resolver obtains the required information and returns the IP address to the client.

The application can then use that IP address to establish the connection.

---

## Common DNS Record Types

DNS zones contain different types of records depending on the information they provide.

| Record | Purpose                                                                       |
| ------ | ----------------------------------------------------------------------------- |
| A      | Maps a hostname to an IPv4 address.                                           |
| AAAA   | Maps a hostname to an IPv6 address.                                           |
| CNAME  | Creates an alias pointing to another hostname.                                |
| MX     | Specifies mail servers responsible for a domain.                              |
| TXT    | Stores text-based information such as verification or email security records. |
| NS     | Specifies the authoritative name servers for a domain.                        |

Example:

```text
example.com.    A       192.0.2.10
```

This record indicates that `example.com` resolves to the IPv4 address `192.0.2.10`.

---

## DNS TTL

TTL stands for **Time To Live**.

It determines how long a DNS response can be cached before it should be queried again.

For example:

```text
TTL = 300
```

means that the response can normally be cached for 300 seconds.

TTL values are important when troubleshooting DNS changes because a recently modified record may not be immediately visible to every client or resolver.

---

## DNS Resolvers

A DNS resolver is responsible for receiving DNS queries from clients and obtaining the required DNS information.

Some commonly used public DNS resolvers are:

| Provider   | IPv4      |
| ---------- | --------- |
| Google DNS | `8.8.8.8` |
| Google DNS | `8.8.4.4` |
| Cloudflare | `1.1.1.1` |
| Cloudflare | `1.0.0.1` |
| Quad9      | `9.9.9.9` |

Different resolvers can be useful when troubleshooting DNS problems.

For example:

```bash
dig github.com @8.8.8.8
```

and:

```bash
dig github.com @1.1.1.1
```

can be used to compare responses from different DNS servers.

---

## Linux DNS Configuration

One of the traditional files used to inspect DNS configuration on Linux is:

```text
/etc/resolv.conf
```

It may contain entries such as:

```text
nameserver 1.1.1.1
nameserver 8.8.8.8
```

The `nameserver` directive specifies which DNS server should be used for name resolution.

On modern Linux distributions, `/etc/resolv.conf` may be managed automatically by services such as **systemd-resolved** or NetworkManager.

The current resolver configuration can also be inspected with:

```bash
resolvectl status
```

when `systemd-resolved` is in use.

---

## DNS Troubleshooting Tools

Several command-line tools are useful when diagnosing DNS problems.

### `dig`

`dig` provides detailed DNS query information.

```bash
dig github.com
```

It can also query a specific DNS server:

```bash
dig github.com @1.1.1.1
```

Specific record types can be requested:

```bash
dig github.com A
dig github.com AAAA
dig gmail.com MX
dig google.com TXT
```

---

### `nslookup`

`nslookup` is another tool for querying DNS servers.

```bash
nslookup github.com
```

It can also be used with a specific DNS server:

```bash
nslookup github.com 1.1.1.1
```

---

### `host`

`host` provides a simpler way to perform DNS lookups.

```bash
host github.com
```

Example use:

```bash
host -t MX gmail.com
```

---

### `ping`

Although `ping` is primarily a connectivity diagnostic tool, it can also help identify DNS problems.

```bash
ping github.com
```

If the hostname cannot be resolved, the command may report a name resolution error.

However, a successful `ping` does not necessarily mean that the application itself is working. ICMP connectivity and application-layer connectivity are different things.

---

### `resolvectl`

On systems using `systemd-resolved`:

```bash
resolvectl status
```

can be used to inspect DNS configuration and active DNS servers.

---

## DNS vs Network Connectivity

One important troubleshooting concept is distinguishing between a network connectivity problem and a DNS problem.

For example:

```bash
ping 8.8.8.8
```

may work while:

```bash
ping google.com
```

fails.

This can indicate that the system has network connectivity but is unable to resolve the hostname.

A useful troubleshooting approach is therefore:

```text
Can I reach an IP address?
        |
        +-- No → Investigate network connectivity
        |
        +-- Yes
             |
             v
Can I resolve a hostname?
        |
        +-- No → Investigate DNS
        |
        +-- Yes → Continue troubleshooting
```

---

## Real-World Examples

DNS is involved in many everyday system administration tasks.

### Git

When running:

```bash
git clone https://github.com/user/repository.git
```

the system must resolve `github.com` before establishing the HTTPS connection.

---

### SSH

When connecting to a server using a hostname:

```bash
ssh user@server.example.com
```

DNS resolution must occur before the SSH connection can be established.

If connecting directly by IP works:

```bash
ssh user@192.0.2.10
```

but the hostname does not:

```bash
ssh user@server.example.com
```

DNS becomes one of the first things to investigate.

---

### Package Management

Commands such as:

```bash
sudo apt update
```

may fail if the system cannot resolve the repositories' hostnames.

For example:

```text
Temporary failure resolving 'archive.ubuntu.com'
```

This can indicate a DNS resolution problem, although network connectivity and other configuration issues should also be checked.

---

## Skills Practiced

* DNS fundamentals
* Linux DNS configuration
* Domain name resolution
* DNS record types
* DNS troubleshooting
* `dig`
* `nslookup`
* `host`
* `resolvectl`
* `/etc/resolv.conf`
* DNS caching and TTL
* Network troubleshooting
* Linux system administration

---

## Labs

The practical exercises for this module are documented in:

```text
lab.md
```

The labs cover DNS queries, record types, different DNS resolvers, local configuration, and practical troubleshooting scenarios.

---

## Troubleshooting

Real-world DNS troubleshooting scenarios are documented in:

```text
troubleshooting.md
```

These scenarios focus on identifying whether a problem is related to DNS resolution, network connectivity, or the application itself.