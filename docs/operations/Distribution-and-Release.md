# Distribution and Release

> Status: Normative release specification
> Last reviewed: 2026-09-11

## Channels

PSDC Web is distributed as a standards-based website and installable progressive
web application. Institutions may additionally package the PWA in a platform
wrapper, but ordinary access SHALL NOT require an application store.

## Release artifacts

A release consists of immutable OCI images, versioned static assets, an SBOM,
source and build provenance, checksums, signatures, database migrations where
applicable, release notes, compatibility metadata and rollback instructions.

## Promotion

Development uses synthetic identities and data. Staging exercises the complete
authentication, policy, gateway, session, update and recovery paths. Production
promotion requires passing tests, review of dependency and vulnerability changes,
accessibility evidence, signed artifacts, successful staging rollback and an
approved institution deployment manifest.

Canary or blue-green delivery protects active sessions. The client detects a new
version, finishes or safely interrupts incompatible work, activates the new
service worker only at a controlled boundary, and retains one verified rollback
release. Schema migrations are expand-compatible before old code is removed.

## Operations

Monitor availability, login success, route latency, streaming errors, client
version, contract mismatch, CSP violation, accessibility regressions, saturation
and dependency health without collecting protected content. Support documentation
identifies the institution owner and status channel from signed configuration.
