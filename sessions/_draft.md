
### Why layout and not page?

`layout.tsx` wraps every route in its subtree. Put `<nav>` there once — it
appears on `/`, `/about`, `/projects`, and any future route automatically.
If you put nav in `page.tsx` you'd copy-paste it into every file, and updating
one link means editing three files.

### Bonus experiment — does layout really persist?

People say "layout doesn't re-render on navigation." Test it now:

```tsx
// temporarily add this line inside <body>, above <nav>
<p style={{ fontSize: 10, padding: 4 }}>layout at: {new Date().toISOString()}</p>
```

Click between pages — the timestamp **updates every time**. That's because
`<a href>` triggers a full browser reload, so everything re-renders including
the layout.

The real "layout persists" behavior only shows with **client-side navigation**
(`<Link>`). Session 4: swap `<a href>` → `<Link>`, run the same test — the
timestamp will stay frozen while only `<main>` swaps. That's the actual proof.

Remove the test line when done.