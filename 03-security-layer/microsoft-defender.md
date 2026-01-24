# Microsoft Defender Security Layer

## Overview

K Creation & Production uses Microsoft Defender as a core part of its endpoint and threat protection strategy. This is built on:

- **Microsoft 365 Business Premium** licences for all users.
- **Microsoft Defender for Endpoint P2** add-on.

## Licensing

- All users are assigned the same licence:
  - Microsoft 365 Business Premium.
  - Microsoft Defender for Endpoint P2.

Microsoft 365 Business Premium provides:

- Office applications.
- Teams.
- SharePoint Online.
- Outlook.
- Other core productivity tools used across departments (Accounting, HR, Production, etc.).

Defender for Endpoint P1 is already included in Business Premium, but the environment uses the **P2 upgrade** for enhanced capabilities.

## Why Defender for Endpoint P2

According to the documentation:

- P2 offers enhanced features on top of P1.
- It provides system administrators with:
  - Advanced threat protection.
  - A clear, comprehensive dashboard for monitoring and response.

This allows:

- Better visibility on endpoint security.
- Improved incident response capabilities.
- Centralised management of security incidents across devices.

## Integration with Intune and Entra ID

Microsoft Defender works together with:

- **Intune**:
  - Device compliance policies.
  - Security baselines (firewall, antivirus, BitLocker).
  - Remote deployment of security configurations.
- **Entra ID**:
  - Device identity (Azure AD join).
  - Security group-based access control.

This combination enables:

- Consistent enforcement of security policies on all managed devices.
- Integration of threat signals into device compliance and conditional access decisions.

## Scope

The Defender layer covers:

- Windows devices (e.g. Windows 11 workstations and servers).
- Devices enrolled and managed through Intune.
- Environments linked to Microsoft 365 services (SharePoint, Teams, Exchange Online).

It complements:

- The network security provided by WatchGuard and Veezo.
- The identity and access management implemented via Entra ID and Conditional Access.
