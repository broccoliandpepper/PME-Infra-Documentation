# Proofing VLAN (VLAN 213)

## Overview

VLAN 213 is a dedicated, isolated network segment designed for packaging proofing systems. These systems are used in color-critical workflows where accuracy and consistency are essential before printing large production runs.

**Network Address**: `172.16.213.0/24`

## Purpose

In the packaging industry, proofing systems allow designers and quality assurance teams to:

- Preview how designs will appear in print.
- Validate colors and layout before committing to production.
- Make corrections in a controlled environment.

## Connected Equipment

### Proofing Servers

| Device | Model | OS | IP Address | Function |
|--------|-------|----|----|----------|
| GMG Server | - | Windows 11 | 172.16.213.40 | GMG ColorProof (color management) |
| CMA Server | - | Windows 11 | 172.16.213.65 | CMA proofing software |

### Large Format Printers

| Device | Model | IP Address | Function |
|--------|-------|------------|----------|
| Screen SC-P7000 | Epson | 172.16.213.54 | Large format printer (proofing) |
| Screen SC-P7500 | Epson | 172.16.213.59 | Large format printer (proofing) |

### Specialty Equipment

| Device | Model | IP Address | Function |
|--------|-------|------------|----------|
| INX CP800 | INX | 172.16.213.60 | Digital proofing system |
| Roland VS-300i (Unit 1) | Roland | - | Printer/cutter combination |
| Roland VS-300i (Unit 2) | Roland | - | Printer/cutter combination |

### Legacy Equipment

| Device | Model | OS | Network Access | Function |
|--------|-------|----|----|----------|
| Cutting Machine | Legacy | Windows XP | VLAN 213 only | Cutting/finishing equipment |

## Network Isolation Rationale

VLAN 213 is isolated for several reasons:

1. **Performance**: Color-critical workflows require stable, low-latency networking.
2. **Consistency**: Dedicated network prevents interference from general user traffic.
3. **Legacy Support**: Windows XP cutting machine runs safely in an isolated segment without external connectivity.
4. **Security**: Equipment is not exposed to internet-facing traffic.

## Connectivity

- **Uplink**: Connected to Aruba switches via VLAN 213 trunk.
- **Internet Access**: Limited (software updates only for compatible devices).
- **Windows XP Machine**: No internet access (isolated for security).
- **Backup**: Devices in this VLAN are not included in standard user backup procedures; equipment-specific backup strategies may apply.

## Access Control

- Only users with proofing responsibilities have network access to VLAN 213.
- Access is managed via:
  - WatchGuard firewall rules.
  - Network Access Control (implied by VLAN segmentation).

## Software & Tools

The proofing environment uses:

- **GMG ColorProof**: Professional color management software.
- **CMA**: Additional proofing software.
- **Roland/Epson/INX drivers**: Specific to each device.
- **Windows 11**: Modern OS for proofing servers.

These tools integrate with the corporate design workflow and allow designers to preview final outputs before production.
