# Cheatsheet: App Router — Special Files

> **Updated:** 2026-05-21

## File Conventions

| File | Route impact | Notes |
|------|-------------|-------|
| `page.tsx` | Makes folder a public URL | Required for a route to exist |
| `layout.tsx` | Wraps page + child routes | Persists on navigation, doesn't re-render |
| `template.tsx` | Like layout, but re-renders | Rare use case |
| `loading.tsx` | Suspense fallback | Must be `'use client'` |
| `error.tsx` | Error boundary UI | Must be `'use client'` |
| `not-found.tsx` | 404 UI | Called via `notFound()` |
| `route.ts` | API endpoint (no UI) | Exports GET, POST, etc. |
| `middleware.ts` | Runs before request | At project root, not in app/ |

## Folder Conventions

```
app/
├── page.tsx              → "/"
├── layout.tsx            → wraps all routes
├── about/
│   └── page.tsx          → "/about"
├── blog/
│   ├── page.tsx          → "/blog"
│   └── [slug]/
│       └── page.tsx      → "/blog/:slug"   (dynamic)
├── (marketing)/          → route group, no URL impact
│   └── landing/
│       └── page.tsx      → "/landing"
└── api/
    └── hello/
        └── route.ts      → GET /api/hello
```

## Server vs Client

```tsx
// Server Component (default) — no directive needed
export default function Page() { ... }

// Client Component — add directive at top
'use client'
export default function Counter() {
  const [count, setCount] = useState(0)
  ...
}
```

> ⚠️ `loading.tsx` and `error.tsx` must be `'use client'`

## Metadata

```tsx
// Static
export const metadata: Metadata = {
  title: 'Page Title',
  description: 'Description',
}

// Dynamic
export async function generateMetadata({ params }) {
  return { title: `Post: ${params.slug}` }
}
```

## Common Gotchas

- `layout.tsx` **does not** re-render on child navigation — good for nav/sidebar
- `page.tsx` receives `params` and `searchParams` as props (not hooks)
- `error.tsx` only catches errors in its subtree, not in the layout above it
- `not-found.tsx` at `app/` level = global 404 page
