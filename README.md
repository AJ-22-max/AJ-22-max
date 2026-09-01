# Juliet Ada Adue

**Frontend Engineer — React & TypeScript**

I build the parts of software that people actually touch: dashboards, editors,
onboarding flows, and the small interactions that decide whether a product feels
finished or not. I have 3+ years on production SaaS: a multi-tenant CRM, school
management platforms, and the marketing sites in front of them. I own features end to end rather than picking
up tickets.

I started out in QA, testing websites and platforms and writing bug reports before
I built them. It shows in what I care about: complex form state that stays predictable,
what a screen looks like before the data arrives, and what happens on a slow connection.

**Currently:** Frontend Engineer at BMG, 2+ years building a multi-tenant CRM
and commerce platform for African businesses.
**Portfolio:** [portfolio-three-eta-onu3egb1ns.vercel.app](https://portfolio-three-eta-onu3egb1ns.vercel.app)
**Open to:** Frontend / Software Engineer roles. Open to relocation.

---

## Tech

**Frontend**
React 18 · TypeScript · JavaScript (ES2022) · Vite · React Router
MUI · Tailwind CSS · Emotion / styled-components · Framer Motion

**Data & tooling**
TanStack Query · Axios · REST · dnd-kit · Git · ESLint

---

## Selected work

Most of the code below lives in private company repositories, so I've written up
what I built and the decisions behind it instead. Where the work *is* public, I've
linked straight to my commit history so you can read the actual changes.

**Publicly browsable commits:**
[School Portal site](https://github.com/advanztek/sch_portal/commits?author=AJ-22-max) ·
[Advanztek site](https://github.com/advanztek/advanztek-landing-page/commits?author=AJ-22-max)

I'm happy to walk through any of the private work in detail, or screen-share it live.

### BMG CRM — multi-tenant CRM & business platform
`React 18 · MUI · TanStack Query · Axios · dnd-kit`

An all-in-one platform for small businesses: clients, projects, tasks,
invoicing, a public storefront, email campaigns, and WhatsApp messaging — each
tenant with its own branding, currency, and domain.

Features I built and own:

- **Invoice editor** with stackable tax rules, brand colour picker, logo upload,
  and live preview — the highest-traffic screen in the product.
- **Attachments system** with in-browser previews for images, video, PDF, and
  Office documents — including previewing a file before it uploads, with object-URL
  lifecycle handling so cycling through files doesn't leak memory. Pasted links
  render as rich preview cards.
- **Project & task management** — drag-and-drop boards via dnd-kit, multi-select
  assignees, date-range and assignee filters, and an archive flow.
- **Admin analytics** — built the acquisition-channel reporting view and the data
  layer behind it.
- **Performance work** — cut oversized PNG payloads by roughly 90% while keeping
  transparency, and added preconnect hints for the media host.
- **Mobile UX pass** across the dashboard: consistent page headers, responsive
  navigation, and a floating action button pattern for small screens.

### SchoolPortal — school management platform
`TypeScript · React`

Administrative dashboard for schools — student records, sessions and terms,
examinations and results, staff administration. What I built:

- **ID card designer** — school logo handling, per-element opacity controls,
  avatar placeholders, and server-side search in the issue picker.
- **Session management** — batched subject carry-forward on session creation,
  with a progress state so a long setup stays visible instead of looking frozen.
- **Student promotion** — session and term selection with old/new intake handling.
- **Overview redesign** — short-form class and programme cards, nickname-first tabs.

### BMG marketing sites — designed and rebuilt from scratch
`React · TypeScript · MUI · Vite`

I redesigned and rebuilt both public-facing BMG sites end to end, design through
to deployment.

- **Homepage and alternative homepage** — full UI design, then built.
- **Authentication, About, documentation and pricing pages**, with pricing driven
  by live plan data rather than hardcoded tiers.
- **Brand refresh** across both sites: new logo assets and a move from the orange
  accent to the current blue system.
- **Docs search**, interactive product demos, a case-study toggle, and the
  legal/compliance pages.
- **Performance** — compressed the About imagery from roughly **8.9 MB to 340 KB**,
  and did a separate pass on the CRM site's load speed.

### Client web applications
`TypeScript · React · Vite · Tailwind · Framer Motion`
**[Browse my 25 commits on the School Portal site →](https://github.com/advanztek/sch_portal/commits?author=AJ-22-max)**

Designed and shipped production sites for Marvel Jeb Co. Ltd, Fidei Polytechnic,
Pamsette Primary School, and the School Portal marketing site — including its
sign-up and sign-in flows, and fixing SPA routing on deployment. Load performance
and accessibility treated as primary concerns rather than afterthoughts.

### NearDropa — delivery & order tracking
`TypeScript · React · MUI · Framer Motion`

Customer-facing order placement, live order tracking, authentication, and
account management screens for a delivery product.

---

## How I work

- I'd rather ask one clarifying question up front than rebuild a feature twice.
- I care about the boring parts: empty states, loading skeletons, error copy,
  and what happens on a slow connection.
- I review my own diffs before anyone else has to.

---

## Get in touch

- **Portfolio:** [portfolio-three-eta-onu3egb1ns.vercel.app](https://portfolio-three-eta-onu3egb1ns.vercel.app)
- **CV:** [Download my CV (PDF)](https://github.com/AJ-22-max/AJ-22-max/blob/main/Juliet-Ada-Adue-CV.pdf)
- **Email:** okpejuliet08@gmail.com
- **GitHub:** [@AJ-22-max](https://github.com/AJ-22-max)
- **Location:** Abuja, Nigeria (WAT, UTC+1) — open to relocation

Happy to walk through any of the work above on a call, or share a live
screen-recording walkthrough of the CRM.
