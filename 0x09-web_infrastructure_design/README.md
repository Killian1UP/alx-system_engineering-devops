# Web Infrastructure Design

This repository contains the design and explanation for different stages of a web infrastructure setup, starting from a simple single-server architecture to a secured, monitored, and scalable infrastructure.

## **0. Simple Web Stack**
A basic one-server infrastructure that hosts the website `www.foobar.com`.

**Components:**
- 1 Server
- 1 Web Server (Nginx)
- 1 Application Server
- Application Files (Code Base)
- 1 Database (MySQL)
- Domain name `foobar.com` with a `www` record pointing to IP `8.8.8.8`

**Key Concepts:**
- **Server:** A physical or virtual machine that hosts applications and services.
- **Domain Name Role:** Translates a human-readable name into an IP address.
- **DNS Record:** The `www` is a CNAME or A record in DNS.
- **Web Server Role:** Handles HTTP requests from clients and serves static content.
- **Application Server Role:** Executes application code to generate dynamic content.
- **Database Role:** Stores and retrieves structured application data.
- **Communication:** Uses HTTP/HTTPS over TCP/IP.

**Issues:**
- Single Point of Failure (SPOF)
- Downtime during maintenance
- Cannot scale for high traffic

---

## **1. Distributed Web Infrastructure**
A three-server setup to improve availability and scalability.

**Additional Components:**
- 2 Servers
- Load Balancer (HAProxy)
- Database replication (Primary-Replica)

**Load Balancer:**
- Distributes traffic between web/application servers.
- Algorithms: Round Robin, Least Connections, etc.
- **Active-Active:** All servers handle traffic simultaneously.
- **Active-Passive:** One server active, another on standby.

**Database Cluster:**
- Primary node handles writes.
- Replica node handles reads.
- Reduces load and improves availability.

**Issues:**
- SPOF in certain points
- No firewall, no HTTPS
- No monitoring

---

## **2. Secured and Monitored Web Infrastructure**
A more robust setup with security and monitoring.

**Additional Components:**
- 3 Firewalls (one per server)
- SSL certificate for HTTPS
- 3 Monitoring clients (Sumologic or similar)

**Security & Monitoring:**
- **Firewalls:** Control inbound/outbound traffic based on rules.
- **HTTPS:** Encrypts communication between client and server.
- **Monitoring:** Tracks server health, logs, and performance metrics.
- **Monitoring Tool Data Collection:** Uses agents to send logs and metrics.
- **QPS Monitoring:** Configure monitoring tool to measure queries per second.

**Issues:**
- SSL termination at load balancer can expose internal traffic.
- Single MySQL write node still a risk.
- Identical servers can be harder to isolate issues.

---

## **3. Scale Up**
An advanced setup splitting components into dedicated servers.

**Additional Components:**
- 1 New Load Balancer (clustered with the existing one)
- Dedicated servers for:
  - Web Server
  - Application Server
  - Database

**Reason for Changes:**
- Improves scalability and fault tolerance.
- Easier maintenance and upgrades.
- Reduces risk of resource contention.

---

## **Usage**
Each design is represented in its respective file:
- `0-simple_web_stack`
- `1-distributed_web_infrastructure`
- `2-secured_and_monitored_web_infrastructure`
- `3-scale_up`

These files contain the diagrams and explanations for each stage.

---

## **Author**
Project completed as part of the **ALX System Engineering DevOps** program.

