# Data model and evidence semantics

| Model | Responsibility | Important boundary |
|---|---|---|
| Workspace | User-owned site collection and priority profile | Ownership is distinct from Search Console property permission |
| Site | Domain, workspace, verification and GSC property association | Domain property and URL-prefix property are not interchangeable |
| Integration | Per-site engine, connection status, granted scope and encrypted credential | A connected credential can later be revoked |
| URL | Original and normalized address, site and inventory origin | Normalization is an application identity convention |
| URL check | Timestamped HTTP, robots, canonical, metadata and local verdict | Technical indexability is not indexed state |
| Index snapshot | URL, engine, checked time, nullable indexed result, coverage/crawl evidence | Null preserves unknown/error rather than becoming false |
| GSC indexing snapshot | Imported or manually entered aggregate totals and declared source update date | Its population can extend beyond tracked sitemap URLs |
| GSC reason | Coverage reason and page count belonging to an imported snapshot | Not an independently inspected URL verdict |
| Score / Action / Submission | Priority history, operator work and outbound notification record | A marked manual action proves operator bookkeeping, not Google acceptance |
| Audit event | Actor, action, target and timestamp | Operational trace is separate from search evidence |

Technical verdicts include valid, blocked, redirected, noindex, canonical mismatch, thin, needs review and error. Google classification includes indexed, not indexed, unknown and authentication error. These are different axes and should not be collapsed.

The current coverage-string helper is heuristic and has a known semantic defect: its positive substring test can match “not indexed” before the negative rules run. Consequently, a stored application classification can disagree with the underlying Google evidence. Preserve the provider verdict and coverage wording; do not present the application label as independently validated indexing truth.

Historical snapshots support comparison only when source, time and denominator are stated. One route computes totals across stored snapshots; such totals must not automatically be described as unique latest URLs. Repeated checks can increase a history count without growing URL inventory.
