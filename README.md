# PulseBoard

A small, fictional SaaS dashboard site — built as a lightweight demo environment for testing website observability with **HeronSignal**.

PulseBoard is not a real product. It exists to generate realistic page views, navigation, clicks, form interaction, and a controlled frontend error, so you can verify HeronSignal is capturing activity correctly.

## What's included

- **Home** (`/`) — hero, feature cards, and an email subscribe form
- **Dashboard** (`/dashboard`) — mock metrics, a static chart, a recent activity list, and demo action buttons
- **About** (`/about`) — a short description and a CTA back to the dashboard

Stack: React + Vite, plain CSS, client-side routing via `react-router-dom`. No backend, no database, no auth.

## Install

```bash
npm install
```

## Run locally

```bash
npm run dev
```

Opens at `http://localhost:5173`.

## Build

```bash
npm run build
```

Outputs a production build to `dist/`.

## Where to add HeronSignal

Open `src/heronsignal.js`. It's imported once in `src/main.jsx`, before the app renders. Replace its contents with the real HeronSignal SDK snippet (script injection, `init()` call, config, etc.) — everything else in the app stays the same.

## Deploy

Any static host works, since this is a plain Vite build.

**Vercel / Netlify**
- Build command: `npm run build`
- Output directory: `dist`

**GitHub Pages**
1. `npm run build`
2. Push the contents of `dist/` to a `gh-pages` branch (or use an action like `peaceiris/actions-gh-pages`)
3. If deploying to a subpath (e.g. `username.github.io/pulseboard`), set `base: '/pulseboard/'` in `vite.config.js` before building

## Notes for HeronSignal testing

- The **Dashboard** page has a **Test Error** button that intentionally throws a controlled JavaScript error, without breaking the rest of the app — useful for verifying frontend error monitoring.
- A natural test journey: Home → Dashboard → Run Demo Action → Refresh Data → Test Error → About → Home → Subscribe.
