---
type: Concept
title: CSAF 2.0 Vulnerability Exploitability eXchange (VEX)
description: Profile 5 of CSAF 2.0 enabling vendors to state whether specific products
  are affected, not affected, or under investigation for a CVE.
category: format
tags:
- cvd
- formats
- vex
- csaf
- exploitability
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

The **CSAF VEX Profile** provides standardized, machine-readable machine-processable assertions regarding product vulnerability status[^iso-iec-29147].

# VEX Justifications for Non-Affected Status
- `component_not_present`
- `vulnerable_code_not_present`
- `vulnerable_code_cannot_be_controlled_by_adversary`
- `inline_mitigations_already_exist`

# Related concepts
- [Formats Index](../index.md)
- [CSAF Base Format](../csaf/csaf-base.md)

[^iso-iec-29147]: International Organization for Standardization, ISO/IEC 29147:2018 Information technology - Security techniques - Vulnerability disclosure, https://www.iso.org/standard/72311.html
