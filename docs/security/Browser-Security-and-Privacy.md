# Browser Security and Privacy

> Status: Normative security specification
> Last reviewed: 2026-09-11

## Trust model

The browser is an untrusted execution environment. Extensions, injected scripts,
shared devices, copied URLs, malicious content and compromised dependencies are
assumed possible. Long-lived provider tokens and service credentials never enter
the browser.

## Required controls

- Use a Web BFF with secure, HTTP-only, same-site cookies and session rotation.
- Use OIDC authorization code with PKCE, strict redirect allowlists, nonce and
  state validation, exact issuer and audience validation, and short-lived tokens.
- Protect mutations with origin checks, CSRF tokens and idempotency controls.
- Apply a restrictive Content Security Policy without unsafe inline script,
  Trusted Types where supported, frame denial, MIME sniffing protection, strict
  referrer policy and explicit Permissions Policy.
- Sanitize and sandbox rendered Markdown, HTML, SVG, documents, media previews,
  model output and federation content. Never execute generated code in page origin.
- Validate uploads by size, type, signature and malware policy before processing.
- Keep secrets and protected content out of URLs, client logs, analytics, crash
  reports, source maps, error pages and browser persistence.
- Rate-limit login, streaming, file and tool endpoints and bind authorization to
  the current subject, institution, session, resource and requested action.
- Present action previews and confirmation for permissions, tools, files, external
  messages and other consequential operations.

## Privacy

Only essential telemetry is enabled by default. Optional product analytics
requires institution policy and user consent where required. Telemetry SHALL use
coarse identifiers, bounded retention and aggregation and SHALL NOT contain
prompt bodies, academic content, file contents, access tokens or private social
content.

Users can view active sessions and devices, revoke them, control memory scopes,
export supported data and request deletion. Shared-device mode disables protected
offline persistence and shortens idle expiry.

## Verification

The release gate includes dependency and secret scans, SBOM and provenance,
browser security tests, authenticated authorization tests, adversarial content
rendering, upload abuse tests, session revocation, privacy data-flow review,
manual accessibility testing and an external review before a public pilot.
