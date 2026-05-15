# Kali Linux Configuration Notes

## Network
- Interface: eth0
- IP: 192.168.50.107 (DHCP)
- Gateway: 192.168.50.1
- DNS: 8.8.8.8 (set in /etc/resolv.conf)

## Persistent Network Config
File: `/etc/network/interfaces`
```
auto eth0
iface eth0 inet dhcp
```

## DNS Fix
```bash
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
sudo chattr +i /etc/resolv.conf
```

## SSH Access
```bash
ssh kali@192.168.50.107
```

## Tailscale
- Node name: kali-attacker
- Tailscale IP: 100.91.141.77
