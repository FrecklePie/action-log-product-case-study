# Selected Product Decisions and Trade-offs

These are concise summaries from the saved decision log and dated Stage reports, not fabricated historical ADR entries.

| Decision | Reasoning | Consequence |
|---|---|---|
| Use Django + PostgreSQL for the local pilot | Keep the first implementation integrated and manageable | Server-rendered UI and a single backend codebase. |
| Centralise action writes | Preserve auditability under concurrent edits | Transaction, version validation, change history and conflict handling. |
| Derive action status rather than storing separate editable status | Avoid contradictory sources of truth | Shared status logic serves register and reporting. |
| Separate dictionary permissions from action editor rights | Reflect different responsibilities | More precise access control without automatic privilege escalation. |
| Fix register ergonomics before adding functions | Users should reach records and essential fields without excessive scrolling | Compact filters and action/deadline/status prioritisation. |
| Preserve the engine but rework Home | Automated PASS did not establish design acceptance | Distinct Overview, navigation cards and assigned-action list. |
| Reject an AI-generated UI despite passing tests | The result was functional but did not match the intended information hierarchy | More explicit design constraints and a visual review gate. |
| Repair focus after a reproduced resize failure | Keyboard navigation must remain predictable | Scoped fix following diagnosis and owner approval. |

## Decision discipline

The project's records distinguished technical checks from human visual acceptance. The final local build retained open manual checks rather than declaring complete release readiness. Design references guided presentation, not new business rules.
