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

### Exploitation Results

After identifying the FTP service running vsftpd 2.3.4, I used the Metasploit Framework to test the known backdoor vulnerability in my isolated Metasploitable 2 laboratory environment.

The exploitation attempt successfully established shell access to the deliberately vulnerable target system.

This exercise demonstrated how vulnerable network services can expose systems to unauthorized remote access.

**Evidence:** A screenshot of the successful Metasploit session has not yet been added to this repository.

**Recorded lab output:**

```text
uid=0(root)
```


---




### 🔍 Network Connectivity Test — Ping

Verified network connectivity between Kali Linux and the Metasploitable 2 target using ICMP ping. The target responded successfully with no packet loss.

![Ping Test](https://github.com/user-attachments/assets/2505d0e9-66d4-48e8-94e4-ef28732fa837)

---

### 🔍 Nmap Service Enumeration Results
The Nmap scan identified multiple open ports and running services, including FTP running vsftpd 2.3.4. These findings helped identify potential security weaknesses for further investigation.

![Nmap Service Enumeration](https://github.com/user-attachments/assets/dde8b771-8aa7-44e3-a29d-3f3fab8d92f0)

## Security Findings and Remediation

**Finding:** The Metasploitable 2 target exposed an FTP service reporting vsftpd 2.3.4, a version associated with a known backdoor vulnerability.

**Security Impact:** A compromised FTP service can potentially allow unauthorized remote access and expose systems to further compromise.

**Recommended Remediation:**

* Replace vulnerable FTP software with a supported, secure version.
* Disable unnecessary services and close unused network ports.
* Restrict network access using appropriate firewall rules.
* Monitor suspicious FTP connections and unexpected shell activity.
* Conduct regular vulnerability assessments and patch-management reviews.

## Defensive Security Perspective

From a SOC Analyst perspective, this lab demonstrates the importance of monitoring exposed network services and identifying suspicious activity.

Potential detection opportunities include unusual FTP connections, unexpected shell activity, intrusion detection system alerts, and SIEM correlation of relevant security events.

## Lessons Learned

This laboratory strengthened my practical understanding of network enumeration, vulnerability identification, exploitation validation, risk assessment, and remediation planning.

All testing was performed against a deliberately vulnerable virtual machine in an isolated laboratory environment.
