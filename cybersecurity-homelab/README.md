# Enterprise Cybersecurity Homelab

## Lab Hardware

| Component | Specification |
| --- | --- |
| CPU | Intel i7-10900K |
| Memory | 64 GB RAM |
| Storage | 2 TB SSD |
| Hypervisor | Proxmox VE |

A self-hosted cybersecurity practice environment built with Proxmox. This portfolio documents virtualization, network security, Active Directory, Windows and Linux administration, security monitoring, and controlled security testing in an isolated lab.

## Project objectives

- Configure and document a segmented virtual lab.
- Practice AD, endpoint, Linux server, and firewall administration.
- Study SIEM, IDS/NSM, log analysis, threat hunting, and incident-response workflows.
- Test only lab-owned intentionally vulnerable systems.

## Architecture overview

Proxmox hosts the virtual environment. pfSense separates an upstream network from an internal lab segment. Windows Server provides Active Directory to a Windows 11 workstation. Ubuntu hosts DVWA and WebGoat. Kali and Metasploitable support controlled testing. Security Onion provides monitoring. Tailscale enables private remote administration without exposing management services.

## Technology stack

Proxmox VE, pfSense, Tailscale, Windows Server and Active Directory, Windows 11, Ubuntu Server, Docker, DVWA, WebGoat, Kali Linux, Metasploitable, Security Onion, Zeek, Suricata, and Elastic Stack concepts.

## Network segmentation and security design

pfSense separates the internal lab from the upstream network. Administrative addresses, domains, hostnames, usernames, and remote-access identifiers are redacted. Security Onion observes mirrored lab traffic.

## Systems and virtual machines

Proxmox; pfSense firewall/router; Windows Server AD domain controller; Windows 11 domain-joined workstation; Ubuntu Docker host; Kali testing workstation; Metasploitable training target; Security Onion monitoring platform.

## Skills demonstrated

Virtualization, network security, Active Directory, Windows and Linux administration, SIEM and network monitoring, IDS/NSM concepts, log analysis, threat hunting, vulnerability assessment, attack simulation, incident-response practice, and documentation.

## Security monitoring and defensive operations

Security Onion supports practice with Zeek and Suricata telemetry, event review, investigation notes, and defensive workflow development. Specific detections or incident outcomes are not claimed unless documented in a walkthrough.

## Offensive-security testing conducted in the isolated lab

Testing is limited to lab-owned, intentionally vulnerable systems such as Metasploitable, DVWA, and WebGoat.

## Repository structure

```text
.
├── README.md
├── architecture/
├── configs/
├── detections/
├── screenshots/
└── walkthroughs/
```

## Screenshots

Sanitized screenshots will be added after review for secrets and identifying infrastructure details.

## Current progress

The hypervisor, firewall/router, Active Directory components, Windows workstation, Ubuntu web-lab host, Kali, Metasploitable, Security Onion, and remote-access design are documented.

## Future roadmap

Add sanitized screenshots, network-flow documentation, detection hypotheses, triage notes, and evidence-based attack-and-detection walkthroughs.

## Ethical-use disclaimer

All offensive-security testing is performed only against systems owned by me inside an isolated lab. Nothing here is intended for unauthorized access. Secrets and identifying infrastructure details have been removed from the public repository.
