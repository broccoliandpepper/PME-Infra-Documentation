> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

This folder documents the Azure-based cloud infrastructure used as part of the modern hybrid environment (Phase 3 and beyond).

The Azure layer provides:

- Virtual networks with a Hub-and-Spoke topology.
- Secure connectivity between on-prem sites and cloud resources.
- Storage services used for backup and data protection.
- Cloud-based identity and device management through Entra ID and Intune.
- Security services such as Microsoft Defender and Microsoft Sentinel.

## Contents

- `hub-spoke-topology.md` – Virtual Networks, subnets, peering and routing.
- `identity-management.md` – Entra ID (Azure AD), hybrid identity, Conditional Access (link with security).
- `endpoint-management.md` – Intune-based device management and configuration.
- `azure-services.md` – Azure Storage, Azure Firewall, VPN Gateway, and related services.