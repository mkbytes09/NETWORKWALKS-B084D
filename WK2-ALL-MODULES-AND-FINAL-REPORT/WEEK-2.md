# Week 2 Project | Footprinting & Network Scanning Phases
## NetworkWalks Cybersecurity Program — Batch NETWORKWALKS-B084D

> **Pentester:** Muhammad Kamil
> **Program / Batch:** NETWORKWALKS-B084D
> **Week:** 2 — Footprinting, Reconnaissance & Network Scanning

---

## Overview

This repository folder contains all five project modules completed during Week 2 of the NetworkWalks cybersecurity training program. Together, the modules walk through the **Footprinting & Reconnaissance** and **Network Scanning** phases of the penetration-testing lifecycle, moving from external, internet-facing OSINT techniques through to internal network discovery.

Each module lives in its own subdirectory with a dedicated `README.md` covering that module's introduction, objectives, deliverables, tools, tool definitions, attacker-usage context, disclaimer, conclusion, and references. A consolidated final report tying all five modules together is also included at the root of this Week 2 folder.

---

## Repository Structure

| # | Subdirectory | Topic |
|---|---------------|-------|
| 1 | `WK2-PM1-FOOTPRINT-WITH-MULTIPLE-TOOLS/` | Footprinting & Reconnaissance with Multiple Kali Tools |
| 2 | `WK2-PM2-FOOTPRINT-WITH-GHDB/` | Footprinting with the Google Hacking Database (GHDB) |
| 3 | `WK2-PM3-FOOTPRINT-WITH-MALTEGO/` | Footprinting & Email Harvesting using Maltego |
| 4 | `WK2-PM4-FOOTPRINT-WITH-theHarvester/` | Footprinting with theHarvester |
| 5 | `WK2-PM5-NETWORK-SCANNING-WITH-ZENMAP/` | Network Scanning with Zenmap |
| — | `Footprinting-Network-Scanning-Phases-Report.docx` | Final consolidated report covering all five modules |

---

## Module Details

### 1. `WK2-PM1-FOOTPRINT-WITH-MULTIPLE-TOOLS/`

**Footprinting & Reconnaissance with Multiple Kali Tools**

- **Target:** networkwalks.com (written permission secured)
- **Tools used:** `whois`, `whatweb`, `nslookup`, `curl -I`, `wafw00f`, `dnsrecon`
- **Summary:** established a baseline external footprint for one authorized target — domain registration details, web technology stack, DNS resolution, HTTP response headers, WAF presence, and a full DNS record enumeration — using six complementary command-line tools, each run individually and documented with its own evidence.
- **Full details:** see `WK2-PM1-FOOTPRINT-WITH-MULTIPLE-TOOLS/README.md`

### 2. `WK2-PM2-FOOTPRINT-WITH-GHDB/`

**Footprinting with the Google Hacking Database (GHDB)**

- **Target:** internet-wide, via public search-engine indexing
- **Tools used:** Google Search (advanced operators), Google Hacking Database (GHDB)
- **Summary:** used Google Dorking and the GHDB's categorized query library to demonstrate how misconfigured or unintentionally exposed systems and files become discoverable through a search engine alone, without any direct interaction with the systems found.
- **Full details:** see `WK2-PM2-FOOTPRINT-WITH-GHDB/README.md`

### 3. `WK2-PM3-FOOTPRINT-WITH-MALTEGO/`

**Footprinting & Email Harvesting using Maltego**

- **Target:** a target organization's domain (written permission secured)
- **Tools used:** Maltego (Community Edition)
- **Summary:** set up and verified a Maltego account, then ran domain-to-email Transforms to map an organization's publicly discoverable email footprint using graphical link analysis.
- **Full details:** see `WK2-PM3-FOOTPRINT-WITH-MALTEGO/README.md`

### 4. `WK2-PM4-FOOTPRINT-WITH-theHarvester/`

**Footprinting with theHarvester**

- **Target:** microsoft.com
- **Tools used:** theHarvester
- **Summary:** enumerated email addresses and subdomains in two passes — a single-source run (Baidu, result limit 1000) and an all-sources run (result limit 50) — to compare how source breadth and result limits each affect the completeness of OSINT coverage.
- **Full details:** see `WK2-PM4-FOOTPRINT-WITH-theHarvester/README.md`

### 5. `WK2-PM5-NETWORK-SCANNING-WITH-ZENMAP/`

**Network Scanning with Zenmap**

- **Target:** own local LAN subnet (`10.0.0.0/24`)
- **Tools used:** Zenmap (Nmap GUI), Nmap
- **Summary:** shifted from external reconnaissance to internal network discovery — identifying live hosts, their IP and MAC addresses, and visualizing the subnet's topology, then exporting the topology graphic for documentation.
- **Full details:** see `WK2-PM5-NETWORK-SCANNING-WITH-ZENMAP/README.md`

---

## Final Consolidated Report

`Footprinting-Network-Scanning-Phases-Report.docx` ties all five modules above into a single formal report, structured as:

1. Liability Disclaimer
2. Introduction
3. Tools Used
4. Activities Performed (4.1 – 4.5, one subsection per module)
5. Recommendations
6. Conclusion
7. Evidence Collection

This is the primary deliverable for submission; the five subdirectories above hold the underlying, module-by-module detail it was built from.

---

## Disclaimer

All activities in this Week 2 project were performed for **educational purposes only**, under the NetworkWalks training program. External-target activities (Modules 1–4) were conducted against networkwalks.com and other domains with written permission or using passive, non-intrusive OSINT techniques; internal network scanning (Module 5) was performed exclusively against the author's own LAN. Each module's own `README.md` contains the full, module-specific disclaimer relevant to its techniques and target scope.
