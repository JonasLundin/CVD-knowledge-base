---
type: Format
title: CSAF Provider Metadata
description: Standard JSON discovery document located at /.well-known/csaf/provider-metadata.json declaring advisory distribution endpoints.
category: format
tags:
- format
- csaf
- provider-metadata
- discovery
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

The **`provider-metadata.json`** file is the standard discovery document placed at `https://<domain>/.well-known/csaf/provider-metadata.json` enabling automated discovery of a vendor's CSAF publication environment[^oasis-csaf-2-0].

# Mandatory Contents
- **Publisher**: Name, namespace, and contact information.
- **OpenPGP Keys**: Public key fingerprints and URLs used to sign advisories.
- **Distribution Endpoints**: Base URLs for directory listings and ROLIE feeds.
- **Canonical URL**: The permanent address of the metadata file itself.

# Related concepts
- [CSAF Distribution](csaf-distribution.md)
- [CSAF Aggregators](csaf-aggregators.md)

[^oasis-csaf-2-0]: OASIS Open, Common Security Advisory Framework Version 2.0 (CSAF v2.0), https://docs.oasis-open.org/csaf/csaf/v2.0/os/csaf-v2.0-os.html
