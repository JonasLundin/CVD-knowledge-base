---
type: Format
title: CSAF Trusted Distribution
description: Mechanisms and directory structures for distributing CSAF advisories securely over HTTP.
category: format
tags:
- format
- csaf
- distribution
- rolie
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2027-12-31T00:00:00Z'
sources:
- id: oasis-csaf-2-0
  resource: https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
  title: Common Security Advisory Framework Version 2.0 (CSAF v2.0)
  author: OASIS Open
  last_modified: '2022-11-18T00:00:00Z'
x-cvd:
  jurisdiction: International
  authority_level: standard
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

The **CSAF Distribution Specification** defines how publishers expose machine-readable advisories to automated harvesters and enterprise vulnerability management systems[^oasis-csaf-2-0].

# Distribution Protocols
1. **Directory-Based**: Static HTTP file tree structured by year (e.g., `/csaf/2026/advisory.json`).
2. **ROLIE Feeds**: Resource-Oriented Lightweight Information Exchange (RFC 8322) syndication feeds.
3. **OpenPGP Verification**: Mandatory cryptographic signatures (`.asc`) accompanying every advisory file.

# Related concepts
- [CSAF Aggregators](csaf-aggregators.md)
- [Provider Metadata](provider-metadata.md)

[^oasis-csaf-2-0]: OASIS Open, Common Security Advisory Framework Version 2.0 (CSAF v2.0), https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
