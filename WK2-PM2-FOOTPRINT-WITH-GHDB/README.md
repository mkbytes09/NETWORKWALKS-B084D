<div align="center">
  
**WEEK 2 | PROJECT MODULE 2**
  
# FOOTPRINTING WITH GOOGLE HACKING DATABASE (GHDB)

</div>


> **Technique:** Google Dorking / GHDB-based OSINT
> **Platform:** Kali Linux + Web Browser
> **Findings file:** `Findings-W2-M2.docx`
> **Author:** `Muhammad Kamil`
> **Date:** `12-11-2026`

---

## Table of Contents

1. [Reconnaissance Introduction](#1-reconnaissance-introduction)
2. [Task Objectives](#2-task-objectives)
3. [Deliverables](#3-deliverables)
4. [Tools Used](#4-tools-used)
5. [Technique Definitions, Attacker Usage & Findings](#5-technique-definitions-attacker-usage--findings)
   - [5.1 Google Dorking (Advanced Search Operators)](#51-google-dorking-advanced-search-operators)
   - [5.2 Google Hacking Database (GHDB)](#52-google-hacking-database-ghdb)
6. [Disclaimer](#6-disclaimer)
7. [Conclusion](#7-conclusion)
8. [References](#8-references)

---

## 1. Reconnaissance Introduction

**Google Dorking**, also called **Google Hacking**, is a passive OSINT (Open Source Intelligence) technique that uses advanced search-engine operators to surface information, files, and devices that were never meant to be publicly discoverable. Instead of scanning a target directly, the "attacker" queries a search engine's index — meaning the activity leaves no trace on the target's own systems, because the search engine, not the tester, performed the crawl.

The **Google Hacking Database (GHDB)**, maintained by Exploit-DB (Offensive Security), is a curated, categorized archive of these search queries ("dorks"). It organizes known-effective dorks into categories such as exposed login portals, sensitive files, error messages, vulnerable servers, and **exposed IoT/webcam devices**.

This module differs from Module 1 in an important way: Module 1's tools (`whois`, `whatweb`, `nslookup`, `curl`, `wafw00f`, `dnsrecon`) were pointed at **one specific, written-permitted target**. Google Dorking, by design, searches the **entire indexed internet**, which means results can surface systems and files belonging to **unrelated third parties** who never gave any testing authorization. That distinction is addressed directly in the [Disclaimer](#6-disclaimer).

---

## 2. Task Objectives

| # | Task | Objective |
|---|------|-----------|
| 1 | Identify 10 live, internet-exposed security camera interfaces | Demonstrate how misconfigured IoT/CCTV devices become indexed and discoverable via search-engine dorking, and record the dork used for each result. |
| 2 | Identify 10 listings of downloadable mathematics eBooks (PDF) | Demonstrate how `filetype:` / directory-listing dorks surface open, unauthenticated file repositories. |

---

## 3. Deliverables

- [x] This `README.md` — methodology, tool/technique explanation, and attacker-perspective analysis.
- [x] `Findings-W2-M2.docx` — the two results tables (10 camera entries, 10 eBook listing entries), each with the dork used and the link found. **This file holds all the actual results; it is referenced below rather than reproduced inline.**

| Table | Contents | Location |
|-------|----------|----------|
| Table 1 | 10x exposed security camera links + dork used for each | `Findings-W2-M2.docx`, Section 1 |
| Table 2 | 10x downloadable mathematics eBook (PDF) listings + dork used for each | `Findings-W2-M2.docx`, Section 2 |

> **Handling note:** Unlike the Module 1 evidence screenshots, the contents of `Findings-W2-M2.docx` should **not** be published to a public portfolio, GitHub repo, or social media. It contains live links to third-party devices and file repositories that are outside the written-permission scope of this course. Keep it in your private submission folder for your instructor only. See [Section 6](#6-disclaimer).

---

## 4. Tools Used

| # | Tool / Technique | Category | Purpose |
|---|-------------------|----------|---------|
| 1 | **Kali Linux** | Operating System / Platform | Base platform for the exercise. |
| 2 | **Web Browser** | Search client | Used to run dork queries against the search engine. |
| 3 | **Google Search (Advanced Operators)** | Passive OSINT | Core dorking technique: `intitle:`, `inurl:`, `intext:`, `filetype:`, `site:`, combined to narrow results. |
| 4 | **Google Hacking Database (GHDB)** | Dork repository | Curated, categorized library of known-effective dorks maintained by Exploit-DB. |

---

## 5. Technique Definitions, Attacker Usage & Findings

### 5.1 Google Dorking (Advanced Search Operators)

**Definition:**
Google Dorking uses a search engine's own advanced operators to filter results down to very specific, often unintentionally exposed, content. Common operators include:

| Operator | Function |
|----------|----------|
| `intitle:` | Restricts results to pages with a specific word in the `<title>` tag. |
| `inurl:` | Restricts results to pages with a specific string in the URL. |
| `intext:` | Restricts results to pages containing a specific string in the body text. |
| `filetype:` | Restricts results to a specific file extension (e.g. `pdf`, `xls`). |
| `site:` | Restricts results to a specific domain. |

**How attackers use it:**
- **Device discovery:** many IP cameras, DVRs, and industrial control panels ship with default web interfaces whose page titles are predictable (e.g. a generic "Live View" string). Because the device is reachable on the open internet with no authentication wall, search-engine crawlers index it like any other web page — an attacker never has to scan a single IP range, the dork does the discovery for them.
- **Sensitive file discovery:** `filetype:` combined with keywords finds open directory listings and unauthenticated file shares, exposing documents, spreadsheets, configuration files, or (as in this task) PDF eBook repositories that were never meant to be publicly linked.
- **Credential and login-portal discovery:** dorks can surface admin login pages, exposed `.env`/config files, or error pages that leak stack traces and internal file paths.
- **Zero direct contact with the target:** because the query only touches the search engine's index, this phase is almost entirely passive and very hard to detect or attribute.

**Findings:** see `Findings-W2-M2.docx`, Section 1 (cameras) and Section 2 (eBooks), for the full tables of results and the exact dork used for each entry.

---

### 5.2 Google Hacking Database (GHDB)

**Definition:**
The GHDB is a public, categorized archive of dorks submitted and verified by the security research community, hosted by Exploit-DB. Categories include Footholds, Files Containing Juicy Info, Vulnerable Servers, Network or Vulnerability Data, Pages Containing Login Portals, and Various Online Devices (which covers exposed cameras, printers, and other IoT interfaces).

**How attackers use it:**
- **Speeds up reconnaissance:** instead of hand-crafting operators, an attacker can pull pre-built, battle-tested dorks straight from the database for a given category of target.
- **Targets known device classes:** the "Various Online Devices" category specifically catalogs dork patterns that surface camera and DVR web interfaces, letting an attacker search opportunistically for *any* exposed device rather than a chosen one.
- **Low skill barrier:** because the dorks are pre-written and categorized, this technique requires no exploit development or scripting, which is part of why it's commonly abused for voyeurism and unauthorized surveillance browsing, not just penetration testing.
- **Combines with other OSINT:** results are frequently cross-referenced with Shodan/Censys for banner data, or with `whois`/`dnsrecon` findings from Module 1 to attribute an exposed device to an organization.

**Findings:** see `Findings-W2-M2.docx` for the specific GHDB-derived queries used for this exercise.

---

## 6. Disclaimer

This exercise was conducted **for educational purposes as part of an authorized training module**. However, it differs materially from Module 1 and that distinction matters:

- **Scope:** Module 1's tools were aimed at one target under written permission. Google Dorking, by its nature, surfaces **unrelated third-party systems** — cameras, file servers, and documents belonging to individuals and organizations who are **not** part of any authorization agreement for this course. Finding a result via a public search engine does not constitute permission to access, view, interact with, download from, or further probe that result.
- **Live camera feeds:** viewing an exposed camera feed, even briefly and even without "hacking" anything, can implicate privacy, surveillance, voyeurism, and computer-misuse laws in many jurisdictions, regardless of whether the device lacked a password. These laws vary significantly by country and by what the camera shows (private property, individuals, minors, etc.). **No camera feed should be accessed, screen-recorded, downloaded, shared, or interacted with beyond confirming it is reachable.**
- **eBook/PDF listings:** many open directory listings of "free" textbooks are hosting copyrighted material without the rights holder's permission. Locating such a listing for an OSINT exercise is different from downloading, redistributing, or hosting the files yourself, which can carry separate copyright liability.
- **Non-publication:** the completed findings document (`Findings-W2-M2.docx`) must **not** be posted publicly (portfolio, GitHub, LinkedIn, social media), since doing so would broadcast live, unauthorized links to third-party systems and copyrighted content. Keep it in your private course submission only.
- If your course's written-permission agreement does not explicitly address internet-wide dorking exercises like this one, it's worth confirming the scope with your instructor before treating the results as "in scope" the same way Module 1's target was.

The author accepts no responsibility for any use of this report, its methodology, or the referenced findings outside the educational context for which it was produced.

---

## 7. Conclusion

This module showed that reconnaissance doesn't always require touching the target at all: a search engine's own index, combined with a handful of advanced operators, is enough to surface devices and files that their owners likely never intended to expose. The **Google Hacking Database** formalizes this into a repeatable, categorized technique that requires minimal technical skill to use, which is exactly why default-credential IoT devices and open file shares remain such a persistent, low-effort target class for real-world attackers.

The clearest takeaway for defenders is that **"security by obscurity" fails the moment a crawler indexes the page**. Devices and files should never rely on an unlisted URL or a default configuration for protection — authentication, network segmentation (keeping admin interfaces off the public internet), and robots.txt / noindex directives for sensitive paths are the actual controls that prevent this class of exposure.

---

## 8. References

1. Exploit-DB – Google Hacking Database (GHDB): <https://www.exploit-db.com/google-hacking-database>
2. MITRE ATT&CK – Search Open Technical Databases (T1596): <https://attack.mitre.org/techniques/T1596/>
3. MITRE ATT&CK – Reconnaissance (TA0043): <https://attack.mitre.org/tactics/TA0043/>
4. OWASP – Google Hacking / Search Engine Discovery: <https://owasp.org/www-project-web-security-testing-guide/>
5. Google – Refine web searches (official operator documentation): <https://support.google.com/websearch/answer/2466433>
6. NIST SP 800-115 – Technical Guide to Information Security Testing and Assessment: <https://csrc.nist.gov/publications/detail/sp/800-115/final>
