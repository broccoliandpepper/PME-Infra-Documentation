> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

SharePoint Online (part of Microsoft 365) is the main storage and collaboration platform. It serves as the primary user-facing storage, replacing heavy on-prem file servers from previous phases.

## Usage

SharePoint Online provides:

- A central repository for documents and files.
- Multi-platform access (PC, Mac).
- Integration with Microsoft Office applications (Word, Excel, PowerPoint).
- Team collaboration features.

## Data Volume Context

In production environments with large file requirements, the need for substantial storage volumes is fundamental. The shift to remote work has increased demand for cloud storage access, impacting costs significantly.

## Maintenance & Housekeeping

SharePoint Online requires regular maintenance:

- **Cleanup cycles**: Every six months, outdated data is reviewed and cleaned up.
- **Archiving**: Data scheduled for deletion is archived to keep it accessible for future use.
- **Backup protection**: All SharePoint Online data is backed up using QNAP NAS and Azure Storage.

## Backup Targets

Data stored in SharePoint Online is protected via:

1. **QNAP NAS (Hybrid Backup Sync)**
   - Automatic backup of SharePoint Online.
   - Can replicate to other QNAP devices (e.g. remote site).

2. **Azure Storage**
   - Additional backup target.
   - Immutability enabled for ransomware protection.

## Archive Server

A dedicated **Archive Server** is used to:

- Store older data offloaded from SharePoint Online.
- Keep archived files accessible for compliance and historical reference.
- Reduce the volume of data stored in SharePoint Online (cost control).

This approach allows:

- Balancing accessibility and cost.
- Maintaining regulatory compliance.
- Freeing up active storage for current work.