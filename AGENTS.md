<!-- BEGIN:nextjs-agent-rules -->

# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` (resolved from this file's directory; in monorepos the `next` package may not be visible from the repo root) before writing any code. Heed deprecation notices.

This block is written and re-added by `next dev` — verify at `node_modules/next/dist/server/lib/generate-agent-files.js`. Removing it from a diff only re-creates the uncommitted change; committing it with your work keeps the tree clean.

<!-- END:nextjs-agent-rules -->

# open_daycare

Daycare management web app (in Spanish). Early stage: `app/` is still the `create-next-app` default; real UI is built screen-by-screen against the design mockups below.

## Toolchain

- Next.js **16.3.0** + React **19.2.8**, App Router, TypeScript `strict`, Tailwind **v4** (via `@tailwindcss/postcss`).
- Single package, no monorepo. Path alias `@/*` → repo root. Entry: `app/layout.tsx`, `app/page.tsx`.

## Commands

- `npm run dev` – dev server (regenerates the `<!-- BEGIN:nextjs-agent-rules -->` block above; commit it to keep the tree clean).
- `npm run build` / `npm start` – prod build & serve.
- `npm run lint` – ESLint flat config (`eslint-config-next` core-web-vitals + typescript).
- Typecheck: `npx tsc --noEmit` (no script defined; `tsconfig` already has `noEmit: true`).
- No test framework is configured.

## Design references (source of truth for screens)

`references/pantallas/*.dc.html` are self-contained HTML mockups of every target screen, and `references/screenshots/*.png` are captured renderings. Consult these before building a screen — they define layout, components, and copy. Target screens include:

`index`, `login`, `activar-cuenta`, `feed`, `crear-publicacion`, `detalle-publicacion`, `avisos`, `ninos`, `agregar-nino`, `perfil-nino`, `resumen-dia`, `foto`, `mi-cuenta`, `familia-feed`, `familia-cuenta`, `vincular-padre`.

Design tokens to mirror: warm cream background `#f6ecdf`, brown text `#3f362e`, coral accent `#f2a78e`; fonts **Fredoka** (display) + **Nunito** (body). UI copy is in Spanish.

`references/pantallas/support.js` is **generated** from `dc-runtime` — never edit it by hand.

## Workflow notes

- Playwright MCP is enabled (`opencode.json`) — use it to visually verify pages against the mockups/screenshots after building.
- `spec` and `spec-impl` skills are installed under `.agents/skills/` (see `skills-lock.json`) for spec-driven work.
- `next-env.d.ts` and `.next/` are gitignored; don't commit them.