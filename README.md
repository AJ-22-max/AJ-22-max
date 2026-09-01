# Juliet Ada Adue

**Frontend Engineer — React & TypeScript**

I build the parts of software that people actually touch: dashboards, editors,
onboarding flows, and the small interactions that decide whether a product feels
finished or not. Most of my work over the last three years has been on
production SaaS — multi-tenant CRM, school management portals, and commerce
front-ends — for teams where I own features end to end rather than picking up
tickets.

I care about the parts that decide whether a product feels finished: complex form
state that stays predictable, what a screen looks like before the data arrives, and
what happens on a slow connection.

**Currently:** Frontend Engineer & CEO at Advanztek Nig. Ltd, building a multi-tenant CRM platform.
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

### School Management Dashboard
`TypeScript · React · Node · PostgreSQL`

Administrative dashboard for schools — student records, sessions and terms,
examinations and results, staff administration. What I built:

- **ID card designer** — school logo handling, per-element opacity controls,
  avatar placeholders, and server-side search in the issue picker.
- **Session management** — batched subject carry-forward on session creation,
  with a progress state so a long setup stays visible instead of looking frozen.
- **Student promotion** — session and term selection with old/new intake handling.
- **Overview redesign** — short-form class and programme cards, nickname-first tabs.

### Marketing & product sites
`TypeScript · React · Vite · Tailwind · Framer Motion`
**[Browse my 25 commits on the School Portal site →](https://github.com/advanztek/sch_portal/commits?author=AJ-22-max)**

Designed and shipped the public-facing sites for Marvel Jeb Co. Ltd, Fidei
Polytechnic, Pamsette Primary School, the School Portal site, and BMG CRM —
including pricing pages driven by live plan data, interactive product demos, and
legal/compliance pages. Work here was as much about load performance and
accessibility as visual design.

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

- **Email:** okpejuliet08@gmail.com
- **GitHub:** [@AJ-22-max](https://github.com/AJ-22-max)
- **Location:** Abuja, Nigeria (WAT, UTC+1) — open to relocation

Happy to walk through any of the work above on a call, or share a live
screen-recording walkthrough of the CRM.
