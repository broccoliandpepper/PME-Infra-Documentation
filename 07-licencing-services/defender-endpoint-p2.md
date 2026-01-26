> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

Microsoft Defender for Endpoint P2 is an add-on licence assigned to all users in addition to Microsoft 365 Business Premium.

It provides advanced endpoint protection, threat detection, and incident response capabilities.

## Why P2 Over P1

Microsoft 365 Business Premium already includes **Defender for Endpoint P1**, which provides basic endpoint protection.

The **P2 upgrade** provides enhanced features:

- Advanced threat protection beyond P1 capabilities.
- Comprehensive security dashboard for administrators.
- Improved monitoring and response workflows.

## Key Capabilities

### Threat Detection & Prevention

- **Endpoint Detection and Response (EDR)**: Continuous monitoring of device behaviour.
- **Behavioural threat analysis**: Detects anomalous activity that may indicate compromise.
- **Advanced attack prevention**: Blocks known and unknown malware, exploits, and zero-days.
- **Network protection**: Blocks connections to malicious IP addresses and domains.

### Vulnerability Management

- **Vulnerability scanning**: Identifies unpatched software and security gaps.
- **Asset inventory**: Centralised view of all managed devices and software.
- **Threat and exposure management**: Risk scoring and remediation guidance.

### Incident Response

- **Unified security dashboard**: Centralised view of all security alerts and incidents.
- **Incident investigation**: Detailed forensics for security events.
- **Response capabilities**: Isolate compromised devices, terminate malicious processes, collect evidence.

### Integration with Intune

Defender for Endpoint P2 integrates with Intune to:

- Enforce compliance policies based on device security state.
- Remediate devices that fall out of compliance.
- Link device health to conditional access decisions.

Example: A device with active malware may be blocked from accessing SharePoint Online until remediated.

## Administrative Dashboard

System administrators have:

- **Real-time visibility**: Security alerts and threats across all endpoints.
- **Clear reporting**: Comprehensive dashboard for monitoring and response.
- **Automation**: Automated response to common threats.
- **API access**: Integration with SIEM tools (e.g. Microsoft Sentinel).

## Scope of Protection

Defender for Endpoint P2 covers:

- **Windows workstations**: Windows 11 devices (primary OS).
- **Application servers**: Windows Server systems running applications.
- **Managed devices**: All devices enrolled in Intune.

## Supported Platforms

- **Windows 10/11**: Full EDR and response capabilities.
- **Windows Server**: Full protection (2016 and later recommended).
- **Mac**: Limited EDR capabilities (depending on M365 subscription tier).
- **Linux**: Limited/emerging support (may vary by plan version).

## Licensing Model

- **Per-user licence**: Assigned to each user across the organisation.
- **Device coverage**: Covers devices enrolled in Intune and Entra ID.
- **Centralised management**: Licences managed via Microsoft 365 admin centre.

## Integration with Other Security Layers

Defender for Endpoint P2 works alongside:

- **AI-based network protection** (on-prem): Complements network-level threat detection.
- **Entra ID Conditional Access**: Device risk signals inform access decisions.
- **Azure Firewall / WatchGuard**: Network-level filtering.

Together, these layers provide:

- Network protection (WatchGuard, AI security appliances).
- Identity protection (Entra ID, Conditional Access).
- Endpoint protection (Defender for Endpoint P2).
- Cloud security (Azure Defender, Sentinel).

## Cost Considerations

By assigning Defender for Endpoint P2 to all users:

- Consistent security posture across the organisation.
- Simplifies licensing and management (single SKU per user).
- Reduces need for third-party endpoint security solutions.
- Integrates with existing Microsoft investment (M365, Azure, Intune).

## Example Scenarios

### Scenario 1: Malware Detection

1. User downloads potentially malicious file.
2. Defender for Endpoint P2 detects and blocks execution.
3. Alert appears in admin dashboard.
4. Administrator is notified.
5. Device remains compliant; no access restriction needed.

### Scenario 2: Unpatched System

1. Device lacks critical security update.
2. Vulnerability assessment flags this in dashboard.
3. Intune compliance policy marks device as non-compliant.
4. Conditional Access may restrict access to sensitive resources.
5. User is prompted to apply updates.

### Scenario 3: Suspected Compromise

1. EDR detects suspicious process behaviour.
2. Alert raised in dashboard with forensic data.
3. Administrator isolates device from network.
4. Device remains offline for investigation.
5. Once remediated, device can be brought back online.