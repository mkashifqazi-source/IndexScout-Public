# Evidence lifecycle

This is a logical flow, not a claim of a durable job scheduler.

~~~mermaid
flowchart TD
  I[URL inventory] --> T[Timestamped technical check]
  T --> C[Inspection candidate selection]
  O[Google property consent] --> C
  C --> G[Google URL Inspection]
  G --> S[URL evidence or error snapshot]
  X[Operator-supplied GSC aggregate] --> A[Separate aggregate snapshot]
  T --> V[Operational view]
  S --> V
  A --> V
  V --> H[Human remediation or manual request]
  H --> R[Later recheck]
  R --> T
~~~

The remediation loop does not imply causal proof: a later indexing change can have multiple causes.
