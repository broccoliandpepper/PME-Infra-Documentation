# 06 - Workload-Specific Infrastructure

## Overview

This folder documents specialised infrastructure components deployed for specific business workloads and remote sites.

K Creation & Production operates in the packaging industry, which requires:

- **Proofing systems** for color-critical workflows (print preview and validation).
- **Remote site infrastructure** in Budapest for distributed operations.

## Contents

- `proofing-vlan.md` – Dedicated VLAN 213 for packaging proofing systems.
- `budapest-site.md` – Budapest office infrastructure and remote connectivity.

## Key Workloads

| Workload | Location | VLAN | Purpose |
|----------|----------|------|---------|
| **Proofing** | Brussels office | 213 | Color-critical package design validation |
| **Remote Office** | Budapest | Multiple (via VPN) | Distributed operations, minimal infrastructure |

## Design Rationale

Specialised workloads are isolated to dedicated network segments to:

- Ensure stable, low-latency performance for critical workflows.
- Prevent interference from general production traffic.
- Manage legacy systems safely (e.g. Windows XP equipment).
- Support remote sites with limited infrastructure footprints.
