01 - Infrastructure Evolution

## Overview

This folder documents the evolution of K Creation & Production’s infrastructure from a legacy on-premise environment to a modern hybrid cloud architecture. It is structured into four chronological phases, each describing the context, main components, and key changes introduced.

Contents:

- `README.md` – This overview and timeline.
- `phase1-legacy-onsite.md` – 2008–2014: On-site legacy infrastructure.
- `phase2-hybrid-multisite.md` – 2014–2019: Hybrid multisite infrastructure.
- `phase3-modern-hybrid.md` – 2019–2025: Modern hybrid infrastructure.
- `phase4-optimization.md` – Current optimization and cloud-first usage.

---

## Timeline

- **2008 – 2014 – Phase 1: On-Prem Legacy Infrastructure**
  - Single-site on-prem Active Directory.
  - VMware ESX virtualisation.
  - NetApp storage, QNAP NAS.
  - Backup to tape library.
  - Approx. 25 VDI and 35 Mac workstations.
  - Local firewall cluster.

- **2014 – 2019 – Phase 2: Hybrid Multisite Infrastructure**
  - Expansion to a **multisite** model:
    - Brussels site.
    - Villers-le-Bouillet datacenter site.
    - Budapest site.
  - VMware Horizon for VDI across sites.
  - Veeam backup (rented, managed by Computerland).
  - QNAP-to-QNAP synchronised backups between sites.
  - On-prem Active Directory remains central.

- **2019 – 2025 – Phase 3: Modern Hybrid Infrastructure**
  - Introduction of **Azure** and modern Microsoft stack:
    - Azure Virtual Networks (Hub and Spoke with VNet peering).
    - Azure Firewall and VPN Gateway (including P2S VPN).
    - Azure Storage for backup and data.
  - Entra ID (Azure AD) for identity and access management.
  - Microsoft 365 Business Premium and Defender for Endpoint P2.
  - Microsoft Intune for MDM/MAM and device compliance.
  - SharePoint Online as main data collaboration platform.
  - Gradual move away from dependency on on-prem Active Directory.

- **2025+ – Phase 4: Optimization & Cloud-First Usage**
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

Documents the initial infrastructure (2008–2014):

- On-prem Active Directory.
- VMware ESX for server virtualisation.
- NetApp storage and QNAP NAS.
- Tape library backups.
- FireWall cluster.
- Approx. 25 VDI, 35 Mac.
- Application servers and on-prem services.

### `phase2-hybrid-multisite.md`

Covers the move to a hybrid, multisite setup (2014–2019):

- Brussels, Villers-le-Bouillet datacenter, Budapest.
- On-prem Active Directory extended.
- VMware Horizon for VDI on multiple sites.
- Veeam backup rented and managed by Computerland.
- Synchronised QNAP-to-QNAP backups.
- Continued use of on-prem application servers and NAS.

### `phase3-modern-hybrid.md`

Describes the introduction of Azure and modern Microsoft cloud services (2019–2025):

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

This folder acts as a **chronological narrative** of the infrastructure you managed:

- Shows how the environment evolved technically and architecturally.
- Highlights key decisions at each phase (virtualisation, multisite, hybrid cloud, optimisation).
- Provides context for other folders (network architecture, security, backup strategy, Azure design).

Each phase file is meant to be self-contained and can be read independently by a recruiter, architect, or technical lead to understand where the infrastructure was at that time and what role you had in its evolution.