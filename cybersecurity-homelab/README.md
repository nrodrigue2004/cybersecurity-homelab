#  Cybersecurity Homelab

A fully self-hosted enterprise-grade cybersecurity lab built on a mini PC using Proxmox. Designed for hands-on offensive and defensive security practice, simulating a realistic corporate environment with attacker infrastructure, vulnerable targets, Active Directory, web applications, and full network monitoring.

---

##  Hardware

| Component | Spec |
|-----------|------|
| CPU | Intel i7-10900K |
| RAM | 64GB |
| Storage | 2TB SSD |
| Hypervisor | Proxmox VE |

---

## 🗺️ Network Topology

```
                        INTERNET
                            │
                    ┌───────▼───────┐
                    │  Work Network │
                    │ 192.168.1.0/24│
                    └───────┬───────┘
                            │
                    ┌───────▼───────┐
                    │    Proxmox    │
                    │ 192.168.1.200 │
                    │    (vmbr0)    │
                    └───────┬───────┘
                            │
                    ┌───────▼───────┐
                    │   pfSense     │  ← WAN: 192.168.1.63
                    │   Firewall    │  ← LAN: 192.168.50.1
                    └───────┬───────┘
                            │ vmbr1 (192.168.50.0/24)
          ┌─────────────────┼─────────────────────────┐
          │                 │                          │
  ┌───────▼──────┐  ┌───────▼──────┐        ┌────────▼───────┐
  │     Kali     │  │ Metasploitable│        │  Ubuntu Server │
  │ 192.168.50   │  │ 192.168.50   │        │  192.168.50    │
  │    .107      │  │    .108      │        │     .109       │
  └──────────────┘  └──────────────┘        └────────────────┘
          │                 │                          │
  ┌───────▼──────┐  ┌───────▼──────┐        ┌────────▼───────┐
  │  Windows     │  │  Windows 11  │        │ Security Onion │
  │  Server 2022 │  │  Workstation │        │  192.168.50    │
  │ 192.168.50.10│  │ 192.168.50   │        │     .20        │
  │  (lab.local) │  │    .111      │        └────────────────┘
  └──────────────┘  └──────────────┘

Remote Access: Tailscale (pfSense as subnet router)
Advertised routes: 192.168.1.0/24, 192.168.50.0/24
```

---

## 🖧 VM Inventory

| VM ID | Name | OS | IP | Role |
|-------|------|----|----|------|
| 100 | pfsense | FreeBSD (pfSense) | 192.168.50.1 (LAN) / 192.168.1.63 (WAN) | Firewall / Gateway / DHCP |
| 101 | kali-attacker | Kali Linux | 192.168.50.107 | Attacker machine |
| 102 | ubuntu-server | Ubuntu Server 24.04 LTS | 192.168.50.109 | Docker host (DVWA, WebGoat) |
| 103 | windows-server | Windows Server 2022 | 192.168.50.10 | Active Directory Domain Controller |
| 104 | windows-workstation | Windows 11 Enterprise | 192.168.50.111 | Domain-joined workstation |
| 105 | security-onion | Security Onion 2.4 | 192.168.50.20 | Network monitoring / IDS / SIEM |
| 200 | metasploitable | Metasploitable 2 | 192.168.50.108 | Vulnerable Linux target |

---

##  Lab Components

###  Offensive
- **Kali Linux** — Full attacker workstation with all standard Kali tools pre-installed
- **Metasploit Framework** — Available on Kali for exploitation

###  Vulnerable Targets
- **Metasploitable 2** — Intentionally vulnerable Linux VM for network/service exploitation practice
- **DVWA (Damn Vulnerable Web App)** — Dockerized web app for SQL injection, XSS, file upload, command injection, and more
- **WebGoat** — OWASP's interactive web vulnerability learning platform

###  Infrastructure
- **pfSense** — Primary firewall, DHCP server, DNS forwarder, and Tailscale subnet router
- **Windows Server 2022** — Active Directory Domain Controller for `lab.local`
  - Domain: `lab.local`
  - Users: `jsmith` (standard user), `labadmin` (domain admin)
- **Windows 11 Workstation** — Domain-joined endpoint simulating a corporate workstation

###  Defensive / Monitoring
- **Security Onion 2.4 (Standalone)** — Full monitoring stack including:
  - Zeek (network analysis)
  - Suricata (IDS/IPS)
  - Elasticsearch + Kibana (log storage and visualization)
  - Logstash (log pipeline)
  - Elastalert (alerting)
  - SOC web interface

---

##  Remote Access

Remote access is handled via **Tailscale** with pfSense configured as a subnet router. This allows access to all lab VMs (`192.168.50.0/24`) and the Proxmox host (`192.168.1.0/24`) from anywhere without exposing any ports publicly.

**Tailscale Machines:**
- `homelab` — pfSense node (subnet router)
- `kali-attacker` — Kali Linux VM

**Approved subnet routes:**
- `192.168.1.0/24` (Proxmox/work network)
- `192.168.50.0/24` (lab VM network)

---

##  Docker Services (Ubuntu Server)

| Service | Port | URL |
|---------|------|-----|
| DVWA | 8080 | http://192.168.50.109:8080 |
| WebGoat | 8081 | http://192.168.50.109:8081/WebGoat |

Both containers are configured with `--restart always` to survive reboots.

---

##  Access Methods

| VM | Method | Address |
|----|--------|---------|
| Proxmox Web UI | HTTPS | https://192.168.1.200:8006 |
| pfSense Web GUI | HTTP | http://192.168.1.63 |
| Kali | SSH | ssh kali@192.168.50.107 |
| Ubuntu Server | SSH | ssh user@192.168.50.109 |
| Windows Server | RDP | 192.168.50.10 |
| Windows Workstation | RDP | 192.168.50.111 |
| Security Onion | HTTPS | https://192.168.50.20 |

---

##  Attack Scenarios

This lab supports a wide range of offensive security exercises:

- **Network exploitation** — Metasploit against Metasploitable 2 services
- **Web application attacks** — SQL injection, XSS, CSRF, file upload on DVWA/WebGoat
- **Active Directory attacks** — Password spraying, Kerberoasting, Pass the Hash, lateral movement
- **Privilege escalation** — From `jsmith` workstation access to domain admin
- **Detection & response** — Monitor all attacks in real time via Security Onion

---

##  Repository Structure

```
cybersecurity-homelab/
├── README.md
├── diagrams/
│   └── network-diagram.svg
└── configs/
    ├── pfsense/
    │   └── notes.md
    ├── proxmox/
    │   └── notes.md
    └── kali/
        └── notes.md
```

---

##  Status

| Component | Status |
|-----------|--------|
| Proxmox hypervisor | ✅ Running |
| pfSense firewall | ✅ Running |
| Tailscale remote access | ✅ Configured |
| Kali Linux | ✅ Running |
| Metasploitable 2 | ✅ Running |
| Ubuntu Server + Docker | ✅ Running |
| DVWA | ✅ Running |
| WebGoat | ✅ Running |
| Windows Server 2022 (AD) | ✅ Running |
| Windows 11 Workstation | ✅ Running |
| Security Onion | ✅ Running |
