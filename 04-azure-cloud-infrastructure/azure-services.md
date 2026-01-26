> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

Several Azure services are used to support the hybrid infrastructure, storage, security, and connectivity requirements.

## Networking & Security

- **Azure Firewall**
  - Deployed in the Hub VNet.
  - Provides centralised network security and filtering.

- **VPN Gateway**
  - Enables:
    - Site-to-Site VPN with on-prem environments.
    - Point-to-Site (P2S) VPN for remote users.
  - Integrated into the Hub VNet.

- **Application Gateway**
  - Handles web application traffic.
  - Works with Web Apps and public IP workloads in Spoke VNets.

- **Route Tables**
  - Control routing between:
    - Hub and Spoke VNets.
    - Subnets inside each VNet.
  - Ensure traffic flows through Azure Firewall where required.

## Compute

- **Virtual Machines (VMs)**
  - Deployed in Spoke subnets:
    - `192.168.100.0/24`
    - `172.16.100.0/24`
  - Used for application workloads and services.

## Storage & Backup

- **Azure Storage**
  - Used as a backup target:
    - Integrated with QNAP NAS via Hybrid Backup Sync and Azure Backup.
  - Immutability feature is used:
    - Backup data cannot be modified or deleted for a defined period.
    - Strengthens protection against ransomware and accidental deletion.

## Integration with On-Prem

Azure services are integrated with on-prem infrastructure via:

- VPN Gateway for network connectivity.
- Entra ID for identity and access.
- QNAP NAS for Hybrid Backup Sync to Azure Storage.

This forms a consistent hybrid model combining on-prem performance with cloud resilience and security.