text
# Document 1: README.md (Network Architecture)

> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

The primary office network is built on a strict VLAN segmentation strategy managed by a WatchGuard Firebox M390 cluster (active/passive configuration). The firewall handles both VLAN management and DHCP services for the entire on-premise infrastructure.

## Network Security Layer

Two security appliances (AI-based traffic inspection devices) are deployed between the WatchGuard Firewall and the core switches, creating an AI-based security inspection layer that analyzes all network traffic packets in real-time.

## Infrastructure Components

- **Firewall**: WatchGuard Firebox M390 (cluster)
- **Switches**: Aruba switches (stacked configuration)
- **Additional switches**: Cisco switches for specific VLANs
- **Wireless**: Aruba Access Points (VLAN 220 trunk)
- **Security appliances**: 2x AI-based traffic analysis devices

## VLAN Segmentation

The network is divided into 7 VLANs, each serving specific business and operational purposes:

| VLAN ID | Name | Subnet | Purpose |
|---------|------|--------|---------|
| 210 | Domain & WiFi | 172.16.210.0/24 | Main user network (domain-joined devices, WiFi clients) |
| 211 | Isolated | 172.16.211.0/24 | Backup servers, NAS archive, remote site NAS (isolated from production) |
| 212 | Storage | 172.16.212.0/24 | Dedicated storage network |
| 213 | Proofing | 172.16.213.0/24 | Proofing systems (specialized servers, printers) |
| 215 | Security | 172.16.215.0/24 | Security appliances and monitoring |
| 219 | Management | 172.16.219.0/24 / 192.168.99.x | Network device management |
| 220 | AP Trunk | - | Trunk to Aruba Access Points (carries multiple VLANs) |

## Physical Topology

Internet (Fiber)
↓
WatchGuard Firebox M390 (Cluster)
↓
AI Security Appliances (2 units)
↓
Aruba Switches (Stacked)
↓
├── Cisco Switches (VLAN trunk)
├── Dell Servers
├── QNAP NAS devices
├── Aruba Access Points
└── End-user devices

text

## Key Network Devices

### WatchGuard Firebox M390 Cluster

- **Role**: Primary firewall, VLAN routing, DHCP server
- **Configuration**: Active/passive high availability
- **Management IP**: 172.16.219.4 (primary), 172.16.219.5 (secondary)

### AI Security Appliances

- **Quantity**: 2 units (redundancy)
- **Position**: Inline between firewall and switches
- **Function**: Real-time traffic inspection, AI-based threat detection

### Aruba Switches

- **Configuration**: Stacked (management 172.16.219.x)
- **Ports**: 48-port configuration (P1-P48)
- **Uplinks**: SFP ports (25-28) for fiber connections

### Cisco Switches

- **Purpose**: Additional port density for specific VLANs
- **Connection**: Trunk connection to Aruba switches

## Network Services

### DHCP

Managed by WatchGuard Firebox M390 for all VLANs except isolated segments.

### DNS

- Internal DNS integrated with on-premise Active Directory (legacy)
- Azure DNS for cloud-joined devices

### VPN

- **Site-to-Site**: Primary site ↔ Remote site (WatchGuard VPN)
- **Point-to-Site**: Azure VPN Gateway for remote users

## Documentation Structure

- `vlan-segmentation.md`: Detailed breakdown of each VLAN with device inventory
- `watchguard-firewall.md`: Firewall configuration, rules, and management
- `network-matrix.md`: Complete device mapping and physical connections