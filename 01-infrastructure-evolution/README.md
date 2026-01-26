# 01 - Infrastructure Evolution

> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

This folder documents the evolution of a mid-sized production company's infrastructure from a legacy on-premise environment to a modern hybrid cloud architecture. It is structured into four chronological phases, each describing the context, main components, and key changes introduced.

Contents:

- `README.md` – This overview and timeline.
- `phase1-legacy-onsite.md` – Phase 1: On-site legacy infrastructure.
- `phase2-hybrid-multisite.md` – Phase 2: Hybrid multisite infrastructure.
- `phase3-modern-hybrid.md` – Phase 3: Modern hybrid infrastructure.
- `phase4-optimization.md` – Current optimization and cloud-first usage.

---

## Timeline

- **Phase 1: On-Prem Legacy Infrastructure (Years 1-6)**
  - Single-site on-prem Active Directory.
  - VMware ESX virtualisation.
  - NetApp storage, QNAP NAS.
  - Backup to tape library.
  - Approx. 25 VDI and 35 Mac workstations.
  - Local firewall cluster.

- **Phase 2: Hybrid Multisite Infrastructure (Years 7-11)**
  - Expansion to a **multisite** model:
    - Primary site (Main Office).
    - Secondary datacenter site (DC Site).
    - Remote international site (Site B).
  - VMware Horizon for VDI across sites.
  - Veeam backup (rented, managed by external MSP).
  - QNAP-to-QNAP synchronised backups between sites.
  - On-prem Active Directory remains central.

- **Phase 3: Modern Hybrid Infrastructure (Years 12-17)**
  - Introduction of **Azure** and modern Microsoft stack:
    - Azure Virtual Networks (Hub and Spoke with VNet peering).
    - Azure Firewall and VPN Gateway (including P2S VPN).
    - Azure Storage for backup and data.
  - Entra ID (Azure AD) for identity and access management.
  - Microsoft 365 Business Premium and Defender for Endpoint P2.
  - Microsoft Intune for MDM/MAM and device compliance.
  - SharePoint Online as main data collaboration platform.
  - Gradual move away from dependency on on-prem Active Directory.

- **Phase 4: Optimization & Cloud-First Usage (Year 18+)**
  - SharePoint Online used as primary user-facing storage.
  - Reduced hardware requirements on-prem thanks to cloud adoption.
  - Repurposing on-prem servers as **backup and archive ring**.
  - Structured backup strategy combining:
    - QNAP NAS (Hybrid Backup Sync, Azure Backup).
    - Azure Storage with immutability enabled.
    - Offline Windows Server used for backups and disconnected after jobs.
  - Data cleanup and archiving routines (e.g. every six months) to control cloud storage growth.

---

## File Details

### `phase1-legacy-onsite.md`

Documents the initial infrastructure (Phase 1):

- On-prem Active Directory.
- VMware ESX for server virtualisation.
- NetApp storage and QNAP NAS.
- Tape library backups.
- FireWall cluster.
- Approx. 25 VDI, 35 Mac.
- Application servers and on-prem services.

### `phase2-hybrid-multisite.md`

Covers the move to a hybrid, multisite setup (Phase 2):

- Primary site, secondary datacenter site, remote international site.
- On-prem Active Directory extended.
- VMware Horizon for VDI on multiple sites.
- Veeam backup rented and managed by external MSP.
- Synchronised QNAP-to-QNAP backups.
- Continued use of on-prem application servers and NAS.

### `phase3-modern-hybrid.md`

Describes the introduction of Azure and modern Microsoft cloud services (Phase 3):

- Hybrid infrastructure with on-prem AD and Entra ID.
- Azure Virtual Networks with Hub and Spoke topology.
- Azure Firewall, VPN Gateway (including P2S VPN).
- Azure Storage (including backup usage).
- SharePoint Online and Microsoft 365.
- Intune, Defender, Sentinel, Azure Defender capabilities.
- Transition phase reducing dependency on on-prem AD.

### `phase4-optimization.md`

Focuses on optimisation and rationalisation of resources:

- SharePoint Online as main collaboration and storage platform for end users.
- Reduction of heavy on-prem hardware requirements.
- Reuse of existing hardware as a **backup archive ring**.
- Backup and archiving strategy:
  - QNAP NAS with SharePoint Online backup and replication.
  - Azure Storage with immutability for ransomware protection.
  - Offline Windows Server for final backup copy (disconnected after each backup).
- Dedicated archive server to offload older data from SharePoint while keeping it accessible.

---

## Purpose of This Folder

This folder acts as a **chronological narrative** of the infrastructure evolution:

- Shows how the environment evolved technically and architecturally.
- Highlights key decisions at each phase (virtualisation, multisite, hybrid cloud, optimisation).
- Provides context for other folders (network architecture, security, backup strategy, Azure design).

Each phase file is meant to be self-contained and can be read independently by a recruiter, architect, or technical lead to understand where the infrastructure was at that time and what decisions were made.
