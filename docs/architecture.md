# Architecture and system design

IndexScout combines a site-scoped URL inventory with three separately attributed evidence streams: technical checks, individual Google URL Inspection snapshots, and imported official GSC Page Indexing aggregates. The interface joins these streams for operational decisions; it does not manufacture a single universal indexing truth.

The browser uses a Next.js App Router application. Server routes resolve the signed-in user and workspace, check that a site belongs to that workspace, and use a server Supabase client. Supabase persists the domain objects and applies row-level policies through workspace, site and URL ownership relationships. A uniqueness constraint and reselect-on-conflict behavior make first-workspace creation tolerant of concurrent requests.

Google OAuth authorizes a property connection. Refresh credentials are encrypted before persistence and decrypted only to construct the server-side Google client. Listing authorized properties supports ownership checks. Inspection is a read operation; the separate sitemap submission path needs broader consent. IndexNow is a distinct notification channel for participating engines.

Inspection batches execute inside the request handler with bounded parallel chunks. An Inngest dependency is present, but the inspected route does not establish an implemented durable background scheduler. Monitoring currently means retained timestamped checks, rechecks, filters and snapshot comparison; unattended monitoring at scale is unverified.

Deployment is described at the boundary level: a Next.js server, Supabase, and external search APIs. A current hosted topology, availability target and capacity envelope were not established by this review. The showcase therefore describes a local MVP, not an operational SaaS service.
