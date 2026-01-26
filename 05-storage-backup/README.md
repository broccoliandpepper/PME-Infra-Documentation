> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

This folder documents the storage and backup architecture, combining cloud and on-prem solutions to ensure data protection, accessibility, and business continuity.

The strategy is designed to:

- Use SharePoint Online as the primary user-facing storage platform.
- Protect data against ransomware and accidental deletion via multiple backup copies.
- Maintain archived data accessible for compliance and historical reference.
- Optimise cloud costs by moving less-frequently accessed data to archive.

## Contents

- `sharepoint-online.md` – Primary storage platform for end users.
- `qnap-backup.md` – QNAP NAS devices used for backup and replication.
- `azure-storage.md` – Azure Storage as cloud backup target with immutability.
- `offline-backup.md` – Windows Server used for offline backup copies.

## Key Components

| Component | Role | Location |
|-----------|------|----------|
| **SharePoint Online** | Primary user-facing storage and collaboration | Cloud (Microsoft 365) |
| **QNAP NAS (Primary Site)** | Backup of SharePoint, replication to Azure, replication to remote site | VLAN 211 (Isolated) |
| **QNAP NAS (Remote Site)** | Remote backup copy, replication from primary site | Remote international site |
| **Azure Storage** | Cloud backup target with immutability enabled | Azure (Public Cloud) |
| **Windows Server** | Offline backup copy (disconnected after backup) | VLAN 211 (Isolated) |

## Design Rationale

**Before cloud migration (Early phases):**

- Heavy on-prem hardware (NetApp, tape library) was required.

**After cloud adoption (Current phase):**

- SharePoint Online reduced the need for heavy on-prem storage.
- On-prem servers are repurposed as a **backup and archive ring**.
- This approach balances cost, resilience, and accessibility.