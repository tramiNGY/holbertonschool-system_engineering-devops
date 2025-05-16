# Web Infrastructure Design

This project is part of the Holberton School **System Engineering & DevOps** curriculum. It focuses on understanding, explaining, and diagramming typical web infrastructure components including servers, DNS, HTTPS, load balancing, monitoring, high availability, and more.

The project teaches how modern websites are deployed and scaled, and how to mitigate common issues like single points of failure (SPOFs), downtime, and security weaknesses.

---

## 📡 Network Basics

**What is a network?**  
A network is a collection of interconnected devices (computers, servers, routers, etc.) that can communicate with each other. It allows data exchange over protocols like TCP/IP.

**Client-Server Model:**  
The web uses a client-server model, where a client (browser) sends a request to a server, and the server responds with data (like a webpage).

**Port & IP Address:**  
An IP address identifies a device on a network. A port number identifies a specific process/service on that device (e.g., HTTP uses port 80, HTTPS uses port 443).

---

## 🖥️ Server Concept

**What is a Server?**  
A server is a computer that provides services or resources to other computers (clients) over a network.

### 🧩 Types of Servers:

- **Web Server:** Serves static content like HTML, CSS, JS.
- **Application Server:** Handles logic, processes requests, and talks to the database.
- **Database Server:** Stores and manages structured data (e.g., MySQL).
- **DNS Server:** Translates domain names into IP addresses.
- **File Server / FTP Server:** Manages file storage and access.

---

## 🌐 Web Server Concept

A **web server** (like Nginx or Apache) receives HTTP/HTTPS requests from clients (usually browsers), and serves them resources such as:

- HTML documents
- Images
- JavaScript and CSS files
- Redirects or reverse proxying to an application server

Web servers are optimized for static content delivery and request handling.

---

## 🌍 DNS (Domain Name System)

DNS translates human-readable domain names (like `google.com`) into IP addresses that computers use to locate services on the internet.

### 📘 TLD (Top-Level Domain)

The **TLD** is the final part of a domain name:
- `.com`, `.org`, `.net`, `.edu`, `.io` etc.

For example, in `www.google.com`:
- `com` is the TLD
- `google` is the second-level domain
- `www` is a subdomain

---

## 📌 DNS Record Types

- **A Record:** Maps a domain name to an IPv4 address.
- **AAAA Record:** Maps a domain name to an IPv6 address.
- **CNAME:** Alias from one domain to another.
- **MX:** Mail server records.
- **NS:** Nameservers for the domain.

For example, `www.foobar.com` → A record → `8.8.8.8`.

---

## 🔀 Load Balancer

A **load balancer** distributes incoming network traffic across multiple backend servers. This ensures:

- Better performance
- High availability
- Redundancy

### 📗 Load Balancing Algorithms:
- **Round Robin:** Rotates through servers sequentially.
- **Least Connections:** Sends traffic to the server with the fewest active connections.
- **IP Hash:** Uses client IP to assign a fixed backend server.

---

## 🧪 Monitoring Concept

Monitoring tools (like Prometheus, Sumo Logic, Datadog, Zabbix) help detect and alert on system health, performance, and availability.

### 📈 What can be monitored:
- Server load, memory usage, disk I/O
- Web server response times, errors
- QPS (Queries Per Second)
- Network latency

**Monitoring tools collect data via agents** (monitoring clients) installed on each server.

---

## 🗃️ What is a Database?

A **database** is a structured collection of data that can be queried and updated efficiently.

- **SQL databases** (e.g., MySQL, PostgreSQL) use structured tables.
- **NoSQL databases** (e.g., MongoDB) store documents or key-value pairs.

### 🔁 Primary/Replica (Master/Slave)

- **Primary (Master):** Handles all writes and reads.
- **Replica (Slave):** Receives read-only copies via replication.

Replication is used for:
- Load distribution
- Fault tolerance
- Backup and recovery

---

## 🔄 Web Server vs Application Server

| Web Server       | Application Server           |
|------------------|-------------------------------|
| Serves static files | Runs business logic (e.g., PHP, Python) |
| Handles HTTP/S   | Can support APIs, dynamic content |
| e.g., Nginx      | e.g., uWSGI, Node.js, Gunicorn |

In most setups, the **web server is in front** and proxies requests to the application server.

---

## ⚠️ Single Point of Failure (SPOF)

A **SPOF** is a component that, if it fails, causes the entire system to fail.

Examples:
- Only one web server
- Only one load balancer
- Only one writable database

Mitigation:
- Redundancy
- Clustering
- High availability (HA) systems

---

## 🛠️ Avoiding Downtime During Deployments

**Deployment Downtime Solutions:**
- **Blue-Green Deployment:** Switch between two environments.
- **Rolling Updates:** Gradually update servers.
- **Canary Releases:** Deploy to small subset of users first.
- **Using Load Balancers:** Temporarily remove server from pool.

Always combine with monitoring and rollback plans.

---

## 🧯 High Availability (HA) Cluster

An **HA cluster** ensures a service is always available even if a component fails.

### 🧩 Cluster Types:

- **Active-Active:** All nodes serve traffic simultaneously. Good for load balancing.
- **Active-Passive:** One node is on standby and takes over if the active node fails.

Use clustering for:
- Load balancers
- Web/app servers
- Databases

---

## 🔐 What is HTTPS?

**HTTPS** (Hypertext Transfer Protocol Secure) is HTTP over **SSL/TLS**, providing:
- **Encryption** (prevents eavesdropping)
- **Authentication** (verifies server identity)
- **Integrity** (prevents tampering)

### 🔑 What is SSL/TLS?

- **SSL** (Secure Sockets Layer) is the older term.
- **TLS** (Transport Layer Security) is the modern, more secure version.
- The **SSL certificate** is issued by a Certificate Authority (CA) and installed on the server.

---

## 🧱 What is a Firewall?

A **firewall** is a security system that controls incoming and outgoing network traffic based on rules.

### 🛡️ What Firewalls Do:

- Block malicious traffic
- Restrict access by IP, port, or protocol
- Protect internal infrastructure
- Can be software-based (e.g., `ufw`, `iptables`) or hardware-based (dedicated appliances)

In a web architecture, you'd place firewalls:
- Between internet and load balancer
- Between load balancer and servers
- Between servers and database

---

## 🏁 Conclusion

Understanding the full web infrastructure stack is essential for DevOps, SRE, and backend engineers. This project guides you through the key components and helps you reason about:

- Scalability
- Availability
- Fault tolerance
- Security
- Deployment

With proper design, you can build systems that are fast, secure, and highly available.

---

## 📌 Acronyms Summary

| Acronym | Meaning |
|--------|---------|
| **LAMP** | Linux, Apache/Nginx, MySQL, PHP/Python |
| **SPOF** | Single Point of Failure |
| **QPS**  | Queries Per Second |
| **HA**   | High Availability |
| **SSL/TLS** | Secure Socket Layer / Transport Layer Security |
