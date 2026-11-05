# AI-Assisted Delivery and Verification

## Division of responsibility

**Product owner:** defines scope, priorities, intended experience and constraints; reviews proposed behaviour and visual output; decides whether an iteration is accepted.

**AI coding agent (Codex):** inspects code and documentation, implements bounded changes, executes tests, and produces evidence and change reports.

**Verification loop:** specify -> delegate -> inspect actual behaviour and screenshots -> identify gaps -> constrain correction -> retest. Automated tests are not a substitute for owner approval or manual platform accessibility testing.

## One concrete example: keyboard focus

During final checks, a resize-related menu-focus regression was reproduced. The agent documented the failure, a bounded change was separately authorised, and the corrective implementation was rechecked over **20 resize/focus cycles**, all passing. This is an example of supervising agent output rather than accepting an initial technical result without challenge.

## Current verification snapshot — Stage 9, 5 November 2026

| Check | Recorded result |
|---|---|
| Django tests | 276 PASS |
| PostgreSQL integrations | 2 PASS |
| Browser checks | 1,325 PASS assertions (not 1,325 separate scenarios) |
| Focus regression | 20 cycles PASS |
| Additional keyboard controls | 8 PASS |
| Contrast pairs | 29 PASS (not a full WCAG audit) |

Tests used synthetic data in an isolated database. The application source, private test archives and internal logs are not included in this public-facing documentation sample.

## Explicitly not verified / not ready

- Native Safari, VoiceOver and 200% browser zoom were not fully manually verified.
- Final release and visual acceptance remained pending at the Stage 9 snapshot.
- Four deployment warnings concerning HTTPS/HSTS and secure cookies required attention before public hosting.
- No production deployment, customer adoption, business ROI or external launch is claimed.

## Provenance

This summary is retrospectively curated from saved Stage 6–9 task instructions, product documents and actual Stage 9 verification logs. It is **not** a complete prompt transcript and does not claim work by an independent human QA team.
