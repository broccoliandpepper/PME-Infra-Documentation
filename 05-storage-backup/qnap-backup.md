> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

QNAP NAS devices are used to back up SharePoint Online data and replicate it across multiple locations for resilience.

## Primary Site QNAP (VLAN 211 - Isolated)

- **Device name**: QNAP Archive / QNAP (as listed in network matrix).
- **IP Address**: 172.16.211.4.
- **Purpose**: Primary backup of SharePoint Online.
- **Location**: Primary office, isolated on VLAN 211 (disconnected from production traffic).

### Hybrid Backup Sync

QNAP Hybrid Backup Sync provides:

- Automatic backup of SharePoint Online to the local QNAP device.
- Scheduled backup jobs (frequency determined by business needs).
- Integration with:
  - SharePoint Online (via HTTPS).
  - Azure Storage (for additional cloud protection).

### Replication to Remote Site

- QNAP-to-QNAP replication over VPN from primary site to remote site.
- Protocol: SMB (Server Message Block).
- Purpose: Off-site copy for disaster recovery.

## Remote Site QNAP

- **Device name**: QNAP Remote Site.
- **IP Address**: 172.16.211.10 (over VPN).
- **Purpose**: Receives replication from primary site QNAP.
- **Network Access**: Over Site-to-Site VPN (WatchGuard).

## Network Isolation

Both QNAP devices are on **VLAN 211 (Isolated)**:

- Separated from production user traffic (VLAN 210).
- Limited connectivity during backup windows.
- HTTPS-only communication to Azure Storage.
- SMB protocol allowed for QNAP-to-QNAP replication.

This isolation:

- Prevents backup operations from affecting user performance.
- Adds a layer of security for sensitive backup data.
- Allows controlled access during scheduled backup times.

## Backup Workflow

SharePoint Online
↓ (HTTPS)
QNAP Primary Site (172.16.211.4)
├─→ (HTTPS) Azure Storage
└─→ (SMB over VPN) QNAP Remote Site (172.16.211.10)

text

## Advantages

- Built-in scheduling and automation.
- Multi-target protection (local, cloud, off-site).
- Integration with Azure for long-term retention.
- Replication for disaster recovery.