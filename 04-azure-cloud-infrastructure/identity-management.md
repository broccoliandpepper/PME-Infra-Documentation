# Identity Management (Entra ID)

## Overview

Entra ID (Azure Active Directory) is used as the main identity and access management system in the modern hybrid infrastructure.

It complements and gradually replaces the dependency on on-prem Active Directory.

## Components

- **Entra ID**
  - Cloud-based identity provider.
  - Used for user authentication and access to cloud resources.
  - Integrated with Microsoft 365 and Azure services.

- **On-Prem Active Directory**
  - Legacy on-prem directory.
  - Gradually reduced dependency as devices and services are moved to Entra ID and the cloud.

- **Entra Cloud Connect / Synchronisation**
  - Synchronisation between on-prem identities and Entra ID.
  - Allows hybrid identity scenarios.

## Usage Scenarios

- **User Authentication**
  - For Microsoft 365 (Office, Teams, SharePoint Online, Outlook).
  - For Azure resources such as Web Apps and management portals.

- **External Users**
  - Managed via Entra ID as “Entra Client” in the diagrams.
  - Access controlled by Conditional Access policies.
  - External user must request access through their KCP contact.

## Device Identity

- **Azure AD Join**
  - All devices are planned to be Azure AD joined.
  - Objective: avoid dependency on local Active Directory.
  - Allows Intune to manage devices using cloud-based policies.

## Benefits

- Centralised cloud identity.
- Integration with Conditional Access.
- Foundation for Intune device management and Microsoft Defender for Endpoint integration.
