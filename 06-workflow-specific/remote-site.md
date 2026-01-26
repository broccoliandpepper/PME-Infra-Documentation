> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

The remote international office serves as a secondary operational site. It supports remote operations with minimal infrastructure footprint, as most employees work remotely.

## Site Characteristics

- **Usage**: Limited on-site presence (primarily remote work).
- **Infrastructure**: Minimal and cost-optimised.
- **Connectivity**: VPN-based connection to primary headquarters.

## Network Infrastructure

### Firewall

| Device | Model | Purpose |
|--------|-------|---------|
| WatchGuard T45 | WatchGuard | Site firewall and gateway |

The WatchGuard T45 provides:

- Local gateway for site traffic.
- Site-to-Site VPN connection to primary site.
- DHCP and network management.

### Storage

| Device | Model | IP Address (over VPN) | Purpose |
|--------|-------|----------|---------|
| QNAP NAS | QNAP | 172.16.211.10 | Backup storage, receives replication from primary site |

The QNAP at remote site:

- Receives backup data from the primary site QNAP (QNAP-to-QNAP replication over VPN).
- Provides off-site resilience for backup data.
- Uses SMB protocol for replication.

## Connectivity to Primary Site

### Site-to-Site VPN

- **Protocol**: IPsec (implied by WatchGuard infrastructure).
- **Encryption**: AES-256 (standard WatchGuard configuration).
- **Endpoint**: WatchGuard Firebox M390 (Primary site) ↔ WatchGuard T45 (Remote site).
- **Allowed Traffic**:
  - Backup replication from primary QNAP to remote QNAP.
  - Management traffic for remote administration.
  - User access (limited, as most work remotely).

### Traffic Flow

Remote Site Users
↓
WatchGuard T45 (local gateway)
↓
Site-to-Site VPN (IPsec)
↓
WatchGuard Firebox M390 (Primary site)
↓
Azure / SharePoint Online / Corporate Services

text

## User Access

- **Remote Work Model**: Most remote site employees work from home or off-site.
- **Access to Corporate Resources**:
  - SharePoint Online (cloud-based).
  - Microsoft 365 (cloud-based).
  - On-prem services via VPN (if needed).

## Backup Infrastructure

The remote site QNAP:

- Receives automatic replication from primary site QNAP.
- Provides a geographically separated backup copy.
- Reduces single-point-of-failure risk.
- Does not require large local server infrastructure.

## Minimal Footprint Design

The remote site is intentionally minimal:

- **No on-site servers** (other than QNAP).
- **No on-site user infrastructure** (dedicated VLAN).
- **Primary reliance on cloud services** (SharePoint Online, Microsoft 365).
- **VPN for remote connectivity** to primary site systems if needed.

This design:

- Reduces operational complexity.
- Lowers costs for a secondary site.
- Supports the organization's remote-first work model.
- Maintains data resilience through off-site backup.

## Future Considerations

As the organization continues cloud-first adoption, the remote site can:

- Further reduce on-prem infrastructure.
- Increase reliance on cloud services.
- Maintain VPN connection for legacy systems (if any).