---
type: Rule
title: 'CNA Rules Section 4: CNA Operational Rules'
description: "Core operational requirements governing CVE ID assignment, multi-party\
  \ coordination, and mandatory publication clocks (\xA74.5.1.3, \xA74.5.1.4)."
category: rule
tags:
- cve
- cna-rules
- v4-2-0
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: cve-operational-rules-4-2-0
  resource: https://www.cve.org/Resources/Roles/Cnas/CNA_Rules_v4.2.0.pdf
  title: CVE Numbering Authority (CNA) Operational Rules, Version 4.2.0
  author: CVE Program
  last_modified: '2026-08-25T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: contractual
  instrument_status: in_force
  provision: CNA Rules Section 4
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Section 4 (CNA Operational Rules)** governs the day-to-day assignment, reservation, coordination, and publication of CVE Records[^cve-operational-rules-4-2-0].

# Key Provisions

## §4.2 Assignment Rules
1. **Assignment Criteria (§4.2.1)**: A CVE ID must only be assigned to a vulnerability that meets the CVE Definition of a vulnerability and violates an explicit security policy.
2. **Scope Adherence (§4.2.2)**: A CNA must only assign CVE IDs to products or services within its approved operational scope.
3. **CNA-LR Escalation (§4.2.4)**: If a product is not covered by any scoped CNA, the assignment request is handled by the appropriate CNA of Last Resort (CNA-LR).

## §4.4 Communication and Coordination
CNAs must communicate in good faith with finders, vendors, and coordinators. Coordination must not be used to unreasonably delay disclosure.

## §4.5 Publishing Clocks
1. **Target Publication Clock (§4.5.1.3)**: Once a vulnerability is publicly disclosed, the assigning CNA **SHOULD** publish the associated CVE Record within **24 hours**.
2. **Mandatory Maximum Clock (§4.5.1.4)**: Under no circumstances may a CNA fail to publish a public vulnerability's CVE Record beyond **72 hours** of public disclosure. Failure to publish within 72 hours triggers Root intervention.

## §4.6 Dispute Resolution and Appeals
Disputes between finders and CNAs, or between two CNAs regarding assignment or scope, are escalated to the supervising Root (§4.6.1), with final appeal to the CVE Board Quality Working Group (QWG).

# Related concepts
- [CNA Operational Rules Index](index.md)
- [Section 5: CVE Record Content](section-5-cve-record-content.md)

[^cve-operational-rules-4-2-0]: CVE Program, CVE Numbering Authority (CNA) Operational Rules, Version 4.2.0, https://www.cve.org/Resources/Roles/Cnas/CNA_Rules_v4.2.0.pdf
