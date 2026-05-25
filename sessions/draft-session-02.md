# Next.js App Setup & App Router File Conventions

> **Date:** — | **Session #:** 2 | **Duration:** —
> **Roadmap:** Phase 1 → Project Setup + App Router Basics + File-based Routing
> **Stream:** ⬜ Not streamed / ✅ Streamed ([YouTube link])

Встановлюємо перший Next.js 16 проект через `create-next-app`, досліджуємо структуру, розбираємось що і навіщо в `app/` директорії — `page.tsx`, `layout.tsx`, спеціальні файли.

---

## Prerequisites

- Node.js 18.17+ встановлений (`node -v`)
- npm / npx доступний
- VS Code або WebStorm

---

## Key Concepts

- **App Router** — файлова система маршрутизації Next.js 16, директорія `app/`
- **Server Component** — за замовчуванням кожен компонент в `app/` — серверний (рендериться на сервері, 0 JS на клієнт)
- **`page.tsx`** — робить папку публічним URL-маршрутом
- **`layout.tsx`** — обгортка що не перемальовується при навігації між дочірніми маршрутами
- **Route Segment** — кожна папка в `app/` = один сегмент URL

---

## Step 1. Створення проекту

```bash
npx create-next-app@latest learn-nextjs-01 \
  --typescript \
  --tailwind \
  --eslint \
  --app \
  --src-dir \
  --no-turbopack \
  --import-alias "@/*"
```

> 📝 `--app` = App Router (не legacy Pages Router)
> 📝 `--src-dir` = код в `src/`, не в корені — чистіша структура
> 📝 `--no-turbopack` = стандартний webpack (turbopack ще experimental)

```bash
cd learn-nextjs-01
npm run dev
```

Відкрити `http://localhost:3000` — має бути стартова сторінка Next.js.

> ✅ Проект запущений? Йдемо далі.

---

## Step 2. Дослідження структури

```
learn-nextjs-01/
├── src/
│   └── app/
│       ├── layout.tsx       ← кореневий layout (html, body)
│       ├── page.tsx         ← маршрут "/"
│       ├── globals.css      ← глобальні стилі
│       └── favicon.ico
├── public/                  ← статичні файли (доступні як /file.png)
├── next.config.ts           ← конфіг Next.js
├── tsconfig.json            ← TypeScript конфіг
├── tailwind.config.ts       ← Tailwind конфіг
└── package.json
```

> 💡 `app/` — це весь роутинг. Папка = URL сегмент. `page.tsx` = публічна сторінка.
> ⚠️ `public/` ≠ `app/`. В `public/` лежать статичні ассети (картинки, шрифти).

---

## Step 3. Читаємо layout.tsx

Відкрити `src/app/layout.tsx`:

```tsx
import type { Metadata } from 'next'

export const metadata: Metadata = {
  title: 'My App',
  description: 'My Next.js app',
}

export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  )
}
```

> 📝 `RootLayout` — єдиний в проекті хто рендерить `<html>` і `<body>`.
> 📝 `children` — це поточна `page.tsx` що рендериться.
> 📝 `metadata` — Next.js автоматично вставить `<title>` і `<meta description>` в `<head>`.

---

## Step 4. Читаємо page.tsx

```tsx
export default function Home() {
  return (
    <main>
      <h1>Hello, Next.js!</h1>
    </main>
  )
}
```

> 📝 Це звичайний React компонент. Але він **Server Component** — рендериться на сервері.
> 💡 Немає `'use client'` → серверний. Є `'use client'` → клієнтський.

**Практика:** Замінити вміст `page.tsx` на щось своє. Зберегти — сторінка оновиться автоматично (HMR).

---

## Step 5. Створення нового маршруту

Створити папку `src/app/about/` і файл `page.tsx`:

```tsx
export default function AboutPage() {
  return (
    <main>
      <h1>About</h1>
      <p>This is the about page.</p>
    </main>
  )
}
```

Відкрити `http://localhost:3000/about` — новий маршрут без жодного конфігу.

> 💡 Ось вся магія App Router: папка `about/` + файл `page.tsx` = маршрут `/about`.

---

## Step 6. Спеціальні файли App Router

Створити по файлу та подивитись як вони виглядають в браузері:

| Файл | Призначення | Коли показується |
|------|------------|-----------------|
| `page.tsx` | Сторінка (публічний URL) | Завжди |
| `layout.tsx` | Обгортка, не перемальовується | Завжди (wraps page) |
| `loading.tsx` | Скелетон/спінер | Поки page завантажується |
| `error.tsx` | UI помилки | При `throw` в page |
| `not-found.tsx` | 404 сторінка | При `notFound()` або неіснуючий URL |

**Практика:** Створити `src/app/about/loading.tsx`:

```tsx
export default function Loading() {
  return <p>Loading about page...</p>
}
```

> ⚠️ `error.tsx` та `loading.tsx` — обов'язково `'use client'` (вимога React/Next.js).

---

## Pomodoros

| # | Duration | Focus |
|---|----------|-------|
| 1 | 25 min   | Steps 1–3: create-next-app, structure, layout.tsx |
| 2 | 25 min   | Steps 4–6: page.tsx, new route, special files |
| 3 | 25 min   | Практичне завдання (exercises/) |

---

## Summary

- [ ] `create-next-app` запущений і відкривається в браузері
- [ ] Розумію різницю `layout.tsx` vs `page.tsx`
- [ ] Створив новий маршрут без конфігу
- [ ] Знаю навіщо `loading.tsx`, `error.tsx`, `not-found.tsx`
- [ ] Розумію що Server Component = дефолт в `app/`

## Mistakes This Session

-

## What's Next

- [ ] Session 3 → Phase 1: Navigation — Link, useRouter, redirect(), notFound()
