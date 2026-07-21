# Enterprise Cybersecurity Homelab

A self-hosted cybersecurity practice environment built with Proxmox. This portfolio documents hands-on virtualization, network security, Windows and Linux administration, security monitoring, and controlled testing in an isolated lab.

## Project objectives

- Configure and document a segmented virtual lab.
- Practice Active Directory, Windows endpoint, Linux server, and firewall administration.
- Study SIEM, IDS/NSM, log analysis, threat hunting, and incident-response workflows.
- Perform vulnerability assessment and attack simulation only against lab-owned, intentionally vulnerable systems.

## Architecture overview

Proxmox hosts the virtual environment. pfSense separates an upstream network from an internal lab segment. Windows Server provides Active Directory to a Windows 11 workstation. Ubuntu hosts DVWA and WebGoat. Kali and Metasploitable support controlled testing. Security Onion provides monitoring. Tailscale enables private remote administration without publishing management services.

## Technology stack

| Area | Technologies |
| --- | --- |
| Virtualization | Proxmox VE, Linux bridges |
| Network security | pfSense, segmentation, DHCP/DNS, Tailscale |
| Identity | Windows Server, Active Directory, Windows 11 |
| Web lab | Ubuntu Server, Docker, DVWA, WebGoat |
| Testing | Kali Linux, Metasploitable |
| Monitoring | Security Onion, Zeek, Suricata, Elastic Stack concepts |

## Network segmentation and security design

- pfSense separates the internal lab from the upstream network.
- Administrative addresses, domains, hostnames, usernames, and remote-access identifiers are redacted.
- Tailscale provides a private administration path rather than public management ports.
- Security Onion is positioned to observe mirrored lab traffic.

## Systems and virtual machines

| System | Purpose |
| --- | --- |
| Proxmox | Virtualization platform and virtual networking |
| pfSense | Firewall, routing, DHCP/DNS, remote-access design |
| Windows Server | Active Directory domain controller |
| Windows 11 | Domain-joined workstation |
| Ubuntu Server | Docker host for DVWA and WebGoat |
| Kali Linux | Controlled testing workstation |
| Metasploitable | Intentionally vulnerable training target |
| Security Onion | IDS, NSM, and SIEM practice |

## Skills demonstrated

Virtualization; network security; Active Directory; Windows and Linux administration; SIEM and network monitoring; IDS/NSM concepts; log analysis; threat hunting; vulnerability assessment; attack simulation; incident-response practice; and documentation.

## Security monitoring and defensive operations

Security Onion is configured as the monitoring platform. The lab supports practice with Zeek and Suricata telemetry, event review, investigation notes, and defensive workflow development. Specific detections or incident outcomes are not claimed unless documented in a walkthrough.

## Offensive-security testing conducted in the isolated lab

Testing is limited to lab-owned, intentionally vulnerable systems such as Metasploitable, DVWA, and WebGoat. Exercises focus on scoped vulnerability assessment and attack simulation, with monitoring and response practice where applicable.

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

Sanitized screenshots will be added after review for secrets and identifying infrastructure details. Placeholder: Security Onion monitoring view and sanitized network topology.

## Current progress

The hypervisor, firewall/router, Active Directory components, Windows workstation, Ubuntu web-lab host, Kali, Metasploitable, Security Onion, and remote-access design are documented. Evidence-based walkthroughs are the next priority.

## Future roadmap

- Add sanitized screenshots and validation evidence.
- Document firewall policy decisions and network-flow expectations.
- Add detection hypotheses, triage notes, and threat-hunting exercises.
- Publish scoped attack-and-detection walkthroughs only when outcomes are documented.

## Ethical-use disclaimer

All offensive-security testing is performed only against systems owned by me inside an isolated lab. Nothing here is intended for unauthorized access. Secrets and identifying infrastructure details have been removed from the public repository.
