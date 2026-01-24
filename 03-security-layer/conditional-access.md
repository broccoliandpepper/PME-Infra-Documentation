# Entra ID Conditional Access

## Overview

Entra ID (Azure Active Directory) is used as the central identity and access management system. Conditional Access policies are enabled to protect access to cloud resources, especially for external users.

## Tenant Structure

The diagrams show:

- **Entra KCP** – The main tenant for K Creation & Production.
- **Entra Client** – External clients accessing KCP resources (e.g. SharePoint Online).

Access is controlled via Conditional Access policies applied in Entra ID.

## External User Access Model

For external users (clients):

1. An external user must request access through their **KCP contact**.
2. Access is granted to specific resources (for example, SharePoint Online) based on business need.
3. Conditional Access policies apply to these external accounts.

This ensures that:

- Only authorised external users gain access.
- Access is traceable to a KCP internal sponsor.
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
- **Veezo** and network segmentation for on-prem traffic control.

Together, they provide:

- Identity-based access control.
- Network and endpoint protection.
- A layered defence model covering cloud and on-prem resources.
