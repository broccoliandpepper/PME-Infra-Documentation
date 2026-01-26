> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Physical Device Inventory

### Firewall Infrastructure

| Device | Model | Serial | IP Address | VLAN | Function |
|--------|-------|--------|------------|------|----------|
| Firebox M390 Primary | WatchGuard M390 | - | 172.16.219.4 | 219 | Active firewall |
| Firebox M390 Secondary | WatchGuard M390 | - | 172.16.219.5 | 219 | Passive firewall |

### Security Appliances

| Device | Model | IP Address | VLAN | Function |
|--------|-------|------------|------|----------|
| AI Security Box 01 | Vendor A | - | VLAN 215 | AI traffic inspection |
| AI Security Box 02 | Vendor A | - | VLAN 215 | AI traffic inspection |

### Switch Infrastructure

| Device | Model | Ports | Management IP | Location |
|--------|-------|-------|---------------|----------|
| Aruba Switch 01 | Aruba (48-port) | P1-P48 + SFP25-28 | 172.16.219.x | Main rack |
| Aruba Switch 02 | Aruba (48-port) | P1-P48 + SFP25-28 | 172.16.219.x | Main rack |
| Dell Switch 01 | Dell | P1-P48 | - | Secondary rack |
| Dell Switch 02 | Dell | P1-P48 | - | Secondary rack |
| Dell Switch 03 | Dell | P1-P48 | - | Secondary rack |
| Dell Switch 04 | Dell | P1-P48 | - | Secondary rack |
| Cisco Switch 01 | Cisco | P1-P24 | - | VLAN 220 distribution |
| Cisco Switch 02 | Cisco | P1-P24 | - | VLAN 220 distribution |

### Storage Infrastructure (VLAN 211 - Isolated)

| Device | Model | Capacity | IP Address | Function |
|--------|-------|----------|------------|----------|
| Dell Server 40TB | Dell | 40 TB | 172.16.211.3 | Backup server |
| Dell Server 60TB | Dell | 60 TB | 172.16.211.2 | Backup server |
| Dell Server 90TB | Dell | 90 TB | 172.16.210.210 | Production storage |
| QNAP Archive | QNAP | - | 172.16.211.4 | Archive storage |
| QNAP Remote Site | QNAP | - | 172.16.211.10 | Remote backup replication |
| Windows Backup Server | Windows Server | - | Dynamic (offline) | Offline backup |

### Proofing Equipment (VLAN 213)

| Device | Model | IP Address | OS | Function |
|--------|-------|------------|-----|----------|
| GMG Proofing Server | Windows 11 | 172.16.213.40 | Windows 11 | GMG ColorProof |
| CMA Proofing Server | Windows 11 | 172.16.213.65 | Windows 11 | CMA proofing |
| Screen SC-P7000 | Epson | 172.16.213.54 | - | Large format printer |
| Screen SC-P7500 | Epson | 172.16.213.59 | - | Large format printer |
| INX CP800 | INX | 172.16.213.60 | - | Digital proofing |
| Roland VS-300i (Unit 1) | Roland | - | - | Printer/cutter |
| Roland VS-300i (Unit 2) | Roland | - | - | Printer/cutter |
| Cutting Machine | Legacy | - | Windows XP | Cutting equipment |

### Print Infrastructure (VLAN 210)

| Device | Model | IP Address | Function |
|--------|-------|------------|----------|
| Canon C165 | Canon | 172.16.210.231 | Office printer |
| Canon IR 5840 | Canon | 172.16.210.230 | Office MFP |

### Wireless Infrastructure

| Device | Model | Quantity | Management VLAN | SSIDs |
|--------|-------|----------|-----------------|-------|
| Aruba Access Points | Aruba | Multiple | 219 | Corporate (VLAN 210), Management (VLAN 219) |

## Port Mapping

### Aruba Switch 01 - Key Connections

| Port | Connected Device | VLAN | Notes |
|------|------------------|------|-------|
| P1-P24 | User workstations | 210 | Access ports |
| P25-P26 (SFP) | WatchGuard M390 uplink | Trunk | All VLANs |
| P27-P28 (SFP) | Aruba Switch 02 stacking | Trunk | Stack connection |

### Aruba Switch 02 - Key Connections

| Port | Connected Device | VLAN | Notes |
|------|------------------|------|-------|
| P1-P12 | QNAP NAS devices | 211/212 | Isolated/storage |
| P13-P24 | Dell servers | 210/211 | Mixed VLANs |
| P27-P28 (SFP) | Aruba Switch 01 stacking | Trunk | Stack connection |

### Cisco Switches - VLAN 220 Trunk

| Switch | Uplink Port | Downlink Ports | Function |
|--------|-------------|----------------|----------|
| Cisco 01 | P24 (to Aruba) | P1-P12 | AP distribution |
| Cisco 02 | P24 (to Aruba) | P1-P12 | AP distribution |

## Cable Infrastructure

### Fiber Connections

- **ISP → WatchGuard**: Single-mode fiber
- **WatchGuard → Aruba (SFP)**: Multi-mode fiber (high-speed trunk)

### Copper Connections

- **Aruba → End devices**: Cat6 UTP
- **Cisco → Access Points**: Cat6 UTP (PoE)

## Remote Site Devices

| Device | Model | IP Address | Function |
|--------|-------|------------|----------|
| WatchGuard T45 | WatchGuard | - | Site firewall |
| QNAP NAS | QNAP | 172.16.211.10 (over VPN) | Backup replication |

**Connection**: Site-to-Site VPN to Primary Site Firebox M390

## Device Access Summary

| Access Method | Allowed VLANs | Protocol | Port |
|---------------|---------------|----------|------|
| Firewall Management | 219, Azure VPN | HTTPS, SSH | 443, 22 |
| Switch Management | 219 | HTTPS, SSH | 443, 22 |
| QNAP Web GUI | 219, 211 (limited) | HTTPS | 443, 8080 |
| Server iDRAC/iLO | 219 | HTTPS | 443 |
| Security Appliance Management | 215, 219 | HTTPS | 443 |