# IndexScout

A site-scoped indexing intelligence dashboard that separates URL inventory, technical eligibility and Google indexing evidence.

Public Technical Overview · Private Development Repository

## Overview

IndexScout is a local MVP for inspecting a site's URL population, retaining evidence and prioritizing indexing work. It joins technical checks, per-URL Google URL Inspection and imported official GSC Page Indexing snapshots without treating them as the same measurement.

## Problem

An operator needs to distinguish a missing URL, a crawl/indexability blocker, an unknown inspection result and a page Google reports as not indexed. These require different next actions. Aggregate GSC reports and individual checks can disagree because their populations and timestamps differ.

## System Architecture

~~~mermaid
flowchart LR
  U[Operator browser] --> N[Next.js application and server routes]
  N --> D[(Supabase: identity, inventory, checks, history)]
  N --> F[Live HTML technical checks]
  N --> G[Google OAuth and Search Console]
  E[GSC aggregate import / manual entry] --> N
  N --> B[IndexNow and separate submission paths]
  N --> H[Human action queue]
~~~

## Core Components

- Workspace/site ownership and verified property connection.
- Normalized URL inventory populated from sitemap and other supported origins.
- Technical checker for robots, HTTP, directives, canonical and basic content/link evidence.
- Google inspection adapter and shared indexed/not-indexed/unknown/auth-error classification.
- Separate official-export snapshots, score history, actions and operational filters/exports.

## Key Technical Workflows

Import inventory → check technical eligibility → select an inspection batch → retain observations/errors → prioritize remediation → recheck. Manual request records track operator work; they do not invoke Request Indexing. Snapshot comparison preserves source and observation time.

## Engineering Decisions

Three evidence streams stay distinct. Authentication errors remain a separate classification. Workspace creation relies on a database uniqueness constraint to handle concurrent first access. Batches use bounded parallel chunks inside a server request; a durable scheduler is not established.

## Reliability / Safety / Validation

Partial batches and expired connections are expected failure cases. Application queue allowance is separate from Google API quota. The source roadmap requires excluding auth errors from manual candidates, but the inspected queue route lacks that explicit exclusion; this remains a private validation item.

## Technology Stack

Next.js, React, TypeScript, Tailwind CSS, Supabase, Google APIs/OAuth, Cheerio, XML parsing and CSV/ZIP import libraries. Additional dependencies are not presented as implemented features without evidence.

## Testing

The roadmap records TypeScript/lint/build checks and manual workflow QA. No fresh source tests or authenticated requests were run for this documentation task. The current coverage-string classifier can misclassify negative indexing wording; labels, count consistency and queue eligibility need focused verification.

## Current Status

Local MVP / private development. Deployment, automated monitoring and production readiness are unverified. This public repository is a documentation case study, with no runnable production source.

## Technical Documentation

- [architecture](docs/architecture.md)
- [data model](docs/data-model.md)
- [workflows](docs/workflows.md)
- [testing and validation](docs/testing-and-validation.md)
- [reliability and failure model](docs/reliability-and-failure-model.md)
- [security and authority](docs/security-and-authority.md)
- [technical decisions](docs/technical-decisions.md)
- [project status](docs/project-status.md)
- [evidence lifecycle](diagrams/evidence-lifecycle.md)

## Repository Notice

This repository contains the public technical documentation for the project. The production source code and internal development materials are maintained separately and are not published here.
