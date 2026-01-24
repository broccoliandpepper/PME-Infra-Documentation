# WatchGuard Firebox M390 Configuration

## Overview
The Brussels office firewall infrastructure is built on a WatchGuard Firebox M390 cluster running in active/passive high availability mode. The firewall serves as the central routing, security, and DHCP infrastructure for all on-premise VLANs.

## Hardware Specifications
- **Model**: WatchGuard Firebox M390
- **Quantity**: 2 units (active/passive cluster)
- **Form Factor**: 1U rackmount
- **Interfaces**: 
  - 8x 1GbE copper ports (01-07, 00)
  - 2x SFP slots (SFP01, SFP02)

## Cluster Configuration

### High Availability
- **Mode**: Active/Passive
- **Failover**: Automatic (heartbeat monitoring)
- **Sync**: Configuration synchronized between both units

### Management IPs
- **Primary (Active)**: 172.16.219.4
- **Secondary (Passive)**: 172.16.219.5
- **Virtual IP**: Configured for seamless failover

## Interface Assignments

### External Interface
- **Port**: Port 00
- **Connection**: Fiber uplink (ISP)
- **Function**: Internet gateway

### Internal Interfaces
- **VLAN 210**: Domain & WiFi traffic
- **VLAN 211**: Isolated backup network
- **VLAN 212**: Storage network
- **VLAN 213**: Proofing systems
- **VLAN 215**: Security appliances
- **VLAN 219**: Management network
- **VLAN 220**: Trunk to Access Points

### SFP Uplinks
- **SFP01, SFP02**: Fiber connection to Aruba switches (high-speed trunk)

## Network Services

### DHCP Server
The firewall manages DHCP for all production VLANs:
- **VLAN 210**: 172.16.210.10 - 172.16.210.250
- **VLAN 211**: Static assignments only (backup servers)
- **VLAN 212**: 172.16.212.10 - 172.16.212.100
- **VLAN 213**: 172.16.213.10 - 172.16.213.250
- **VLAN 219**: Static assignments only (infrastructure)

### NAT Configuration
- **Outbound NAT**: VLAN 210, 213 have internet access
- **No NAT**: VLAN 211 (isolated), VLAN 212 (storage-only)

### VPN Services

#### Site-to-Site VPN
- **Remote Site**: Budapest office
- **Protocol**: IPsec
- **Encryption**: AES-256
- **Remote Gateway**: WatchGuard T45 (Budapest)
- **Allowed Traffic**: 
  - VLAN 211 (Brussels) ↔ Budapest NAS (backup replication)
  - Management access (172.16.219.x)

#### Azure VPN Gateway Integration
- **Connection Type**: Site-to-Site VPN (Brussels ↔ Azure Hub VNet)
- **Azure Gateway**: VPN Gateway in Hub VNet (10.0.0.0/16)
- **Routing**: Route table directs cloud-bound traffic through Azure VPN

## Security Policies

### Firewall Rules (High-Level)
1. **VLAN 210 → Internet**: Allow HTTPS, DNS, Microsoft 365 services
2. **VLAN 210 → Azure**: Allow via VPN tunnel (Entra ID, SharePoint, Intune)
3. **VLAN 211 → Azure Storage**: Allow HTTPS only (backup traffic)
4. **VLAN 211 → Internet**: Deny (isolated network)
5. **VLAN 213 → Internet**: Allow limited (software updates only)
6. **VLAN 219 → Any**: Allow (management network)
7. **Any → VLAN 211**: Deny (except controlled backup windows)

### Intrusion Prevention
- **IPS Engine**: Enabled on all WAN-facing interfaces
- **Signature Updates**: Automatic (WatchGuard subscription)
- **Gateway AntiVirus**: Enabled for HTTP/HTTPS inspection

### Application Control
- **Microsoft 365**: Allowed and prioritized
- **Cloud Storage (non-Microsoft)**: Blocked (data loss prevention)
- **Remote Desktop**: Allowed only from VLAN 219

## Integration with Veezo Security Layer

### Traffic Flow
```
Internet
    ↓
WatchGuard Firebox M390 (L3 routing, NAT, VPN)
    ↓
Veezo Box 01 & 02 (AI-based packet inspection)
    ↓
Aruba Switches (L2 switching, VLAN distribution)
```

### Veezo Placement Rationale
- **Position**: Post-firewall, pre-switch
- **Visibility**: All internal East-West traffic + North-South traffic
- **Function**: Complement firewall rules with AI-based behavioral analysis
- **Management**: Veezo interfaces on VLAN 215 (Security)

## Monitoring & Logging

### Log Destinations
- **Local Storage**: 30 days retention on firewall itself
- **Syslog Server**: Potential integration with Microsoft Sentinel (future)

### Monitored Events
- VPN connection/disconnection events
- IPS/Gateway AV alerts
- DHCP lease assignments
- Configuration changes

## Backup & Recovery

### Configuration Backup
- **Frequency**: Automatic daily backup
- **Storage**: QNAP NAS (VLAN 211)
- **Retention**: 90 days

### Disaster Recovery
- **RTO**: < 1 hour (passive unit takes over automatically)
- **RPO**: < 5 minutes (real-time configuration sync)

## Management Access

### Allowed Sources
- **VLAN 219**: Full administrative access (SSH, HTTPS)
- **Azure VPN**: Remote admin access from authorized endpoints

### Authentication
- **Local accounts**: Emergency access only
- **RADIUS/LDAP**: Integrated with on-premise Active Directory (legacy phase)
- **Future**: Entra ID integration for admin authentication
