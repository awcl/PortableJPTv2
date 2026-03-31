# PortableJPTv2

Offline eJPTv2 + TryHackMe cheat sheet.

258 entries. 21 calculators. 782 quiz + flashcard questions. Single HTML file. No dependencies.

**[Live](https://awcl.github.io/PortableJPTv2/)** | **[Download](index.html)**

```
wget https://raw.githubusercontent.com/awcl/PortableJPTv2/main/index.html -O index.html
```

```
curl -o index.html https://raw.githubusercontent.com/awcl/PortableJPTv2/main/index.html
```

```
certutil -urlcache -f https://raw.githubusercontent.com/awcl/PortableJPTv2/main/index.html index.html
```

```
iwr -Uri https://raw.githubusercontent.com/awcl/PortableJPTv2/main/index.html -OutFile index.html
```

```
python3 -c "import urllib.request;urllib.request.urlretrieve('https://raw.githubusercontent.com/awcl/PortableJPTv2/main/index.html','index.html')"
```

---

### Home View

| | |
|:--|:--|
| **Ref (49)** | OSI, TCP/UDP, DNS, HTTP, SNMP, SMB, WinRM, pen test phases, exam skills map, CVSS, AV evasion, CVE table, social engineering, host discovery, recon methodology, Windows kernel, IIS/WebDAV, network mapping, exploitation methodology |
| **Recon (9)** | WHOIS, DNS, Sublist3r, theHarvester, Google dorks, wafw00f, OSINT |
| **Scan (20)** | Standard first scan, Nessus, port reference, Nmap (flags, NSE, evasion, output reading), fping, Masscan, db_nmap, Wireshark, TShark |
| **Enum (14)** | MSF search syntax, SMB, HTTP, FTP, SSH, MySQL, MSSQL, SMTP, WinRM, RDP, rsync, enum4linux |
| **Exploit (20)** | PsExec, evil-winrm, EternalBlue, Samba, vsftpd, Tomcat, Shellshock, WebDAV, libssh |
| **Web (16)** | Directory busting, SQLi, sqlmap, LFI, WPScan, XSS, Burp Suite, ZAP, WMAP, webshells |
| **PostEx (23)** | Decision trees, stuck checklist, Meterpreter, Mimikatz, local enum, persistence, clearing tracks |
| **PrivEsc (19)** | LinPEAS/WinPEAS, sudo, SUID, cron, UAC bypass, PrintSpoofer, token impersonation, AlwaysInstallElevated |
| **Pivot (9)** | autoroute step-by-step walkthrough, portfwd, ProxyChains + config, SSH tunneling, Socat relay |
| **Passwd (9)** | Hydra, John, hashcat + rules, Kerberoasting, Pass-the-Hash |
| **Payload (12)** | msfvenom, Netcat, reverse shells, multi/handler, TTY upgrade, Shellter, Socat TLS |
| **Xfer (4)** | Windows/Linux file delivery, NFS mount, SSH key auth |
| **Quick (14)** | Default credentials, wordlists, regex patterns, useful paths, Linux/Windows commands, flag hunting |
| **Comply (8)** | NIST CSF, ISO 27001, PCI DSS, HIPAA, GDPR, GRC, Lynis |
| **Links (11)** | GTFOBins, Exploit-DB, CrackStation, RevShells, HackTricks, SecLists, hexed.it, CyberChef, Binwalk |

### Calculators

| | | | |
|:--|:--|:--|:--|
| Port Lookup | Reverse Shell | Hash Identifier | Nmap Builder |
| Subnet / CIDR Calculator | Hash Crack Builder | Hydra Builder | msfvenom Builder |
| File Transfer | Gobuster Builder | Sweep Builder | enum4linux Builder |
| smbclient Builder | Wordlist Picker | Base64 Codec | URL Codec |
| Chmod Calculator | XOR Encoder | JWT Decoder | Cron Reader |
| Magic Bytes / Hex Lookup | | | |

### Quiz

| Deck | Questions | Exam Weight |
|:--|:--|:--|
| D1 Assessment Methodologies | 145 | 25% |
| D2 Host & Network Pentesting | 177 | 35% |
| D3 Web App Pentesting | 86 | 15% |
| D4 Host & Network Auditing | 124 | 25% |

| Deck | Questions | Notes |
|:--|:--|:--|
| Bonus: Ports & Services | 50 | Port-to-service mapping |
| Bonus: Nmap | 50 | Flags, scan types, output |
| Bonus: Tool Selection | 50 | Which tool for which task |
| Bonus: MSF Modules | 50 | Module path identification |
| Bonus: Hash ID & Cracking | 50 | Prefixes, modes, workflows |

### Flashcards

Same 782 questions in a swipeable playing-card format. Tap to flip, drag to navigate. Portrait and landscape support.

---

Requires JavaScript. 504 KB. Works offline from file:// or USB.

BSD 3-Clause License. For authorized penetration testing and certification prep only.
