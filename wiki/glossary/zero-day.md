---
type: Glossary
title: Zero-Day Vulnerability
description: A software or hardware flaw known to threat actors or researchers before the vendor has developed or distributed an effective patch.
category: glossary
tags:
- cvd
- glossary
- zero-day
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: cve-glossary
  resource: https://www.cve.org/Resources/General/Glossary
  title: CVE Program Terminology and Glossary
  author: CVE Program
  last_modified: '2024-03-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: voluntary
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Definition

A **zero-day vulnerability** refers to a security defect in software, firmware, or hardware that is publicly discovered, weaponized, or actively exploited before the responsible vendor or maintainer has released an official security update or mitigation[^cve-glossary].

# Impact on Coordinated Disclosure
- **Immediate Threat**: Zero-day disclosures collapse normal voluntary embargo periods; coordinators and vendors shift into emergency out-of-band advisory response mode.
- **KEV Catalog Ingestion**: Observed in-the-wild zero-day exploitation satisfies mandatory criteria for CISA KEV catalog inclusion under BOD 26-04.
- **Mitigation Focus**: When patch engineering requires extended validation, vendors issue temporary workarounds, firewall filters, or attack surface reduction directives.

# Related concepts
- [Glossary Index](index.md)
- [CISA KEV Catalog](../reference-data/kev/kev.md)
- [Embargo Management](../process/embargo-management.md)

[^cve-glossary]: CVE Program, CVE Program Terminology and Glossary, https://www.cve.org/Resources/General/Glossary
