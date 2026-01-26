> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

An offline Windows Server is used to store a final, disconnected copy of backup data. This approach adds an additional layer of protection against ransomware and network-based attacks.

## Purpose

The offline backup server:

- Receives a copy of all backed-up data (both archived files and SharePoint Online content).
- Is disconnected from the network after each backup operation.
- Serves as a "last-resort" recovery point in case of catastrophic failure.

## Security Rationale

By disconnecting the backup server after each backup:

- **Ransomware Protection**: If ransomware infiltrates the network, it cannot reach this disconnected device.
- **Data Integrity**: The offline copy remains untouched and unmodified.
- **Accidental Deletion Protection**: Protects against human errors or misconfigurations.

## Backup Workflow

QNAP NAS (172.16.211.4)
↓ (Network connected)
Windows Backup Server (VLAN 211)
↓
[Copy data]
↓
[Disconnect from network]
↓
[Server remains offline until next backup cycle]

text

## Network Access

- **During Backup**: Server is connected to VLAN 211 (Isolated).
- **After Backup**: Server is disconnected from network and power (optional, depending on procedure).
- **Location**: VLAN 211 (same isolated segment as QNAP and other backup infrastructure).

## Data Stored

The offline server receives copies of:

- Archived files (offloaded from SharePoint Online).
- SharePoint Online backup data (from QNAP NAS).

## Recovery Scenario

In case of catastrophic failure:

1. Reconnect the Windows Backup Server to the network.
2. Recover data from the offline copy.
3. Restore to SharePoint Online, QNAP, or other target.

This ensures that even a complete failure of cloud and on-prem connectivity can be recovered from.

## Operational Considerations

- **Backup Frequency**: Aligned with QNAP backup cycles (automatic scheduling).
- **Verification**: Periodic testing of restore procedures to verify data integrity.
- **Storage Capacity**: Must be sized to accommodate SharePoint Online and archive data volumes.