# Exercise 01: First Routes in App Router

> **Topic:** Phase 1 — App Router, file-based routing
> **Difficulty:** Easy
> **Estimated time:** ~20 min
> **Session:** #2

## Task

Побудувати міні-сайт з 3 сторінками використовуючи тільки файлову структуру `app/` — без жодного роутер-конфігу.

### Вимоги:

1. **Home** (`/`) — заголовок "Welcome", короткий опис, посилання на `/about` і `/projects`
2. **About** (`/about`) — заголовок "About Me", 2-3 речення про себе
3. **Projects** (`/projects`) — заголовок "My Projects", список з 3 проектів (можуть бути вигадані)
4. **Спільний layout** — навігація (Home | About | Projects) видна на всіх сторінках
5. **Loading UI** — додати `loading.tsx` хоча б для однієї сторінки

### Структура що має вийти:

```
src/app/
├── layout.tsx        ← nav + children
├── page.tsx          ← "/"
├── about/
│   └── page.tsx      ← "/about"
└── projects/
    ├── page.tsx      ← "/projects"
    └── loading.tsx   ← loading UI
```

## Setup

```bash
npx create-next-app@latest ex-01-routes --typescript --tailwind --app --src-dir --no-turbopack --import-alias "@/*"
cd ex-01-routes
npm run dev
```

## Hints

1. `layout.tsx` — це місце для навігації. `children` — поточна сторінка.
2. Для навігації між сторінками використай `<a href="/about">` — але після наступної сесії заміниш на `<Link>`.
3. `loading.tsx` може просто повернути `<p>Loading...</p>` — цього достатньо.

<details>
<summary>Solution — layout.tsx</summary>

```tsx
export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <html lang="en">
      <body>
        <nav>
          <a href="/">Home</a>
          {' | '}
          <a href="/about">About</a>
          {' | '}
          <a href="/projects">Projects</a>
        </nav>
        <main>{children}</main>
      </body>
    </html>
  )
}
```

### Пояснення

`layout.tsx` — persistent wrapper. При переходах між сторінками layout залишається, перемальовується тільки `{children}`. Саме тому тут правильно розміщувати навігацію — вона не мигає при переходах.

</details>

<details>
<summary>Solution — projects/loading.tsx</summary>

```tsx
'use client'

export default function Loading() {
  return (
    <div>
      <p>Loading projects...</p>
    </div>
  )
}
```

### Пояснення

`loading.tsx` — це автоматична Suspense обгортка від Next.js. Показується поки `page.tsx` рендериться (особливо актуально при async data fetching). Файл обов'язково `'use client'`.

</details>
