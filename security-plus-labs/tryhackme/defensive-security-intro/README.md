# TryHackMe: Defensive Security Intro

✅ Room completed: 100%

## Overview
Introduces defensive security through a scenario where you help a SOC analyst (Joe) protect **FakeBank** from an ongoing attack — detecting, investigating, and containing it.

## Task 1: Think Like a Defender
Defensive security is the process of defending and securing devices and systems. It focuses on detecting and investigating attacks, and responding before damage occurs — unlike offensive security, defenders don't attack systems, they monitor and protect them.

**Question:** What is the main goal of defensive security?
**Answer:** `Detect and respond to attacks`

## Task 2: Detect Suspicious Activity
**Scenario:** Joe, an apprentice SOC analyst, notices his monitoring dashboard flagging suspicious activity and investigates using a simulated SOC dashboard.

**Question:** Which source IP address is generating the suspicious traffic?
**Answer:** `32.122.195.63`
**Explanation:** The dashboard flagged a "Web Discovery Attack" — automated directory enumeration detected on admin endpoints — with this IP as the source.

**Other alerts on the dashboard (for context):**

| Alert | Severity | Status | Source |
|---|---|---|---|
| Web Discovery Attack | — | New | 32.122.195.63 |
| Suspicious Port Scanning | High | Assigned | 203.0.113.5 |
| Unusual Database Query Pattern | Medium | Investigating | Internal-DB-01 |
| SQL Injection Attack | Critical | Unassigned | 198.51.100.45 |

## Task 3: Identify the Attack
**Goal:** Figure out what the attacker is actually trying to do by digging into the "Web Discovery Attack" alert.

**Attack details:**
- Type: Web Discovery Attack (automated directory enumeration)
- Severity: Medium
- Attack Started: 14/07/2025, 10:21:39
- Duration: 16 minutes 32 seconds
- URLs Attempted: 31
- Blocked Requests: 10

**Question:** Copy the latest URL that the attacker has tried to find.
**Answer:** `https://fakebank.com/admin`
**Explanation:** The attacker was probing for admin panels and hidden paths — a classic reconnaissance technique before an actual exploit attempt (interestingly, mirroring the real hidden page found in the Offensive room!).

## Task 4: Stop the Attack
Once the attacker is identified, the immediate priority in defensive security is **containment** — stopping the attack while it's happening.

**Action taken:** Blocked the attacker's IP (`32.122.195.63`) via a firewall rule (action: BLOCK, then Applied).

**Question:** When the success message appears, copy the flag.
**Answer:** `THM{FAKEBANK-SECURED}`
**Explanation:** Containment is a core SOC responsibility — blocking the source IP at the firewall level immediately stops further malicious requests, completing the incident response cycle: detect → investigate → contain.

---

## Reflection: Offensive vs Defensive
Doing both rooms back-to-back made the two sides of security click for me:
- **Offensive security** is proactive — actively probing a system (like using `dirb` to find hidden pages) to find weaknesses before attackers do.
- **Defensive security** is reactive/protective — monitoring dashboards, investigating alerts, and containing threats (like blocking a malicious IP) once something suspicious is detected.

Interestingly, both rooms used the same fictional target (FakeBank) with a hidden admin/discovery angle — showing how the same vulnerability looks from an attacker's perspective (finding it) versus a defender's perspective (detecting and stopping the attempt to find it). This is exactly why SOC analysts benefit from understanding offensive techniques — it helps them recognize what an attack in progress actually looks like.
