---
type: Procedure
title: Vulnerability Embargo Management
description: Principles, operational guidelines, and coordination practices for managing
  disclosure embargos across finders, vendors, and coordinators.
category: procedure
tags:
- process
- embargo
- cvd
- coordination
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: first-cvd-guide
  resource: https://www.first.org/global/sigs/vulnerability-coordination/multiparty/cvd-v1.1
  title: Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1)
  author: Forum of Incident Response and Security Teams (FIRST)
  last_modified: '2020-09-01T00:00:00Z'
- id: iso-iec-30111
  resource: https://www.iso.org/standard/72312.html
  title: "ISO/IEC 30111:2019 Information technology \u2014 Security techniques \u2014\
    \ Vulnerability handling processes"
  author: International Organization for Standardization (ISO) / IEC
  last_modified: '2019-10-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: guidance
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Embargo management** establishes a mutually agreed, temporary window of non-disclosure during which vendors investigate reported vulnerabilities, engineer security patches, and prepare synchronized public advisories[^first-cvd-guide].

# Principles of Embargo Coordination

## Mutual Agreement and Good Faith
Embargos are voluntary agreements between finders, affected vendors, and neutral coordinators. Neither party can unilaterally impose a legally binding embargo in the absence of explicit contractual non-disclosure agreements.

## Target Timelines and Flexibility
1. **Industry Baseline**: While typical industry targets range around 90 days from initial confirmation, actual remediation intervals depend upon vulnerability severity, exploit complexity, hardware dependencies, and downstream supply-chain impact.
2. **Extensions**: Extensions should be negotiated collaboratively when firmware validation, carrier certification, or complex regression testing requires additional time.
3. **Premature Termination**: An embargo is automatically terminated if active in-the-wild exploitation is detected or if vulnerability details are publicly leaked. In such cases, vendors and coordinators immediately transition to emergency advisory publication.

# Related concepts
- [Multi-Party Coordination](multi-party-coordination.md)
- [Advisory Publication](advisory-publication.md)
- [CNA Rules Section 4](../programmes/cve/cna-operational-rules/section-4-cna-operational-rules.md)

[^first-cvd-guide]: Forum of Incident Response and Security Teams (FIRST), Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1), https://www.first.org/global/sigs/vulnerability-coordination/multiparty/cvd-v1.1
[^iso-iec-30111]: International Organization for Standardization (ISO) / IEC, ISO/IEC 30111:2019 Information technology — Security techniques — Vulnerability handling processes, https://www.iso.org/standard/72312.html
