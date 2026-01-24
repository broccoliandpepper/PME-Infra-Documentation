# Veezo AI-Based Predictive Protection

## Role in the Architecture

Two Veezo appliances are deployed between the WatchGuard Firebox M390 firewall and the Aruba switches. All traffic between the firewall and the internal network passes through this layer, allowing Veezo to:

- Analyse all network packets in real time.
- Detect vulnerabilities and security gaps.
- Block malicious activity proactively.

This creates an AI-based predictive protection bridge across the network infrastructure.

## Key Capabilities (as described by Veezo)

### 1. AI-Based Predictive Protection

- Defines and continuously updates security rules and detection engines.
- Acts as an adaptive and transparent bridge across the network.
- Proactively identifies vulnerabilities and closes security gaps.
- Monitors active threats and applies stricter security policies where needed.
- Blocks malicious activity instantly to keep the network environment protected.

### 2. Real-Time Risk Mitigation

- Designed to reduce the risk of cyber-attacks and hacking in a highly digitalised environment.
- Provides instant response to malicious threats.
- Maintains a permanent audit of the security situation and real-time position of overall security.
- Helps communicate clearly with management by providing concise assessments of cyber risks.

### 3. Continuous Vulnerability Diagnosis

Veezo continuously diagnoses the infrastructure for vulnerabilities, focusing on:

- Unauthorised VPN access from devices.
- Human errors (e.g. temporary permission changes, overly permissive rules).
- Excessive exposure through unnecessary open ports.
- Unpatched devices and applications.
- Weaknesses related to unmanaged devices.
- Suspicious or dangerous behaviour such as phishing attempts.

By reporting in these areas, Veezo helps organisations address threats proactively and improve their security posture.

### 4. Community-Based Improvement

- The **Veezo Community** contributes to better accuracy and efficiency over time.
- Collective intelligence improves detection capabilities and pattern recognition.

## Placement in the Network

Veezo is positioned inline between:

- **Upstream**: WatchGuard Firebox M390 (L3 routing, VLANs, VPN, NAT).
- **Downstream**: Aruba switches (L2 switching, VLAN distribution).

This gives Veezo visibility on:

- North–South traffic (Internet ↔ internal network).
- East–West traffic (between VLANs and internal systems).

## Management

- Veezo appliances are part of the security VLAN/management segment.
- They provide dashboards and reporting for:
  - Vulnerabilities.
  - Dangerous behaviour.
  - Exposure and misconfigurations.

Reference: https://veezo.org/whatuk.html (link included in original diagram).
