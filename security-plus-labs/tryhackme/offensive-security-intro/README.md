# TryHackMe: Offensive Security Intro

✅ Room completed

## Overview
A hands-on introduction to offensive security — hacking a fake banking website (legally, in a safe environment) to experience how an ethical hacker approaches a target.

## Task 1: Think Like a Hacker!
**Question:** Which term describes simulating a hacker's actions to find system vulnerabilities?
**Answer:** `Offensive Security`
**Explanation:** Offensive security means proactively thinking like an attacker to find weaknesses before real attackers do.

## Task 2: Starting the Lab
A fake banking application called **FakeBank** was launched to simulate a real target.

**Question:** What is the bank account number shown in the FakeBank application?
**Answer:** `8881`

## Task 3: Find Hidden Pages
**Goal:** Find a weakness in the FakeBank website — a common mistake is leaving hidden pages accessible.

**Tool used:** `dirb` — a directory brute-forcing tool that discovers hidden URLs/pages by testing a wordlist of common names against a target site.

**Output:**
---- Scanning URL: http://fakebank.thm/ ----
http://fakebank.thm/bank-transfer (CODE:200|SIZE:4663)
http://fakebank.thm/images (CODE:301|SIZE:179)
**Question:** Dirb found one URL, `http://fakebank.thm/images`. What is the other hidden URL?
**Answer:** `http://fakebank.thm/bank-transfer`
**Explanation:** This is exactly the kind of exposed functionality an attacker looks for during reconnaissance — sensitive functionality left publicly accessible without any obvious link from the main site.

## Task 4: Attack the Admin Page
**Goal:** Exploit the hidden `/bank-transfer` admin panel — it allowed adding money to an account with no authentication required.

**Steps:**
1. Navigated to `http://fakebank.thm/bank-transfer`
2. Selected account `8881`, deposited $2000
3. Clicked "Deposit Money" — success popup confirmed the exploit

**Question:** When your balance turns positive, a pop-up with green text appears. Enter the green words.
**Answer:** `BANK-HACKED`
**Explanation:** This demonstrated a **broken access control** vulnerability — a sensitive financial function was exposed on an unlisted URL with zero authentication. In a real attack, this is how someone could manipulate account balances without ever needing valid admin credentials, just by finding the hidden page.
