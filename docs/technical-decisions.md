# Technical decisions

These records summarize explicit product rules or mechanisms visible in the private source. They do not assign invented dates or claim undocumented historical evaluations.

## Keep technical and Google evidence separate

**Context:** Local crawl evidence, official exports and per-URL inspection have different times and populations.

**Decision:** Retain distinct models, labels and classifications.

**Why:** A technical blocker explains eligibility, whereas indexed state belongs to Google's observation. Export totals can include URLs outside the tracked inventory.

**Alternatives considered:** The roadmap explicitly rejects ambiguous merged Google-indexed labeling.

**Consequences:** More fields and reconciliation work, but disagreement remains inspectable.

**Current status:** Implemented models/helpers; UI count consistency still requires QA.

## Keep Google Request Indexing manual

**Context:** The integration inspects URLs and can separately submit sitemaps.

**Decision:** Provide a human request queue and action history without claiming automatic URL indexing.

**Why:** An inspection result and a recorded manual action do not invoke Google's manual request workflow.

**Alternatives considered:** Automatic/guaranteed Google-indexing positioning is explicitly rejected by the roadmap.

**Consequences:** Human work remains part of the process; application allowance is advisory bookkeeping.

**Current status:** Queue and action routes exist; auth-error candidate eligibility needs private review.

## Serialize workspace identity through a database constraint

**Context:** Concurrent requests can both observe no workspace.

**Decision:** Use unique ownership and reselect after a uniqueness conflict.

**Why:** The database resolves the identity race.

**Alternatives considered:** No separate historical comparison is documented.

**Consequences:** Creation is tolerant of a duplicate insert attempt, while profile initialization remains best effort.

**Current status:** Supported by the workspace helper and migration.
