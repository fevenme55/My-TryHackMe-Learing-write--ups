# TryHackMe: Inside a Computer System
✅ Room completed: 100%

## Overview
Part of the Computer Fundamentals module. Before learning to secure a system, you first need to understand what you're securing — this room covers the core components of a computer and how it boots up.

## Task 1: Introduction
**Analogy:** Just like defending a castle requires knowing its layout (treasure room, food storage, commander's quarters) and who can access each area, defending a computer system requires understanding its components and how they connect. You can't protect what you don't understand.

**Learning Objective:** Recognize and understand the functions of various computing components.

## Task 2: Inside a Computer System
Uses a **human body analogy** to explain each core component:

| Component | Human Body Analogy | Function |
|---|---|---|
| Motherboard | Skeleton and Nerves | Connects all components; holds CPU socket, RAM slots, expansion slots, and ports |
| CPU | The Brains | Executes instructions and performs calculations; modern CPUs use multiple cores in parallel |
| RAM | Short-term Memory | Volatile temporary storage the CPU needs quick access to; loses data when powered off |
| Storage (SSD/HDD) | Long-term Memory | Permanent storage; HDDs use moving parts (cheaper, larger), SSDs use memory chips (faster) |
| Network Adapter | Vocal Cords | Lets the computer communicate with other systems, wired or wireless |
| Power Supply (PSU) | Heart and Lungs | Supplies power to all components; system fails if PSU can't meet power demand |
| Graphics Card | Visual Cortex | Processes and outputs visual information to displays |
| Input/Output | Senses | Input devices (keyboard, mouse) send data in; output devices (monitor, speakers) send data out |

**Interactive exercises:** Answered knowledge-check questions for all 8 components, then completed a drag-and-drop exercise placing each on its correct motherboard connector.

**Flag:** `THM{4llpccomp0n3nts1d3nt1f13d}`

## Task 3: What Happens When You Press the Start Button?
Covers the **boot sequence** — using the analogy of the human body waking up in the morning:

1. **Press Power Button** — signal sent to the PSU to allow power to flow
2. **Firmware Starts (UEFI/BIOS)** — initializes and coordinates hardware components; UEFI is the modern replacement for BIOS
3. **Power-On Self Test (POST)** — checks that required hardware is present, configured, and functioning
4. **Select Boot Device** — UEFI follows a priority list to determine which device to boot from (typically SSD/HDD with the OS)
5. **Initiate Bootloader** — loads the operating system into RAM, then UEFI hands control to the OS

**Interactive exercises:** Answered a knowledge-check question for each boot step, then completed a drag-and-drop exercise arranging the steps in correct order.

## Task 4: Conclusion
This room covered the core components of a computer system and how it boots up. These fundamentals matter for cybersecurity because you'll often need to recall how each component functions and interacts — the boot process especially, since it's sometimes targeted by attackers.

**Next room:** Computer Types — exploring how different combinations of components create diverse types of computer systems.

## What I Learned
This room gave me a clear mental model of both the physical building blocks of a computer and what happens the moment you power it on. Understanding the boot process (POST, UEFI, bootloader) is directly relevant to SOC work, since boot-level attacks (like bootkits or firmware tampering) are a real threat vector.
