# PENETRATION-TESTING-REPORT
Practical cybersecurity lab work featuring automated reconnaissance, web server fingerprinting, WAD detection, and local LAN network mapping.
# Penetration Testing Report: Footprinting & Network Scanning

## Overview
This repository contains my practical submission for **Week 2** of the Cybersecurity & Ethical Hacking internship program at **Networkwalks** (Batch: B084-Networkwalks). 

The project documents two core reconnaissance phases:
1. **Footprinting & Reconnaissance (W2-PM1):** Information gathering against the target domain `networkwalks.com` using multiple Kali Linux tools.
2. **Network Discovery & Scanning (W2-PM5):** Scanning a local network using Zenmap (Nmap GUI) to discover active hosts, map IP/MAC addresses, and generate a network topology.

---

## Author & Metadata
* **Pentester:** Zobida Mohammad
* **Program/Batch:** B084-Networkwalks
* **Date:** Nov 13, 2026
* **Modules Completed:** 
  * W2-PM1 (Multiple Kali Tools)
  * W2-PM5 (Zenmap Scanning)
* **Target / Permission:** `networkwalks.com` (Written permission secured) & Personal local LAN network

---

## Tools Used

| Tool | Purpose |
| :--- | :--- |
| **Kali Linux & Windows** | Operating systems used for reconnaissance and scanning activities |
| **WHOIS** | Find domain registration details (owner, dates, name servers) |
| **WhatWeb** | Fingerprint web technologies (server, CMS, plugins, IP) |
| **Nslookup** | Resolve the domain name to its IP address using DNS |
| **Curl (`-I`)** | Read the HTTP response headers of the website |
| **Wafw00f** | Detect whether a Web Application Firewall protects the site |
| **DNSRecon** | Enumerate all DNS records (NS, MX, SPF, TXT, SRV) |
| **Zenmap (Nmap GUI)** | Scan the local subnet to find live hosts, IPs, and MAC addresses |
| **Terminal** | Local IP and MAC address identification (`ip a`) |

---

## Summary of Activities Performed

### 1. Footprinting & Reconnaissance (`networkwalks.com`)
* **WHOIS:** Retrieved domain registrar information (GoDaddy), registration/expiry dates, and name servers (`NS6135.HOSTGATOR.COM`).
* **WhatWeb:** Fingerprinted the target web stack, identifying **Apache**, **WordPress 7.0.4**, and **WP Download Manager 3.3.58**.
* **Nslookup:** Resolved `networkwalks.com` to target IP address `192.232.216.135`.
* **Curl (`-I`):** Inspected HTTP response headers, revealing server details and exposing the WordPress REST API endpoint `/wp-json/`.
* **Wafw00f:** Identified that the website is protected behind a **ModSecurity (SpiderLabs)** Web Application Firewall.
* **DNSRecon:** Enumerated detailed DNS, mail servers, and service records.

### 2. Network Discovery (`Zenmap / Nmap`)
* Configured local subnet targets and performed a **Ping Scan (`-sn`)** to identify active devices on the network.
* Collected IP and MAC addresses of live hosts, verified latency, and documented network topology visuals.

---

## Risk Analysis & Findings

| # | Finding / Risk | Observation | Potential Impact | Risk Level |
| :-: | :--- | :--- | :--- | :--- |
| **1** | Web technology exposed | WhatWeb identified WordPress and WP Download Manager versions | Attackers may use version info to check for known software advisories | Medium |
| **2** | Server IP address visible | Nslookup resolved domain to `192.232.216.135` | Provides the direct network location of the web service | Low |
| **3** | HTTP technical details exposed | Curl returned headers and exposed `/wp-json/` | Assists with technology fingerprinting and enumeration | Low |
| **4** | WAF technology identifiable | Wafw00f identified ModSecurity (SpiderLabs) | Reveals information regarding the web application's security architecture | Low |
| **5** | DNS infrastructure info exposed | DNSRecon mapped DNS, mail, and service records | Helps build a broader infrastructure and target profile | Medium |
| **6** | Active local network hosts | Zenmap scan identified live active hosts on the subnet | Unknown or unauthorized devices may be present on a network | Medium |

*Note: Findings represent reconnaissance observations and information gathering, not exploited vulnerabilities.*

---

## Key Recommendations
1. **Review Public Exposure:** Regularly audit what web technologies, CMS versions, and plugins are publicly visible.
2. **Patch & Update:** Keep CMS platforms, plugins, and web software updated against security advisories.
3. **Tune HTTP Headers:** Inspect HTTP response headers to limit unnecessary technical disclosure.
4. **Monitor WAF Settings:** Keep Web Application Filters (ModSecurity) enabled and properly tuned.
5. **Maintain Authorization:** Always ensure reconnaissance and scanning are strictly restricted to systems with explicit written permission.

---

## Disclaimer
> All activities documented in this project were performed strictly for educational and research purposes on authorized targets or my own local network. Unauthorized scanning or testing against systems without permission is illegal.
