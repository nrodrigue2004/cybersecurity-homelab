# pfSense Configuration Notes

## Purpose
pfSense provides routing, policy enforcement, DHCP, and DNS services for the isolated homelab.

## Segmentation design
- WAN connects to the upstream network; its address is intentionally omitted.
- LAN serves the internal lab segment using <LAB_SUBNET> and <PFSENSE_ADDRESS> in public examples.
- DHCP leases and DNS records support lab systems without publishing real hostnames or addresses.
- Firewall policy permits only the flows required for administration, updates, and approved lab exercises.

## Administrative safeguards
- Administration is performed over HTTPS from an authorized management path.
- Configuration exports, firewall backups, and logs remain private because they can contain infrastructure details.
- Rule changes are documented with purpose, affected segment, verification steps, and rollback considerations.

## Validation
After a policy change, verify expected connectivity, confirm unwanted paths remain blocked, and record the result in the relevant walkthrough or change note.
