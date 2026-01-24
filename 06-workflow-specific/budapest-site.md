# Budapest Site Infrastructure

## Overview

The Budapest office serves as a secondary operational site for K Creation & Production. It supports remote operations with minimal infrastructure footprint, as most employees work remotely.

## Site Characteristics

- **Usage**: Limited on-site presence (primarily remote work).
- **Infrastructure**: Minimal and cost-optimised.
- **Connectivity**: VPN-based connection to Brussels headquarters.

## Network Infrastructure

### Firewall

| Device | Model | Purpose |
|--------|-------|---------|
| WatchGuard T45 | WatchGuard | Site firewall and gateway |

The WatchGuard T45 provides:

- Local gateway for site traffic.
- Site-to-Site VPN connection to Brussels.
- DHCP and network management.

### Storage

| Device | Model | IP Address (over VPN) | Purpose |
|--------|-------|----------|---------|
| QNAP NAS | QNAP | 172.16.211.10 | Backup storage, receives replication from Brussels |

The QNAP in Budapest:

- Receives backup data from the Brussels QNAP (QNAP-to-QNAP replication over VPN).
- Provides off-site resilience for backup data.
- Uses SMB protocol for replication.

## Connectivity to Brussels

### Site-to-Site VPN

- **Protocol**: IPsec (implied by WatchGuard infrastructure).
- **Encryption**: AES-256 (standard WatchGuard configuration).
- **Endpoint**: WatchGuard Firebox M390 (Brussels) ↔ WatchGuard T45 (Budapest).
- **Allowed Traffic**:
  - Backup replication from Brussels QNAP to Budapest QNAP.
  - Management traffic for remote administration.
  - User access (limited, as most work remotely).

### Traffic Flow

Budapest Users
↓
WatchGuard T45 (local gateway)
↓
Site-to-Site VPN (IPsec)
↓
WatchGuard Firebox M390 (Brussels)
↓
Azure / SharePoint Online / Corporate Services



## User Access

- **Remote Work Model**: Most Budapest employees work from home or off-site.
- **Access to Corporate Resources**:
  - SharePoint Online (cloud-based).
  - Microsoft 365 (cloud-based).
  - On-prem services via VPN (if needed).

## Backup Infrastructure

The Budapest QNAP:

- Receives automatic replication from Brussels QNAP.
- Provides a geographically separated backup copy.
- Reduces single-point-of-failure risk.
- Does not require large local server infrastructure.

## Minimal Footprint Design

The Budapest site is intentionally minimal:

- **No on-site servers** (other than QNAP).
- **No on-site user infrastructure** (VLAN).
- **Primary reliance on cloud services** (SharePoint Online, Microsoft 365).
- **VPN for remote connectivity** to Brussels systems if needed.

This design:

- Reduces operational complexity.
- Lowers costs for a secondary site.
- Supports the company's remote-first work model post-COVID.
- Maintains data resilience through off-site backup.

## Future Considerations

As the company continues cloud-first adoption, the Budapest site can:

- Further reduce on-prem infrastructure.
- Increase reliance on cloud services.
- Maintain VPN connection for legacy systems (if any).
