# CLAUDE.md — Smitha Webinar Funnel

## Project Overview

This is a **Next.js 14 landing page / funnel** for a free healthcare communication masterclass webinar hosted by **Smitha Chowdary Kankanala** through the **CHCP (Center for Healthcare Communication Practice)**.

**Live URL:** https://smitha-new.vercel.app/
**Deployed on:** Vercel (static export)
**Event:** April 19, 2026, 11:00 AM IST

---

## Client Context

**Client:** Smitha Chowdary Kankanala  
**Organization:** CHCP — Center for Healthcare Communication Practice  
**Target audience:** Doctors, nurses, and healthcare leaders  
**Value proposition:** Bridges the gap between knowing what to say and executing communication effectively in high-pressure healthcare moments — using the "CHCP system"

**Webinar topics covered:**
- Why communication fails among skilled medical practitioners
- Navigating hierarchy and escalation in healthcare
- Team communication breakdowns
- Patient communication strategies
- Decision-making and advocacy clarity

---

## Tech Stack

| Layer | Choice |
|---|---|
| Framework | Next.js 14.1.0 (App Router) |
| Language | TypeScript |
| Styling | Tailwind CSS 3.4 + global CSS |
| Fonts | Bebas Neue (headings), Barlow (body) via next/font/google |
| Deployment | Vercel — static export (`output: 'export'`) |

---

## Project Structure

```
smitha-webinar/
├── app/
│   ├── layout.tsx         # Root layout — fonts, metadata, glow effects
│   ├── page.tsx           # Single-page app — all content + JS logic
│   ├── globals.css        # Base styles, glow effects, Tailwind directives
│   └── sitemap.ts         # Sitemap generation
├── public/
│   ├── chcp-logo.png      # CHCP organization logo
│   ├── thumbnail.png      # OG/Twitter social share image
│   └── robots.txt
├── next.config.js         # Static export config, images unoptimized
├── tailwind.config.js     # Custom colors, fonts, animations
├── vercel.json            # Vercel deployment config
└── package.json
```

> Note: There are several loose files in the root (`.html`, `.tsx`, `.css`, `.js`, `.txt`) that are **artifacts from the original build process** — not part of the Next.js app. They can be cleaned up but are not served.

---

## Design System

**Color palette:**
- Background: `#0B1017` (near-black, custom `dark` token)
- Primary accent: `#14B87E` (teal, maps to `teal` token)
- Muted text: `#8FA3B3`
- Text: white

**Typography:**
- `font-bebas` (Bebas Neue) — display/headings, uppercase
- `font-barlow` (Barlow) — body copy, weights 300/400/500/600

**Effects:**
- Fixed radial glow blobs (teal, blurred) in top-left and mid-right via `.glow-left` / `.glow-right`
- Gradient accents inline throughout sections

---

## Page Architecture

`app/page.tsx` is a **single large client component** (`'use client'`). It contains:

1. **Countdown timer** — counts down to April 19, 2026 11:00 AM IST using DOM manipulation via `useEffect`
2. **FAQ accordion** — toggle open/close via class manipulation
3. **Seat scarcity counter** — fake urgency countdown from ~66 seats
4. **Registration popup** — modal with form validation (name, email, WhatsApp, healthcare role)
5. **Form logic** — client-side validation with real-time feedback + error states
6. **All page HTML** — hero, event details, "who this is for", social proof, FAQ, CTA sections

**Global functions on `window`:** `openPopup`, `closePopup`, `handleFormSubmit` — these are set on `window` because the HTML inside the component uses inline `onclick` attributes.

---

## Known Issues / Things to Watch

- `page.tsx` is **426KB** — extremely large single file with all HTML inlined as JSX. Should be broken into components eventually.
- Form submission (`handleFormSubmit`) only logs data to console — **no actual backend integration yet**. Needs an API endpoint or third-party service (e.g. ConvertKit, Mailchimp, Make.com webhook).
- `verification.google` in metadata is set to `'your-google-verification-code'` — placeholder, needs real value.
- `output: 'export'` in next.config.js means **no server-side features** (API routes, middleware, ISR) work — pure static site.
- Images are `unoptimized: true` — no Next.js image optimization.

---

## Key Commands

```bash
npm run dev      # Start local dev server (http://localhost:3000)
npm run build    # Static export build → ./out/
npm run start    # Serve built output
npm run lint     # ESLint
```

---

## Deployment

- Deployed automatically via Vercel on push to main branch
- `vercel.json` uses `@vercel/next` builder
- Static export goes to `./out/` directory
- `trailingSlash: true` is set — all routes end with `/`

---

## Installed Skills

- `vercel-labs/next-skills` — Next.js best practices, Server/Client Component guidance, data fetching patterns, caching, SEO, upgrade guidance
- `tirth8205/code-review-graph` — Structural knowledge graph for efficient code reviews (blast radius analysis, 8x token reduction)
