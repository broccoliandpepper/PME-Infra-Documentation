# VLAN Segmentation Details

## VLAN 210 - Domain & WiFi
**Subnet**: 172.16.210.0/24  
**Gateway**: Managed by WatchGuard Firewall  
**Purpose**: Primary user network for domain-joined workstations and WiFi clients

### Connected Devices
- KCP user workstations (Windows 11, Azure AD joined)
- Mac workstations (35 units)
- WiFi clients via Aruba APs
- Network printers:
  - Canon C165: 172.16.210.231
  - Canon IR 5840: 172.16.210.230
- Dell Server 90TB: 172.16.210.210

### Security Policies
- Full access to SharePoint Online (HTTPS)
- Microsoft Defender for Endpoint P2 enforcement
- Conditional Access policies via Entra ID
- MFA required for external access

---

## VLAN 211 - Isolated
**Subnet**: 172.16.211.0/24  
**Gateway**: Managed by WatchGuard Firewall  
**Purpose**: Isolated network for backup infrastructure and archive storage

### Connected Devices
- Dell Server 40TB: 172.16.211.3 (backup server)
- QNAP Archive: 172.16.211.4
- Dell Server 60TB: 172.16.211.2 (backup server)
- QNAP Budapest: 172.16.211.10 (remote site replication)
- Offline Windows Server (disconnected after backup operations)

### Network Restrictions
- **No direct internet access** (by design)
- Limited connectivity to VLAN 210 (controlled backup windows)
- HTTPS-only communication to Azure Storage
- SMB protocol allowed for QNAP-to-QNAP replication

### Backup Workflows
1. **SharePoint Online → QNAP NAS**: HTTPS protocol via QNAP Hybrid Backup Sync
2. **QNAP → Azure Storage**: HTTPS protocol with immutability enabled
3. **QNAP → Windows Server**: Local offline copy (server disconnected post-backup)
4. **QNAP Brussels → QNAP Budapest**: SMB replication over VPN

---

## VLAN 212 - Storage
**Subnet**: 172.16.212.0/24  
**Gateway**: Managed by WatchGuard Firewall  
**Purpose**: Dedicated high-speed storage network

### Usage
- Historical NetApp storage (legacy phase 1-2)
- Ring backup storage using repurposed hardware post-cloud migration
- iSCSI/NFS traffic isolation from production network

---

## VLAN 213 - Proofing
**Subnet**: 172.16.213.0/24  
**Gateway**: Managed by WatchGuard Firewall  
**Purpose**: Isolated network for packaging proofing systems (color-critical workflows)

### Connected Devices

#### Proofing Servers
- **GMG Server**: Windows 11, IP 172.16.213.40
- **CMA Server**: Windows 11, IP 172.16.213.65

#### Proofing Printers
- **Screen SC-P7000**: 172.16.213.54
- **Screen SC-P7500**: 172.16.213.59
- **Roland VS-300i** (2 units): dedicated IPs
- **INX CP800**: 172.16.213.60

#### Legacy Equipment
- **Cutting Machine**: Windows XP (isolated, no internet access)

### Network Isolation Rationale
- Color-critical workflows require stable, low-latency environment
- Legacy OS (Windows XP) security isolation
- Prevent interference from general production traffic

---

## VLAN 215 - Security
**Subnet**: 172.16.215.0/24  
**Gateway**: Managed by WatchGuard Firewall  
**Purpose**: Security monitoring and appliance management

### Connected Systems
- Veezo security appliances (management interface)
- Potential future SIEM/monitoring tools
- Security event collectors

---

## VLAN 219 - Management
**Subnet**: 172.16.219.0/24 (some devices on 192.168.99.x)  
**Gateway**: Managed by WatchGuard Firewall  
**Purpose**: Out-of-band management for network infrastructure

### Connected Devices
- WatchGuard Firebox M390 Primary: 172.16.219.4
- WatchGuard Firebox M390 Secondary: 172.16.219.5
- Aruba Switch 01: 172.16.219.x (management IP)
- Aruba Switch 02: 172.16.219.x (management IP)
- Dell server iDRAC/iLO interfaces
- QNAP administrative interfaces

### Access Control
- Restricted to IT administrators only
- SSH/HTTPS management protocols
- No user traffic allowed

---

## VLAN 220 - AP Trunk
**Configuration**: Trunk mode (802.1Q)  
**Purpose**: Carry multiple VLANs to Aruba Access Points

### Trunk Configuration
- **Native VLAN**: None (security best practice)
- **Allowed VLANs**: 210 (user WiFi), 219 (AP management)
- **Connection**: Aruba switches → Cisco switches → Access Points

### WiFi SSIDs Mapping
- **Corporate SSID**: VLAN 210 (domain authentication required)
- **Management SSID**: VLAN 219 (admin access only)
