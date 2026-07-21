# Kali Linux Configuration Notes

## Purpose
Kali Linux is the designated testing workstation for authorized exercises against lab-owned systems.

## Network configuration
- The virtual NIC is attached to the isolated lab segment through pfSense.
- Addressing is provided through DHCP; documented examples use placeholders such as <KALI_ADDRESS>, <LAB_SUBNET>, and <DNS_RESOLVER>.
- DNS resolution is verified with standard Linux tools before each exercise.

## Administrative practice
- Keep the operating system and testing tools updated.
- Use a dedicated, non-personal administrative account and a password manager; credentials are never stored in this repository.
- Restrict remote administration to the private remote-access design documented for the lab.

## Scope
Testing is limited to systems owned for this isolated homelab, including intentionally vulnerable targets. Record objective, authorization, observed telemetry, and cleanup steps in a walkthrough before and after each exercise.
