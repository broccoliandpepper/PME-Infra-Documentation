# Infrastructure Documentation - Portfolio Project

> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Mission

Evolve the infrastructure to meet modern standards and business needs, secure systems and data against current and emerging threats, support users and services with reliability and responsiveness, and maintain operational continuity through proactive monitoring and updates.

## Context

ICT System Engineer role managing the complete infrastructure transition from on-premise to cloud for a mid-sized production company (packaging industry), spanning 3 sites: primary office, secondary datacenter site, and remote international site.

## Timeline

- **Phase 1 (Years 1-6)**: Legacy on-site infrastructure (AD, VMware ESX, NetApp)
- **Phase 2 (Years 7-11)**: Hybrid multisite deployment (VMware Horizon, Veeam)
- **Phase 3 (Years 12-17)**: Modern hybrid infrastructure (Azure migration, Entra ID)
- **Current Phase (Year 18+)**: Cloud-first optimization (SharePoint Online, multi-layer backup)

## Key Technologies

- **Cloud**: Microsoft Azure (Hub-Spoke VNets, Storage, Firewall)
- **Identity**: Entra ID, Conditional Access, MFA
- **Endpoint Management**: Microsoft Intune, Azure AD Join
- **Security**: AI-based network protection, Microsoft Defender for Endpoint P2, Sentinel
- **Productivity**: Microsoft 365 Business Premium (Office, Teams, SharePoint)
- **Backup**: QNAP Hybrid Backup Sync, Azure Storage (immutability), offline Windows Server
- **Network**: WatchGuard Firebox M390 cluster, VLAN segmentation (210-220), Aruba APs

## Repository Structure

Each folder contains a dedicated README with technical details and rationale for design decisions.

infrastructure-documentation/
│
├── README.md # Project overview, mission, timeline
│
├── 01-infrastructure-evolution/
│ ├── README.md # History of 4 phases
│ ├── phase1-legacy-onsite.md # Phase 1: AD on-prem, VMware ESX, NetApp
│ ├── phase2-hybrid-multisite.md # Phase 2: VMware Horizon, Veeam, QNAP sync
│ ├── phase3-modern-hybrid.md # Phase 3: Azure migration, Entra ID, Hub-Spoke
│ └── phase4-optimization.md # Current: SharePoint, backup strategy
│
├── 02-network-architecture/
│ ├── README.md # On-prem network overview
│ ├── vlan-segmentation.md # Detail of 7 VLANs (210-220)
│ ├── watchguard-firewall.md # Firebox M390 cluster config
│ └── network-matrix.md # Complete device mapping
│
├── 03-security-layer/
│ ├── README.md # Overall security strategy
│ ├── ai-protection.md # AI security appliances, capabilities
│ ├── microsoft-defender.md # Defender for Endpoint P2
│ └── conditional-access.md # Entra ID policies
│
├── 04-azure-cloud-infrastructure/
│ ├── README.md # Azure Cloud architecture
│ ├── hub-spoke-topology.md # VNets, peering, subnets
│ ├── identity-management.md # Entra ID, MFA, Azure AD Join
│ ├── endpoint-management.md # Intune (MDM/MAM), compliance policies
│ └── azure-services.md # Sentinel, Defender, Application Gateway
│
├── 05-storage-backup/
│ ├── README.md # Storage and backup strategy
│ ├── sharepoint-online.md # Usage, bi-annual archiving
│ ├── qnap-backup.md # Hybrid Backup Sync, replication
│ ├── azure-storage.md # Immutability, anti-ransomware
│ └── offline-backup.md # Disconnected Windows Server
│
├── 06-workload-specific/
│ ├── README.md # Business-specific infrastructures
│ ├── proofing-vlan.md # VLAN 213: GMG, CMA, Roland, SC-P7000/7500
│ └── remote-site.md # WatchGuard T45, NAS, Site-to-Site VPN
│
├── 07-licensing-services/
│ ├── README.md # Microsoft 365 stack
│ ├── m365-business-premium.md # Office, Teams, SharePoint
│ └── defender-endpoint-p2.md # Licensing and features
│
└── assets/
├── diagrams/ # Architecture diagrams