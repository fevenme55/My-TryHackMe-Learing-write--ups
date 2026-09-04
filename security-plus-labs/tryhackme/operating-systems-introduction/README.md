# TryHackMe: Operating Systems: Introduction
✅ Room completed: 100%

## Overview
This room explores what an operating system really does behind the scenes — privileges, user management, memory handling, and processes — then applies it hands-on by investigating a mystery Linux computer to gather real system information.

## Task 1: Introduction
**Scenario:** A friend gifted an old computer, saying it "used to run well" but nothing else. Before deciding to upgrade, wipe, sell, or repurpose it, the goal is to figure out exactly what's on the machine.

**Learning Objectives:**
- Understand what an operating system is and the role it plays
- Explain the core duties of an operating system
- Identify common OS types and their typical use cases
- Practice interacting with an OS to gather system information

**Prerequisites:** Inside a Computer System, Computer Types

## Task 2: The Invisible Manager

An **operating system (OS)** is the core software that coordinates everything happening on a computer. It sits between the user, applications, and hardware, acting as the invisible manager keeping the whole machine running as one unified system.

**Layer stack:** User → Applications → Operating System → Hardware

**Airport analogy:**
- Hardware (CPU, RAM, storage) = the runways, airplanes, fuel systems, radar
- Applications = the airlines and passengers requesting services
- Operating system = the entire air traffic control system, scheduling resources, managing traffic, resolving conflicts, ensuring safety

Without an OS, every application would need direct control over the CPU, memory, files, devices, and security — causing constant conflicts. The OS solves this by acting as the central organizer.

### System Privilege Layers
- **Kernel space:** The privileged, locked-down core of the OS. This is where the kernel runs, with unrestricted access to CPU, memory, storage, and all hardware.
- **User space:** Where all standard applications run, deliberately prevented from accessing hardware directly. Apps must make a **system call** to request the kernel act on their behalf (e.g., to save a file, play a sound, or connect to Wi-Fi).

**Airport analogy continued:** Kernel space = the control tower (only trusted air-traffic controllers can directly control runways and radar). User space = airlines and passengers on the ground, who radio requests (system calls) to the tower instead of touching the equipment directly. This separation keeps the OS reliable — one faulty app can't crash the whole system.

### Operating System Duties

| OS Responsibility | What the OS Does | Example |
|---|---|---|
| Process Management | Creates, schedules, prioritizes, and terminates running programs; decides CPU time per process | Opening multiple apps at once without freezing |
| Memory Management | Allocates RAM to processes, protects memory from other processes, reclaims memory when closed, uses virtual memory when RAM runs low | Multiple apps running isolated so they don't crash each other |
| File System Management | Organizes files into directories, handles naming, paths, permissions, metadata | Creating a folder, saving a photo, setting a file to "read only" |
| User Management | Handles multiple user accounts, authentication, and permissions | Logging in with a password; keeping files private from other accounts |
| Device Management | Loads drivers and provides a hardware abstraction layer so apps can say "print this" or "play this sound" | Plugging in a new mouse/printer and having it work immediately |

### Operating System Security
Every OS acts as a security foundation before any antivirus, firewall, or security tool is introduced. At a basic level, an OS handles:
- **Authentication:** Verifies identity via login passwords and biometrics
- **Permissions:** Controls what each user/app can read, write, or execute
- **Isolation:** Keeps every process in its own protected box (kernel/user space separation)
- **System Protection:** Safeguards critical system files and settings from unauthorized changes

### Hands-On: Investigating the Mystery Computer
Used the `About This Computer` shortcut to open System Monitor on the Ubuntu MATE lab machine.

**Questions:**
- Which OS space has unrestricted access to hardware? → `Kernel Space`
- Which OS responsibility manages user accounts, authentication, and permissions? → `User Management`
- What version of Ubuntu MATE is the computer running? → `1.26.2`
- How much memory is allocated to the machine? → `1.9 GiB`

## Task 3: OS Interaction and Landscape

### OS Interfaces
- **Graphical User Interface (GUI):** Visual representation via icons, windows, menus. Like tapping a destination in a navigation app and letting it generate directions.
- **Command-line Interface (CLI):** Text-based commands for precision, control, and speed. Like entering exact GPS coordinates — direct and accurate, but only if you know the correct syntax.

**Example:** Listing the contents of the `ubuntu` user's `home` directory — GUI requires clicking through folders, CLI requires running `ls ubuntu`.

### The Operating System Landscape

| OS Type | Primary Use Case | Key Characteristics |
|---|---|---|
| Desktop | Personal computers, daily work, gaming, content creation | Rich graphic interface, runs many apps at once, user-focused |
| Server | Web hosting, databases, cloud services, back-end | Headless (no GUI), maximum uptime, multi-user, remote access |
| Mobile | Smartphones and tablets | Touch-based UI, power efficient, always connected, app sandboxing |
| Embedded | Appliances, cars, IoT devices, smart TVs, routers | Tiny footprint, runs on limited hardware |
| Virtual/Cloud | Lab machines, containers, cloud instances | Lightweight, scalable, rapid deployment |

### Real World Operating Systems

**Desktop:**
- Windows (Windows 10 end-of-life, Windows 11)
- macOS (Sonoma 14, Sequoia 15, Tahoe 26)
- Linux — a family of open-source distributions (Ubuntu, Debian, Fedora)

**Server:**
- Windows Server (2016, 2019, 2022, 2025) — large networks, data centers, corporate environments
- Linux (Ubuntu Server, Debian, CentOS, Red Hat) — vast majority of web servers, reliable and open-source
- Unix (IBM AIX, Oracle Solaris) — large enterprises, finance, telecom, government

**Mobile:**
- Android (14–16, manufacturer versions) — most widely used mobile OS
- iOS (17, 18, 26) — Apple's mobile OS

**Embedded and IoT Devices:**
- Embedded Linux (OpenWrt, Ubuntu Core, Yocto Project) — specialized OS for dedicated-function devices
- Real-Time OS (FreeRTOS, VxWorks, QNX) — guaranteed response times (e.g., aircraft controls)

**Virtual and Cloud:**
- Cloud/VM (Ubuntu LTS, Amazon Linux, Rocky Linux) — data centers hosting websites, apps, streaming
- Container-optimized (Alpine Linux, Bottlerocket AWS, Flatcar Linux) — lightweight alternatives to VMs

**Why so many OS?** Different devices demand different capabilities — laptops need user-friendliness and multitasking, servers need stability and uptime, mobile needs power efficiency, embedded systems need a tiny lightweight footprint. No single OS fits every situation, so an ecosystem of operating systems has evolved.

### Hands-On: Continuing the Investigation

**Questions:**
- What Type is listed for the `/dev/root` device in the File Systems tab of System Monitor? → `ext4`
- After opening the Home directory, how many user directories exist? → `3`
- What is the flag value in `note.txt` inside Alex's Documents folder? → `THM{new_pc_for_free!}`

## Task 4: Conclusion

This room covered what an OS really does behind the scenes — privileges, user management, memory handling, and processes — then applied it by investigating a real Linux system's hardware and file systems.

### Key Terminology
- **Operating system (OS):** The core software that manages hardware, applications, and all system resources.
- **Kernel space:** The OS's highly privileged area with direct hardware access; home of the kernel.
- **User space:** The area where regular applications run with limited permissions for safety and stability.
- **Graphical user interface (GUI):** The visual part of the OS — windows, icons, menus — interacted with via clicking/tapping.
- **Command-line interface (CLI):** A text-based interface for controlling the system with precision and speed.

**Next up:** Windows Basics, Linux CLI Basics, Windows CLI Basics — deeper hands-on rooms in the Operating System module.

## What I Learned
This room made the abstract idea of "an operating system" concrete by connecting it to real security concepts: kernel/user space separation is the foundation of process isolation, and OS-level authentication/permissions are the first line of defense before any security tool gets involved. Investigating a real system's file types, memory, and user directories using both GUI and CLI tools is a directly transferable skill for SOC-level triage work.
