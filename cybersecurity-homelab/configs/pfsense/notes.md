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
- Node name: homelab
- Tailscale IP: 100.108.187.106
- Advertised routes: 192.168.1.0/24, 192.168.50.0/24
- Both routes approved in Tailscale admin console

## Web GUI Access
- LAN: http://192.168.50.1 (from lab network)
- WAN: http://192.168.1.63 (WAN GUI access rule enabled)
- Note: HTTPS unavailable due to anti-lockout rule — HTTP only

## Firewall Notes
- Default LAN-to-WAN NAT enabled (lab VMs have internet access)
- WAN GUI access rule added via `easyrule pass wan tcp any any 80`
