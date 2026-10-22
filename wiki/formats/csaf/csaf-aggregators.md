---
type: Format
title: CSAF Aggregators
description: Synchronized services that harvest, validate, and mirror CSAF feeds across multiple vendors.
category: format
tags:
- format
- csaf
- aggregator
- mirroring
status: draft
generated:
  by: manual-curation
  at: '2026-09-27T00:00:00Z'
stale_after: '2028-06-30T00:00:00Z'
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

**CSAF Aggregators** are automated distribution components specified within the OASIS Common Security Advisory Framework (CSAF) Version 2.0 that collect, mirror, and index CSAF documents published across multiple independent security vendors[^oasis-csaf-2-0].

# Operational Architecture and Verification

An aggregator discovers vendor security advisories by crawling `provider-metadata.json` endpoints across trusted domains. It verifies the cryptographic OpenPGP signatures of each retrieved document, validates structural compliance against normative JSON schemas, and compiles unified mirror indexes (such as `aggregator.json`). This centralized indexing enables downstream vulnerability scanners, national CSIRTs, and enterprise asset management systems to ingest all vendor advisories across Europe and international supply chains through standardized, authenticated interfaces without polling hundreds of individual vendor portals.

# Related concepts
- [CSAF Formats Index](index.md)
- [CSAF Advisories](csaf-security-advisory.md)
- [CSAF Trusted Providers](provider-metadata.md)

[^oasis-csaf-2-0]: OASIS Open, Common Security Advisory Framework Version 2.0 (CSAF v2.0), https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
