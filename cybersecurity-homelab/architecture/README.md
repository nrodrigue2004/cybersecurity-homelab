# Architecture

The diagram below preserves the lab's functional design while removing live addresses, hostnames, credentials, and management URLs.

![Sanitized network diagram](../diagrams/network-diagram.svg)

## Segmentation summary

- **Upstream and internal lab networks:** pfSense separates the lab segment from the upstream path.
- **Identity and endpoints:** Windows Server provides Active Directory services to a domain-joined Windows workstation.
- **Application services:** Ubuntu hosts intentionally vulnerable training applications in the lab.
- **Testing systems:** Kali Linux and Metasploitable support controlled exercises only.
- **Monitoring:** Security Onion receives mirrored traffic for IDS/NSM and investigation practice.
- **Remote administration:** Tailscale is used for private administration without publishing management services.

Public documentation uses placeholders such as <LAB_SUBNET>, <INTERNAL_DOMAIN>, and <SECURITY_ONION_HOST>.
