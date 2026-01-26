> **Disclaimer**: This document is a representation of previous professional missions and technical work for portfolio and educational purposes only. The information has been anonymized in compliance with data protection regulations. The author is not responsible for any use, interpretation, or implementation of the content described herein. This document does not constitute professional advice and should not be used as a basis for infrastructure decisions without proper assessment and validation.

## Overview

This folder documents the multi-layer security architecture implemented for a mid-sized production company. It combines:

- An AI-based predictive protection layer (security appliances) inline on the on-prem network.
- Microsoft Defender–based endpoint protection as part of Microsoft 365 Business Premium + Defender for Endpoint P2.
- Identity-level protection using Entra ID (Azure AD) with Conditional Access for external users.

The goal is to continuously reduce cyber risk, detect vulnerabilities, and protect both on-prem and cloud resources.

## Contents

- `veezo-ai-protection.md` – AI-based predictive network protection layer.
- `microsoft-defender.md` – Endpoint and threat protection based on Microsoft Defender.
- `conditional-access.md` – Entra ID conditional access and external user governance.