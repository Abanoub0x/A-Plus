# 🖥️ CompTIA A+ Knowledge Summary

This repo contains my **summarized notes** while studying for the **CompTIA A+** exam.  
It’s a quick reference and a portfolio of concepts I’ve learned and practiced.

---

## 📚 Contents
- 🖥️ [Hardware & BIOS/UEFI](#️-hardware--biosuefi)  
- ⚙️ [Windows Basics](#️-windows-basics)  
- 🗂️ [System Folders & Architecture](#️-system-folders--architecture)  
- 💻 [Operating Systems & Administration](#-operating-systems--administration)  
- 🌍 [Environment Variables](#-environment-variables)  
- 🌐 [Networking & Remote Access](#-networking--remote-access)  
- 🔐 [Security, Threats & Malware](#-security-threats--malware)  
- 🛠️ [Troubleshooting & Backup](#-troubleshooting--backup)  
- ☁️ [Virtualization, Cloud & Enterprise Tools](#️-virtualization-cloud--enterprise-tools)  
- 🧩 [How Firmware, Drivers & OS Work Together](#-how-firmware-drivers--os-work-together)  

---

## 🖥️ Hardware & BIOS/UEFI
- Installing & troubleshooting PCs, mobile devices, peripherals, CPUs, RAM, GPUs, and storage.  
- BIOS vs UEFI: startup process, Secure Boot, GPT vs MBR, partition limits.  
- Key system folders:  
  - `C:\Program Files` (64-bit apps)  
  - `C:\Program Files (x86)` (32-bit apps)  
  - `C:\Windows\System32` (64-bit system files)  
  - `C:\Windows\SysWOW64` (32-bit compatibility layer)  
  - `C:\ProgramData` (hidden, machine-wide app data)  
  - `C:\Users\<name>` (user profiles)

---

## ⚙️ Windows Basics
- **OS Versions**: Windows 7/8/10/11 (features, servicing, UAC defaults, security baselines).  
- **File Systems**: FAT32, exFAT, NTFS, ext4 (Linux), APFS (Apple).  
- **Safe Boot Options**: Safe Mode, Safe Mode w/ Networking, Safe Mode w/ Command Prompt.  
- **Core utilities**:  
  - `msconfig`  
  - `taskmgr`  
  - `services.msc`  
  - `regedit`  
  - `diskmgmt.msc`  
  - `compmgmt.msc`

---

## 🗂️ System Folders & Architecture
- `System32` → 64-bit binaries on 64-bit OS.  
- `SysWOW64` → 32-bit binaries on 64-bit OS (Windows-on-Windows).  
- `ProgramData` → machine-wide application data.  
- `AppData` (`Roaming`, `Local`) → user-specific application data.  
- **NTFS features**: permissions, inheritance, compression, encryption (EFS), **Alternate Data Streams (ADS)**.

---

## 💻 Operating Systems & Administration
- Installing and configuring Windows, Linux, and mobile OS.  
- Administration tools:  
  - **MMC Snap-ins**: Event Viewer, Services, Local Users & Groups, Device Manager  
  - **Disk Management**: MBR vs GPT  
  - **Task Scheduler**: run tasks by event/time/startup  
  - **Windows Firewall w/ Advanced Security**: inbound/outbound rules, allow/block apps  
  - **Control Panel/Settings**: accounts, BitLocker, Region, Features  
- **Accounts & Services**:  
  - Local, Microsoft, and domain (AD) accounts  
  - Built-in service accounts: LocalSystem, LocalService, NetworkService  
  - Services vs processes, start types (Auto/Delayed/Manual/Disabled)  
- **SIDs (Security Identifiers)**:  
  - Format: `S-1-5-21-<domainID>-<rid>`  
  - Used by Windows for user, group, and security object identity  
- **Automation**:  
  - `schtasks`, PowerShell `Register-ScheduledTask`  
  - WMI/CIM via PowerShell (`Get-CimInstance`)

---

## 🌍 Environment Variables
- **Scopes**: process/session, user, system (admin)  
- **Common variables**:  
  - `%PATH%` → executable lookup  
  - `%TEMP%`, `%TMP%` → temp files  
  - `%USERPROFILE%` → user directory  
  - `%APPDATA%`, `%LOCALAPPDATA%` → application data  
  - `%PROGRAMFILES%`, `%SYSTEMROOT%`  
- **Examples**:
  ```cmd
  echo %PATH%
  set MYVAR=hello
  setx MYVAR "hello"
  setx PATH "%PATH%;C:\Tools"

## 🌐 Networking & Remote Access
- **Core Networking**: IP addressing (IPv4/IPv6), DNS, DHCP  
- **Ports & Protocols**:  
  - FTP (21)  
  - SSH (22)  
  - RDP (3389)  
  - SMB (445)  
- **Authentication & Access Control**: RADIUS, TACACS+, Kerberos, AAA  
- **Remote Access**: RDP, VPNs, SSH  
- **Troubleshooting Tools**: ping, ipconfig, tracert, netstat

---

## 🔐 Security, Threats & Malware
- **CIA Triad**: Confidentiality, Integrity, Availability  
- **Encryption & Access Control**: BitLocker, EFS, DRM  
- **Security Tools**: firewalls, IDS/IPS, sandboxing, test environments  
- **Malware Types**:  
  - viruses  
  - worms  
  - trojans  
  - ransomware  
  - spyware  
  - adware  
  - rootkits  
  - keyloggers  
  - botnets  
- **Social Engineering**:  
  - phishing  
  - spear-phishing  
  - smishing  
  - vishing  
  - pretexting  
  - impersonation  
  - tailgating  
  - baiting  
- **Indicators of Compromise**: unusual CPU/network usage, crashes, slowdowns  
- **Mobile Security**: APKs, firmware, rooting basics, secure device management

---

## 🛠️ Troubleshooting & Backup
- **Diagnose Issues**: RAM, CPU, GPU, drivers, services, firewalls, malware  
- **Tools**: Safe Mode, `sfc`, `chkdsk`, Event Viewer  
- **Backup Strategies**: full, incremental, differential, snapshots, cloud  
- **Disaster Recovery**: restoring system & data

---

## ☁️ Virtualization, Cloud & Enterprise Tools
- **Virtual Machines & Hypervisors**: Type 1 vs Type 2  
- **Cloud Service Models**:  
  - IaaS  
  - PaaS  
  - SaaS  
- **Remote Monitoring & Management (RMM)** tools  
- **Ticketing Systems**: workflows and IT support  
- **Enterprise Sysadmin Basics**

---

## 🧩 How Firmware, Drivers & OS Work Together
- **Firmware (BIOS/UEFI)**: initializes hardware, passes control to bootloader  
- **Drivers**: translators between OS and hardware  
- **Operating System**: manages processes, memory, hardware, and provides APIs for apps

