# HomeLab

Personal homelab running on Proxmox VE. Built this to get hands-on experience with self-hosting, networking, and security tooling. Still a work in progress.

---

## Hardware

| Component | Details |
|-----------|---------|
| Hypervisor | Proxmox VE |
| RAM | 16GB |
| Storage | ~240GB LVM |
| Network | Home LAN |

---

## Infrastructure

```
Proxmox Host (192.168.1.50)
├── CT 100 — Grafana + Prometheus
├── CT 101 — Gitea
├── CT 102 — Authelia
├── CT 103 — Splunk Enterprise
├── CT 106 — Nginx Proxy Manager
├── CT 107 — Trilium Notes
├── VM 104 — Kali Linux 2025.4
└── VM 105 — Windows 11
```

---

## Services

### Grafana + Prometheus
Monitoring stack. Prometheus scrapes metrics from the Proxmox host via Node Exporter. Grafana visualizes it with the Node Exporter Full dashboard.

> _Screenshot coming soon_

---

### Gitea
Self-hosted Git server. Acts as a local mirror of my GitHub repos so I have an offline copy of everything.

> _Screenshot coming soon_

---

### Authelia
SSO and 2FA gateway. Sits in front of internal services so everything requires authentication before you can access it. Supports TOTP.

> _Screenshot coming soon_

---

### Splunk Enterprise
SIEM for log ingestion and analysis. Using it to learn log analysis and practice detection engineering. Configured to receive logs on port 9997.

> _Screenshot coming soon_

---

### Nginx Proxy Manager
Reverse proxy with a web UI. Routes traffic to internal services and handles SSL. Also wired up to a Cloudflare Tunnel for when I need external access.

> _Screenshot coming soon_

---

### Trilium Notes
Self-hosted note taking app. Using it to document the homelab and take notes while studying. All data stays local.

> _Screenshot coming soon_

---

### Kali Linux 2025.4
Used for CTF practice, pentesting labs, and general security research. Full desktop environment.

> _Screenshot coming soon_

---

### Windows 11
General use and Windows-specific testing. Also planning to use it for malware analysis down the road.

> _Screenshot coming soon_

---

## Networking

```
Internet
    |
 Router
    |
192.168.1.0/24
    |
Proxmox (192.168.1.50)
    |
vmbr0 bridge
    |-- LXC containers
    |-- VMs
```

Everything is local only right now. Cloudflare Tunnel is set up but DNS records are pulled so nothing is public facing. Planning to add Tailscale for remote access.

---

## Planned

- Tailscale for remote access
- Authelia protecting all services through NPM
- Splunk ingesting logs from all containers
- Network segmentation with VLANs
- Wazuh for HIDS

---

## Notes

Still learning as I go. A lot of this was set up through trial and error. Happy to answer questions if anything here looks interesting.
