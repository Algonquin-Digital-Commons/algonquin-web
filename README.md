# PSDC Web

The institution-neutral browser and progressive-web client for the Post Secondary
Digital Commons. This repository owns the web experience, its browser-facing
backend boundary, accessibility conformance, branding contract, and release
specifications. It does not own AI inference, identity authority, academic data,
compute scheduling, social servers, or media processing.

> Status: Documentation and architecture complete; implementation not started

## Product scope

The client provides one coherent entry point for:

- landing, discovery, help, consent, privacy, and account controls;
- Chat for policy-routed AI conversations;
- Study for institution-authorized academic assistance;
- Work for tools, files, plans, and accountable agent actions;
- Code for repository-aware development sessions;
- Campus for services, clubs, events, navigation, and notifications;
- cross-device session continuity with the desktop and mobile clients.

## Required boundaries

```text
Browser / installable PWA
        |
        v
PSDC Web BFF and session boundary
        |
        v
Commons gateways and versioned domain contracts
        |
        +-- identity broker and policy
        +-- AI gateway
        +-- academic service
        +-- session relay
        +-- media and social APIs
        +-- campus services
```

The browser SHALL NOT connect directly to model runtimes, institutional identity
providers, LMS databases, compute workers, storage databases, or upstream social
application databases. The BFF uses secure, HTTP-only, same-site session cookies;
OIDC authorization code with PKCE terminates at the governed session boundary.

## Repository responsibilities

| Owns | Does not own |
|---|---|
| Browser UI shell and navigation | AI models or inference engines |
| Web BFF and browser session security | Institutional identity authority |
| Accessibility and responsive behaviour | Academic source-of-truth data |
| Branding and theme contract | Compute scheduling or worker control |
| Client-side state and offline-safe rules | Fediverse servers or moderation authority |
| Web release and PWA packaging | Media transformation pipelines |
| Contract adapters and client conformance tests | Sibling-domain databases |

## Architecture documents

- [Web Client Architecture](docs/architecture/Web-Client-Architecture.md)
- [Experience and Feature Scope](docs/product/Experience-and-Feature-Scope.md)
- [Browser Security and Privacy](docs/security/Browser-Security-and-Privacy.md)
- [Distribution and Release](docs/operations/Distribution-and-Release.md)
- [Open WebUI Provenance Policy](docs/upstream/Open-WebUI-Provenance-Policy.md)

## Upstream foundation decision

The project may import only the verified BSD-3-Clause-eligible Open WebUI v0.6.5
material selected by ADR-0009. No source is imported during the documentation
phase. At the implementation gate, the exact tag, immutable commit, source
checksum, file inventory, dependency lock, license evidence, SBOM, security
review, and accessibility baseline SHALL be recorded before code enters history.

If that evidence gate fails, the team SHALL build the web shell from a clean
implementation against the same Commons contracts. Later Open WebUI releases are
not an automatic source because their licensing must be assessed independently.

## Institution white-labelling

Institution forks provide signed branding, allowed modules, domains, identity
issuer references, legal links, support contacts, feature policy, and deployment
configuration. They SHALL NOT fork shared API semantics or copy common services.

Algonquin's downstream fork is `Algonquin-Digital-Commons/algonquin-web`.
