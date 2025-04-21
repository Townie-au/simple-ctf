# simple-ctf
tryhackme simple-ctf walkthrough
# TryHackMe - Simple CTF Walkthrough

**Date completed:21st April 2025  
**Level:** Beginner  
**Focus:** Linux enumeration, password cracking, privilege escalation

---

## 🔎 Overview

Simple CTF is a beginner-friendly room designed to practice reconnaissance, file discovery, and privilege escalation. You’ll gain experience with Nmap, Gobuster, and navigating Linux systems to uncover flags.

---

## 🧰 Tools Used

- Nmap  
- Gobuster  
- Netcat  
- Hydra (optional)  
- Linux CLI

---

## 🔍 Enumeration

### Nmap

```bash
nmap -sC -sV -oN nmap.txt [TARGET_IP]
Open ports:

22/tcp SSH

80/tcp HTTP

Web Recon
Used Gobuster to brute-force directories:

bash
Copy
Edit
gobuster dir -u http://[TARGET_IP] -w /usr/share/wordlists/dirb/common.txt
Discovered:

/robots.txt – contains possible credentials

/simple – contains CMS or login portal

💥 Exploitation
Used found credentials to SSH into the system.

Looked for user.txt:

bash
Copy
Edit
cat /home/[user]/user.txt
Enumerated system for privesc opportunities using:

bash
Copy
Edit
find / -perm -4000 -type f 2>/dev/null
Escalated to root and retrieved root.txt.

🏁 Flags (Redacted)
user.txt: THM{**********}

root.txt: THM{**********}

🧠 What I Learned
Don't overlook robots.txt — it may leak critical info

Directory brute-forcing is essential

SUID files and sudo configs are often privesc leads
