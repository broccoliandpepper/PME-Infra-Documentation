# Endpoint Management (Intune)

## Overview

Microsoft Intune is used for Mobile Device Management (MDM) and Mobile Application Management (MAM). It replaces many traditional on-prem Group Policy functions.

## Scope

- All users have:
  - Microsoft 365 Business Premium licence.
  - Microsoft Defender for Endpoint P2 add-on.

This provides:

- Productivity tools (Office, Teams, SharePoint Online, Outlook).
- Security and management capabilities tied to Intune and Defender.

## Intune Usage

According to the documentation:

- Intune is used to:
  - Deploy applications (e.g. Office, TeamViewer).
  - Apply compliance policies.
  - Configure:
    - BitLocker.
    - Firewall.
    - Antivirus settings.
  - Manage device configurations remotely via cloud security groups.

## Replacement of GPOs

Intune allows replication of many functions traditionally handled by on-prem Active Directory Group Policies:

- Configuration deployment.
- Security baselines.
- Compliance enforcement on devices.

## Users & Devices Configuration

- All users are assigned:
  - Microsoft 365 Business Premium.
  - Defender for Endpoint P2.

This setup:

- Standardises the environment across departments (Accounting, HR, Production, etc.).
- Provides administrators with a central dashboard for monitoring security and compliance.
