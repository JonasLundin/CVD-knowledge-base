---
type: Format
title: OpenVEX Specification
description: Minimal, interoperable JSON-LD specification for exchanging Vulnerability Exploitability eXchange (VEX) data.
category: format
tags:
- format
- vex
- openvex
- metadata
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
  authority_level: voluntary
  instrument_status: in_force
  checked_at: '2026-09-27T00:00:00Z'
---

# Summary

**OpenVEX** is a lightweight, embeddable specification designed to assert whether a software product is affected by a given vulnerability[^oasis-csaf-2-0].

# Core Design
- **Minimal Schema**: Focuses strictly on machine-readable status assertions (`not_affected`, `affected`, `fixed`, `under_investigation`).
- **JSON-LD Native**: Compatible with graph and decentralized semantic architectures.
- **PURL Integration**: Uses Package URL (purl) identifiers to link assertions to exact binary artifacts.

# Related concepts
- [CSAF VEX Profile](../csaf/csaf-vex.md)
- [CycloneDX VEX](cyclonedx-vex.md)

[^oasis-csaf-2-0]: OASIS Open, Common Security Advisory Framework Version 2.0 (CSAF v2.0), https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
