# Security and authority

The inspected application enforces user/workspace/site ownership at server boundaries, and the database schema defines ownership-based row-level policies. Schema presence does not prove the deployed database has those migrations and policies installed.

Google credentials are server-side encrypted integration data. Client credentials and the encryption secret must remain runtime secrets. OAuth property permission is checked separately from application tenancy. Inspection needs read access; sitemap submission is an explicit write capability and requires the corresponding grant. IndexScout should therefore not be described as wholly read-only.

The manual Google request flow retains human execution authority. URL Inspection returns Google evidence; local scoring prioritizes work and has no authority to guarantee indexing. IndexNow cannot establish a Google submission.

Fetching operator-selected URLs introduces a network trust boundary. This review did not establish comprehensive SSRF protection, response-size isolation or browser sandboxing for IndexScout. No such guarantee is inferred from the stronger controls in the separate LPI project. Exports and diagnostics can contain site-specific information and should be reviewed before sharing.

The public case study includes no credentials, actual property IDs, customer inventory, deployment endpoints or operational key material.
