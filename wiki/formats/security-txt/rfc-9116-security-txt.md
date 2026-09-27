---
type: Format
title: 'RFC 9116: A File Format to Aid in Security Vulnerability Disclosure'
description: Internet Standard establishing the /.well-known/security.txt machine-readable discovery mechanism for vulnerability disclosure policies.
category: format
tags:
- format
- rfc-9116
- security-txt
- discovery
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: rfc-9116
  resource: https://www.rfc-editor.org/rfc/rfc9116
  title: 'RFC 9116: A File Format to Aid in Security Vulnerability Disclosure'
  author: Internet Engineering Task Force (IETF)
  last_modified: '2022-04-01T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: voluntary
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**RFC 9116** specifies a standardized text file placed at `/.well-known/security.txt` enabling security researchers to quickly identify an organization's vulnerability reporting contacts and coordinated disclosure policies[^rfc-9116].

# Field Specifications

## Mandatory Fields
- **`Contact:`**: URI indicating reporting email address (`mailto:`) or web intake form (`https://`). Must be present.
- **`Expires:`**: Timestamp indicating when the policy expires and must be reviewed.

## Standard Optional Fields
- **`Canonical:`**: The official, authoritative URL where this `security.txt` file is hosted.
- **`Encryption:`**: Link to the organization's PGP public key or S/MIME certificate.
- **`Acknowledgements:`**: Link to the hall of fame or contributor recognition page.
- **`Policy:`**: Direct URL to the organization's Coordinated Vulnerability Disclosure policy.
- **`Hiring:`**: Link to career opportunities within the security team.
- **`Preferred-Languages:`**: Comma-separated list of natural language tags (RFC 5646) preferred for vulnerability reports (e.g., `en, fr, sv`).

# Related concepts
- [Formats Index](../index.md)
- [Intake and Reporting](../../process/intake-and-reporting.md)

[^rfc-9116]: Internet Engineering Task Force (IETF), RFC 9116: A File Format to Aid in Security Vulnerability Disclosure, https://www.rfc-editor.org/rfc/rfc9116
