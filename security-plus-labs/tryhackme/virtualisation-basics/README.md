# TryHackMe | Virtualisation Basics

## Room Overview

This room explains why virtualization became a foundational concept in modern IT. It builds on the "one server = one application" problem that early data centers faced, then walks through how hypervisors, virtual machines, and containers solve it by allowing multiple isolated environments to safely share the same physical hardware.

---

## Task 1 — Introduction

Before virtualization, IT infrastructure followed a simple but wasteful rule: **one server = one application**. If a company needed a website, database, email service, and internal app, they needed four separate physical servers.

This approach caused real problems:

- **High cost** — buying, powering, cooling, and maintaining multiple physical servers is expensive.
- **Low utilization** — most servers only used 5–20% of their actual capacity, wasting CPU, memory, and storage.
- **Slow deployment** — provisioning a new physical server could take days or weeks.
- **Hard to scale** — scaling up usually meant buying yet another physical machine.

Virtualization was created to solve exactly this problem: sharing hardware safely and efficiently across multiple independent workloads.

---

## Task 2 — Virtualization Overview

Virtualization introduced a new question: *what if multiple applications could share the same physical server safely?*

The answer is the **hypervisor** — a virtualization layer that acts as a referee between virtual machines (VMs), giving each one the ability to behave like an independent physical computer, even though they're all running on shared hardware.

**The Building Analogy:**

- A single person living alone in a 10-floor building uses one floor but pays to maintain the whole building — wasteful, just like a server running only one application.
- Dividing the building into separate apartments lets multiple tenants live independently while sharing core infrastructure (electricity, water, elevators) — cheaper and more efficient for everyone.

Mapped to virtualization:

| Building Analogy | Virtualization |
|---|---|
| The building | The physical server |
| The apartments | Lab machines (VMs) |
| The tenants | Applications / operating systems |
| The building manager | The hypervisor |

**Task Answers:**
- What does virtualization enable multiple applications to share? → `physical hardware`
- What is the name of the software that manages the resources for each lab machine? → `hypervisor`

---

## Task 3 — Virtualization Components

### Hypervisor (The Building Manager)

A hypervisor is the core technology behind virtualization. It:

- Divides a physical computer into multiple virtual ones.
- Gives each lab machine its own share of CPU, memory, and storage.
- Keeps everything isolated and safe.
- Manages the lifecycle of lab machines (start, stop, pause, clone, delete).

There are two types:

| Type | Description | Best for |
|---|---|---|
| **Type 1** | Runs directly on physical hardware | Fast, efficient — servers and professional environments |
| **Type 2** | Runs inside an existing operating system | Easier to install — learning, testing, small setups |

| Use Case | Type 1 | Type 2 |
|---|---|---|
| Test Malicious Files | | X |
| Production Server | X | |
| Database Server | X | |
| Software Testing | | X |
| Kali Linux | | X |
| Data Center | X | |

> ⚠️ When testing malicious files in a VM, care must be taken so the host machine isn't infected by malware in the guest. This is usually done by using a different OS for host and guest, or isolating the guest so it can't communicate with the host.

### Lab Machines (The Apartments)

A **Lab Machine (VM)** is a virtual computer created by the hypervisor. Even though it's virtual, it behaves like a real machine:

- It has its own virtual CPU, RAM, storage, and network.
- It can run any operating system (Windows, Linux, etc.).
- It's completely isolated from other VMs — if one breaks, the others keep working.

VMs can be deployed locally using tools like **Oracle VirtualBox** and **VMware Workstation**, both of which act as Type 2 hypervisors.

### Containers (The Rooms Inside the Apartment)

A **container** is a lightweight, isolated environment that runs a single application and its dependencies. Instead of bringing a whole separate operating system, a container borrows the host's kernel.

Because containers share the kernel:

- They start almost instantly and use fewer resources than full VMs.
- They must match the host system's type (a Windows container can't run on a Linux machine).
- They remain isolated from each other — a misbehaving container doesn't affect the others.
- They run consistently anywhere, ideal for development, testing, and scalable deployments.

**Docker** is the most common tool for deploying containers.

**Relationship diagram:**
Physical Server
└── Hypervisor
├── Virtual Machine A
└── Virtual Machine B
├── Container A
└── Container B
In summary: VMs provide the "full apartment" — maximum separation and flexibility. Containers offer lightweight "rooms" — ideal for scalable, fast-deploying applications.

**Task Answers:**
- A user wants to deploy a study lab to practice cybersecurity exercises. Which type of hypervisor will they use? → `type 2`
- A company wants to host multiple small applications in the same lab machine. What should they use? → `containers`

---

## Task 4 — Managing Virtual Machines

**Scenario:** As the person responsible for AutoGalo's virtual environment, I used the **Virtualization Manager** tool to investigate and manage the company's infrastructure.

### Fixing the Mail Server Issue

Everyone in the company stopped receiving emails. Checking the **Lab Machines** section of Virtualization Manager showed `Mail-SERVER` in an **Error** state.

**Fix:** Used the restart (blue square) button to rerun the VM. After restarting, `Mail-SERVER` returned to a **Running** state with no errors.

### Creating a Lab Machine

Created a new VM to host the marketing team's website:

| Field | Value |
|---|---|
| Name | `Marketing-VM` |
| CPU Cores | 4 |
| Memory | 8 GB |
| Disk Size | 100 GB |

After creation, `Marketing-VM` appeared at the top of the Lab Machines list with a **Stopped** status and a DHCP-assigned IP.

### Analyzing Hardware Usage

Reviewed the **Hosts** section to check physical server health:

| Host | CPU | Memory | Storage | VMs | Status |
|---|---|---|---|---|---|
| HV-PROD-01 | 45% | 68% | 72% | 3 | Connected — has capacity for more VMs |
| HV-PROD-02 | 98% | 90% | 95% | 8 | Connected — nearly at full capacity, needs to be reported |
| HV-BACKUP-01 | 0% | 0% | 30% | 0 | Disconnected — server is not running |

**Task Answers:**
- Name of the lab machine that has been running the longest → `FileServer-01`
- Name of the lab machine using the biggest amount of memory → `DB-Cluster-01`
- How many VMs are in the running state after solving the `Mail-SERVER` issue → `9`
- Name of the physical machine hosting most of the VMs → `HV-PROD-02`

---

## Task 5 — Conclusion

### Key Terminology

| Term | Definition |
|---|---|
| **Virtualization** | Enables a single physical computer to act like multiple separate computers |
| **Hypervisor** | The "manager" software that creates and runs virtual machines |
| **Lab Machine (VM)** | A whole virtual computer inside the real one, with its own OS |
| **Container** | A small, isolated box for one app that shares the host's system |
| **Container Images** | A pre-packed recipe/template used to create containers |
| **Network Ports** | Numbered entry points that apps use to communicate over the network |

### Key Benefits of Virtualization

- Cost savings
- Better resource usage
- Safe testing environment for cybersecurity
- Faster deployment
- Flexibility
- Portability
- Scalability
- Centralized management

---

## Summary / Takeaways

- Virtualization solves the "one server = one application" inefficiency by letting multiple isolated environments share physical hardware safely.
- The **hypervisor** is the core software that makes this possible, dividing hardware resources and enforcing isolation between VMs.
- **Type 1 hypervisors** run directly on hardware (production/data center use); **Type 2 hypervisors** run inside an OS (learning/testing — this is what VirtualBox and VMware Workstation are).
- **Containers** are a lighter-weight alternative to full VMs, sharing the host kernel for faster startup and lower resource use, at the cost of OS-type flexibility.
- Hands-on practice with Virtualization Manager reinforced real SOC-relevant skills: diagnosing VM errors, provisioning new lab machines, and monitoring host capacity/health — directly applicable to managing home lab environments in VirtualBox
