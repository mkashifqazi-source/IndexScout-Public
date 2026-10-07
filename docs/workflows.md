# Workflows and state transitions

1. Authenticate and resolve the owner workspace.
2. Add a site and establish its ownership/property association.
3. Import sitemap inventory and normalize URL identity.
4. Run technical checks, retaining observations and a local diagnostic verdict.
5. Connect Google with the consent appropriate to the operation.
6. Select inspection candidates using technical eligibility, prior checks, freshness and priority; submit a bounded batch.
7. Store Google observations or error snapshots and expose source-specific classifications.
8. Review blockers and candidate actions, export filtered evidence or record a manual request.

Aggregate GSC snapshots can be imported from CSV/ZIP or entered manually. The application records this operator-supplied evidence; it does not cryptographically verify export origin or independently reproduce the aggregate totals.

A technical check first evaluates robots access, then HTTP status/redirect behavior, header and HTML directives, canonical relationships and basic content/link evidence. The inspected checker operates on fetched HTML, so JavaScript-only changes are outside that observation. Content-length heuristics are local triage signals, not Google requirements.

An expired/revoked connection must trigger reconnection or reinspection, rather than converting an authorization failure into a negative indexing verdict. The classification helper gives auth errors a distinct category. The roadmap requires their exclusion from request candidates; the inspected manual-queue route does not explicitly filter that category. This intended-versus-observed discrepancy requires private validation before an end-to-end exclusion guarantee.

Manual queue allowance is application bookkeeping based on recently completed actions, with cooldown and score ordering in candidate display. The action-recording path does not establish atomic enforcement of that allowance. It is not a live read of Google's remaining manual-request allowance, and marking an action does not call Request Indexing. Inspection capacity, manual queue policy and IndexNow notification are separate mechanisms.
