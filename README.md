# PME- Infrastructure Documentation

## Mission
Evolve the infrastructure to meet modern standards and business needs, secure systems and data against current and emerging threats, support users and services with reliability and responsiveness, and maintain operational continuity through proactive monitoring and updates.

## Context
ICT System Engineer role managing the complete infrastructure transition from on-premise to cloud for K Creation & Production (packaging industry), spanning 3 sites: Brussels, Villers-le-Bouillet datacenter, and Budapest.

## Timeline
- **2008-2014**: Legacy on-site infrastructure (AD, VMware ESX, NetApp)
- **2014-2019**: Hybrid multisite deployment (VMware Horizon, Veeam)
- **2019-2025**: Modern hybrid infrastructure (Azure migration, Entra ID)
- **Current**: Cloud-first optimization (SharePoint Online, multi-layer backup)

## Key Technologies
- **Cloud**: Microsoft Azure (Hub-Spoke VNets, Storage, Firewall)
- **Identity**: Entra ID, Conditional Access, MFA
- **Endpoint Management**: Microsoft Intune, Azure AD Join
- **Security**: Veezo AI protection, Microsoft Defender for Endpoint P2, Sentinel
- **Productivity**: Microsoft 365 Business Premium (Office, Teams, SharePoint)
- **Backup**: QNAP Hybrid Backup Sync, Azure Storage (immutability), offline Windows Server
- **Network**: WatchGuard Firebox M390 cluster, VLAN segmentation (210-220), Aruba APs

## Repository Structure
Each folder contains a dedicated README with technical details and rationale for design decisions.

kcp-infrastructure-documentation/
│
├── README.md                          # Vue d'ensemble du projet, mission, timeline
│
├── 01-infrastructure-evolution/
│   ├── README.md                      # Historique des 4 phases (2008-2025)
│   ├── phase1-legacy-onsite.md        # 2008-2014: AD on-prem, VMware ESX, NetApp
│   ├── phase2-hybrid-multisite.md     # 2014-2019: VMware Horizon, Veeam, QNAP sync
│   ├── phase3-modern-hybrid.md        # 2019-2025: Azure migration, Entra ID, Hub-Spoke
│   └── phase4-optimization.md         # Actuel: SharePoint, backup strategy
│
├── 02-network-architecture/
│   ├── README.md                      # Vue d'ensemble réseau on-prem
│   ├── vlan-segmentation.md           # Détail des 7 VLANs (210-220)
│   ├── watchguard-firewall.md         # Config cluster Firebox M390
│   └── network-matrix.png             # Schéma (extrait du PDF)
│
├── 03-security-layer/
│   ├── README.md                      # Stratégie de sécurité globale
│   ├── veezo-ai-protection.md         # Veezo appliances, capabilities
│   ├── microsoft-defender.md          # Defender for Endpoint P2
│   └── conditional-access.md          # Entra ID policies
│
├── 04-azure-cloud-infrastructure/
│   ├── README.md                      # Architecture Cloud Azure
│   ├── hub-spoke-topology.md          # VNets, peering, subnets
│   ├── identity-management.md         # Entra ID, MFA, Azure AD Join
│   ├── endpoint-management.md         # Intune (MDM/MAM), compliance policies
│   └── azure-services.md              # Sentinel, Defender, Application Gateway
│
├── 05-storage-backup/
│   ├── README.md                      # Stratégie de stockage et backup
│   ├── sharepoint-online.md           # Utilisation, archivage semestriel
│   ├── qnap-backup.md                 # Hybrid Backup Sync, réplication
│   ├── azure-storage.md               # Immutabilité, anti-ransomware
│   └── offline-backup.md              # Serveur Windows déconnecté
│
├── 06-workload-specific/
│   ├── README.md                      # Infrastructures métier spécifiques
│   ├── proofing-vlan.md               # VLAN 213: GMG, CMA, Roland, SC-P7000/7500
│   └── budapest-site.md               # WatchGuard T45, NAS, VPN BO
│
├── 07-licensing-services/
│   ├── README.md                      # Stack Microsoft 365
│   ├── m365-business-premium.md       # Office, Teams, SharePoint
│   └── defender-endpoint-p2.md        # Licensing et features
│
└── assets/
    ├── diagrams/                      # Schémas d'architecture

