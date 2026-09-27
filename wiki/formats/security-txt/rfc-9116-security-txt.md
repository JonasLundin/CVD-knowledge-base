---
type: Concept
title: RFC 9116 security.txt File Format
description: Standardized text file hosted at /.well-known/security.txt defining vulnerability
  reporting contacts, encryption keys, and policy links.
category: format
tags:
- cvd
- formats
- security-txt
- rfc-9116
- discovery
status: draft
generated:
  by: agent:kb-researcher-writer
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: iso-iec-29147
  resource: https://www.iso.org/standard/72311.html
  title: ISO/IEC 29147:2018 Information technology - Security techniques - Vulnerability
    disclosure
  author: International Organization for Standardization
  last_modified: '2018-10-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: binding
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**RFC 9116** defines **security.txt**, a standardized machine-readable text file hosted under `/.well-known/security.txt` that allows security researchers to easily find contact information, disclosure policies, and public encryption keys[^iso-iec-29147].

# Mandatory and Recommended Directives
- `Contact:` (Mandatory) URI specifying email address, web form, or reporting portal.
- `Expires:` (Mandatory) Timestamp indicating when the information in the file must be renewed.
- `Encryption:` PGP key or key server link for secure submissions.
- `Policy:` Link to the organization's coordinated vulnerability disclosure policy.
- `Acknowledgments:` Page recognizing researchers who reported verified vulnerabilities.

# Related concepts
- [Formats Index](../index.md)
- [Intake and Reporting](../../process/intake-and-reporting.md)

[^iso-iec-29147]: International Organization for Standardization, ISO/IEC 29147:2018 Information technology - Security techniques - Vulnerability disclosure, https://www.iso.org/standard/72311.html
