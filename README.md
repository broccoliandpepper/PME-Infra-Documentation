# PME-Infra-Documentation

Documentation of the evolution of a small business (PME) infrastructure from a legacy on‑premise environment to a modern hybrid cloud architecture, structured in four chronological phases.

![License](https://img.shields.io/github/license/broccoliandpepper/PME-Infra-Documentation)
![Last Commit](https://img.shields.io/github/last-commit/broccoliandpepper/PME-Infra-Documentation)
![Issues](https://img.shields.io/github/issues/broccoliandpepper/PME-Infra-Documentation)
![Topics](https://img.shields.io/github/topics/broccoliandpepper/PME-Infra-Documentation)

---

## 🎯 Overview

This repository documents how a typical SME can move from a legacy, loosely managed on‑prem environment to a more secure and manageable hybrid cloud setup.  
It focuses on pragmatic design choices rather than “greenfield” ideal architectures.  
Each phase describes the context, existing pain points, proposed target design and key changes introduced.  
The goal is to provide reusable patterns for IT admins, consultants and system engineers working with Windows Server, M365, Entra ID and network/security appliances.

---

## 🧩 Phases

The documentation is organised into four main phases (each with its own folder and diagrams):

1. **Phase 1 – Legacy on‑prem**  
   - Flat network, aging servers, limited documentation  
   - Basic backup, weak identity and security hygiene

2. **Phase 2 – Stabilisation & cleanup**  
   - Consolidation of roles and services  
   - Improved backup, monitoring and basic security baselines

3. **Phase 3 – Hybrid cloud introduction**  
   - Integration with Microsoft 365 / Entra ID  
   - Initial hybrid identity, mail and file services

4. **Phase 4 – Modernised hybrid infra**  
   - Segmented network (VLAN/DMZ), hardened endpoints, Intune/Defender  
   - Cloud‑centric identity and access, standardised operations

> The exact structure and names of folders/files are documented in the repo tree so that you can navigate each phase easily.

---

## ✨ What this repository provides

- High‑level **architecture diagrams** and network maps for each phase  
- Detailed **component descriptions** (servers, NAS, firewall, M365 services, security tools)  
- **Change logs** explaining what is introduced, modified or decommissioned at each step  
- Example **workflows** (backup, onboarding, incident handling, license management)  
- Checklists and notes you can adapt for your own SME environments

---

## 🛠️ Tech & prerequisites

This is a **documentation** repository – no code to run – but it is built around:

- Windows Server / Active Directory  
- Microsoft 365 (Exchange Online, SharePoint/OneDrive, Teams)  
- Entra ID, Defender, Intune  
- Network appliances (firewall, VLANs, VPN, DMZ)  
- NAS / storage and backup solutions

You don’t need these products to read the docs, but they help to understand the scenarios.

---

## 🗺️ How to use this repo

1. **Browse by phase**  
   - Start with the `Phase-1` folder to understand the initial situation  
   - Move through `Phase-2`, `Phase-3`, `Phase-4` to see the evolution

2. **Focus on what you need**  
   - Network/security teams: look at diagrams, VLAN/DMZ design, firewall notes  
   - Infra/M365 admins: focus on identity, mail, file and endpoint sections  
   - Project leads: use the phase descriptions and change logs as a roadmap template

3. **Adapt to your context**  
   - Use the checklists and workflows as starting points  
   - Replace products, sizes and constraints with your own

---

## 📐 Architecture & diagrams

For each phase you will typically find:

- A high‑level **logical diagram** (identity, apps, data)  
- A **network topology** diagram (LAN, VLANs, DMZ, remote access)  
- Notes on security controls (firewall rules, endpoint protection, backup strategy)

> You can reuse the structure to document your own environments (for audits, projects, or handover).

---

## 🚧 Limitations & scope

- This is a **reference scenario**, not a vendor‑approved blueprint.  
- Sizing, SKUs and exact products are intentionally generic so it can be reused across SMEs.  
- It focuses on **clarity and practical trade‑offs**, not on perfect zero‑trust implementation.

---

## 🤝 Contributing / feedback

Suggestions, corrections and real‑world feedback are welcome.  
If you use this structure to document your own infra, feel free to open an issue and share what worked or what you changed.

---

## 📄 License

This project is licensed under the license file included in this repository.  
See the [LICENSE](LICENSE) file for details.
