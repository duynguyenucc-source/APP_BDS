# AGENTS.md

## Workspace Overview

This repository is a workspace for a Vietnamese real-estate pawn management project, not a single finished application.

Current top-level areas:

- `docs/` stores product and implementation context.
- `Ai-wedsite/` is a separate Next.js website project with its own `AGENTS.md`.
- `gitpull/so-ban-hang-ai/` is a separate Vite + React application.

Closest-file rules apply:

- If you work inside `Ai-wedsite/`, follow `Ai-wedsite/AGENTS.md` first.
- If a subproject later adds its own `AGENTS.md`, that file overrides this root file for work inside that subtree.

## Source Of Truth

For the pawn-management product, the current source of truth is:

- `docs/superpowers/specs/2026-06-28-app-quan-ly-cam-co-bds-ben-tre-design.md`

Use that spec before inventing new workflows, fields, or screens.

Key business assumptions from the current spec:

- Single-user Vietnamese web app.
- Main domains: customer, property, pawn dossier, payment, document, reminder task.
- Default interest: `4%` per month.
- Default service fee: `3%` of loan amount, collected once at disbursement.
- OCR/AI suggestions must never auto-commit into official records without user confirmation.

## Where To Work

Before changing code, identify the real target area:

- Product/spec work for the pawn-management app: update `docs/` first unless an implementation folder is explicitly provided.
- Website-cloning or reverse-engineering work: use `Ai-wedsite/`.
- Sales/inventory demo app work: use `gitpull/so-ban-hang-ai/`.

Do not mix these projects together.

If the request is about the pawn-management app and no implementation directory exists yet, prefer one of these actions:

1. extend the product docs,
2. create a clearly named new app folder,
3. ask for confirmation only if writing into an existing unrelated app would be risky.

## Dev Commands

There is no single root install/build/test flow yet. Run commands in the correct subproject.

### `Ai-wedsite/`

- Install: `npm install`
- Dev: `npm run dev`
- Build: `npm run build`
- Lint: `npm run lint`
- Type check: `npm run typecheck`
- Full check: `npm run check`

### `gitpull/so-ban-hang-ai/`

- Install: `npm install`
- Dev: `npm run dev`
- Build: `npm run build`
- Start built server: `npm run start`
- Type check: `npm run lint`

## Implementation Expectations

- Keep all user-facing product flows in Vietnamese unless the user asks otherwise.
- Preserve clear separation between approved business data and AI/OCR-generated suggestions.
- Treat land records, ID cards, contracts, receipts, and customer information as sensitive data.
- Prefer explicit status transitions over hidden automation for dossier lifecycle changes.
- Add or update tests when business rules, calculations, or persistence behavior change.

## Data And Security Rules

- Never assume OCR output is correct; route it through a review step.
- Never silently change interest, fee, due-date, or payment history logic.
- Avoid storing secrets, API keys, or sample personal documents in the repository.
- Redact or use mock data when creating fixtures, screenshots, or examples.

## Documentation Rules

- When product behavior changes, update the relevant spec in `docs/`.
- Keep new folders and filenames descriptive and stable.
- Document important assumptions near the code or in nearby Markdown instead of leaving them implicit.

## Agent Workflow

- Read the nearest `AGENTS.md`, then inspect the target folder before editing.
- Prefer the smallest change that satisfies the request.
- Verify with the relevant local checks for the subproject you touched.
- If the requested work conflicts with the pawn-management spec, call out the conflict and follow the user's latest explicit direction.
