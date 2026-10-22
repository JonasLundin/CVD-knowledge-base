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

**Section 4 (CNA Operational Rules)** governs the core operational mechanics of CVE assignment, multi-party coordination, and public disclosure requirements[^cve-operational-rules-4-2-0].

> [!NOTE]
> **Legal Nature**: Operational mandates under Section 4 contractually govern participating CNAs without constituting statutory obligations.

# Operational Requirements and Publication Mandates

- **Assignment Boundaries**: A CNA may assign CVE IDs exclusively to vulnerabilities falling within its documented, approved scope, verifying that the issue meets the CVE Definition of a vulnerability.
- **Publishing Vulnerability Information (§4.5.2)**: Supplier and participating CNAs must ensure that public vulnerability advisories and security bulletins are accurately disseminated and aligned with the corresponding CVE Records submitted to the CVE registry.
- **Publication Clocks**: Under Section 4.5, once a vulnerability is disclosed publicly, the assigning CNA is obligated to populate and publish the CVE Record without undue delay (target within 24 hours, mandatory maximum threshold triggering Root intervention).
- **Dispute Escalation**: Inter-CNA disagreements over scope collisions or assignment validity escalate through the supervising Root to the CVE Board Quality Working Group (QWG).

# Related concepts
- [CNA Operational Rules Index](index.md)
- [Section 5: CVE Record Content](section-5-cve-record-content.md)

[^cve-operational-rules-4-2-0]: CVE Program, CVE Numbering Authority (CNA) Operational Rules, Version 4.2.0, https://www.cve.org/Resources/Roles/Cnas/CNA_Rules_v4.2.0.pdf
