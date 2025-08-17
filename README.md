# 🖥️ CompTIA A+ Knowledge Summary

This repo contains my **summarized notes** while studying for the **CompTIA A+** exam.  
It’s a quick reference and a portfolio of concepts I’ve learned and practiced.

---

## 📚 Contents
- ⚙️ [Windows Basics](#️-windows-basics)
- 🗂️ [System Folders & Architecture](#️-system-folders--architecture)
- 🔧 [Operating Systems & Administration](#-operating-systems--administration)
- 🌍 [Environment Variables](#-environment-variables)
- 📡 [Networking & Remote Access](#-networking--remote-access)
- 🔐 [Security, Threats & Hardening](#-security-threats--hardening)
- 🧰 [Troubleshooting & Recovery](#-troubleshooting--recovery)
- ☁️ [Virtualization, Cloud & Enterprise Tools](#️-virtualization-cloud--enterprise-tools)
- 🧩 [How Firmware, Drivers & OS Work Together](#-how-firmware-drivers--os-work-together)
- 📝 [Useful Command References](#-useful-command-references)

---

## ⚙️ Windows Basics
- **OS versions & channels**: core differences across Windows 7/8/10/11 (features, servicing, UAC defaults, security baselines).
- **File systems**: FAT32, exFAT, **NTFS** (permissions, compression, EFS), Linux **ext4**, Apple **APFS** (snapshots).
- **Boot firmware**:
  - **BIOS + MBR** (legacy, 2 TB limit, 4 primary partitions).
  - **UEFI + GPT** (modern, >2 TB, many partitions, Secure Boot, faster startup).
- **Safe boot options**: Safe Mode, Safe Mode w/ Networking, Safe Mode w/ Command Prompt.
- **Core utilities**: `msconfig`, `taskmgr`, `services.msc`, `regedit`, `diskmgmt.msc`, `compmgmt.msc`.

---

## 🗂️ System Folders & Architecture
- `C:\Windows\System32` → 64-bit system files on 64-bit Windows.
- `C:\Windows\SysWOW64` → 32-bit system files/redirector (name is historical).
- `C:\Program Files` (64-bit apps) vs `C:\Program Files (x86)` (32-bit apps).
- `C:\ProgramData` (hidden, machine-wide app data) and `C:\Users\<name>\AppData` (per-user).
- **NTFS features**: permissions (DAC), inheritance, compression, EFS, **Alternate Data Streams (ADS)**.

---

## 🔧 Operating Systems & Administration
- **Install & configure**: Windows, Linux, and mobile OS.
- **Administration tools**:
  - **MMC** snap-ins (Event Viewer, Services, Local Users & Groups, Device Manager via `devmgmt.msc`).
  - **Disk Management** (partitions/volumes, MBR vs GPT).
  - **Task Scheduler** (automation by event/time/startup).
  - **Windows Firewall** with Advanced Security (inbound/outbound, profiles).
  - **Control Panel & Settings** for accounts, network, devices, BitLocker, Region, Optional Features.
- **Accounts & services**:
  - Built-in service accounts: **LocalSystem**, **LocalService**, **NetworkService** (least privilege vs network identity).
  - User accounts: local, Microsoft account, domain (AD) accounts.
  - Services vs processes, start types (Auto/Delayed/Manual/Disabled), service logon accounts.
- **SIDs (Security Identifiers)**:
  - Format: `S-1-5-21-<domainID>-<rid>`. Identify users, groups, and well-known principals.
- **Automation**:
  - **Task Scheduler**: `schtasks` / PowerShell `Register-ScheduledTask`.
  - **WMI/CIM** via PowerShell: query/manage OS, services, hardware (`Get-CimInstance Win32_...`).

---

## 🌍 Environment Variables
**What they are:** Key-value pairs the OS and apps use for configuration and path resolution.

- **Scopes**:
  - **Process/session**: exists only for current shell/app.
  - **User**: persists for the current user.
  - **System**: persists machine-wide (requires admin to edit).

- **Common vars**:
  - `%PATH%` → where Windows looks for executables.
  - `%TEMP%` / `%TMP%` → temp file locations.
  - `%USERPROFILE%` → `C:\Users\<User>`.
  - `%APPDATA%` / `%LOCALAPPDATA%` → roaming/local app data.
  - `%PROGRAMFILES%`, `%PROGRAMFILES(X86)%`, `%SYSTEMROOT%`.

---
## 🌐 Networking & Remote Access  
### Core Networking Concepts  
- **IPv4 vs IPv6**:  
  - IPv4: 32-bit (e.g., `192.168.1.1`), NAT, limited addresses.  
  - IPv6: 128-bit (e.g., `2001:0db8:85a3::8a2e:0370:7334`), no NAT, built-in security.  
- **DHCP (Dynamic Host Configuration Protocol)**:  
  - Assigns IP addresses automatically (UDP port 67/68).  
  - `ipconfig /release` and `ipconfig /renew` to refresh leases.  
- **DNS (Domain Name System)**:  
  - Resolves hostnames to IPs (e.g., `google.com` → `142.250.190.78`).  
  - Uses UDP port 53; troubleshoot with `nslookup` or `dig`.  


### Key Ports & Protocols  
| Port | Protocol | Use Case                     |  
|------|----------|------------------------------|  
| 21   | FTP      | File transfers (unencrypted) |  
| 22   | SSH      | Secure remote shell          |  
| 23   | Telnet   | Unencrypted remote access    |  
| 25   | SMTP     | Email sending                |  
| 53   | DNS      | Domain name resolution       |  
| 80   | HTTP     | Web traffic (unsecured)      |  
| 443  | HTTPS    | Web traffic (encrypted)      |  
| 3389 | RDP      | Remote Desktop Protocol      |  
| 445  | SMB      | File/print sharing (Windows) |  

### Remote Access Technologies  
- **RDP (Remote Desktop Protocol)**:  
  - Windows-native remote GUI access (port 3389).  
  - Requires client (`mstsc.exe`) and host enablement.  
- **VPN (Virtual Private Network)**:  
  - Encrypted tunnel for secure remote access (e.g., IPSec, OpenVPN).  
- **SSH (Secure Shell)**:  
  - Encrypted command-line access (Linux/Windows via OpenSSH).  

### Troubleshooting Commands  
```cmd
ping google.com           # Test connectivity  
tracert google.com        # Trace network path  
netstat -ano              # List active connections + PIDs  
nslookup google.com       # DNS lookup  
ipconfig /all             # Detailed network config  



## 🔐 Security, Threats & Malware  

### Core Security Principles (CIA Triad)  
- **Confidentiality**:  
  - Encryption (AES-256, RSA)  
  - Access controls (RBAC, least privilege)  
- **Integrity**:  
  - Hashing (SHA-256, MD5* [deprecated])  
  - Digital signatures (PKI, certificates)  
- **Availability**:  
  - Redundancy (RAID, failover clusters)  
  - DDoS mitigation (cloudflare, rate limiting)  

---

### 🚨 Common Threats & Attacks  

#### Malware Types  
| Type          | Description                          | Example                |  
|---------------|--------------------------------------|------------------------|  
| **Virus**     | Attaches to files; requires execution | ILOVEYOU (2000)       |  
| **Worm**      | Self-replicating; spreads via networks | WannaCry (2017)       |  
| **Trojan**    | Masquerades as legitimate software   | Emotet banking Trojan |  
| **Ransomware**| Encrypts files for ransom            | Locky, REvil          |  
| **Spyware**   | Steals data (keystrokes, screenshots)| Pegasus (mobile)      |  
| **Rootkit**   | Gains kernel-level access            | Stuxnet               |  

#### Social Engineering Attacks  
| Type            | Method                              | Defense                     |  
|-----------------|-------------------------------------|-----------------------------|  
| **Phishing**    | Fake emails/websites                | Verify sender URLs          |  
| **Spear Phishing** | Targeted phishing (e.g., CFO fraud) | Multi-factor authentication |  
| **Vishing**     | Voice call scams ("IT support")     | Hang up & verify            |  
| **Tailgating**  | Unauthorized physical access        | Badge readers               |  
| **Quid Pro Quo**| "Free service" for credentials      | Employee training           |  

---

### 🛡️ Security Tools & Mitigations  

#### Encryption Technologies  
- **Full-Disk Encryption**: BitLocker (Windows), FileVault (macOS), LUKS (Linux)  
- **File-Level Encryption**: EFS (Windows), GPG (cross-platform)  
- **VPN Protocols**: IPSec, OpenVPN, WireGuard  

#### Access Control  
- **RBAC (Role-Based Access Control)**: Assign permissions by job function  
- **MAC (Mandatory Access Control)**: Used in military/government (SELinux)  
- **Password Policies**:  
  - Minimum length (12+ chars)  
  - Complexity requirements  
  - Regular rotation (90 days)  

#### Defense Tools  
| Tool Category       | Examples                          | Purpose                          |  
|---------------------|-----------------------------------|----------------------------------|  
| **Firewalls**       | Windows Defender Firewall, pfSense | Block unauthorized traffic       |  
| **IDS/IPS**         | Snort, Suricata                   | Detect/prevent intrusions        |  
| **SIEM**           | Splunk, Wazuh                     | Centralized threat monitoring    |  
| **Sandboxing**      | Cuckoo Sandbox, Windows Sandbox   | Analyze suspicious files safely  |  

---

### 🚦 Indicators of Compromise (IoCs)  
- **System Symptoms**:  
  - Unexpected CPU/RAM usage spikes  
  - Unusual network traffic (e.g., beaconing)  
  - Disabled security tools (firewall/AV)  
- **Log Red Flags**:  
  - Multiple failed login attempts  
  - New admin accounts (`net user`)  
  - Unusual process executions (`tasklist`)  

---

### 📜 Compliance & Best Practices  
- **Regular Updates**: Patch OS/apps (WSUS, `apt upgrade`)  
- **Backup 3-2-1 Rule**:  
  - 3 copies of data  
  - 2 different media types  
  - 1 offsite copy  
- **Mobile Device Management (MDM)**:  
  - Remote wipe (Intune, Jamf)  
  - Containerization (separate work/personal data)  
