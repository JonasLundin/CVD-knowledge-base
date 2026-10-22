---
type: Role
title: Downstream Distributor
description: Package maintainers, Linux distributions, and cloud platforms packaging and distributing upstream software components.
category: role
tags:
- role
- downstream
- distributor
- packaging
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: first-cvd-guide
  resource: https://www.first.org/global/sigs/vulnerability-coordination/multiparty/guidelines-v1.1
  title: Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1)
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2020-09-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: voluntary
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Downstream distributors** (such as Linux operating system distributions, container registry curators, and cloud managed service providers) receive upstream vulnerability notifications and coordinate backported fixes[^first-cvd-guide].

# Key Coordination Role
- **Private Pre-Notification Lists**: Participating in embargoed security lists (e.g., `linux-distros`).
- **Backporting**: Re-engineering upstream security fixes for long-term support (LTS) release branches.
- **Synchronized Release**: Timing package updates simultaneously with upstream public disclosure.

# Related concepts
- [Multi-Party Coordination](../process/multi-party-coordination.md)
- [Vendor PSIRT](vendor-psirt.md)

[^first-cvd-guide]: Forum of Incident Response and Security Teams (FIRST), Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1), https://www.first.org/global/sigs/vulnerability-coordination/multiparty/guidelines-v1.1
