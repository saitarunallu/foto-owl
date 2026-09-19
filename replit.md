# Foto Owl

Native React Native photo discovery app for collecting and saving images from Picsum.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/foto-owl/app/` — Expo Router screens for auth, gallery, favorites, detail, and profile
- `artifacts/foto-owl/context/AppContext.tsx` — small centralized state provider for auth, session, favorites, and theme
- `artifacts/foto-owl/services/storage.ts` — AsyncStorage persistence helpers
- `artifacts/foto-owl/components/ui.tsx` — small reusable inputs, buttons, cards, and empty/loading states
- `artifacts/foto-owl/types/` — assignment domain types

## Architecture decisions

- Registration and login are intentionally local because the internship assignment explicitly asks for local credentials and session persistence.
- Favorites store the Picsum image objects, not just IDs, so saved images remain viewable without a second API request.
- The gallery fetches the required 50 Picsum records once and progressively reveals them through FlatList `onEndReached`.
- Shared app state uses React Context; search, filters, forms, loading, and pagination remain local screen state.

## Product

Foto Owl lets a user register, sign in, discover Picsum images, search and filter by author, save favorites, open full-size details, download to the device gallery, edit their profile, and choose light or dark mode.

## Where things live

_Populate as you build — short repo map plus pointers to the source-of-truth file for DB schema, API contracts, theme files, etc._

## Architecture decisions

_Populate as you build — non-obvious choices a reader couldn't infer from the code (3-5 bullets)._

## Product

_Describe the high-level user-facing capabilities of this app once they exist._

## User preferences

_Populate as you build — explicit user instructions worth remembering across sessions._

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
