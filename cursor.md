# BTS ERP — Cursor project notes

This file is the working brief for Cursor in this folder.

## Project

**BTS ERP** is an ERP for BTS (Base Transceiver Station) operations: sites, assets, inventory, work orders, vendors, and related finance/ops workflows.
l
Workspace: `BTS_ERP`

## Stack

- **Runtime:** Node.js
- **Language:** TypeScript (strict). Do not add new `.js` / `.jsx` source files.
- **App framework:** Next.js (App Router) — UI and API in one project
- **UI:** React with TypeScript (`.tsx`)
- **API:** Next.js Route Handlers under `app/api/`
- **Package manager:** npm (unless a lockfile for another tool appears)

Database and auth are not chosen yet. Do not add a DB or auth library unless asked.

## How to work here

- Prefer small, focused changes. Do not refactor unrelated code.
- Match existing naming, folder layout, and TypeScript patterns.
- Do not commit unless asked. Do not add secrets (`.env*`, keys, passwords) to git.
- After UI changes, verify the real user flow (click, type, submit, navigate), not only a screenshot.
- Keep types accurate. Avoid `any`. Use `unknown` and narrow when the type is unclear.
- Shared types live in a dedicated place (e.g. `types/` or `lib/types.ts`), not copied across files.

## Project layout (target)

```
BTS_ERP/
  app/                 # Next.js App Router (pages + layouts)
  app/api/             # Route handlers (Node.js server)
  components/          # Reusable UI
  lib/                 # Server/client helpers, domain logic
  types/               # Shared TypeScript types
  public/              # Static assets
```

Use Server Components by default. Add `"use client"` only when the component needs browser APIs, state, or event handlers.

## Domain (typical modules)

- Sites / towers / BTS records
- Assets and spare parts
- Inventory and stock movement
- Work orders / tickets / maintenance
- Vendors, purchase, and invoices
- Users, roles, and audit trail

## Conventions

- Keep business rules in `lib/` (or similar), not only in React components.
- Use clear domain names (`site`, `workOrder`, `asset`) instead of generic `data` / `item`.
- API routes: validate input, return typed JSON, use proper HTTP status codes.
- Prefer `async`/`await`. Handle errors; do not swallow exceptions.
- Path aliases: use `@/` if `tsconfig` defines it.

## Out of scope unless asked

- Force-push, hard reset, or rewriting git history
- Committing credentials
- Extra docs or README unless the task needs them
- Switching away from TypeScript or Next.js
