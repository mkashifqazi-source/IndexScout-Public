# Reliability and failure model

| Failure | Observed handling / consequence |
|---|---|
| Missing or inactive Google connection | Inspection refuses to proceed and asks for connection/reconnection |
| Invalid refresh grant during a batch | The route attempts to retain accumulated evidence and returns a reconnect result; that early-path insert is not checked for persistence failure |
| Other individual API errors | Stored as unknown/error evidence rather than a successful negative verdict |
| Robots retrieval failure | Robots state remains unknown; later checking can continue |
| Redirect or non-success HTTP response | Diagnostic verdict records the observed condition |
| Snapshot persistence error | Route reports failure; successful remote calls alone do not guarantee retained evidence |
| Concurrent first workspace access | Database uniqueness plus reselect resolves an insert race |

Bounded parallel chunks limit simultaneous inspections, but the route is still a request-bound operation. Host deadlines, upstream quotas and partial-batch interruption remain practical constraints. The presence of a maximum batch size is not proof of quota reservation, global rate coordination or resumable job execution.

Snapshots preserve history; old authorization errors and fresh page evidence can coexist. The interface must show their timestamps and connection state. Official export update time, import time and inspection time describe different observations.

No SLA, automated alert delivery, transactional whole-batch guarantee or load-test result is claimed. The private deployment review should resolve history-versus-latest aggregation and action eligibility before relying on dashboard totals.
