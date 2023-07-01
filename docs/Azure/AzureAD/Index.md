---
title: Azure AD DS and self-managed AD DS
categories: 
  - "azuread"
---

- `Managed Domain` using AD DS. Microsoft creates and manages resources
- `Self-Managed` Legacy resources like VM, Windows Server, Guest OS and OnPrem AD DS.
{: .msg-info}

### Why to choose `Managed AD DS`
- `small subset` of features. There are no complexities like `AD Forests`, `Domain Sites` and `Replication Links`
- Supports Legacy Auth mechanism like `NTLM` and `Kerberos`

### Why to choose `Self Managed AD DS`
- Extend capabilities like `AD Forests Trusts`, `Domain Sites` etc.

### Deployment models for `Self-Managed AD DS`
- `Standalone cloud only AD-DS`
    - No Connection with OnPrem AD DS. Sepearte Credentials required to login
- `Resource Forest deployment`
    - Join and Create existing AD Forest
    - Connect OnPrem AD DS using Express Routes or VPN
- `Extend OnPremise Domain to Azure`
    - 