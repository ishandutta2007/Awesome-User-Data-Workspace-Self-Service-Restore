# Awesome-User-Data-Workspace-Self-Service-Restore

# Awesome User Data Workspace & Self-Service Restore

> A curated list of top User Data Workspace and Self-Service Restore platforms — both SaaS/Hosted commercial solutions and open-source alternatives for virtual desktops, workspace backup, and end-user initiated recovery.  
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Druva Data Security for Endpoints](#druva-data-security-for-endpoints)
  - [Amazon WorkSpaces](#amazon-workspaces)
  - [VMware Horizon Cloud](#vmware-horizon-cloud)
  - [Nutanix Frame / NGT Self-Service Restore](#nutanix-frame--ngt-self-service-restore)
  - [Citrix Workspace](#citrix-workspace)
  - [Azure Virtual Desktop (with Nerdio)](#azure-virtual-desktop-with-nerdio)
  - [Workspot](#workspot)
- [Open-Source Software](#-open-source-software)
  - [Bekane](#bekane)
  - [Eclipse Che](#eclipse-che)
  - [Nextcloud](#nextcloud)
  - [Backrest](#backrest)
  - [Apache Guacamole](#apache-guacamole)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted User Data Workspace and Self-Service Restore platforms. These are not open-source but are included as reference points for feature comparison.

### Druva Data Security for Endpoints
**Type:** SaaS endpoint backup with self-service restore  
Druva provides a 100% SaaS platform for endpoint and cloud application data protection, with **self-service restore** delegated to end-users through an easy-to-use experience [citation:1]. Users can initiate their own restore of data to any of their devices via the Druva inSync client, searching for filenames and selecting the correct device [citation:12]. This reduces IT resource requirements while ensuring business continuity against accidental or malicious data loss and ransomware [citation:1].  
**Best for:** Organizations wanting fully managed endpoint backup with genuine end-user self-service recovery across Windows, Mac, Linux, Android, and iOS.

### Amazon WorkSpaces
**Type:** Managed cloud desktop with admin-initiated restore  
Amazon WorkSpaces provides managed virtual cloud desktops. Automatic snapshots are scheduled every 12 hours, and WorkSpaces can be **restored** to the last known healthy state via the AWS console or CLI [citation:4][citation:15]. Restoration recreates both root and user volumes from snapshots, rolling back applications and settings to the snapshot point [citation:15]. **Important:** Restore is an **IT administrator action**, not a user self-service feature in the standard product.  
**Best for:** Organizations wanting managed Windows or Linux cloud desktops with snapshot-based recovery controlled by IT.

### VMware Horizon Cloud
**Type:** VDI with user-initiated desktop reset  
Horizon Cloud supports **dedicated desktops** where users can reset their own desktops from Workspace ONE if the desktop stops responding [citation:14]. This is configured in Horizon Cloud (not VMware Identity Manager) and requires connectors version 2018.1.1.0 or later. The reset command appears in Workspace ONE only for desktops where the option is enabled.  
**Best for:** Organizations using Horizon Cloud with dedicated desktops wanting user-initiated reset for unresponsive desktops.

### Nutanix Frame / NGT Self-Service Restore
**Type:** VDI with file-level self-service restore  
Nutanix Guest Tools (NGT) includes a **Self-Service Restore (SSR)** feature for Windows VMs, allowing users to restore desired files from VM snapshots through a web interface or the `ngctl` utility [citation:6][citation:22]. Users select snapshots by date range, mount the snapshot disk, and copy files back — all without IT intervention. Requires NGT 2.0 installed and SSR enabled on the VM [citation:22].  
**Best for:** Nutanix environments wanting file-level user self-service restore from snapshots rather than full desktop rollback.

### Citrix Workspace
**Type:** Workspace platform with self-service password reset  
Citrix Workspace provides access to virtual apps and desktops. Its self-service capabilities center on **Self-Service Password Reset** (SSPR), allowing users to reset passwords and unlock accounts without IT help [citation:2]. This is a credentials self-service feature rather than data/workspace restore.  
**Best for:** Citrix environments wanting to reduce helpdesk load for password-related issues.

### Azure Virtual Desktop (with Nerdio)
**Type:** Cloud VDI with Nerdio self-service restore  
Azure Virtual Desktop (AVD) natively lacks end-user self-service restore. However, Nerdio Manager for Enterprise (Premium license) adds a **RESTORE** feature allowing users to restore desktops from previous backups, provided host pool backups are enabled [citation:5]. Administrators configure restore behavior (e.g., automatically resize back after a set period).  
**Best for:** AVD deployments where Nerdio is used and Premium licensing is available for self-service recovery.

### Workspot
**Type:** Cloud desktop with IT-administered restore  
Workspot offers built-in cloud desktop backup and restore within the same cloud region. IT administrators configure daily, weekly, and monthly backup schedules, and can restore a desktop to a previous version in one click [citation:8]. The blog explicitly describes **IT administrator** restore, not end-user self-service.  
**Best for:** Workspot deployments where IT controls desktop recovery for business continuity.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Workspace and Self-Service Restore tools. The open-source ecosystem is fragmented across VDI brokers, cloud workspace backup, and file-level restore interfaces.

### Bekane
**Stack:** Python (Django) / Vue.js / Proxmox | **License:** AGPL-3.0  
An open-source VDI and broker solution built specifically for **Proxmox VE**. It provides a web portal for users to access their virtual desktops, with **snapshot creation and fast restoration** for IT support, training, labs, and quickly resetting environments [citation:10][citation:18]. Supported actions include starting, stopping, resetting VMs, and restoring snapshots. Integrates with LDAP/OIDC for authentication and offers granular RBAC and auditing [citation:18].  
**Important nuance:** Snapshot restore is available, but the documentation describes IT support/training use cases rather than clearly defined **end-user** self-service restore. The project is actively developed and community-driven.  
**Best for:** Organizations running Proxmox wanting an open-source VDI broker with snapshot-based recovery and full on-premises control.

### Eclipse Che
**Stack:** Java / Kubernetes | **License:** EPL-2.0  
Eclipse Che is an open-source Kubernetes-native IDE and developer workspace platform. When backups are configured, **workspace backups** are available in the Che dashboard within a Backups tab, showing both Active (existing) and Deleted workspaces [citation:26][citation:27]. Users can **restore a workspace from a backup** through the dashboard, selecting from internal registry backups or providing an external backup image URL, then configuring compute limits and editor before starting the restore [citation:27]. This enables recovery of uncommitted source code changes from deleted or stopped workspaces.  
**Best for:** Development teams using Eclipse Che wanting self-service workspace recovery for uncommitted code and environment restoration.

### Nextcloud
**Stack:** PHP / JavaScript | **License:** AGPL-3.0  
Nextcloud provides a secure, private workspace for files and collaboration. Its self-service recovery capabilities are **file-level**: deleted files go to the **Trash Bin** (restorable for up to 30 days) and **Version History** allows restoring previous versions of individual files [citation:11]. The Trash Bin is limited to 50% of remaining storage quota, with oldest deleted files removed first if exceeded. **Limitation:** This is file recovery within a sync-and-share workspace, not full desktop or VM restore.  
**Best for:** Teams wanting self-service file recovery (deletion and versioning) within a self-hosted collaboration workspace.

### Backrest
**Stack:** Go / Restic | **License:** GPL-3.0  
Backrest is a web-accessible backup solution built on **restic** that provides a WebUI for creating repos, browsing snapshots, and **restoring files** [citation:23]. It runs as a standalone lightweight binary (with restic as its sole dependency) and supports S3, B2, Azure, GCS, local, SFTP, and rclone remotes. While not a workspace platform itself, it provides the **self-service restore interface** layer: users can browse and restore files from snapshots via a web UI rather than the CLI.  
**Best for:** Teams already using restic who want a web-based self-service restore UI for file-level recovery, deployable on NAS or Docker.

### Apache Guacamole
**Stack:** Java / JavaScript | **License:** Apache-2.0  
Apache Guacamole is a clientless remote desktop gateway that provides web-based access to VMs and desktops via RDP, VNC, and SSH [citation:19]. While **not a backup/restore tool**, it is a common open-source building block for workspace access portals where self-service recovery might be layered on top (e.g., pairing Guacamole for access with Backrest for restore). It requires three containers: frontend, guacd backend, and a database for authentication and configuration [citation:19].  
**Best for:** Organizations building custom open-source workspace access portals that need clientless remote desktop connectivity, often paired with a backup/restore tool.

---

## 📊 Comparison at a Glance

| Software | License | Type | Self-Service Restore | Restore Scope | Self-Hosted | Best For |
|----------|---------|------|----------------------|---------------|-------------|----------|
| **Druva** | Proprietary | Endpoint backup | ✅ User-initiated | Files/endpoint | ❌ | Fully managed endpoint self-restore |
| **Amazon WorkSpaces** | Proprietary | Cloud desktop | ❌ IT-admin only | Full desktop | ❌ | Managed desktops with IT recovery |
| **VMware Horizon** | Proprietary | VDI | ✅ User reset | Desktop reset | ❌ | Dedicated desktop reset |
| **Nutanix NGT SSR** | Proprietary | VDI + file restore | ✅ User file restore | Files from snapshots | ❌ | File-level self-service restore |
| **Citrix Workspace** | Proprietary | Workspace access | ✅ Password reset | Credentials only | ❌ | Self-service password reset |
| **AVD + Nerdio** | Proprietary | Cloud VDI | ✅ (Nerdio Premium) | Desktop restore | ❌ | AVD with Nerdio Premium |
| **Workspot** | Proprietary | Cloud desktop | ❌ IT-admin only | Full desktop | ❌ | IT-controlled desktop recovery |
| **Bekane** | AGPL-3.0 | Proxmox VDI | (IT/support focus) | Snapshot restore | ✅ | Open-source Proxmox VDI |
| **Eclipse Che** | EPL-2.0 | Dev workspaces | ✅ User restore | Workspace + code | ✅ | Self-service developer workspace restore |
| **Nextcloud** | AGPL-3.0 | File workspace | ✅ Trash/versions | Files only | ✅ | Self-service file recovery |
| **Backrest** | GPL-3.0 | Restic WebUI | ✅ User restore | Files | ✅ | Web UI for restic restore |
| **Apache Guacamole** | Apache-2.0 | Remote gateway | ❌ (access only) | N/A | ✅ | Clientless workspace access |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source User Data Workspace or Self-Service Restore tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem **splits** between VDI platforms with snapshot restore (Bekane), developer workspace backup (Eclipse Che), and file-level self-service restore (Nextcloud, Backrest). No single open-source project fully replicates Druva's end-user endpoint self-restore at the same scope.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
