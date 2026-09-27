---
type: Glossary
title: Proof of Concept (PoC)
description: Demonstration code, exploit payload, or reproducible methodology confirming the practical exploitability of a vulnerability.
category: glossary
tags:
- cvd
- glossary
- proof-of-concept
- exploit
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-12-31T00:00:00Z'
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

A **Proof of Concept (PoC)** is an artifact, demonstration script, or technical documentation proving that a theorized security vulnerability can be executed against a target application or operating environment[^cve-glossary].

# Role in Disclosure and Triage
- **Validation Acceleration**: Providing a minimal, benign PoC allows vendor PSIRTs and CNA coordinators to reproduce defects rapidly without ambiguous back-and-forth communication.
- **Weaponization Risks**: Releasing fully functional weaponized PoCs during an active embargo violates coordinated disclosure agreements and increases malicious exploitation risk.
- **EPSS and CVSS Threat Metrics**: Public availability of PoC exploit code directly increases a vulnerability's EPSS probability score and CVSS Threat metric values.

# Related concepts
- [Glossary Index](index.md)
- [Triage and Validation](../process/triage-and-validation.md)
- [EPSS](../reference-data/epss/epss.md)

[^cve-glossary]: CVE Program, CVE Program Terminology and Glossary, https://www.cve.org/Resources/General/Glossary
