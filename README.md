# Azure Hybrid Identity Patterns

Practical architecture notes for hybrid identity scenarios involving AD DS, Microsoft Entra ID, Entra Connect, Azure-hosted workloads, and cloud migration decision-making.

> This repository is not a step-by-step deployment guide.  
> It is a collection of architecture patterns, decision points, and migration considerations.


<p align="center">
  <img src="./assets/assets/AzureHybridIdentity.png" alt="Azure Hybrid Identity Patterns" width="100%">
</p>

---

## Why this repository exists

Many Azure migration discussions are not only about moving virtual machines.
They are about understanding identity, DNS, authentication flows, legacy dependencies, and the target operating model.

This repo summarizes common patterns for deciding when to:

- keep workloads cloud-native with Microsoft Entra ID
- extend AD DS into Azure with domain controllers on Azure VMs
- keep AD DS on-prem and connect through VPN/ExpressRoute
- use Entra Connect in staging mode for migration or disaster recovery
- gradually reduce AD DS dependencies over time

---

## Core building blocks

### Microsoft Entra ID

Modern cloud identity platform for SaaS, Azure, conditional access, MFA, app registrations, enterprise applications, OIDC, OAuth2 and SAML-based authentication.

### Active Directory Domain Services

Classic Windows identity platform providing domain join, Kerberos, NTLM, LDAP/LDAPS, Group Policy, AD DNS and traditional service account patterns.

### Domain Controllers on Azure VMs

Writable AD DS domain controllers deployed as Azure virtual machines to provide AD DS, DNS and authentication services close to Azure-hosted workloads.

### Microsoft Entra Connect

Synchronization engine between AD DS and Microsoft Entra ID. Commonly used for hybrid identity scenarios.

### Entra Connect Staging Mode

A prepared Entra Connect server that imports and synchronizes internally but does not export changes. Useful for validation, migration and disaster recovery.

### VPN / ExpressRoute

Connectivity layer between on-premises infrastructure and Azure. Required for hybrid scenarios where systems across both environments need to communicate.

---

## High-level decision question

Before choosing a pattern, clarify the target state:

```text
Are we preserving AD-dependent workloads in Azure,
or are we trying to modernize away from AD DS dependencies?
```

---



