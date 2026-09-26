# Coordinated Vulnerability Disclosure Knowledge Base

An English-language [Open Knowledge Format (OKF)](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md) bundle covering coordinated vulnerability disclosure as practised and regulated today: the CVE Program and its CNA Operational Rules, the CVE Record Format, the European vulnerability database, advisory and VEX formats, scoring and prioritisation systems, the disclosure process itself, and the EU and national law that frames it.

The bundle will contain concise original summaries with provision-level citations to primary sources. It does not reproduce full legal instruments, rules, guidance documents, or standards.

Current release: **none yet** (`VERSION` 0.0.0)

> **Scaffold:** the manifest, section structure, validator and registers are in place. No concepts have been ingested yet; every section index describes what will go there.

> **General orientation only:** once populated, do not rely on this knowledge base for decisions that determine, demonstrate, or materially affect legal or regulatory compliance. Verify the current primary sources and obtain qualified professional advice before making CVE-assignment, disclosure-timing, embargo, regulatory-reporting, or other compliance-impacting decisions.

## Use With Meerkat

[Meerkat](https://github.com/zegit-zoo/meerkat) can serve the bundle as CLI, MCP, or HTTP without conversion:

```sh
mk --kb-dir . search "publication deadline"
mk --kb-dir . show programmes/cve/cna-operational-rules/section-4-5-publication
mk --kb-dir . list --category law
mk --kb-dir . mcp serve
mk --kb-dir . http serve --port 4004
```

Run these commands from the repository root. The knowledge bundle itself is under `wiki/`; Meerkat's `--kb-dir` reads that content-repository layout. The paths above are the planned concept IDs and resolve once ingestion has reached them.

The Markdown remains usable without Meerkat or any other tool.

## Coverage

The intended corpus includes:

- CNA Operational Rules v4.2.0 and CVE Record Format 5.2.0, CVE Services, Roots and CNA types;
- the ENISA European vulnerability database and CISA KEV;
- CSAF 2.0, OpenVEX and other VEX forms, RFC 9116 security.txt;
- CVSS 4.0, EPSS, SSVC, CWE and product identifiers;
- the disclosure process, roles, and the standards and guidance that describe it;
- the EU and national law that requires or protects disclosure, with pointers into the CRA and NIS2 bundles.

Coverage is measured in `coverage.yaml`. Each gate names a glob over `wiki/`, the expected number of concepts where the corpus is finite, and the count actually present. A missing official source is recorded as a research gap rather than filled by inference.

## Structure

`kb.yaml` declares the bundle's slug, extension key (`x-cvd`), categories and sections. Every section has an `index.md` describing what belongs there.

| Section | Contents |
|---|---|
| [`programmes/`](wiki/programmes/index.md) | Vulnerability identification and cataloguing programmes: the CVE Program with its rules, record format, services and root structure; the ENISA European vulnerability database; CISA's Known Exploited Vulnerabilities catalogue. |
| [`formats/`](wiki/formats/index.md) | Machine-readable advisory, VEX and discovery formats. |
| [`reference-data/`](wiki/reference-data/index.md) | Scoring, prioritisation and identification systems used in disclosure. |
| [`process/`](wiki/process/index.md) | The disclosure lifecycle: intake channels, triage, embargo and coordination including multi-party coordination, advisory publication and updates, safe-harbour terms, bug bounty interfaces, PSIRT operations. |
| [`roles/`](wiki/roles/index.md) | Finder or reporter, vendor or manufacturer, coordinator, CSIRT, CNA, Root, Top-Level Root, Secretariat, Authorized Data Publisher, downstream distributor. |
| [`law/`](wiki/law/index.md) | Legal instruments that require or shape disclosure. EU law is summarised for its disclosure provisions and linked to the sibling bundles for the rest. |
| [`standards/`](wiki/standards/index.md) | ISO/IEC 29147 (disclosure) and ISO/IEC 30111 (handling), ETSI TR 103 838, the FIRST PSIRT Services Framework and CVD guidelines, recorded as identifiers, scope and links. |
| [`guidance/`](wiki/guidance/index.md) | Official and programme guidance on running disclosure. |
| [`jurisdictions/`](wiki/jurisdictions/index.md) | National CVD frameworks: the CSIRT designated as coordinator under NIS2 Article 12(1), national policies, safe-harbour status. |
| [`timeline/`](wiki/timeline/index.md) | CNA Operational Rules and Record Format versions, ENISA Root establishment, EUVD launch, CVSS and EPSS releases, CRA and NIS2 dates that touch disclosure. |
| [`glossary/`](wiki/glossary/index.md) | Terms as defined by the CVE Program glossary, ISO/IEC 29147 and 30111, and EU law where they differ. |

## Source And Publication Policy

- Binding claims cite the CVE Program's published rules and schemas, the OJEU or EUR-Lex for EU law, an official national gazette, or the publishing organisation's official specification site.
- Official guidance is labelled non-binding.
- A standard provides presumption of conformity only when its reference is cited in the OJEU for the requirements concerned.
- Publicly accessible drafts are linked, not copied.
- CVE Records themselves are never republished; concepts cite the record identifier and link to cve.org.
- Programme rules are summarised per numbered section so that a citation names the section a claim rests on.
- Agent-generated content stays `status: draft` until a human verifies it against the cited source.
- Superseded material is retained and marked rather than silently deleted.

This repository is not legal advice, is not a conformity assessment, does not certify any product or organisation, and must not be used as the basis for compliance-impacting decisions.

## Validate

```sh
python3 -m pip install -r requirements-dev.txt
python3 -m unittest tools/test_validate.py
python3 tools/validate.py wiki
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Corrections with exact primary-source citations are welcome. Do not submit copied standards text, private compliance evidence, or confidential information.

## Related Knowledge Bases

- [CRA-knowledge-base](https://github.com/JonasLundin/CRA-knowledge-base): Regulation (EU) 2024/2847, the Cyber Resilience Act
- [NIS2-knowledge-base](https://github.com/JonasLundin/NIS2-knowledge-base): Directive (EU) 2022/2555 and its national transpositions
- [AI-Act-knowledge-base](https://github.com/JonasLundin/AI-Act-knowledge-base): Regulation (EU) 2024/1689 as amended
- [Conformity-Assessment-knowledge-base](https://github.com/JonasLundin/Conformity-Assessment-knowledge-base): the New Legislative Framework, modules, accreditation and notified bodies
- [Software-Supply-Chain-knowledge-base](https://github.com/JonasLundin/Software-Supply-Chain-knowledge-base): SBOM formats, attestation, provenance and VEX
- [NIST-CSF-knowledge-base](https://github.com/JonasLundin/NIST-CSF-knowledge-base): NIST Cybersecurity Framework 2.0
- [knowledge-base-template](https://github.com/JonasLundin/knowledge-base-template): the shared template every bundle in the series is built from

## Licence

Original summaries, structure, and metadata are licensed under [CC BY 4.0](LICENSE). Source documents, rules, specifications and standards retain their own terms; see [NOTICE](NOTICE).

This project is independent and is not affiliated with or endorsed by The MITRE Corporation, the CVE Program, ENISA, CISA, CERT/CC, FIRST, OASIS, the European Commission, ISO, IEC, ETSI, Google Cloud, or Meerkat. Repository: https://github.com/JonasLundin/CVD-knowledge-base
