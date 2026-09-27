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

**CSAF Aggregators** are automated intermediary services that regularly crawl known CSAF providers, verify digital signatures, and re-publish consolidated feeds for national or sector-wide consumption[^oasis-csaf-2-0].

# Key Operations
- **Discovery**: Crawls `provider-metadata.json` lists.
- **Integrity Validation**: Verifies OpenPGP signatures against declared keys.
- **Mirroring**: Maintains high-availability mirrors for critical sector incident response teams.

# Related concepts
- [CSAF Distribution](csaf-distribution.md)
- [Provider Metadata](provider-metadata.md)

[^oasis-csaf-2-0]: OASIS Open, Common Security Advisory Framework Version 2.0 (CSAF v2.0), https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
