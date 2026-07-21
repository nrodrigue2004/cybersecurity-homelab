# Proxmox Configuration Notes

## Purpose
Proxmox VE is the hypervisor platform for the homelab virtual machines.

## Host design
- The host is documented publicly as <PROXMOX_HOST>; its management address and web interface URL are intentionally omitted.
- Separate virtual bridges connect the upstream path and the isolated internal lab segment.
- Public examples refer to <UPSTREAM_SUBNET> and <LAB_SUBNET> rather than the live network plan.

## Virtual machine inventory
The environment hosts pfSense, Windows Server with Active Directory, a Windows workstation, Ubuntu application services, Kali Linux, Metasploitable, and Security Onion. Resource allocation is adjusted as lab requirements change and is not treated as a production capacity plan.

## Administrative practice
- Apply host updates deliberately and validate VM networking after maintenance.
- Keep backups and exported VM configurations private because they may contain machine names, network settings, or credentials.
- Document changes that affect segmentation, monitoring visibility, or domain services.
