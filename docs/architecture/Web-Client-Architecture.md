# Web Client Architecture

> Status: Normative specification; implementation gated
> Owner: PSDC Web Working Group; accountable maintainer RedjiJB until delegation
> Last reviewed: 2026-09-11

## Purpose

PSDC Web is the institution-neutral browser client and installable progressive
web application. It presents shared platform capabilities without embedding an
institution, identity vendor, model provider, LMS, storage engine, or social
product into the portable client.

## Components

| Component | Responsibility | Trust boundary |
|---|---|---|
| Web shell | Navigation, layout, accessibility, localization, module loading | Untrusted browser runtime |
| Browser state | Ephemeral view state and encrypted or non-sensitive preferences | User device |
| Web BFF | Session cookie, CSRF defense, token exchange, response shaping, rate limits | Server-side web boundary |
| Contract clients | Typed adapters for common gateway and domain APIs | Versioned service boundary |
| Branding loader | Validates signed institution presentation and legal metadata | Institution configuration boundary |
| Telemetry adapter | Consent-aware, privacy-minimized client and BFF signals | Operations boundary |
| PWA worker | Static asset cache, update activation, offline-safe shell | Origin-scoped browser sandbox |

## Session and request flow

1. The browser loads a signed release from the institution web origin.
2. The branding loader verifies schema and signature before applying local values.
3. Sign-in starts OIDC authorization code flow with PKCE through the Web BFF.
4. The BFF validates issuer, audience, nonce, state, code verifier, and assurance.
5. The BFF stores upstream tokens server-side and gives the browser a rotated,
   secure, HTTP-only, same-site session cookie.
6. The browser sends a CSRF-bound request to the BFF.
7. The BFF applies session, authorization, quota, and request-shaping policy and
   calls the owning Commons gateway or domain API.
8. Streaming responses use a bounded SSE or WebSocket contract with sequence,
   reconnect cursor, cancellation, and backpressure.
9. Consequential agent actions render a preview and confirmation level before the
   BFF submits the command; the resulting receipt is shown and retained by policy.

## Routes and capability modules

The normative route families are `/`, `/chat`, `/study`, `/work`, `/code`,
`/campus`, `/sessions`, `/files`, `/notifications`, `/settings`, `/privacy`,
`/accessibility`, `/help`, and `/admin` for authorized administrators. An
institution may disable a module, but may not silently redirect a common route to
an unrelated or proprietary service.

## Contracts

- OpenAPI 3.1 defines request, response, error, pagination, and streaming setup.
- AsyncAPI and CloudEvents define notifications and session events.
- OIDC with PKCE defines interactive authentication.
- The institution manifest defines branding, origins, issuer, support and policy.
- The AI gateway contract defines chat, tools, usage, errors and model aliases.
- The session continuity contract defines event sequence, reconnection, handoff,
  approvals, receipts, cancellation and content references.

Typed clients are generated from pinned schemas. Contract versions support the
current major and one prior major during a declared migration window.

## State

Browser persistence is limited to non-sensitive preferences, accessibility
settings, encrypted device-scoped drafts where enabled, cache metadata, and the
opaque session identifier cookie. Tokens, institutional source records, model
credentials, authorization policy, and durable conversation state remain on
server-side owning services.

The service worker caches only versioned static assets and explicitly public or
user-approved offline material. Sign-out clears origin storage, invalidates the
server session, and unregisters protected cached content.

## Availability and degradation

The static shell remains able to display service status, help, privacy, sign-out,
and recovery guidance during dependency outages. Each capability fails
independently. Identity failure blocks new login; AI failure does not remove
academic deadlines already cached under policy; an academic outage does not
disable general AI; federation failure does not disable private campus services.

Every request has a timeout, cancellation, stable error class, correlation ID,
and retry policy. The client never retries a consequential mutation without an
idempotency key.

## Acceptance criteria

- Current and prior supported contracts pass compatibility tests.
- WCAG 2.2 AA automated and manual testing passes for every critical journey.
- Authentication, CSRF, XSS, CSP, cookie, redirect, clickjacking and session
  fixation tests pass.
- No protected token appears in browser storage, logs, URLs, telemetry or errors.
- Every capability has loading, empty, success, degraded, error and recovery UI.
- A signed neutral manifest and an Algonquin manifest produce distinct branding
  without source changes.
- The release works as a browser site and installable PWA without a proprietary
  application store.
