# proposito.ve

Companion app to DevsForVenezuela. This file is the baseline for all work in this repo. Keep decisions and suggestions within this stack unless I say otherwise.

## Project description

A free, volunteer-based web platform connecting wellness professionals (psychologists, physical therapists, social workers) with people affected by natural disasters. Professionals register and get verified, survivors request help, coordinators match them manually.

### Roles
- **Professionals**: register, then get verified before they can take part.
- **Survivors**: submit requests for help.
- **Coordinators**: manually match professionals with survivors.

## Tech stack

### Frontend
- Next.js (App Router) with TypeScript
- Tailwind CSS
- shadcn/ui, Vega preset
- Custom Tailwind theme using the proposito.ve palette: green, muted terracotta, warm sand, warm neutrals

### Backend / Data
- Supabase (Postgres, RLS, Auth, Storage)
- `@supabase/ssr` client helpers (client + server)

### Hosting / Infra
- Vercel

### Version control / project management
- GitHub
- GitHub Issues + Project board

### Notifications (only if proposito.ve needs them)
- TBD: Twilio or email, one channel for v1

## Open questions (TODO: resolve, then delete this section)

1. Is proposito.ve a separate repo/app, or a module inside the `devsforvenezuela` monorepo?
2. Does it share the same Supabase project/database as DevsForVenezuela, or get its own?

Until these are answered, do not assume either way. Ask me before making decisions that depend on them (schema, auth, env vars, deploy config, repo structure).

## Working rules

- Before making changes, check the existing repo and config for anything that already settles a stack choice, and flag anything that conflicts with this file.
- Use TypeScript everywhere. Avoid `any`.
- Use the App Router (no Pages Router).
- Style with Tailwind and the theme tokens. Do not hardcode colors; use the palette tokens.
- Add UI primitives through shadcn/ui rather than hand-rolling them.
- Every Supabase table gets RLS enabled, with explicit policies. Never ship a table without them.
- Use the `@supabase/ssr` helpers for Supabase clients. Keep client and server helpers separate.
- Never commit secrets. Use environment variables, and keep `.env.example` up to date.
- Do not add new dependencies or services outside this stack without asking first.
