# Proxmox Configuration Notes

## Host
- Hostname: homelab04
- IP: 192.168.1.200/24
- Gateway: 192.168.1.1
- Web UI: https://192.168.1.200:8006

## Network Bridges

| Bridge | Port | Subnet | Purpose |
|--------|------|--------|---------|
| vmbr0 | nic1 | 192.168.1.0/24 | Upstream/work network |
| vmbr1 | none | 192.168.50.0/24 | Internal lab network |

## VM Summary

| ID | Name | Cores | RAM | Disk | Bridge |
|----|------|-------|-----|------|--------|
| 100 | pfsense | 2 | 2GB | 20GB | vmbr0 + vmbr1 |
| 101 | kali-attacker | 2 | 4GB | 40GB | vmbr1 |
| 102 | ubuntu-server | 2 | 4GB | 40GB | vmbr1 |
| 103 | windows-server | 2 | 4GB | 60GB | vmbr1 |
| 104 | windows-workstation | 2 | 6GB | 60GB | vmbr1 |
| 105 | security-onion | 4 | 12GB | 200GB | vmbr1 |
| 200 | metasploitable | 1 | 512MB | 8GB | vmbr1 |

## ISO Storage
- Location: /var/lib/vz/template/iso/
- Storage pool: local

## VM Storage
- Storage pool: pve-data
- Total: ~909GB
