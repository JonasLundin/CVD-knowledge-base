---
type: Procedure
title: 'Process: Intake Channels and Security.txt'
description: Establishing discoverable intake mechanisms (RFC 9116 security.txt, PGP
  keys, web forms) for vulnerability submission.
category: procedure
tags:
- cvd
- process
- intake
- security-txt
- rfc-9116
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
  provision: ISO/IEC 29147 Clause 5, RFC 9116
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**Intake and Reporting** is the initial phase of the coordinated vulnerability disclosure lifecycle, establishing secure, publicly discoverable channels through which external security researchers (finds) can submit vulnerability reports to a vendor or coordinator.

# Modern Intake Standards: RFC 9116 (security.txt)

The IETF standard **RFC 9116** specifies a machine-readable text file hosted at `/.well-known/security.txt` containing contact and policy details:

```text
Contact: mailto:psirt@example.com
Contact: https://example.com/security/report
Encryption: https://example.com/pgp-key.asc
Acknowledgments: https://example.com/security/hall-of-fame
Policy: https://example.com/security/cvd-policy
Preferred-Languages: en, de, fr
Canonical: https://example.com/.well-known/security.txt
Expires: 2027-12-31T23:59:59.000Z
```

# Intake Handling Procedures

1. **Receipt Acknowledgment**: The vendor PSIRT should automatically acknowledge report submission within **24–72 hours**.
2. **Encrypted Communications**: Provide PGP keys, S/MIME, or TLS-encrypted portal interfaces to protect vulnerability details in transit.
3. **Safe-Harbor Commitment**: Publicly commit to good-faith researcher safe harbor, promising not to initiate civil or criminal legal action against researchers adhering to the policy.

# Related concepts
- [Triage, Reproduction, and Impact Assessment](triage-and-validation.md)
- [Finder (Security Researcher)](../roles/finder.md)
- [Vendor PSIRT](../roles/vendor-psirt.md)
- [Legal Safe Harbor](../glossary/safe-harbor.md)

[^first-cvd-guide]: Forum of Incident Response and Security Teams (FIRST), Guidelines for Coordinated Vulnerability Disclosure (FIRST CVD v1.1), https://www.first.org/global/sigs/vulnerability-coordination/multiparty/cvd-v1.1
