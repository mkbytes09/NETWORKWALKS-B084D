<div align="center">
  
**WEEK 2 | PROJECT MODULE 1**
  
# FOOTPRINTING & RECONNAISSANCE ATTACKS
# WITH MULTIPLE KALI TOOLS

</div>

> **Target:** `www.networkwalks.com` (written permission obtained)
> **Platform:** Kali Linux
> **Author:** `Muhammad Kamil`
> **Date:** `08-11-2026`

---

## Table of Contents

1. [Reconnaissance Introduction](#1-reconnaissance-introduction)
2. [Task Objectives](#2-task-objectives)
3. [Deliverables](#3-deliverables)
4. [Tools Used](#4-tools-used)
5. [Tool Definitions, Attacker Usage & Evidence](#5-tool-definitions-attacker-usage--evidence)
   - [5.1 whois](#51-whois)
   - [5.2 whatweb](#52-whatweb)
   - [5.3 nslookup](#53-nslookup)
   - [5.4 curl -I](#54-curl--i)
   - [5.5 wafw00f](#55-wafw00f)
   - [5.6 dnsrecon](#56-dnsrecon)
6. [Disclaimer](#6-disclaimer)
7. [Conclusion](#7-conclusion)
8. [References](#8-references)

---

## 1. Reconnaissance Introduction

**Reconnaissance** (also called *footprinting* or *information gathering*) is the first phase of the cyber kill chain and of almost every penetration test. Before an attacker sends a single exploit, they try to learn as much as possible about the target: who owns the domain, what IP addresses and name servers it uses, which web technologies are running, and what defences sit in front of the application.

Reconnaissance is divided into two categories:

| Type | Description | Example in this project |
|------|-------------|--------------------------|
| **Passive** | Information is collected without directly interacting with the target's systems, or by using third-party data sources. Very hard for the target to detect. | `whois` lookups, public DNS queries |
| **Active** | The tester or attacker directly interacts with the target (sending requests, probing services). May appear in logs and trigger alerts. | `whatweb`, `curl -I`, `wafw00f`, `dnsrecon` |

The information gathered here shapes every later stage: attackers use it to select exploits that match the discovered software versions, to plan social-engineering campaigns using registrant details, and to design attacks that avoid or bypass a Web Application Firewall (WAF). Defenders perform the same exercise to see their organisation **the way an attacker sees it**, and to reduce that exposure before it is abused.

This module is mapped to **MITRE ATT&CK Tactic TA0043 – Reconnaissance**.

---

## 2. Task Objectives

The objective of this module is to perform a footprinting and reconnaissance assessment of a **written-permitted** target using native Kali Linux tools, and to understand how each tool contributes to an attacker's picture of the target.

| # | Task | Objective |
|---|------|-----------|
| 1 | Run `whois` | Identify domain registration details (registrar, registrant, creation/expiry dates, name servers). |
| 2 | Run `whatweb` | Fingerprint the web technologies (web server, CMS, frameworks, scripting languages, JavaScript libraries). |
| 3 | Run `nslookup` | Resolve the domain name to its IP address(es). |
| 4 | Run `curl -I` | Read HTTP response headers to identify server software, security headers and redirects. |
| 5 | Run `wafw00f` | Detect whether a Web Application Firewall is protecting the target and identify the vendor. |
| 6 | Run `dnsrecon` | Enumerate DNS records (A, AAAA, MX, NS, TXT, SOA, SRV, etc.). |

---

## 3. Deliverables

- [x] This `README.md` report documenting the methodology, tools and findings.
- [x] Screenshot evidence for each of the six tasks:

| # | Evidence Name | Tool |
|---|---------------|------|
| 1 | `WHOIS-TOOL-RESULT` | whois |
| 2 | `WHATWEB-TOOL-RESULT` | whatweb |
| 3 | `NSLOOKUP-TOOL-RESULT` | nslookup |
| 4 | `CURL-TOOL-RESULT` | curl |
| 5 | `WAFW00F-TOOL-RESULT` | wafw00f |
| 6 | `DNSRECON-TOOL-RESULT` | dnsrecon |

- [x] Tool definitions explained from an attacker's perspective.
- [x] Disclaimer, conclusion and references.

---

## 4. Tools Used

| # | Tool | Category | Purpose | Type of Recon |
|---|------|----------|---------|---------------|
| 1 | **Kali Linux** | Operating System / Platform | Penetration-testing distribution that ships with all tools below. | – |
| 2 | **whois** | Domain intelligence | Retrieves domain registration and ownership data. | Passive |
| 3 | **whatweb** | Web fingerprinting | Identifies web technologies, CMS, server and plugins. | Active |
| 4 | **nslookup** | DNS resolution | Resolves a domain name to IP address(es) and queries DNS records. | Passive / Active |
| 5 | **curl** (`-I`) | HTTP client | Fetches HTTP response headers from the web server. | Active |
| 6 | **wafw00f** | WAF detection | Detects and fingerprints Web Application Firewalls. | Active |
| 7 | **dnsrecon** | DNS enumeration | Enumerates DNS records, zone transfers, brute-forces subdomains. | Active |

---

## 5. Tool Definitions, Attacker Usage & Evidence

---

### 5.1 whois

**Definition:**
`whois` is a command-line client for the WHOIS protocol (RFC 3912). It queries public registration databases maintained by registries and registrars and returns information about a domain name or IP block.

**How attackers use it:**
- Identify the **registrar**, **registrant organisation**, and sometimes names, emails and phone numbers of administrative/technical contacts, which are useful for **phishing and social engineering**.
- Discover the **name servers** in use, which guides later DNS enumeration.
- Check **creation, update and expiry dates**. Expired or soon-to-expire domains may be hijacked, and very new domains help attackers judge how mature the target's infrastructure is.
- Find **related domains** registered by the same owner to widen the attack surface.
- Identify IP ranges and ASN ownership via WHOIS on IP addresses.

**Command used:**
```bash
whois networkwalks.com
```

**Evidence – WHOIS-TOOL-RESULT:**

![WHOIS-TOOL-RESULT](Evidences-and-POCse/WHOIS-TOOL-RESULT.png)

**Key observations:**
- Registrar: `<fill in>`
- Creation / expiry date: `<fill in>`
- Name servers: `<fill in>`
- Registrant privacy / redaction: `<fill in>`

**Defensive note:** Enable WHOIS privacy protection and use role-based email addresses rather than personal ones.

---
