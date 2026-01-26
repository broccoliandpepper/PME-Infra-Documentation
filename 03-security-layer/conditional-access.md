> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

Entra ID (Azure Active Directory) is used as the central identity and access management system. Conditional Access policies are enabled to protect access to cloud resources, especially for external users.

## Tenant Structure

The architecture includes:

- **Primary Tenant** – The main organizational tenant.
- **External Client Tenants** – External clients accessing organizational resources (e.g. SharePoint Online).

Access is controlled via Conditional Access policies applied in Entra ID.

## External User Access Model

For external users (clients):

1. An external user must request access through their **internal contact**.
2. Access is granted to specific resources (for example, SharePoint Online) based on business need.
3. Conditional Access policies apply to these external accounts.

This ensures that:

- Only authorised external users gain access.
- Access is traceable to an internal sponsor.
- Permissions are limited to the required resources.

## Conditional Access Objectives

Key goals of Conditional Access in this environment include:

- Enforcing Multi-Factor Authentication (MFA) for users where needed.
- Controlling access to:
  - SharePoint Online.
  - Microsoft 365 applications.
- Applying policies depending on:
  - User type (internal vs external).
  - Device state (managed vs unmanaged, via Intune).
  - Risk level signalled by Microsoft security tools.

## Relation to Other Security Layers

Conditional Access works alongside:

- **Microsoft Defender for Endpoint P2** for device and threat signals.
- **Intune** for device compliance status.
- **AI security appliances** and network segmentation for on-prem traffic control.

Together, they provide:

- Identity-based access control.
- Network and endpoint protection.
- A layered defence model covering cloud and on-prem resources.