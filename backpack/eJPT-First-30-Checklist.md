# eJPT Exam — First 30 Minutes

## 0. Setup (2 min)

- [ ] Open index.html on local machine (flash drive or file://)
- [ ] Open AI chat, paste exam prompt
- [ ] Notepad or text editor open for logging: IPs, creds, flags, answers

## 1. Read the Letter of Engagement (3 min)

- [ ] Note the target network range (CIDR)
- [ ] Note any specific hostnames, domains, or IPs called out
- [ ] Note scope boundaries — what is in / out of scope
- [ ] Note any credentials provided (check carefully, easy to miss)

## 2. Host Discovery (3 min)

```
fping -a -g [CIDR] 2>/dev/null > hosts.txt
cat hosts.txt
```

- [ ] Count live hosts — this is your target list for the entire exam
- [ ] If hosts seem low, try: `nmap -sn [CIDR]` as a second pass

## 3. Initial Scan — All Hosts (5 min)

```
nmap -sS -sV -sC --top-ports 1000 -T4 -oN quick.txt -iL hosts.txt
```

- [ ] While this runs, start reading the 35 questions
- [ ] Flag which questions are D4 compliance (answer those from memory/notes immediately)

## 4. Triage Scan Results (5 min)

For each host, note in your log:

```
[IP] — [OS guess] — [open ports: services]
```

Flag instant wins:
- [ ] FTP 21 — try `anonymous` login
- [ ] SMB 445 — try `enum4linux -a`, null session, smbclient -N
- [ ] HTTP 80/443/8080 — open in browser, check /robots.txt
- [ ] SSH 22 — hold for cred spray later
- [ ] MySQL 3306 — try `root` with blank password
- [ ] MSSQL 1433 — try `sa` with blank password
- [ ] WinRM 5985 — hold for cred spray later
- [ ] RDP 3389 — hold for cred spray later
- [ ] Anything vsftpd 2.3.4, SMBv1, Tomcat, Rejetto, libssh 0.6-0.8 → exploit immediately

## 5. Full Port Scan on Key Targets (background, 5 min)

```
nmap -sS -sV -p- -T4 -oN full_[IP].txt [IP]
```

- [ ] Run on the 2–3 most interesting hosts while you work on quick wins
- [ ] Also run UDP top 50 on at least one host:

```
nmap -sU --top-ports 50 -T4 -oN udp.txt [IP]
```

## 6. Start Exploiting (remaining time)

Work host by host. For each:

1. **Enumerate** — service-specific enum (SMB users/shares, HTTP dirs, SQL databases)
2. **Exploit** — match version to known exploit (searchsploit, MSF search)
3. **Post-exploit** — whoami, sysinfo, hashdump, /etc/shadow, flag hunt
4. **Pivot check** — second NIC? `/etc/hosts`? `arp -a`? → autoroute if yes
5. **Cred spray** — try every found credential on every host and service
6. **Log** — record every flag, credential, and answer as you go

## Ongoing Habits

- [ ] Every time you find a credential, try it on EVERY host (SSH, SMB, RDP, WinRM, FTP, web logins)
- [ ] Every time you get a shell, check for second NICs and /etc/hosts before moving on
- [ ] Answer questions as you find evidence — don't save them all for the end
- [ ] If stuck for 15+ minutes on one host, move to another and come back
