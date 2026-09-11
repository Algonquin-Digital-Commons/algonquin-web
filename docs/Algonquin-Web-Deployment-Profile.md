# Algonquin Web Deployment Profile

> Status: Normative institution profile; deployment gated
> Owner: Algonquin Digital Commons; accountable maintainer RedjiJB until delegation
> Contact: jean0319@algonquinlive.com
> Last reviewed: 2026-09-11

## Identity and product boundary

The product name is **Algonquin Digital Commons**. Algonquin's institution-approved
identity provider remains the authority for students, faculty and staff; the
Commons identity broker normalizes claims so the web client does not depend on
provider-specific identifiers or APIs.

The deployment SHALL provide the common landing, Chat, Study, Work, Code, Campus,
session, file, notification, settings, privacy, accessibility and help routes.
An unavailable or unapproved backend disables its module with an explicit status
rather than redirecting to an unrelated service or fabricating data.

## Branding package

The signed branding package contains:

- product name and institution identifier;
- approved wordmark, icons, colours, typography tokens and accessible contrasts;
- canonical web origins and deep-link allowlist;
- sign-in label and institution identity-discovery metadata;
- privacy, acceptable-use, accessibility and support links;
- support contact `jean0319@algonquinlive.com` during the founder bootstrap phase;
- enabled modules, feature flags and release channel;
- signature, schema version, issue time, expiry and rollback version.

Branding SHALL pass contrast, zoom, high-contrast, screen-reader, reduced-motion
and keyboard tests. It SHALL not replace security text, conceal AI-generated
content, misrepresent institutional authority or inject executable code.

## Access

Users access the client through its institution-controlled HTTPS origin as a
normal responsive website. Supported browsers may install it as a PWA. Desktop
and mobile clients deep-link to the same session and account contracts. The web
experience does not require installation from a proprietary application store.

## Data and privacy

Algonquin-selected residency, retention, recovery, analytics and consent values
are supplied through the signed deployment manifest before a pilot. They SHALL
conform to common schemas and Algonquin institutional approval and may tighten,
but not weaken, common security and privacy requirements.

## Release gate

Deployment requires verified identity registration, approved origins and legal
links, a signed manifest, passing common contract tests, WCAG 2.2 AA evidence,
security and privacy review, artifact provenance, SBOM, rollback rehearsal,
service ownership and incident escalation. These are deployment evidence, not
unresolved architecture choices.
