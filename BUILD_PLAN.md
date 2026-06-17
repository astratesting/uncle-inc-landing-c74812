# Uncle Inc. — Build Plan

## 1. PRODUCT
A dark-themed marketing landing page for **Uncle Inc.**, an AI-assisted MVP development platform that turns a founder's idea into a working, deployed MVP through a guided agentic pipeline (spec → architecture → build → deploy). The site has one job: convert founder visitors into sign-ups by making the value legible in under ten seconds and giving them exactly two clear next actions — "Start a build" or "Read the docs." Every section is engineered to move that visitor down the page; no decorative filler, no invented social proof.

## 2. WHO IT'S FOR
- **Primary ICP:** non-technical solo founder or technical co-founder at a seed-stage startup, ages 25–45, with limited engineering time and a defined idea they want shipped within 2–4 weeks.
- **Tone implications:** dense, direct, slightly opinionated. No hand-holding language ("Let us help you succeed!"). Mono-font code snippets and terminal-style UI to signal "this is built by builders, for builders." Short sentences. Active voice. Engineering jargon used correctly.
- **Pain being addressed:** founders spend months and tens of thousands of dollars to validate an idea with a real product; Uncle collapses that loop into a single AI-driven pipeline they can run in an evening.

## 3. LOOK & FEEL

### Visual system
- **Vibe:** dark, terminal-grade, analytical. Closer to a Vercel/Linear feel than a SaaS template. Slight grain noise overlay (2% opacity) to break up flat black.
- **Palette (locked, use only these):**
  - `ink` `#0a0a0f` — page background
  - `ink-2` `#11111a` — elevated surface
  - `ink-3` `#1a1a25` — border / muted
  - `indigo` `#4f46e5` — primary action
  - `cyan` `#06b6d4` — accent / code highlight
  - `teal` `#14b8a6` — secondary accent / success
  - `text` `#e6e6ef` — body
  - `mute` `#7a7a8c` — secondary text
- **Typography:**
  - Headings: **Space Grotesk** 600/700. Tight tracking (-0.02em). Display sizes 72/56/44/32/24.
  - Body: **Inter** 400/500 (loaded as fallback alongside Space Grotesk for paragraph legibility).
  - Code/UI labels: **JetBrains Mono** 400/500. Used for badges, version numbers, terminal blocks.
- **Layout:** 1280px max content width, 24px gutter, 96–128px section vertical padding, asymmetric 12-col grid, hairline `ink-3` borders (1px) instead of cards-with-shadows. Hover states use a 1px border shift to `indigo` + 200ms ease.
- **Iconography:** thin-stroke line icons (Lucide, 1.25px stroke), 20px default, never decorative.
- **Imagery:** none. Use rendered mockups (terminal windows, code blocks, JSON snippets) instead of stock photos.
- **Motion:** subtle. Fade-up 8px on scroll-in (once, 400ms). No parallax. Buttons have a 1px outline that fills on hover. A pulsing 8px dot in the nav "Live build" badge is the only ambient motion.

### Sections (top to bottom on `/`)

1. **Nav (sticky, 64px)** — left: wordmark `uncle/inc` in mono. center: links `Build`, `Process`, `Pricing`, `Docs`. right: `Sign in` (ghost) + `Start a build` (filled indigo).
2. **Hero** — 80vh. Two-column desktop (60/40). Left: kicker badge `v0.4 · AGENTIC BUILD PIPELINE` (mono, teal). H1: "From idea to deployed MVP in an evening." Sub: "Describe what you want. Our agent pipeline writes the spec, the code, the tests, and the deploy. You wake up to a live URL." Two CTAs: primary indigo "Start a build →", secondary ghost "See the process". Right: a terminal mockup (rounded 12px, `ink-2` bg, 1px border, top traffic-light dots, mono font) showing 6 lines of a real-feeling build log: `> uncle init "marketplace for dog walkers"`, `> analyzing…`, `> generating spec.md (1,204 tokens)`, `> scaffolding next.js + supabase…`, `> deploying to vercel…`, `✓ live at https://doglop.vercel.app`.
3. **Social strip (NOT fake testimonials)** — neutral, factual: built with Next.js · TypeScript · Supabase · Tailwind · Vercel. Five small mono labels separated by `·`. No logos of customers.
4. **Features (3-up grid, then 2-up alternating rows)** — 5 features total, each with: small mono label (`01 / SPEC`), 24px heading, 2-line description, 80x80 mini-visual (terminal snippet or JSON block rendered as code):
   - `01 / SPEC` — Natural-language spec generation. Output is editable markdown.
   - `02 / ARCHITECT` — Data model, routes, auth — auto-derived.
   - `03 / BUILD` — Code written against your stack, not a generic template.
   - `04 / TEST` — Unit + e2e tests generated alongside every feature.
   - `05 / SHIP` — One-click deploy with preview URLs per branch.
5. **Process timeline** — vertical 4-step strip with hairline connector: `Describe → Plan → Approve → Ship`. Each step: mono index, title, 1-sentence description, estimated time.
6. **Pricing** — 3 tiers, equal cards, indigo top-border on highlighted "Founder" tier:
   - **Solo — $0**: 1 active project, community support, public repos only.
   - **Founder — $49/mo** (highlighted): 5 active projects, private repos, 50k build tokens/mo, email support.
   - **Studio — $199/mo**: 25 active projects, team seats, 250k tokens, priority queue, SSO.
   - Sub-line in mono under cards: "Tokens are compute units our agents consume. 1 token ≈ 1 generated file."
7. **FAQ** — 6 questions, two-column on desktop (Q left, A right), each in a 1px-bordered row. Topics: what counts as a build token, can I bring my own repo, do you write production code, what stacks are supported, is the code mine, can I cancel anytime.
8. **Final CTA** — centered. H1 "Ship something this week." One primary button. Below in mono: "No credit card. First build is free."
9. **Footer** — 4 columns: Product (Build, Pricing, Changelog, Roadmap), Resources (Docs, API, Status, GitHub), Company (About, Contact, Terms, Privacy), and a small newsletter input. Bottom row: `© 2026 Uncle Inc.` left, `uncle/inc` wordmark right.

## 4. USER FLOWS
This is a single marketing page, so the only flows are micro-conversions:
- **Flow A — Primary conversion:** Land on hero → read H1 → click `Start a build` → routes to `/signup` (placeholder route returning a "Coming soon" page that the user can implement next; the link is real, the route is honest).
- **Flow B — Secondary conversion:** Scroll to pricing → click tier CTA → same `/signup?plan=founder` route.
- **Flow C — Docs deflection:** Click `Docs` in nav → `/docs` placeholder page with a 3-bullet "What you'll find here" and a mailto link to founders@uncle.inc.
- **States:** Nav becomes opaque + 1px bottom border after the user scrolls > 40px. FAQ rows toggle open/close (one at a time, accordion). No error states required for this static page.

## 5. PAGES / ROUTES
| Route | Purpose | Layout & main elements |
|---|---|---|
| `/` | Primary landing page | Nav → Hero → StackStrip → Features → Process → Pricing → FAQ → CTA → Footer. Single document, anchor-linked. |
| `/signup` | Honest placeholder for the CTA target | Centered card on `ink` bg. H1 "Sign up is invite-only right now." Mono paragraph + `Request access` button (mailto). Real route, not a fake form. |
| `/docs` | Honest placeholder for nav link | 3-skeleton blocks ("Getting started", "CLI reference", "Pipeline config") each labeled `coming soon` in mono. |
| `/changelog` | Real, empty-state changelog | Header `Changelog` + 3 empty entries dated 2026-04, 2026-05, 2026-06 each with a single honest bullet (e.g. "Added spec generation for Next.js 14 projects."). No invented metrics. |
| `not-found.tsx` | 404 | Centered mono block. |

## 6. CORE FEATURES
Each is a real, implementable component with explicit behavior.

- **StickyNav** — fixed top, `backdrop-blur` + 70% `ink` bg, 1px bottom border appears on scroll. Mobile (<768px): collapses links into a slide-down panel toggled by a 24px hamburger; CTAs remain visible.
- **HeroTerminal** — pure JSX/CSS, no real terminal. Renders a 6-line build log with a 1.2s `▍` caret blink on the last line. Renders server-side identically; the caret uses a CSS `animate-pulse`.
- **FeatureCard** — numbered mono index, 24px Space Grotesk title, 2-line Inter body, 80x80 inner visual (one of: `{ ... }` JSON mockup, `> npm run build` snippet, route table `GET /api/x`). 1px border, 16px radius, hover → border becomes `indigo`.
- **ProcessStep** — vertical timeline item with a 1px vertical connector line, 32px circle containing the mono index, title, time estimate.
- **PricingCard** — three variants via prop. Highlighted card: 1px `indigo` top border + `teal` "Most chosen" mono badge. CTA button disabled-styled if free tier, indigo-filled otherwise.
- **FAQItem** — accordion using `<details>`/`<summary>` for zero-JS, with custom `+ / −` indicator via `[open]` selector.
- **CTABand** — full-width band with a faint radial indigo-to-teal gradient at 8% opacity, large H1, single primary button, mono fine print.
- **Footer** — 4-column grid desktop, stacked mobile. Newsletter input is a real `<form action="mailto:">` (no fabricated endpoint).
- **RevealOnScroll** — small client component wrapping children with `IntersectionObserver`; adds `opacity-100 translate-y-0` once. SSR-safe (starts `opacity-0 translate-y-2`).

## 7. DATA MODEL
Static site — no DB. The only "data" is a typed module `lib/content.ts` exporting:
```ts
export const features: Feature[]     // 5 items: index, kicker, title, body, visualKind
export const processSteps: Step[]    // 4 items: index, title, body, eta
export const pricingTiers: Tier[]    // 3 items: name, price, cta, highlighted, features[]
export const faq: QA[]               // 6 items: q, a
export const changelog: Entry[]      // 3 items: date, items[]
```
All consumed by the page components. This keeps copy editable in one place without inventing a CMS.

## 8. AUTH
Not applicable to this milestone — the landing page has no auth-gated surface. The `/signup` route is an honest placeholder, not a form that pretends to register users. No Supabase, NextAuth, or Clerk is wired in this build; adding them is a separate milestone. Do not ship a fake form.

## 9. FILES
```
package.json
next.config.js
tsconfig.json
postcss.config.js
tailwind.config.ts
app/globals.css
app/layout.tsx
app/page.tsx
app/signup/page.tsx
app/docs/page.tsx
app/changelog/page.tsx
app/not-found.tsx
components/Nav.tsx
components/Hero.tsx
components/StackStrip.tsx
components/Features.tsx
components/FeatureCard.tsx
components/Process.tsx
components/Pricing.tsx
components/PricingCard.tsx
components/FAQ.tsx
components/FAQItem.tsx
components/CTA.tsx
components/Footer.tsx
components/RevealOnScroll.tsx
components/icons.tsx
lib/content.ts
lib/cn.ts
```

## 10. ACCEPTANCE
- [ ] `npm install && npm run dev` starts the app on port 3000 with zero errors and zero console warnings.
- [ ] `npm run build` completes successfully (TypeScript strict on).
- [ ] `/` renders Nav → Hero → StackStrip → Features → Process → Pricing → FAQ → CTA → Footer in that order.
- [ ] Color tokens in `tailwind.config.ts` are exactly `#0a0a0f`, `#4f46e5`, `#06b6d4`, `#14b8a6` (plus the derived `ink-2/3`, `text`, `mute`).
- [ ] Space Grotesk is applied to `h1`–`h6`; JetBrains Mono is applied to `.mono` utility class and the terminal mockup.
- [ ] Page background is `#0a0a0f`; no white sections, no light-mode flash on load.
- [ ] Nav links to `/docs` and `/changelog` work; `/signup` renders a real placeholder (not a fake form).
- [ ] Nav becomes opaque after 40px scroll (verifiable in DevTools by toggling a class).
- [ ] Mobile (<768px): nav collapses, single-column hero, single-column pricing, footer stacks.
- [ ] No fake testimonials, no invented user counts, no star ratings, no customer logos, no "as seen in" press. StackStrip lists only Uncle's own technology choices.
- [ ] FAQ uses native `<details>`/`<summary>` — open/close works with JS disabled.
- [ ] All copy lives in `lib/content.ts`; no string literals are duplicated across components.
- [ ] Lighthouse on `/`: Performance ≥ 90, Accessibility ≥ 95, Best Practices ≥ 95, SEO ≥ 95.
- [ ] Buttons have visible focus rings (2px teal outline, 2px offset).
- [ ] No external image fetches; all visuals are inline JSX/CSS.

FILES: ["package.json","next.config.js","tsconfig.json","postcss.config.js","tailwind.config.ts","app/globals.css","app/layout.tsx","app/page.tsx","app/signup/page.tsx","app/docs/page.tsx","app/changelog/page.tsx","app/not-found.tsx","components/Nav.tsx","components/Hero.tsx","components/StackStrip.tsx","components/Features.tsx","components/FeatureCard.tsx","components/Process.tsx","components/Pricing.tsx","components/PricingCard.tsx","components/FAQ.tsx","components/FAQItem.tsx","components/CTA.tsx","components/Footer.tsx","components/RevealOnScroll.tsx","components/icons.tsx","lib/content.ts","lib/cn.ts"]# Uncle Inc. — Build Plan

## 1. PRODUCT
A dark-themed marketing landing page for **Uncle Inc.**, an AI-assisted MVP development platform that turns a founder's idea into a working, deployed MVP through a guided agentic pipeline (spec → architecture → build → deploy). The site has one job: convert founder visitors into sign-ups by making the value legible in under ten seconds and giving them exactly two clear next actions — "Start a build" or "Read the docs." Every section is engineered to move that visitor down the page; no decorative filler, no invented social proof.

## 2. WHO IT'S FOR
- **Primary ICP:** non-technical solo founder or technical co-founder at a seed-stage startup, ages 25–45, with limited engineering time and a defined idea they want shipped within 2–4 weeks.
- **Tone implications:** dense, direct, slightly opinionated. No hand-holding language ("Let us help you succeed!"). Mono-font code snippets and terminal-style UI to signal "this is built by builders, for builders." Short sentences. Active voice. Engineering jargon used correctly.
- **Pain being addressed:** founders spend months and tens of thousands of dollars to validate an idea with a real product; Uncle collapses that loop into a single AI-driven pipeline they can run in an evening.

## 3. LOOK & FEEL

### Visual system
- **Vibe:** dark, terminal-grade, analytical. Closer to a Vercel/Linear feel than a SaaS template. Slight grain noise overlay (2% opacity) to break up flat black.
- **Palette (locked, use only these):**
  - `ink` `#0a0a0f` — page background
  - `ink-2` `#11111a` — elevated surface
  - `ink-3` `#1a1a25` — border / muted
  - `indigo` `#4f46e5` — primary action
  - `cyan` `#06b6d4` — accent / code highlight
  - `teal` `#14b8a6` — secondary accent / success
  - `text` `#e6e6ef` — body
  - `mute` `#7a7a8c` — secondary text
- **Typography:**
  - Headings: **Space Grotesk** 600/700. Tight tracking (-0.02em). Display sizes 72/56/44/32/24.
  - Body: **Inter** 400/500 (loaded as fallback alongside Space Grotesk for paragraph legibility).
  - Code/UI labels: **JetBrains Mono** 400/500. Used for badges, version numbers, terminal blocks.
- **Layout:** 1280px max content width, 24px gutter, 96–128px section vertical padding, asymmetric 12-col grid, hairline `ink-3` borders (1px) instead of cards-with-shadows. Hover states use a 1px border shift to `indigo` + 200ms ease.
- **Iconography:** thin-stroke line icons (Lucide, 1.25px stroke), 20px default, never decorative.
- **Imagery:** none. Use rendered mockups (terminal windows, code blocks, JSON snippets) instead of stock photos.
- **Motion:** subtle. Fade-up 8px on scroll-in (once, 400ms). No parallax. Buttons have a 1px outline that fills on hover. A pulsing 8px dot in the nav "Live build" badge is the only ambient motion.

### Sections (top to bottom on `/`)

1. **Nav (sticky, 64px)** — left: wordmark `uncle/inc` in mono. center: links `Build`, `Process`, `Pricing`, `Docs`. right: `Sign in` (ghost) + `Start a build` (filled indigo).
2. **Hero** — 80vh. Two-column desktop (60/40). Left: kicker badge `v0.4 · AGENTIC BUILD PIPELINE` (mono, teal). H1: "From idea to deployed MVP in an evening." Sub: "Describe what you want. Our agent pipeline writes the spec, the code, the tests, and the deploy. You wake up to a live URL." Two CTAs: primary indigo "Start a build →", secondary ghost "See the process". Right: a terminal mockup (rounded 12px, `ink-2` bg, 1px border, top traffic-light dots, mono font) showing 6 lines of a real-feeling build log: `> uncle init "marketplace for dog walkers"`, `> analyzing…`, `> generating spec.md (1,204 tokens)`, `> scaffolding next.js + supabase…`, `> deploying to vercel…`, `✓ live at https://doglop.vercel.app`.
3. **Social strip (NOT fake testimonials)** — neutral, factual: built with Next.js · TypeScript · Supabase · Tailwind · Vercel. Five small mono labels separated by `·`. No logos of customers.
4. **Features (3-up grid, then 2-up alternating rows)** — 5 features total, each with: small mono label (`01 / SPEC`), 24px heading, 2-line description, 80x80 mini-visual (terminal snippet or JSON block rendered as code):
   - `01 / SPEC` — Natural-language spec generation. Output is editable markdown.
   - `02 / ARCHITECT` — Data model, routes, auth — auto-derived.
   - `03 / BUILD` — Code written against your stack, not a generic template.
   - `04 / TEST` — Unit + e2e tests generated alongside every feature.
   - `05 / SHIP` — One-click deploy with preview URLs per branch.
5. **Process timeline** — vertical 4-step strip with hairline connector: `Describe → Plan → Approve → Ship`. Each step: mono index, title, 1-sentence description, estimated time.
6. **Pricing** — 3 tiers, equal cards, indigo top-border on highlighted "Founder" tier:
   - **Solo — $0**: 1 active project, community support, public repos only.
   - **Founder — $49/mo** (highlighted): 5 active projects, private repos, 50k build tokens/mo, email support.
   - **Studio — $199/mo**: 25 active projects, team seats, 250k tokens, priority queue, SSO.
   - Sub-line in mono under cards: "Tokens are compute units our agents consume. 1 token ≈ 1 generated file."
7. **FAQ** — 6 questions, two-column on desktop (Q left, A right), each in a 1px-bordered row. Topics: what counts as a build token, can I bring my own repo, do you write production code, what stacks are supported, is the code mine, can I cancel anytime.
8. **Final CTA** — centered. H1 "Ship something this week." One primary button. Below in mono: "No credit card. First build is free."
9. **Footer** — 4 columns: Product (Build, Pricing, Changelog, Roadmap), Resources (Docs, API, Status, GitHub), Company (About, Contact, Terms, Privacy), and a small newsletter input. Bottom row: `© 2026 Uncle Inc.` left, `uncle/inc` wordmark right.

## 4. USER FLOWS
This is a single marketing page, so the only flows are micro-conversions:
- **Flow A — Primary conversion:** Land on hero → read H1 → click `Start a build` → routes to `/signup` (placeholder route returning a "Coming soon" page that the user can implement next; the link is real, the route is honest).
- **Flow B — Secondary conversion:** Scroll to pricing → click tier CTA → same `/signup?plan=founder` route.
- **Flow C — Docs deflection:** Click `Docs` in nav → `/docs` placeholder page with a 3-bullet "What you'll find here" and a mailto link to founders@uncle.inc.
- **States:** Nav becomes opaque + 1px bottom border after the user scrolls > 40px. FAQ rows toggle open/close (one at a time, accordion). No error states required for this static page.

## 5. PAGES / ROUTES
| Route | Purpose | Layout & main elements |
|---|---|---|
| `/` | Primary landing page | Nav → Hero → StackStrip → Features → Process → Pricing → FAQ → CTA → Footer. Single document, anchor-linked. |
| `/signup` | Honest placeholder for the CTA target | Centered card on `ink` bg. H1 "Sign up is invite-only right now." Mono paragraph + `Request access` button (mailto). Real route, not a fake form. |
| `/docs` | Honest placeholder for nav link | 3-skeleton blocks ("Getting started", "CLI reference", "Pipeline config") each labeled `coming soon` in mono. |
| `/changelog` | Real, empty-state changelog | Header `Changelog` + 3 empty entries dated 2026-04, 2026-05, 2026-06 each with a single honest bullet (e.g. "Added spec generation for Next.js 14 projects."). No invented metrics. |
| `not-found.tsx` | 404 | Centered mono block. |

## 6. CORE FEATURES
Each is a real, implementable component with explicit behavior.

- **StickyNav** — fixed top, `backdrop-blur` + 70% `ink` bg, 1px bottom border appears on scroll. Mobile (<768px): collapses links into a slide-down panel toggled by a 24px hamburger; CTAs remain visible.
- **HeroTerminal** — pure JSX/CSS, no real terminal. Renders a 6-line build log with a 1.2s `▍` caret blink on the last line. Renders server-side identically; the caret uses a CSS `animate-pulse`.
- **FeatureCard** — numbered mono index, 24px Space Grotesk title, 2-line Inter body, 80x80 inner visual (one of: `{ ... }` JSON mockup, `> npm run build` snippet, route table `GET /api/x`). 1px border, 16px radius, hover → border becomes `indigo`.
- **ProcessStep** — vertical timeline item with a 1px vertical connector line, 32px circle containing the mono index, title, time estimate.
- **PricingCard** — three variants via prop. Highlighted card: 1px `indigo` top border + `teal` "Most chosen" mono badge. CTA button disabled-styled if free tier, indigo-filled otherwise.
- **FAQItem** — accordion using `<details>`/`<summary>` for zero-JS, with custom `+ / −` indicator via `[open]` selector.
- **CTABand** — full-width band with a faint radial indigo-to-teal gradient at 8% opacity, large H1, single primary button, mono fine print.
- **Footer** — 4-column grid desktop, stacked mobile. Newsletter input is a real `<form action="mailto:">` (no fabricated endpoint).
- **RevealOnScroll** — small client component wrapping children with `IntersectionObserver`; adds `opacity-100 translate-y-0` once. SSR-safe (starts `opacity-0 translate-y-2`).

## 7. DATA MODEL
Static site — no DB. The only "data" is a typed module `lib/content.ts` exporting:
```ts
export const features: Feature[]     // 5 items: index, kicker, title, body, visualKind
export const processSteps: Step[]    // 4 items: index, title, body, eta
export const pricingTiers: Tier[]    // 3 items: name, price, cta, highlighted, features[]
export const faq: QA[]               // 6 items: q, a
export const changelog: Entry[]      // 3 items: date, items[]
```
All consumed by the page components. This keeps copy editable in one place without inventing a CMS.

## 8. AUTH
Not applicable to this milestone — the landing page has no auth-gated surface. The `/signup` route is an honest placeholder, not a form that pretends to register users. No Supabase, NextAuth, or Clerk is wired in this build; adding them is a separate milestone. Do not ship a fake form.

## 9. FILES
```
package.json
next.config.js
tsconfig.json
postcss.config.js
tailwind.config.ts
app/globals.css
app/layout.tsx
app/page.tsx
app/signup/page.tsx
app/docs/page.tsx
app/changelog/page.tsx
app/not-found.tsx
components/Nav.tsx
components/Hero.tsx
components/StackStrip.tsx
components/Features.tsx
components/FeatureCard.tsx
components/Process.tsx
components/Pricing.tsx
components/PricingCard.tsx
components/FAQ.tsx
components/FAQItem.tsx
components/CTA.tsx
components/Footer.tsx
components/RevealOnScroll.tsx
components/icons.tsx
lib/content.ts
lib/cn.ts
```

## 10. ACCEPTANCE
- [ ] `npm install && npm run dev` starts the app on port 3000 with zero errors and zero console warnings.
- [ ] `npm run build` completes successfully (TypeScript strict on).
- [ ] `/` renders Nav → Hero → StackStrip → Features → Process → Pricing → FAQ → CTA → Footer in that order.
- [ ] Color tokens in `tailwind.config.ts` are exactly `#0a0a0f`, `#4f46e5`, `#06b6d4`, `#14b8a6` (plus the derived `ink-2/3`, `text`, `mute`).
- [ ] Space Grotesk is applied to `h1`–`h6`; JetBrains Mono is applied to `.mono` utility class and the terminal mockup.
- [ ] Page background is `#0a0a0f`; no white sections, no light-mode flash on load.
- [ ] Nav links to `/docs` and `/changelog` work; `/signup` renders a real placeholder (not a fake form).
- [ ] Nav becomes opaque after 40px scroll (verifiable in DevTools by toggling a class).
- [ ] Mobile (<768px): nav collapses, single-column hero, single-column pricing, footer stacks.
- [ ] No fake testimonials, no invented user counts, no star ratings, no customer logos, no "as seen in" press. StackStrip lists only Uncle's own technology choices.
- [ ] FAQ uses native `<details>`/`<summary>` — open/close works with JS disabled.
- [ ] All copy lives in `lib/content.ts`; no string literals are duplicated across components.
- [ ] Lighthouse on `/`: Performance ≥ 90, Accessibility ≥ 95, Best Practices ≥ 95, SEO ≥ 95.
- [ ] Buttons have visible focus rings (2px teal outline, 2px offset).
- [ ] No external image fetches; all visuals are inline JSX/CSS.

FILES: ["package.json","next.config.js","tsconfig.json","postcss.config.js","tailwind.config.ts","app/globals.css","app/layout.tsx","app/page.tsx","app/signup/page.tsx","app/docs/page.tsx","app/changelog/page.tsx","app/not-found.tsx","components/Nav.tsx","components/Hero.tsx","components/StackStrip.tsx","components/Features.tsx","components/FeatureCard.tsx","components/Process.tsx","components/Pricing.tsx","components/PricingCard.tsx","components/FAQ.tsx","components/FAQItem.tsx","components/CTA.tsx","components/Footer.tsx","components/RevealOnScroll.tsx","components/icons.tsx","lib/content.ts","lib/cn.ts"]