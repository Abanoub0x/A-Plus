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

- **CMD examples**:
  ```cmd
  :: show one
  echo %PATH%

  :: set for current CMD session (temporary)
  set MYVAR=hello

  :: set permanently for current user (new processes only)
  setx MYVAR "hello"

  :: append to PATH (user scope)
  setx PATH "%PATH%;C:\Tools"
