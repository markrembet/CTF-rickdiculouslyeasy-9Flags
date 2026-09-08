# CTF - VM RickdiculouslyEasy 9 Flags

**Professional Security Assessment Report**  

[![Flags](https://img.shields.io/badge/Flags-9%2F9-success)](./report/)
[![Points](https://img.shields.io/badge/Points-130%2F130-blue)](./report/)
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green)](https://www.vulnhub.com/)
[![Platform](https://img.shields.io/badge/Platform-VulnHub-orange)](https://www.vulnhub.com/)

---

## Overview

This repository contains a professional write-up and security assessment report of the **RickdiculouslyEasy** virtual machine from VulnHub.

The machine is a beginner-level *boot-to-root* CTF themed around *Rick and Morty*. The goal was to collect all flags (total **130 points**) and obtain root access through a complete penetration testing methodology:

**Reconnaissance → Scanning → Enumeration → Exploitation → Privilege Escalation**

| Item              | Detail                          |
|-------------------|---------------------------------|
| **Author**        | Mark Delano Rembet              |
| **Target**        | RickdiculouslyEasy (VulnHub)    |
| **OS**            | Fedora Server                   |
| **Total Flags**   | 9 / 9                           |
| **Total Points**  | 130 / 130                       |
| **Final Access**  | Root                            |

---

## Tools Used

| Tool              | Purpose                                      |
|-------------------|----------------------------------------------|
| Nmap              | Port scanning, service & version detection   |
| Hydra             | Password brute-force (FTP & SSH)             |
| Dirsearch         | Web directory brute-forcing                  |
| Netcat            | Interaction with non-standard services       |
| FTP Client        | Anonymous FTP enumeration                    |
| SSH Client + SCP  | Remote access & data exfiltration            |
| Python 3          | Custom wordlist generation                   |
| Strings / Unzip   | File analysis & protected archive extraction |

---

## Flag Summary

| # | Flag Name                          | Points | Location / Method                          |
|---|------------------------------------|--------|--------------------------------------------|
| 1 | TheyFoundMyBackDoorMorty           | 10     | Nmap banner (port 13337)                   |
| 2 | Whoa this is unexpected            | 10     | Anonymous FTP (`FLAG.txt`)                 |
| 3 | Yeah d- just don't do it.          | 10     | `/passwords/` (web directory listing)      |
| 4 | Get off the high road Summer!      | 10     | SSH as Summer (Command Injection → winter) |
| 5 | There is no Zeus, in your face     | 10     | Port 9090 (Cockpit – no authentication)    |
| 6 | Flip the pickle Morty!             | 10     | Bind shell on port 60000 (Netcat)          |
| 7 | 131333                             | 20     | `/home/Morty` (strings + unzip)            |
| 8 | And Awwwaaaaayyyy we Go!           | 20     | Binary `safe` (parameter 131333)           |
| 9 | Ionic Defibrillator                | 30     | `/root` (Privilege Escalation via sudo)    |

**Total: 130 Points**

---

## Methodology Highlights

1. **Reconnaissance**  
   Full port scan with Nmap (`-sC -p- -A`) revealed multiple open ports including non-standard services.

2. **Enumeration**  
   - Anonymous FTP access  
   - Web directory discovery (`/passwords/`, `robots.txt`)  
   - OS Command Injection via `tracertool.cgi`

3. **Exploitation**  
   - Credential discovery from HTML source and steganography  
   - Custom wordlist generation based on password hints  
   - SSH access on non-standard port (22222)

4. **Privilege Escalation**  
   Weak sudo configuration allowed escalation from `RickSanchez` to `root`.

---

## Full Report

The complete professional report (English version with screenshots) is available here:

**[Download PDF Report (English)](./report/Security_Assessment_Report_RickdiculouslyEasy_EN.pdf)**

> Also available in Indonesian:  
> [Laporan Pengujian Keamanan (ID)](./report/Laporan_Pengujian_Keamanan_RickdiculouslyEasy_ID.pdf)

The report includes:
- Detailed step-by-step methodology
- Key screenshots from the original assessment
- Tool analysis
- Challenges & solutions
- Security recommendations

---

## Repository Structure

```text
.
├── README.md
└── reports/
    ├── Security_Assessment_Report_RickdiculouslyEasyEN.pdf   # English (recommended)
    └── Laporan_Pengujian_Keamanan_RickdiculouslyEasy.pdf      # Indonesian
```

---

## Disclaimer

This write-up and report were created **for educational purposes only** as part of a Certified Ethical Hacker (CEH) training.

- All testing was performed in a controlled lab environment (VulnHub).
- Do **not** use any techniques described here against systems you do not own or have explicit permission to test.
- The author is not responsible for any misuse of the information contained in this repository.

---

## Author

**Mark Delano Rembet**  

---

*Happy Hacking & Keep Learning!*
