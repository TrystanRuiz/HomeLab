# 🏠 HomeLab

A personal homelab built on **Proxmox VE** running on bare metal. This repo documents the full infrastructure, services, and configuration.

---

## 🖥️ Hardware

| Component | Details |
|-----------|---------|
| Hypervisor | Proxmox VE |
| CPU | x86_64 |
| RAM | 16GB |
| Storage | ~240GB LVM |
| Network | Spectrum ISP |

---

## 🗺️ Infrastructure Overview

```
Proxmox Host (192.168.1.50)
├── CT 100 — Grafana + Prometheus   (Monitoring)
├── CT 101 — Gitea                  (Self-hosted Git)
├── CT 102 — Authelia               (SSO / Auth gateway)
├── CT 103 — Splunk Enterprise      (SIEM / Log analysis)
├── CT 106 — Nginx Proxy Manager    (Reverse proxy)
├── CT 107 — Trilium Notes          (Self-hosted notes)
├── VM 104 — Kali Linux 2025.4      (Penetration testing)
└── VM 105 — Windows 11             (General use / Testing)
```

---

## 🧩 Services

### 📊 Grafana + Prometheus (CT 100)
**Purpose:** Infrastructure monitoring and metrics visualization

- **Prometheus** scrapes metrics from the Proxmox host via Node Exporter
- **Grafana** displays dashboards with CPU, RAM, disk, and network metrics
- Node Exporter Full dashboard (ID 1860) pre-configured
- Accessible at `http://192.168.1.191:3000`

> 📸 _Screenshot placeholder — Grafana dashboard_

---

### 🐙 Gitea (CT 101)
**Purpose:** Self-hosted Git server — local mirror of all GitHub repositories

- Full GitHub-compatible Git server
- All repositories mirrored from GitHub
- Accessible at `http://192.168.1.70:3000`

> 📸 _Screenshot placeholder — Gitea dashboard_

---

### 🔐 Authelia (CT 102)
**Purpose:** Single Sign-On (SSO) and two-factor authentication gateway

- Protects internal services with a unified login portal
- Supports TOTP (2FA) via Google Authenticator or similar
- Argon2id password hashing
- Accessible at `https://192.168.1.89:9091`

> 📸 _Screenshot placeholder — Authelia login page_

---

### 🔎 Splunk Enterprise (CT 103)
**Purpose:** SIEM — log ingestion, search, and security event analysis

- Splunk Enterprise 10.2.1
- Configured to receive logs on port 9997
- Web UI for searching and analyzing logs
- Accessible at `http://192.168.1.111:8000`

> 📸 _Screenshot placeholder — Splunk search interface_

---

### 🔁 Nginx Proxy Manager (CT 106)
**Purpose:** Reverse proxy for routing traffic to internal services

- Web-based UI for managing proxy hosts
- Integrates with Cloudflare Tunnel for optional external access
- Manages SSL termination
- Admin at `http://192.168.1.208:81`

> 📸 _Screenshot placeholder — NPM dashboard_

---

### 📝 Trilium Notes (CT 107)
**Purpose:** Self-hosted knowledge base and note-taking

- Hierarchical note structure
- All data stored locally on Proxmox
- Accessible at `http://192.168.1.221:8080`

> 📸 _Screenshot placeholder — Trilium interface_

---

### 🐉 Kali Linux 2025.4 (VM 104)
**Purpose:** Penetration testing and security research

- Full Kali Linux desktop environment
- Pre-installed security toolset
- Used for CTFs, lab testing, and security practice

> 📸 _Screenshot placeholder — Kali desktop_

---

### 🪟 Windows 11 (VM 105)
**Purpose:** General use and Windows-specific testing

- Windows 11 Home
- UEFI boot with TPM 2.0
- Used for testing Windows-specific tooling and malware analysis

> 📸 _Screenshot placeholder — Windows 11 desktop_

---

## 🌐 Networking

```
Internet
    │
Spectrum Router (71.47.x.x public)
    │
192.168.1.0/24 LAN
    │
Proxmox Host (192.168.1.50)
    │
Linux Bridge (vmbr0)
    ├── All LXC containers (DHCP)
    └── All VMs (DHCP)
```

- All services are **local network only** — not publicly accessible
- Cloudflare Tunnel installed but DNS records removed for privacy
- Remote access via **Tailscale** (planned)

---

## 🔒 Security

- All containers use SSH key authentication
- Authelia provides SSO with 2FA support
- Cloudflare Tunnel available for secure external access when needed
- Proxmox API tokens used instead of root credentials where possible
- Services isolated in separate LXC containers

---

## 🗓️ Planned

- [ ] Tailscale for remote access
- [ ] Authelia wired up to protect all services via NPM
- [ ] Splunk receiving logs from all containers
- [ ] pfSense or OPNsense for network segmentation
- [ ] Wazuh for host-based intrusion detection

---

## 📁 Repo Structure

```
HomeLab/
├── README.md          # This file
├── docs/              # Architecture diagrams and notes
└── screenshots/       # Service screenshots (coming soon)
```
