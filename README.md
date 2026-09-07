# Flowbase — B2B/SaaS Landing Page

Portfolio piece built to demonstrate **SvelteKit** fluency alongside the interactive
pricing / feature / lead-capture UI patterns common to B2B SaaS marketing sites.

Flowbase is a **fictional** product (a project & scheduling tool for small teams) — no real
company, no real customers, no backend.

## Stack

- [SvelteKit](https://svelte.dev/docs/kit) (Svelte 5, runes)
- [Tailwind CSS v4](https://tailwindcss.com) (`@tailwindcss/vite`, forms + typography plugins)
- Svelte's built-in reactivity (`$state` / `$derived`) for the pricing toggle, feature
  tabs, and form validation — no external state library
- Svelte transitions (`fly`, `fade`) for panel motion — no animation library
- `@sveltejs/adapter-vercel`, fully prerendered

## Interactive pieces

| Component | Pattern |
| --- | --- |
| `FeatureShowcase.svelte` | Tabbed feature detail panel, transitioned with `{#key}` + `fly`/`fade` over a stacked grid cell (no layout jump) |
| `PricingTable.svelte` | Monthly/Annual switch; tier prices recompute reactively via `$state` with zero flicker |
| `DemoForm.svelte` | Client-side validation (required fields + email format) with `$derived` errors, blur/submit-gated messages, and a mock success state |

## Develop

```bash
npm install
npm run dev
```

## Build

```bash
npm run build      # outputs via adapter-vercel
npm run preview    # preview the production build
npm run check      # svelte-check / typecheck
```

## Deploy

Push to GitHub and import the repo in Vercel — the Vercel adapter is already configured,
no project settings needed. The site is 100% prerendered, so it serves as static assets.

## Structure

```
src/
  lib/
    components/   Hero, DashboardMock, LogoStrip, FeatureShowcase,
                  PricingTable, Testimonials, DemoForm, Footer, Nav, Icon
    data/         features.json, pricingTiers.json
  routes/
    +layout.svelte / +layout.ts (prerender)
    +page.svelte  (assembles the single-page site)
```
