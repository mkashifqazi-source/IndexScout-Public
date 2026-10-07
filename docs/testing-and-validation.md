# Testing and validation

The source package exposes lint and build commands. The roadmap records historical TypeScript, lint and build passes and defines manual QA for authentication, site setup, inventory import, audit, inspection, filters, exports, details navigation and action-board counts. No dedicated automated test suite was established from the inspected package and file inventory.

This documentation task did not run builds, authenticated checks or network requests. Historical passes are reported as source-recorded observations, not fresh verification.

Important acceptance cases are: revoked Google tokens remain auth errors; official aggregates remain separate from URL Inspection; repeated snapshots do not inflate unique-URL summaries; filters and CSV exports use the same population; queue cooldown and allowance behave across repeated requests; and ownership checks reject cross-workspace objects. The queue auth-error discrepancy and classification of coverage strings deserve focused private regression tests.

Monitoring validation should compare like-for-like source populations and timestamps. A site with technically valid pages is not evidence of indexing success. API quota and browser/manual-request limits must be verified independently before deployment capacity is claimed.
