# pfSense Configuration Notes

## Network Interfaces

| Interface | Name | IP | Network |
|-----------|------|----|---------|
| vtnet0 | LAN | 192.168.50.1/24 | Lab VM network (vmbr1) |
| vtnet1 | WAN | 192.168.1.63/24 (DHCP) | Work/upstream network (vmbr0) |

## DHCP Server (LAN)
- Range: 192.168.50.100 - 192.168.50.200
- Gateway: 192.168.50.1
- DNS: 8.8.8.8, 8.8.4.4

## Tailscale
- Package: pfSense-pkg-Tailscale
- Role: Subnet router
- Routes approved in Tailscale admin console

## Web GUI Access
-Management protocol: HTTPS

