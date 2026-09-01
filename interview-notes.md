# Interview notes — 5pm

Everything below is drawn from your real commits. All of it is true and you can defend it.

---

## 1. YOUR FOUR STORIES (memorise the shape, not the words)

### STORY A — "Tell me about something technically interesting you built"
**The link-preview / attachments system. This is your best story. Lead with it.**

- **Situation:** Users pasted URLs into task comments and attachments. They rendered as raw blue text — no context, easy to miss what a link actually was.
- **Task:** Make pasted links render as rich preview cards, like Slack or Notion.
- **Action:**
  - Built an unfurl service that fetches the target page and reads its Open Graph tags (title, description, image, site name).
  - Guarded it against SSRF: a server that fetches arbitrary user-supplied URLs can be tricked into hitting internal addresses — cloud metadata endpoints, localhost, private IP ranges. I validate and block those before any fetch happens.
  - Two layers of not-refetching: an in-memory cache keyed on the normalised URL with a 10-minute TTL (so bursts of the same link cost one fetch), and the resolved metadata persisted to a `link_meta` column alongside the attachment (so it survives restarts and renders instantly forever after).
  - On the frontend, the preview appears live as you paste, before upload, so you can confirm it's the right link before committing.
- **Result:** Links became scannable. And the SSRF guard meant a user-facing convenience feature didn't quietly become a way into our internal network.

> **Why this story wins:** frontend + backend + security + caching + UX in one feature. If they only remember one thing about you, make it this.
> If they ask "what's SSRF?" — Server-Side Request Forgery. You make the server fetch a URL you control, and use it to reach things you can't reach directly.

---

### STORY B — "Tell me about a time you improved performance"

- **Situation:** Dashboard loaded slowly, badly so on Nigerian mobile connections.
- **Task:** Cut the payload without losing visual quality.
- **Action:** Profiled what was actually heavy — oversized PNGs exported far larger than their display size. Recompressed them, preserving transparency where the design needed it. Added preconnect hints so the browser opens the connection to the media host early instead of waiting.
- **Result:** ~90% smaller image payloads. Noticeably faster on slow connections.

> If they push — *"why not WebP/AVIF?"* — that's a fair question, and a good answer is "that was the next step; the quick win was recompression, and I shipped that first." Never pretend you did something you didn't.

---

### STORY C — "Tell me about a technical decision you made"
**Multi-currency in a multi-tenant product.**

- **Situation:** Businesses in different countries issue invoices in different currencies.
- **Task:** Decide what determines the currency shown on any given document.
- **Action:** The tempting shortcut is geolocating the viewer's IP. I argued against it: an invoice's currency is a property of the *business and the document*, not of whoever happens to be looking at it. A Nigerian client viewing a Ghanaian business's invoice must see the Ghanaian amount — anything else is wrong, and with money, wrong is expensive. I moved formatting into a helper that *requires* an explicit currency, so you cannot accidentally render an amount with a defaulted one.
- **Result:** Correct amounts everywhere; the class of bug was designed out rather than fixed case by case.

> **This is your seniority story.** It shows judgment, not just coding.

---

### STORY D — "Tell me about a bug that was hard to track down"

- **Situation:** Currency symbols and certain characters rendered as empty boxes (tofu) in the UI.
- **Task:** Find out why.
- **Action:** Not a data problem — the brand font simply had no glyphs for those characters. Fixed with a font fallback chain to Noto Sans, so any glyph the brand font lacks is picked up by a font that has it.
- **Result:** Symbols render correctly without abandoning the brand typeface.

> Shows you debug from evidence rather than guessing, and that you know rendering and i18n are real problem areas.

---

## 2. THE QUESTION YOU MUST NOT BE CAUGHT BY

**"Your GitHub doesn't have much public code."**

Your answer:

> "Everything I've built for the last three years is commercial and private — a multi-tenant CRM, school portals, client sites. My contribution graph shows the volume, and there are two repos where my commits are public and you can read them. I can't publish my employer's code, but I'm happy to screen-share and walk you through any of it live, or talk through any decision in detail."

Calm, factual, no apology. This is the normal situation for working engineers. Then immediately offer Story A — turn the weak question into your best answer.

---

## 3. TECHNICAL QUESTIONS TO EXPECT (React / frontend)

- `useMemo` vs `useCallback`, and when *not* to reach for them
- Why keys matter in lists, and why index-as-key breaks things
- `useEffect`: dependency arrays, cleanup, why it runs twice in StrictMode
- Controlled vs uncontrolled inputs
- TanStack Query: caching, staleness, invalidation after mutation — you use this daily, so speak from experience, not theory
- State management: why Zustand over Redux or Context here
- How you'd debug a slow-rendering list
- Accessibility basics: semantic HTML, labels, keyboard navigation, focus management
- CSS: flexbox vs grid, and your responsive strategy

Say *"I don't know, but here's how I'd find out"* when it's true. It reads as senior. Bluffing is the one thing that reliably fails an interview.

---

## 4. ASK THEM THESE

- What does the frontend stack look like, and what's the biggest source of tech debt?
- How do features go from idea to production here? Who writes the specs?
- What does code review look like on your team?
- What would a successful first three months look like in this role?
- *(If this is VanHack rather than the employer directly:)* Which companies are you matching me with, and what does their sponsorship process look like?

---

## 5. RELOCATION / LOGISTICS

- Be straightforward: currently in Abuja, relocation-ready, husband relocating too.
- Expect *"do you need sponsorship?"* — answer plainly, yes. Nothing to apologise for; it's exactly the situation VanHack exists to handle.
- **Salary:** if pushed, it's fine to say *"I'd like to understand the role better first, and I'd welcome your range."* Don't name a number blind — the Nigeria/Canada gap means an anchor from your local market will badly undersell you.
- Have ready: notice period, earliest start date.

---

## 6. LAST 30 MINUTES BEFORE THE CALL

- [ ] Test camera, mic, internet. Have a phone hotspot as backup.
- [ ] Open your GitHub profile in a tab — glance at it so it's fresh in your mind.
- [ ] Have BMG CRM running locally, ready to screen-share if invited to.
- [ ] Water. Notepad. Quiet room. Door shut.
- [ ] Read Story A once more. That's your opener.

---

## 7. STORY A — DEEP DIVE (know this cold)

File: `bmg-crm/src/services/link-unfurl.service.js` (261 lines, yours)
Frontend: `LinkCard` in `Attachments.jsx:209`, live preview at line 913

**Your SSRF defences, in order:**
1. Protocol allowlist — http/https only
2. DNS-resolve hostname, check EVERY returned IP (`all: true`), not just the string
3. Block private ranges: 10/8, 127/8, 0/8, 169.254/16 (cloud metadata), 172.16/12,
   192.168/16, 100.64/10 CGNAT, multicast. IPv6: ::1, fe80, fc/fd, IPv4-mapped.
4. Block hostnames: localhost, *.localhost, *.local, *.internal
5. `redirect: "manual"` + re-check every hop, max 4 redirects
6. 6s timeout, 1MB cap, streamed via reader and cancelled at the limit
7. Content-type must be HTML

**THE POINT TO LEAD WITH:** the manual redirect handling. If fetch follows redirects
automatically, an attacker gives you an innocent public URL that 302s to
169.254.169.254 (AWS metadata) and your SSRF check is bypassed on hop one.
Re-checking every hop is the correct defence and most people miss it.

**Then:** cheerio parses og:title -> twitter:title -> <title> with fallbacks, resolves
relative image URLs against the final URL, caches in-memory on a 10-min TTL,
persists to the `link_meta` column.

**IF THEY ASK ABOUT DNS REBINDING** (they'd be right to):
"Yes — that's a time-of-check-to-time-of-use gap. The hardened fix is pinning the
resolved IP and connecting to it directly through a custom HTTP agent. I scoped this
as acceptable for a low-privilege preview feature and documented that tradeoff in the
file header rather than leaving it implicit."
-> Your own header comment says "not a hardened proxy". Naming your threat model's
   limits is a senior signal. This gotcha is your best moment, not your worst.

**DELIVERY:**
- 90 seconds, then STOP and let them ask.
- Open on the problem, not the tech: "pasted links rendered as raw blue text with
  no context." SSRF comes up when they ask why it was hard.
- Have the file open in case they invite a screen-share.

---

## 8. IF THEY ASK ABOUT TESTING (they will)

You have NOT written the Playwright or React Testing Library specs — your team lead did.
Do not claim them. Nothing is on your CV or README saying you did.

**Honest answer that still lands well:**
"Our codebase has Playwright end-to-end coverage and React Testing Library component
tests — my team lead owns most of that suite. I work in that codebase daily and my
features have to pass it, so I read and debug those tests, but I haven't been the one
authoring the suite. Writing more of it myself is something I want to do more of."

>> Wanting to grow into something is a perfectly good answer. Claiming it and then
>> failing a follow-up is not. Same rule as everything else today.

**What you CAN claim on quality:** you review your own diffs, you handle empty states,
loading and error paths deliberately, and you shipped a QA batch of client-reported
fixes (real commits, Aug 2026).
