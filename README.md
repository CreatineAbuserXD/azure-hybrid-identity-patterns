# Azure Hybrid Identity Patterns

Practical architecture notes for hybrid identity scenarios involving AD DS, Microsoft Entra ID, Entra Connect, Azure-hosted workloads, and cloud migration decision-making.

> This repository is not a step-by-step deployment guide.  
> It is a collection of architecture patterns, decision points, and migration considerations.


<p align="center">
  <img src="./assets/AzureHybridIdentity.png" alt="Azure Hybrid Identity Patterns" width="100%">
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

---

## High-level decision question

Before choosing a pattern, clarify the target state:

```text
Are we preserving AD-dependent workloads in Azure,
or are we trying to modernize away from AD DS dependencies?
```

---



