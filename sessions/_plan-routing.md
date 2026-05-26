# Routing Plan — Sessions 04–07

One app (`nextjs_01`) grows across four sessions.
Each step adds something you'd want in a real site — not a demo fragment.

---

## Session 04 — Layouts and Pages (continued)
**Docs:** `getting-started/layouts-and-pages`

- Shared data module `src/lib/projects.ts` — single source for list and detail
- Nested layout `app/projects/layout.tsx` — wraps all `/projects/*`, root layout untouched
- Dynamic segment `app/projects/[slug]/page.tsx` — `[slug]` captures the URL value
- `params` is `Promise<{ slug: string }>` in Next.js 15+ — must be `await`ed
- `PageProps<'/projects/[slug]'>` — globally available type helper, no import
- `generateStaticParams` — list known slugs → pre-rendered as static
- `notFound()` + segment-level `not-found.tsx` for unknown slugs
- `<Link>` introduced to link list items to detail pages (mechanics in Session 05)

**Deliverable:** `/projects/nextjs_01` etc. work; unknown slug → custom 404;
"PROJECTS" sub-header appears on all `/projects/*` routes.

---

## Session 05 — Linking and Navigating
**Docs:** `getting-started/linking-and-navigating`

- Timestamp experiment — prove `<a href>` = full reload
- `<Link>` mechanics — client-side transitions, layout stays mounted
- Prefetching: static routes (full) vs dynamic routes (partial or none)
- `loading.tsx` fires for real — `/projects/[slug]` is dynamic, add skeleton
- `useLinkStatus` for slow networks (reference)

**Deliverable:** `<a href>` → `<Link>` everywhere in nav and home page;
`app/projects/loading.tsx` visibly fires on navigation to `/projects/[slug]`.

---

## Session 06 — Route Groups
**Organize routes without changing URLs.**

- `(group)` folders — no effect on the URL
- Restructure `app/` into `(marketing)/` (home, about) and leave `projects/` separate
- Multiple root layouts — each group can have its own layout

**Deliverable:** app restructured into route groups; URLs unchanged; two layouts coexist.

---

## Session 07 — Special Files With Real Data
**`loading.tsx`, `error.tsx`, `not-found.tsx` — now with actual async.**

Context: by this point we've done at least one session of data fetching
(Phase 2 Server Components or Phase 3 fetch()). Now the special files make sense.

- `loading.tsx` next to a page that actually awaits a fetch → Suspense fires
- `error.tsx` — throw intentionally, watch the boundary catch it
- `not-found.tsx` — already covered in session 4; review segment-level vs global

**Deliverable:** Projects list loaded from a real source (JSON file or API).
Loading spinner, error state, and 404 all visibly work — no artificial delays.

---

## What comes after (Phase 2+)
- **Server vs Client Components** — convert components as understanding grows
- **Parallel routes + Intercepted routes** — modal pattern on the projects grid
  (these require solid Dynamic routes first)
- **Middleware** — auth guard on a future protected section
