# ABTalks — Redesign

A mobile-first redesign of ABTalks' 60-day coding challenge experience for
Indian college students: landing page, student dashboard, and a single
challenge day, built around one real habit — showing up, shipping something,
and proving it with a GitHub commit + a LinkedIn post.

## Route map

```text
/
/dashboard
/day/12
```

Each route is a real folder with its own `index.html`, so they resolve
cleanly on any static host (Vercel, Netlify, GitHub Pages) at exactly the
paths above — no rewrites or query params needed.

## Stack

Plain HTML/CSS/JS. No build step, no framework, no dependencies. Every page
is self-contained (styles and mock data are inlined) so it renders correctly
whether it's opened directly as a file, dropped into any static host, or
served from a subpath. `data/mock.json` documents the same mock data shape
in plain JSON for reference.

## Design approach

- **Mobile-first at 390px.** Every screen was designed for a phone at 11pm,
  not a desktop at 2pm. Desktop gets a centered "app shell" treatment on the
  dashboard/day pages, and a wider marketing layout on the landing page.
- **Dark, ink-based UI** — because the brief states students use this late
  at night on their phones. A bright, cheerful SaaS palette would fight the
  actual usage context.
- **Signature element: the commit grid.** A 60-cell streak grid, styled like
  a GitHub contribution graph, appears on all three screens (preview on the
  landing page, full grid on the dashboard, a mini context-strip on the day
  page). It's the one visual thread tying the product together, and it's
  grounded in the real mechanic (a GitHub commit) rather than an invented
  gamification layer.
- **Type system:** Space Grotesk for display headlines, JetBrains Mono for
  data/labels/streak counts (a real developer typeface, used deliberately
  for a coding-challenge product), Inter for body copy.

## Thoughtful addition: one-tap LinkedIn draft

The two proof-of-work steps (commit + post) aren't equally easy at midnight.
Writing a LinkedIn caption from scratch is real friction that causes streak
drop-off. The Day page includes a **"Draft my post"** button that turns the
day's task into an editable, ready-to-post LinkedIn caption in one tap —
students still write/edit it themselves, but they're never starting from a
blank textbox at midnight.

## Edge cases handled

- **First day, no streak** — the dashboard's state switcher includes a
  "Day 1 (new)" view: 0-day streak, a welcoming banner, a beginner-friendly
  first task, and an empty streak grid instead of a broken-looking 0%.
- **A missed day** — baked into the default dashboard state: Day 7 is shown
  as missed on the streak grid, with a plain-language banner explaining the
  streak reset and when it restarted. History isn't hidden or deleted.
- **An empty profile** — the "Empty profile" state shows no track selected,
  zero streak, an empty badge state with a clear call to action ("Pick a
  track"), instead of blank cards or a 500-style broken layout.

  (These three states are switchable live via the pill control at the top
  of `/dashboard` — the default view on load is "Day 12," matching the
  route map above, so the automated screenshot lands on the fully-populated
  state.)

## Local preview

No build step required — just serve the folder statically:

```bash
python3 -m http.server 8000
# then visit:
# http://localhost:8000/
# http://localhost:8000/dashboard/
# http://localhost:8000/day/12/
```

## Deploy

Any static host works as-is. Two options:

**Vercel / Netlify:** drag-and-drop this folder (or connect the GitHub repo)
with no build command and `.` as the output directory.

**GitHub Pages:** push this folder to a repo and enable Pages on the `main`
branch root — the folder-per-route structure already matches what Pages
expects.

## Folder structure

```text
/
├── index.html          → route: /
├── dashboard/
│   └── dashboard.html       → route: /dashboard
├── day/
│   └── 12/
│       └── page.html   → route: /day/12
├── data/
│   └── mock.json         (reference copy of the mock data)
└── src/                  (source partials + assembly script, not required at runtime)
```
