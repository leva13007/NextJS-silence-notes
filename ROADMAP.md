# Roadmap

> Next.js 16 learning path — from zero to confident.
>
> Based on:
> - **Core:** [Next.js Official Docs](https://nextjs.org/docs)
> - **Reference:** [roadmap.sh/nextjs](https://roadmap.sh/nextjs)

## Format

```
- ⬜ Topic not started yet
- 🔄 Topic in progress
- ✅ Topic completed → [session](sessions/...) | [note](notes/...)
```

---

## Phase 1: Getting Started
- ✅ Project setup — create-next-app, folder structure, tsconfig, eslint
- 🔄 File-based routing — page.tsx, layout.tsx; folder = route, no config
- ⬜ Navigation — Link, useRouter, notFound()
- ⬜ Dynamic routes — [slug], route params, generateStaticParams
- ⬜ Nested layouts + Route groups — per-section layout, (group) folders
- ⬜ Special files in context — loading.tsx, error.tsx, not-found.tsx (з реальним async)

## Phase 2: React Foundations for Next.js
- ⬜ Server Components vs Client Components — the mental model
- ⬜ "use client" directive — when and why
- ⬜ Suspense & streaming — loading UI, React.Suspense
- ⬜ useState, useEffect in the App Router context

## Phase 3: Data Fetching
- ⬜ fetch() in Server Components — async/await, no useEffect
- ⬜ Static vs Dynamic rendering — generateStaticParams, dynamic = 'force-dynamic', searchParams
- ⬜ Caching & revalidation — revalidatePath, revalidateTag, next.revalidate
- ⬜ Route Handlers — API routes in app/api/

## Phase 4: Mutations & Forms
- ⬜ Server Actions — "use server", form actions
- ⬜ useFormStatus, useActionState (React 19)
- ⬜ Optimistic updates — useOptimistic
- ⬜ Validation — zod + server actions

## Phase 5: Styling
- ⬜ Tailwind CSS — setup, utility classes, responsive design
- ⬜ CSS Modules — local scoped styles
- ⬜ Global styles & CSS variables
- ⬜ clsx / cn() utility — conditional classes

## Phase 6: Advanced Routing
- ⬜ Parallel routes — @slot, одночасні лейаути
- ⬜ Intercepting routes — (.) конвенція, modal pattern
- ⬜ Middleware — matcher, redirects, auth guards

## Phase 7: Authentication
- ⬜ NextAuth.js (Auth.js v5) — setup, providers, session
- ⬜ Protected routes — middleware + session check
- ⬜ JWT vs Database sessions

## Phase 8: Database & ORM
- ⬜ Prisma setup — schema, migrations, client
- ⬜ PostgreSQL + Prisma — connecting to DB
- ⬜ Drizzle ORM — alternative to Prisma
- ⬜ Server Actions + DB — CRUD operations

## Phase 9: Optimization
- ⬜ next/image — automatic optimization, lazy loading
- ⬜ next/font — Google Fonts, local fonts, no layout shift
- ⬜ Metadata API — title, description, OpenGraph
- ⬜ Bundle analysis — @next/bundle-analyzer

## Phase 10: Deployment
- ⬜ Vercel deployment — git integration, env vars, preview deploys
- ⬜ Environment variables — .env.local, NEXT_PUBLIC_ prefix
- ⬜ Edge runtime — when to use
- ⬜ Self-hosting — Docker, standalone output

## Todo / Ideas:
- ⬜ tRPC + Next.js — type-safe API layer
- ⬜ Zustand — global state management
- ⬜ React Query / TanStack Query — server state
- ⬜ Testing — Jest, React Testing Library, Playwright E2E
