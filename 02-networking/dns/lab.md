# DNS Lab

## Objective

Practice basic DNS queries in Linux and understand how different DNS record types provide different kinds of information.

The lab focuses on:

* Resolving domain names.
* Identifying IPv4 and IPv6 records.
* Querying mail servers.
* Identifying authoritative name servers.
* Inspecting SOA records.
* Understanding DNS responses using `dig`.
* Comparing `host`, `dig`, and `nslookup`.

---

## 1. Basic DNS Resolution

### Using `host`

```bash
host github.com
```

The command returned an IPv4 address:

```text
github.com has address 4.228.31.150
```

It also displayed information about the domain's mail server.

### Using `dig`

```bash
dig github.com
```

The response included:

```text
QUESTION SECTION:
;github.com.    IN    A

ANSWER SECTION:
github.com.    ...    IN    A    4.228.31.150
```

This shows that the default query performed by `dig` was an `A` record lookup.

The DNS server used by the system was:

```text
192.168.0.1#53
```

`192.168.0.1` is the local DNS resolver used by the network, while port `53` is the standard DNS port.

The query completed successfully in a few milliseconds.

### Using `nslookup`

```bash
nslookup github.com
```

The command also returned:

```text
Server:    192.168.0.1
Address:   192.168.0.1#53

Name:      github.com
Address:   4.228.31.150
```

### Comparison

The three commands can perform DNS lookups, but present the information differently:

* `host` provides a concise result.
* `nslookup` provides a simple interactive-style DNS lookup.
* `dig` provides much more detailed information and is especially useful for troubleshooting.

---

## 2. Querying Specific DNS Record Types

### A Record

```bash
dig github.com A
```

The response contained:

```text
github.com.    38    IN    A    4.228.31.150
```

An `A` record maps a hostname to an IPv4 address.

The `38` value represents the remaining TTL of the cached response at the resolver.

---

### MX Record

```bash
dig github.com MX
```

The response contained:

```text
github.com.    300    IN    MX    0 github-com.mail.protection.outlook.com.
```

An `MX` record specifies the mail server responsible for receiving email for a domain.

In this case, the domain uses Microsoft Outlook mail infrastructure.

The `0` value represents the mail server preference/priority.

---

### AAAA Record

```bash
dig github.com AAAA
```

The query returned:

```text
ANSWER: 0
```

No `AAAA` record was returned for `github.com`.

`AAAA` records are used to map hostnames to IPv6 addresses.

The response had:

```text
status: NOERROR
```

This means the DNS query itself completed successfully; it simply did not return an IPv6 address for the requested name.

The response also included an `SOA` record in the `AUTHORITY SECTION`, providing information about the DNS zone.

---

## 3. Name Server Records

### NS Record

```bash
dig github.com NS
```

The query returned multiple authoritative name servers, including:

```text
dns1.p08.nsone.net.
dns2.p08.nsone.net.
dns3.p08.nsone.net.
dns4.p08.nsone.net.

ns-1707.awsdns-21.co.uk.
ns-421.awsdns-52.com.
ns-520.awsdns-01.net.
ns-1283.awsdns-32.org.
```

`NS` records identify the authoritative DNS name servers for a domain.

Multiple name servers provide redundancy and improve availability.

This also demonstrated that GitHub's DNS infrastructure uses multiple DNS providers/infrastructures, including NS1 and Amazon DNS infrastructure.

---

## 4. SOA Record

```bash
dig github.com SOA
```

The response included:

```text
github.com.    900    IN    SOA
ns-1707.awsdns-21.co.uk.
awsdns-hostmaster.amazon.com.
1
7200
900
1209600
86400
```

`SOA` stands for **Start of Authority**.

The SOA record contains administrative and operational information about a DNS zone.

Important fields include:

* Primary name server.
* Administrative contact.
* Serial number.
* Refresh interval.
* Retry interval.
* Expiration interval.
* Negative caching TTL.

The presence of `awsdns` indicates that AWS DNS infrastructure is involved in the authoritative DNS configuration for the zone. It does not mean that all of GitHub's infrastructure is hosted on AWS.

---

## 5. CNAME Record

```bash
dig github.com CNAME
```

The response returned:

```text
ANSWER: 0
```

No `CNAME` record was returned for `github.com`.

A `CNAME` record is used to create an alias from one hostname to another.

For example:

```text
www.example.com → example.com
```

A CNAME lookup returning no answer does not indicate a DNS failure. It means that the requested hostname does not have a CNAME record in the response.

---

## 6. Understanding `dig` Output

During the labs, several important sections of the `dig` output were identified.

### QUESTION SECTION

Shows what was requested:

```text
github.com.    IN    A
```

This means:

> Query the `A` record for `github.com`.

### ANSWER SECTION

Contains the direct answer to the query:

```text
github.com.    ...    IN    A    4.228.31.150
```

### AUTHORITY SECTION

Contains information about the authoritative DNS zone, such as an SOA record.

### SERVER

Shows which DNS resolver answered the query:

```text
192.168.0.1#53
```

### Query Time

Shows how long the DNS query took:

```text
Query time: 21 msec
```

### MSG SIZE rcvd

Shows the size, in bytes, of the DNS response received.

---

## 7. DNS Record Summary

| Record | Purpose                    | Example                                  |
| ------ | -------------------------- | ---------------------------------------- |
| A      | IPv4 address               | `github.com → 4.228.31.150`              |
| AAAA   | IPv6 address               | IPv6 address                             |
| MX     | Mail server                | `github-com.mail.protection.outlook.com` |
| NS     | Authoritative name servers | `dns1.p08.nsone.net`                     |
| CNAME  | Hostname alias             | `www.example.com → example.com`          |
| SOA    | Zone authority information | Primary DNS server and zone parameters   |

---

## Key Takeaways

* DNS translates domain names into information used to establish network connections.
* `A` records provide IPv4 addresses.
* `AAAA` records provide IPv6 addresses.
* `MX` records identify mail servers.
* `NS` records identify authoritative name servers.
* `SOA` records contain administrative information about a DNS zone.
* `CNAME` records create aliases between hostnames.
* `dig` provides detailed information and is particularly useful for DNS troubleshooting.
* The local system can use a router or local resolver to perform DNS queries.
* A successful DNS query does not necessarily mean that the requested record exists.
* `NOERROR` can be returned even when a specific record type has no answer.

---

## Next Steps

Further labs will focus on:

* Querying specific DNS resolvers.
* Comparing DNS responses from different providers.
* Inspecting `/etc/resolv.conf`.
* Using `resolvectl`.
* Investigating DNS caching.
* Troubleshooting DNS resolution failures.
* Distinguishing DNS problems from general network connectivity problems.