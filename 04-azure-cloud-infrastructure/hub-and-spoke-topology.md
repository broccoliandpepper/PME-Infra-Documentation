> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

The Azure network infrastructure is built using a Hub-and-Spoke Virtual Network topology. This design connects on-premises environments to Azure while segmenting workloads across different VNets and subnets.

## Virtual Networks

The following VNets and address spaces are configured:

- **Hub VNet**
  - Address space: `10.0.0.0/16`
  - Subnets:
    - `10.0.1.0/24`
    - `10.0.2.0/24`

- **Spoke VNet 1 (Public IP workloads)**
  - Address space: `192.168.0.0/16`

- **Spoke VNet 2 (Private workloads)**
  - Address space: `172.16.0.0/16`
  - Subnets:
    - `192.168.100.0/24`
    - `172.16.100.0/24`

## Core Components

- **Azure Firewall**
  - Deployed in the Hub VNet.
  - Central point for traffic inspection and filtering.

- **VPN Gateway**
  - Deployed in the Hub VNet.
  - Provides connectivity:
    - Between on-prem networks and Azure (site-to-site).
    - For remote users via Point-to-Site (P2S) VPN.

- **Application Gateway**
  - Handles web application traffic.
  - Works together with subnets and public IP workloads.

- **Route Tables**
  - Used to control traffic flows between:
    - Hub and Spoke VNets.
    - Subnets inside each VNet.
  - Ensure that traffic passes through Azure Firewall where required.

## VNet Peering

Hub and Spoke VNets are connected via VNet peering:

- **Hub VNet ↔ Spoke 1**
- **Hub VNet ↔ Spoke 2**

This allows:

- Centralised security and routing via the Hub (Azure Firewall, VPN Gateway).
- Segregation of workloads into different Spokes.

## On-Prem Connectivity

The on-prem networks include:

- `172.16.0.0/16` – Primary office LAN.
- `192.168.0.0/16` – Other on-prem segments.

Connectivity between on-prem and Azure is achieved through:

- VPN Gateway in the Hub VNet.
- Route tables that define which traffic is sent to Azure.

## Resources in Spokes

- **Spoke 1 (Public)**:
  - Public-facing workloads using public IPs.
  - Web App and Application Gateway.

- **Spoke 2 (Private)**:
  - Private workloads without direct public exposure.
  - Virtual Machines (VMs) in subnets such as `192.168.100.0/24` and `172.16.100.0/24`.

## Summary

The Hub-and-Spoke Azure topology provides:

- Centralised security and connectivity via the Hub.
- Separation of public and private workloads into dedicated Spokes.
- Integrated connectivity with on-prem networks for a hybrid infrastructure.