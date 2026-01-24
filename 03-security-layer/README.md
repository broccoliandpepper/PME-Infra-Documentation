# 03 - Security Layer

## Overview

This folder documents the multi-layer security architecture implemented for K Creation & Production. It combines:

- An AI-based predictive protection layer (Veezo appliances) inline on the on-prem network.
- Microsoft Defender–based endpoint protection as part of Microsoft 365 Business Premium + Defender for Endpoint P2.
- Identity-level protection using Entra ID (Azure AD) with Conditional Access for external users.

The goal is to continuously reduce cyber risk, detect vulnerabilities, and protect both on-prem and cloud resources.

## Contents

- `veezo-ai-protection.md` – AI-based predictive network protection (Veezo).
- `microsoft-defender.md` – Endpoint and threat protection based on Microsoft Defender.
- `conditional-access.md` – Entra ID conditional access and external user governance.
