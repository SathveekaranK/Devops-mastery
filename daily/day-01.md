# Day 1 — Servers, Networking & DNS

**Status:** Completed  
**Score:** 9/10  
**Date:** 2026-08-23  
**Level:** Beginner

## Objectives
- Understand what a server is
- Understand client/server communication
- Understand IP addresses and ports
- Understand the purpose of DNS
- Observe basic networking behavior using Windows commands

## Concepts Learned

### 1. Server
A server can refer to a computer/system, or more precisely the software/service running on a system, that provides a service to clients. A server is not necessarily only physical hardware.

Example:

```text
AWS EC2 machine
      ↓
Ubuntu Linux
      ↓
Nginx process
      ↓
Web server
```

### 2. Client and Server
A client sends a request to a server. The server processes the request, potentially queries a database or performs another operation, and returns a response.

```text
Client
   ↓ request
Server
   ↓ processing
Server
   ↓ response
Client
```

### 3. IP Address
An IP address identifies a network endpoint/host so traffic can be delivered to the correct machine or interface.

Example:

```text
192.168.1.10
```

### 4. Ports
A port identifies the network service/endpoint receiving traffic on a host. It should not be thought of as directly identifying a process, although a process/application commonly listens on a port.

```text
192.168.1.10:8080
       │      │
       │      └── Port
       └───────── IP
```

Common examples encountered:
- 22 — SSH
- 80 — HTTP
- 443 — HTTPS
- 53 — DNS

### 5. DNS
DNS (Domain Name System) resolves human-readable domain names to IP addresses.

```text
google.com
     ↓
    DNS
     ↓
IP address
```

### 6. Basic Website Request Flow
A simplified model learned today:

```text
Browser
   ↓
DNS
   ↓
Server
   ↓
Application
   ↓
Response
   ↓
Browser
```

A more detailed version to learn later will include TCP, TLS, HTTP, caching, load balancing, and databases.

## Hands-on Practice
The following commands were run successfully on Windows:

```bash
ipconfig
ping google.com
nslookup google.com
```

### Observations
- `ipconfig` displayed IPv4/IPv6 information, gateway information, and temporary addressing information.
- `ping google.com` returned replies including response time in milliseconds and packet sent/received statistics.
- `nslookup google.com` returned DNS resolver information and Google's resolved addresses, including a non-authoritative answer.

## Assessment
**Result: 9/10 — Passed**

The learner demonstrated strong understanding of:
- Client/server model
- Server concept
- IP addressing
- Ports
- DNS
- Basic website request flow
- Practical networking observations

### Minor corrections
- A server is not necessarily only hardware; the term can also refer to the software/service providing a response.
- A port identifies a network service/endpoint rather than directly identifying a process.

## Next Step
**Day 2 — Operating Systems & Linux Fundamentals**

Planned concepts:
- What an operating system is
- Kernel vs operating system
- Programs vs processes
- What happens when a program runs
- Why Linux is important in DevOps
- First Linux hands-on practice
