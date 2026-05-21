# Glossary

> Next.js & React terminology dictionary. Grows with every session.

---

## A

**App Router** — the file-based routing system introduced in Next.js 13+. Uses the `app/` directory. Supports Server Components by default.

**async Server Component** — a React Server Component that can `await` data directly in the component body, without `useEffect`.

## C

**Client Component** — a component marked with `"use client"`. Runs in the browser. Has access to browser APIs, useState, useEffect, event handlers.

**CSR (Client-Side Rendering)** — rendering happens in the browser. React fetches data and builds the DOM on the client.

## D

**Dynamic Rendering** — page is rendered on each request (not cached). Triggered by reading request-specific data (cookies, headers, searchParams).

## E

**Edge Runtime** — lightweight JS runtime (not full Node.js). Faster cold starts. Used for Middleware and some Route Handlers.

## F

**fetch()** — the native browser API, extended by Next.js in Server Components to support caching (`next.revalidate`, `next.tags`).

**File-based Routing** — routes are defined by folder/file structure inside `app/`. No manual route registration needed.

## L

**Layout** — `layout.tsx` — a persistent UI wrapper. Does not re-render when child routes change. Shared UI like nav, sidebar.

## M

**Metadata API** — `export const metadata` or `generateMetadata()` in page/layout files. Sets `<title>`, `<meta>`, OpenGraph tags.

**Middleware** — `middleware.ts` at project root. Runs before a request is completed. Used for auth, redirects, locale detection.

## P

**Pages Router** — the legacy routing system using `pages/` directory. Still supported but App Router is the recommended approach.

**PPR (Partial Prerendering)** — experimental Next.js 14+ feature. Combines static shell with dynamic streaming holes.

## R

**RSC (React Server Components)** — components that render on the server. No JS sent to client. Cannot use hooks or browser APIs.

**Route Handler** — `route.ts` in `app/`. The App Router equivalent of API routes. Exports `GET`, `POST`, etc. functions.

**Route Segment** — each folder in `app/` is a route segment. Maps to a URL segment.

## S

**Server Action** — an async function marked with `"use server"`. Runs on the server. Called from forms or client components. The recommended mutation pattern.

**Server Component** — the default in App Router. Renders on server. Zero client JS. Can fetch data directly.

**SSG (Static Site Generation)** — page is rendered at build time. Output is a static HTML file.

**SSR (Server-Side Rendering)** — page is rendered on the server on each request.

**Static Rendering** — the default. Next.js renders and caches the route at build time (or first request).

**Streaming** — sending UI in chunks. Used with `loading.tsx` and React `Suspense`. Improves TTFB.

**Suspense** — React boundary for async rendering. Shows fallback until children are ready.

## T

**TTFB (Time to First Byte)** — how long it takes the browser to receive the first byte from the server.

## U

**`"use client"`** — directive at top of file. Makes the component a Client Component.

**`"use server"`** — directive at top of function or file. Makes it a Server Action.
