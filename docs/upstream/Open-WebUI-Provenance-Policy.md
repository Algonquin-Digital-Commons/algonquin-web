# Open WebUI Provenance Policy

> Status: Normative import policy; no source imported
> Last reviewed: 2026-09-11

## Decision

ADR-0009 permits evaluation of the BSD-3-Clause-eligible Open WebUI v0.6.5
baseline as an initial interface foundation. It does not authorize copying code
by name or tag alone. No Open WebUI source is part of this repository during the
documentation phase.

## Import gate

Before any import, a pull request SHALL record:

- the canonical upstream URL, exact tag and immutable commit;
- a cryptographic checksum of the reviewed source archive;
- file-level license and copyright inventory;
- imported, removed, generated and vendored file inventory;
- locked dependency graph, license report, SBOM and vulnerability report;
- security review of authentication, sessions, uploads, rendering and plugins;
- WCAG 2.2 AA baseline and remediation plan;
- the downstream patch boundary and update strategy;
- the responsible maintainers and vulnerability response route.

The evidence must prove that every imported file is eligible under its actual
license. Post-v0.6.5 code or assets require a separate licensing decision and ADR.

## Failure path

If the evidence cannot establish compatible, maintainable and secure source, the
team SHALL perform a clean implementation of the PSDC Web specifications. The
Commons API, branding and session contracts remain authoritative regardless of
which UI foundation is selected.
