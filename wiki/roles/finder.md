---
type: Role
title: 'Role: Finder (Security Researcher)'
description: Individual, academic, or organization discovering a vulnerability and
  reporting it to the vendor or coordinator in good faith.
category: role
tags:
- cvd
- role
- finder
- researcher
- safe-harbor
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: first-cvd-guide
  resource: https://www.first.org/global/sigs/vulnerability-coordination/multiparty/cvd-v1.1
  title: Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1)
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2020-09-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: rule
  instrument_status: in_force
  provision: ISO/IEC 29147 Clause 4.1
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

A **Finder** (or security researcher / reporter) is an individual, research group, academic institution, or commercial entity that identifies an exploitable vulnerability in an ICT product or service and seeks to report it to the affected vendor, open-source steward, or national CSIRT in good faith.

# Rights, Expectations & Safe Harbor

### 1. Good-Faith Research Parameters
- Does not intentionally compromise the privacy, safety, or availability of systems or user data.
- Avoids exfiltrating data beyond what is strictly necessary to prove a vulnerability exists.
- Provides sufficient reproduction details (e.g. proof-of-concept scripts, step-by-step traces) to allow the vendor to reproduce the flaw.

### 2. Legal Safe Harbor
Finders operating within published CVD policies (e.g. under RFC 9116 or DISA safe-harbor terms) are legally protected against civil litigation or criminal referral under national computer crime laws (e.g. CFAA in the US, Section 202c StGB in Germany).

# Related concepts
- [Vendor PSIRT](vendor-psirt.md)
- [Coordinator](coordinator.md)
- [Intake Channels and Security.txt](../process/intake-and-reporting.md)
- [Legal Safe Harbor](../glossary/safe-harbor.md)

[^first-cvd-guide]: Forum of Incident Response and Security Teams (FIRST), Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1), https://www.first.org/global/sigs/vulnerability-coordination/multiparty/cvd-v1.1
