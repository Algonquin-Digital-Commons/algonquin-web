# Experience and Feature Scope

> Status: Normative product scope
> Last reviewed: 2026-09-11

## Users

The experience supports prospective visitors, students, faculty, staff,
researchers, developers, club participants, moderators, service operators, and
institution administrators. Authorization—not navigation visibility alone—sets
the capabilities available to a user.

## Initial complete product slice

The first implementation milestone SHALL include:

1. institution-branded landing, help, legal, privacy and accessibility pages;
2. institutional sign-in, sign-out, session expiry and account recovery guidance;
3. Chat with model aliases, streaming, cancellation, citations, file references,
   usage visibility and policy errors;
4. Study with read-only course, deadline and approved content context;
5. Work with plans, files, tool previews, confirmation and action receipts;
6. Code session discovery and handoff to the desktop client where local execution
   is required;
7. Campus service, club and event discovery through versioned adapters;
8. notification preferences and cross-device session continuity;
9. user-controlled data export, deletion request and session/device revocation;
10. administrator health and configuration visibility without secret exposure.

## Deliberate exclusions from the first slice

- autonomous grade submission, enrollment changes, payments, emergency response,
  medical diagnosis, disciplinary action, or unsupervised consequential actions;
- direct browser access to local files or shell execution;
- direct model-provider keys or identity-provider tokens in the browser;
- behavioral advertising, sale of usage data, or unrelated student profiling;
- dependency on a proprietary app store, analytics platform, notification vendor,
  identity vendor, model provider, or cloud runtime.

These exclusions are settled safety and portability boundaries. A later addition
requires its own specification, threat model, institutional authority, explicit
confirmation model, receipt semantics, and ADR where the trust boundary changes.

## Design requirements

- Responsive layouts SHALL support keyboard, touch, pointer, switch, screen
  reader, zoom, reduced motion, high contrast and narrow-screen use.
- Language SHALL be plain, respectful and explicit about whether information is
  authoritative, generated, cached, delayed or unavailable.
- AI output SHALL be distinguishable from institutional records and human content.
- Consequential actions SHALL show the target, inputs, effects, policy, cost,
  confirmation level, cancellation opportunity and resulting receipt.
- The user SHALL control notification channels, history visibility, devices,
  memory scopes, personalization and cross-device handoff.

## Success measures

The first slice is successful when representative users can sign in, complete
the critical journeys without accessibility blockers, understand AI and
institutional authority boundaries, recover from dependency failures, and export
or revoke their state. Product analytics use consented, minimized events and may
not substitute engagement for academic or wellbeing outcomes.
