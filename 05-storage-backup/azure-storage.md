> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

Azure Storage is used as a cloud-based backup target, providing off-site resilience and protection against data loss.

## Integration

Azure Storage is accessed via:

- **QNAP NAS**: Hybrid Backup Sync and Azure Backup.
- **Azure Backup services**: Direct integration for other workloads.

## Key Feature: Immutability

One of the most valuable features of Azure Storage is **immutability**:

- Backup data cannot be modified or deleted for a defined period.
- Provides protection against:
  - Ransomware attacks (malware cannot overwrite backups).
  - Accidental deletion.
  - Insider threats or human error.

## Backup Strategy

Azure Storage serves as:

1. **Long-term backup target** for SharePoint Online data backed up via QNAP.
2. **Immutable copy** that satisfies compliance and data protection requirements.
3. **Off-site resilience** separate from on-prem infrastructure.

## Cost Considerations

Azure Storage costs are optimised through:

- Regular archiving of old SharePoint Online data (every six months).
- Moving less-frequently accessed data to archive tiers if needed.
- Reducing the volume of active data stored in SharePoint Online.

## Access Control

Azure Storage access is:

- Controlled via Azure RBAC (Role-Based Access Control).
- Limited to backup and recovery operations.
- Integrated with Entra ID for authentication.

## Immutability Policy Example

Once a backup is written to Azure Storage with immutability enabled:

- The data is locked for a specified retention period (e.g. 30, 90, or 365 days).
- No deletions or modifications are allowed during this period.
- Even storage administrators cannot bypass this protection.

This strengthens overall resilience against modern threats.