# TryHackMe | Computer Types

## Room Overview

This room follows Sophia, a summer intern at Nova Labs, as she learns to identify and distinguish between the many types of computers we interact with directly (laptops, phones) and indirectly (servers, IoT devices, embedded systems). The room emphasizes that computer design is always a trade-off between portability, performance, reliability, and cost — there is no single "best" computer, only the right tool for the job.

---

## Task 1 — Introduction

Sophia noticed her neighbor's smart fridge connecting to WiFi and realized computers now hide inside everyday objects — kitchen appliances, doorbells, and more. This room's goal: learn to identify and distinguish between computers used directly (laptops, smartphones) and indirectly (servers, IoT devices, embedded systems), and understand what makes each type suited to its purpose.

---

## Task 2 — Sophia's Summer of Hidden Computers (Month 1)

Sophia learned two key lessons in her first month:
1. Not all computers are meant to move.
2. Not all computers are meant for people to sit in front of.

She was introduced to four computer types that look similar but serve very different purposes:

| Computer Type | Screen & Keyboard | Main Purpose |
|---|---|---|
| Laptop | Yes | Portable everyday computing |
| Desktop | Yes | Sustained performance at a fixed location |
| Workstation | Yes | Precision and reliability for professional tasks |
| Server | No | Providing services to many users over a network |

She started with a **laptop** — great for emails and documents, but it slowed down under long tasks since staying cool in a small, battery-powered device is difficult. A **desktop** ran the same tasks smoothly for longer thanks to wall power and better cooling — designed for consistency, not mobility. For professional work like simulations and 3D models, a **workstation** used specialized components to prioritize accuracy and reliability. Finally, a room full of screenless machines turned out to be **servers** — always running, answering requests from many users at once.

**Task Answers:**
- Which computer type usually runs without a dedicated screen and keyboard? → `server`
- What kind of computer with specialized components would one buy to carry out precision work? → `workstation`

---

## Task 3 — Sophia's Summer of Hidden Computers (Month 2)

By her second month, Sophia started noticing computers she'd never interacted with directly — hiding inside doors, lamps, and coffee machines.

| Type | What it is | Examples |
|---|---|---|
| Smartphone | Pocket-sized computer optimized for battery life and connectivity | iPhone, Android phone |
| Tablet | Touch-first computer with a larger screen | iPad, drawing tablet |
| IoT device | Network-connected device with a single purpose | Thermostat, smart doorbell, fitness tracker |
| Embedded computer | Computer built into another device | Coffee maker controller, automatic door sensor, lamp dimmer chip |

**IoT vs. Embedded:** Both can be small and single-purpose, but the key difference is connectivity. IoT devices connect to a network to report data or receive commands. Embedded computers might not connect to anything — they quietly do their job inside a machine, often for years without anyone knowing they exist (e.g., the tiny computer inside an automatic door frame detecting movement and signaling the motor to open).

**Task Answers:**
- What is the currently most popular pocket-sized computer? → `smartphone`
- What kind of computer would you expect to find in a coffee machine? → `embedded computer`

---

## Task 4 — Why Computers Come in Different Flavors

Sophia asked: *why not just build one computer that does everything?* Gabriel's answer: **because every design is a trade-off.**

- **Mobility costs power** — smaller, portable computers must sacrifice sustained performance.
- **Reliability costs money** — servers and critical systems use redundancy (extra power supplies, disks) to avoid failure.
- **Purpose shapes everything** — you touch a phone, you ask a server for information, an IoT device works quietly without demanding attention.

*There is no best computer. There is only the right tool for the job.*

### Interactive Challenge: Find the Hidden Computers

Goal: find all 8 hidden computers in a room without making more than 3 mistakes.

**Actual computers found:**
- Smart TV ✓
- Robot Vacuum ✓
- Smartwatch ✓
- Smart Fridge ✓
- Smart Speaker ✓
- Security Cam ✓
- WiFi Router ✓
- Thermostat ✓

**Not computers:** Desk Lamp, Coffee Mug, Office Chair, Pen, Textbook, Plant

### Interactive Challenge: The Hot Laptop

Investigated cooling systems on two machines:

| Machine | Cooling Components | Result |
|---|---|---|
| Laptop | Tiny fan, heat pipes, heat sink — all limited by thin design | Throttles under load |
| Desktop | Large fans, airflow space, tower cooler — excellent cooling capacity | Sustained performance |

This demonstrated directly why laptops sacrifice performance for portability.

### Interactive Challenge: The Server Room

Gabriel explained that servers run the business 24/7 and asked Sophia to test what happens if power is disconnected. Tested three scenarios on a server with two redundant power supplies (Power A and Power B):

| Scenario | Result |
|---|---|
| Both On | Server stays ONLINE |
| One Off | Server stays ONLINE |
| Both Off | Server goes OFFLINE |

**Key lesson:** *"Redundant power reduces a single failure point."* Uptime improves when redundancy is combined with backups and monitoring.

### Interactive Challenge: The Right Tool

Final matching challenge — matched 3 real-world jobs to the computer type that handles them best:

| Job | Best Computer Type |
|---|---|
| Edit 4K video all day | Workstation (pro hardware) |
| Host a website 24/7 | Server (always on) |
| Ring when button pressed | Embedded (does one job) |

**Flag:** `THM{8_computer_types}`

---

## Task 5 — Summary

Sophia's final report: *"I arrived thinking computers had screens and keyboards. I leave knowing they are everywhere, especially where I do not see them."*

The room covered eight types of computers and how decisions are made when choosing one over another. The most critical computers aren't always the fastest or flashiest — sometimes they're the silent chips that keep doors opening, planes flying, and coffee machines brewing.

**Final Quiz — Score: 5/5**
1. Why do laptops throttle more than desktops? → Less cooling space
2. What does server redundancy prevent? → Single point of failure
3. Why do smartphones last longer on battery than laptops? → Optimized for efficiency
4. Which feature is more common in workstations? → ECC RAM and certified drivers
5. In many smart homes, what coordinates devices? → Hub or cloud service

---

## Summary / Takeaways

- Computer design is always a set of trade-offs: **mobility vs. sustained power**, **reliability vs. cost**, and **purpose vs. flexibility**. There's no universally "best" computer — only the right tool for a given job.
- **Laptops** trade cooling capacity for portability, causing them to throttle under sustained load; **desktops** and **workstations** trade portability for consistent performance and precision.
- **Servers** rely on redundancy (dual power supplies, backups, monitoring) to minimize single points of failure and maintain 24/7 uptime — a concept directly relevant to SOC/infrastructure monitoring work.
- **IoT devices** and **embedded computers** look similar (small, single-purpose) but differ in connectivity — IoT reports to a network, embedded systems often operate invisibly with no network connection at all.
- Many computers that matter most in daily life are the ones we never see — embedded chips in doors, appliances, and infrastructure — a useful mindset shift when thinking about attack surface and asset inventory in a security context.
