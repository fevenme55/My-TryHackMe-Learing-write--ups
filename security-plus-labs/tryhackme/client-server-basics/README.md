# TryHackMe: Client-Server Basics
✅ Room completed: 100%

## Overview
This room covers how the client-server model works, using a pizza delivery analogy, then applying it to real web communication with HTTP — including hands-on inspection of real HTTP traffic using browser DevTools.

## Task 1: Introduction
Before this room, most computers worked alone — storing their own files and running their own programs without talking to other systems. Early networks like ARPANET, CYCLADES, NPL, and NSFNET were built to connect computers so they could exchange information and share resources, which eventually became the modern internet.

Just like people specialize in skills and offer them as a service, computer systems started to specialize too — this room explains how systems use each other's services through the client-server model.

**Learning Objectives:**
- Understand the Client-Server model
- Understand these concepts on a surface level: DNS, Client, Server, Port, Protocol, Network

## Task 2: Pizza Delivery (Client-Server Analogy)
This task explains the client-server model using a pizza delivery analogy: Alice wants pizza, tells Bob (client) her order, Bob drives to Luigi's Pizza (server) and places the order, the employee makes it, and Bob brings it home.

**Mapping the analogy to networking concepts:**

| Analogy | Concept | Meaning |
|---|---|---|
| Alice → Bob → Luigi's | Client & Server | Bob is the client requesting a service; Luigi's is the server providing it |
| "One large pepperoni & a coke" → "Coming right up!" | Request & Response | Client sends a request, server sends back a response |
| The order itself (structured, understood by both sides) | Protocol | Rules and language both sides agree on to communicate |
| Takeout / Restaurant / Delivery doors | Port | A specific access point for a specific type of service |
| Luigi's Pizza sign ↔ 192.168.1.10 | DNS | Translates a human-friendly name (domain) into a machine address (IP) |

### Client & Server
The client always initiates the request — the server never reaches out first. Alice is the client; Luigi's is the server. In web terms: a browser (client) requests a webpage, and the server serves it.

### Request & Response
If a request is malformed or the resource doesn't exist, the server sends back an **error response** instead (e.g., "no pepperoni pizzas available"). In computer terms: a browser requests a webpage, and if something's wrong, the server returns an error instead of the page.

### Protocol
A protocol is the agreed-upon way client and server communicate. It defines:
- Which commands are understood (e.g., the `GET` command)
- How a request is structured
- What syntax/language is used
- What response is given for valid vs. faulty requests

### Port
A port identifies a **specific service** running on a system. To access a service, the client must connect using the correct port — like choosing the right door (Takeout, Restaurant, Delivery) at Luigi's. A single server can run multiple services at once, each on a different port.

### DNS
DNS (Domain Name Service) translates a human-readable name (like a website domain) into an **IP address** — the server's actual network location, similar to a home address but for computers.

### Questions
**Q:** What do we use to identify a specific service on a server?
**A:** `port`

**Q:** What do we call the address of a server?
**A:** `IP address`
**Explanation:** DNS resolves a domain name into an IP address, telling the client exactly where the server is on the network.

## Task 3: Web Communication in Practice

**HTTP(S) Basics**
- HTTP(S) = Hypertext Transfer Protocol (Secure), a *stateless* client-server protocol
- Stateless = each request is handled independently; the server doesn't remember past requests
- Websites fake "memory" using cookies/session tokens (e.g., staying logged in)

**HTTP Methods (9 core commands)**
`GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS, CONNECT, TRACE`
- **GET** is the most common — used to retrieve a resource, e.g. `GET https://tryhackme.com/index.php`
- The browser (client) builds this request automatically when you type a URL

**Key Response Fields**
| Field | Meaning |
|---|---|
| Scheme | Protocol used (HTTP/HTTPS) |
| Host | Server name being requested |
| Filename | File requested (`/` = `index.html`) |
| Address | IP the site is hosted on |
| Status | Success/failure code (e.g., 200 OK) |

A response has two parts: **headers** (metadata) and **body** (actual content, e.g. raw HTML).

### Hands-On: Inspecting Real GET Requests
Using Firefox DevTools (F12 → Network tab) on `http://httpdemo.local:8080`, I saw 4 GET requests fire on page load:

| Method | File | Type | Size |
|---|---|---|---|
| GET | / | html | 737 B |
| GET | style.css | css | 349 B |
| GET | script.js | js | 355 B |
| GET | favicon.ico | html | 520 B |

Clicking the first request showed: Scheme = http, Host = httpdemo.local:8080, Status = 200 OK, plus response headers (Content-Length, Content-Type, Server).

### Questions
**Q:** What would be the host in `https://www.iamlearning.thm/contact`?
**A:** `www.iamlearning.thm`
**Explanation:** The host is the domain between the scheme and the first `/` — `/contact` is the path, not part of the host.

**Q:** What would be the scheme in `https://www.iamlearning.thm/contact`?
**A:** `https`
**Explanation:** The scheme is the protocol at the start of the URL, before `://`.

## Task 4: Conclusion
This room covered how devices communicate on the internet using the client-server model — the client initiates a request, the server responds (like ordering a pizza: you ask, they deliver). We saw this in practice with the HTTP protocol, inspecting real requests and responses using browser DevTools.

Next step: the follow-up room covers virtualization basics — the infrastructure that supports these client-server services.

## What I Learned
This room made the client-server model concrete — every webpage load is actually multiple separate requests happening behind the scenes. Using DevTools to inspect real traffic is a skill directly relevant to a SOC role, where reading request/response data is part of investigating web-based activity.
