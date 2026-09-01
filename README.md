# Juliet Ada Adue

**Frontend Engineer — React & TypeScript**

I build the parts of software that people actually touch: dashboards, editors,
onboarding flows, and the small interactions that decide whether a product feels
finished or not. Most of my work over the last three years has been on
production SaaS — multi-tenant CRM, school management portals, and commerce
front-ends — for teams where I own features end to end rather than picking up
tickets.

I work comfortably across the stack. My centre of gravity is React, but I write
the Express/Postgres endpoints behind my own features when that's what ships the
work faster.

**Currently:** Frontend Engineer at Advanztek, building a multi-tenant CRM platform.
**Open to:** Frontend / Software Engineer roles. Open to relocation.

---

## Tech

**Frontend**
React 18 · TypeScript · JavaScript (ES2022) · Vite · React Router
MUI · Tailwind CSS · Emotion / styled-components · Framer Motion

**State & data**
TanStack Query · Zustand · Axios · Socket.IO · REST

**Testing & tooling**
Playwright · React Testing Library · Vitest · ESLint · Git · Turborepo

**Backend**
Node.js · Express · PostgreSQL · Redis · AWS S3 · JWT · Joi

---

## Selected work

Most of the code below lives in private company repositories, so I've written up
what I built and the decisions behind it instead. Where the work *is* public, I've
linked straight to my commit history so you can read the actual changes.

**Publicly browsable commits:**
[School Portal](https://github.com/advanztek/sch_portal/commits?author=AJ-22-max) ·
[Advanztek site](https://github.com/advanztek/advanztek-landing-page/commits?author=AJ-22-max)

I'm happy to walk through any of the private work in detail, or screen-share it live.

### BMG CRM — multi-tenant CRM & business platform
`React 18 · MUI · TanStack Query · Zustand · Socket.IO · dnd-kit · Playwright`

An all-in-one platform for small businesses: clients, projects, tasks,
invoicing, a public storefront, email campaigns, and WhatsApp messaging — each
tenant with its own branding, currency, and domain.

Features I built and own:

- **Invoice editor** with stackable tax rules, brand colour picker, logo upload,
  and live preview — the highest-traffic screen in the product.
- **Attachments system** with in-browser previews for images, video, PDF, and
  Office documents, plus rich link unfurling (Open Graph fetch behind an
  SSRF-guarded service) so pasted URLs render as preview cards.
- **Project & task management** — drag-and-drop boards via dnd-kit, multi-select
  assignees, date-range and assignee filters, and an archive flow.
- **Admin analytics** — acquisition-channel charts and reporting views built on
  Recharts.
- **Performance work** — cut oversized PNG payloads by roughly 90% while keeping
  transparency, and added preconnect hints for the media host.
- **Mobile UX pass** across the dashboard: consistent page headers, responsive
  navigation, and a floating action button pattern for small screens.
- **Backend work behind my own features** — payment handling, multi-currency and
  bank details, scheduled automations, and overdue-invoice alerting, built in
  Express against PostgreSQL and Redis.

### School Portal — student & staff management
`TypeScript · React · Turborepo · Node · PostgreSQL`
**[Browse my 25 commits →](https://github.com/advanztek/sch_portal/commits?author=AJ-22-max)**

A portal covering enrolment, results, sessions, and staff administration for
secondary schools, built as a monorepo with separate applications sharing a
common component layer. I worked across the dashboard overview, sign-up and
authentication flows, and error/toast handling.

### Marketing & product sites
`TypeScript · React · Vite · Tailwind · Framer Motion`

Built and shipped the public-facing sites for Fidei Polytechnic, Marvel Jeb Co.
Ltd, Pamsette Primary School, and BMG CRM — including pricing pages driven by
live plan data, interactive product demos, and legal/compliance pages. Work
here was as much about load performance and accessibility as visual design.

### NearDropa — delivery & order tracking
`TypeScript · React · MUI · Framer Motion`

Customer-facing order placement, live order tracking, authentication, and
account management screens for a delivery product.

---

## How I work

- I'd rather ask one clarifying question up front than rebuild a feature twice.
- I care about the boring parts: empty states, loading skeletons, error copy,
  and what happens on a slow connection.
- I write tests for the flows that would actually cost money if they broke.
- I review my own diffs before anyone else has to.

---

## Get in touch

- **Email:** okpejuliet08@gmail.com
- **GitHub:** [@AJ-22-max](https://github.com/AJ-22-max)
- **Location:** Abuja, Nigeria (WAT, UTC+1) — open to relocation

Happy to walk through any of the work above on a call, or share a live
screen-recording walkthrough of the CRM.
