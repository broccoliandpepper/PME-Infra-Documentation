> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

This folder documents specialised infrastructure components deployed for specific business workloads and remote sites.

The organization operates in the production industry, which requires:

- **Proofing systems** for color-critical workflows (print preview and validation).
- **Remote site infrastructure** for distributed operations.

## Contents

- `proofing-vlan.md` – Dedicated VLAN 213 for proofing systems.
- `remote-site.md` – Remote office infrastructure and connectivity.

## Key Workloads

| Workload | Location | VLAN | Purpose |
|----------|----------|------|---------|
| **Proofing** | Primary office | 213 | Color-critical design validation |
| **Remote Office** | Remote international site | Multiple (via VPN) | Distributed operations, minimal infrastructure |

## Design Rationale

Specialised workloads are isolated to dedicated network segments to:

- Ensure stable, low-latency performance for critical workflows.
- Prevent interference from general production traffic.
- Manage legacy systems safely (e.g. Windows XP equipment).
- Support remote sites with limited infrastructure footprints.