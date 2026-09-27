---
type: Format
title: CycloneDX VEX Formulation
description: Embedded vulnerability exploitability metadata within OWASP CycloneDX Software Bill of Materials (SBOM).
category: format
tags:
- format
- vex
- cyclonedx
- sbom
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

**CycloneDX VEX** enables organizations to embed vulnerability status assertions directly inside an OWASP CycloneDX Software Bill of Materials (SBOM)[^oasis-csaf-2-0].

# Capabilities
- **Co-located BOM & VEX**: Directly links components to exploitability states inside a single manifest.
- **Analysis State**: Records analysis state (`resolved`, `not_affected`, `in_triage`, `exploitable`) and remediation recommendations.
- **Justification Support**: Matches CSAF and OpenVEX justifications for false positive elimination.

# Related concepts
- [OpenVEX](openvex.md)
- [CSAF VEX](../csaf/csaf-vex.md)

[^oasis-csaf-2-0]: OASIS Open, Common Security Advisory Framework Version 2.0 (CSAF v2.0), https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
