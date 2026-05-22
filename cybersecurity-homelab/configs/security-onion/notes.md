# Security Onion Configuration Notes

## Network Details

| Setting | Value |
|---------|-------|
| Hostname | nathan |
| Management NIC | ens18 |
| Management IP | 192.168.50.20/24 |
| Gateway | 192.168.50.1 |
| DNS | 8.8.8.8, 8.8.4.4 |
| Monitoring NIC | bond0 (ens19 as slave) |
| Version | Security Onion 2.4.211 Standalone |

## Web UI Access
URL: `https://192.168.50.20`

To allow analyst access from a subnet:
```bash
sudo so-firewall includehost analyst 192.168.1.0/24
sudo so-firewall --apply apply
```

## ⚠️ Critical: Proxmox Traffic Mirroring

Proxmox Linux bridges don't forward inter-VM traffic to other VMs by default. Two persistent fixes are required for Security Onion to see lab traffic.

**On Proxmox** — add to `/etc/network/interfaces` under the `vmbr1` block:
post-up tc qdisc add dev vmbr1 handle ffff: ingress && tc filter add dev vmbr1 parent ffff: matchall action mirred egress mirror dev tap105i1

**On Security Onion** — add to `/etc/rc.d/rc.local`:
```bash
ip link set bond0 mtu 1500
ip link set ens19 down
ip link set ens19 master bond0
ip link set ens19 up
ip link set bond0 up
ip link set bond0 promisc on
ip link set ens19 promisc on
```
