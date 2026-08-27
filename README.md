# A26 Schedule Heatmap

**When are students in class?** A course-density heatmap across undergraduate programs at
Université Laval for the **Fall 2026** (automne 2026 / A26) session, so a club can spot the free
hours to hold an event.

**Live demo:** https://ulyssegagne.github.io/schedule-heatmap/ · **by Ulysse Gagné**

---

## What it does

- **Weekly heatmap** (Mon–Fri × half-hour), monochrome — light = free, dark = busy — with the
  number printed in every cell. The hero of the page.
- **Two measures**
  - **Students** (default) — sum of the section capacities in class at each moment (classes
    assumed full). Big lectures outweigh small seminars.
  - **Classes** — how many class sessions overlap.
- **Core vs All courses** — *Core* is the required common core of the 7 programs; *All courses*
  adds every optional in-discipline elective with a fixed Fall-2026 schedule (any IFT-, GLO-, GIF-,
  GEL-, MAT-, or STT- course), so upper years show a fuller load.
- **Filters** — program, year, and *All classes* vs *In-person only*.
- **Timeline** — the 16 weeks, with reading week and exams marked.
- **Course table** — all 108 courses (core + electives, electives tagged), searchable and sortable.
- **Shareable views** — every control encodes into a short link, e.g. `…/?s=4hAD`.

## Programs

Baccalauréat in **IFT** (informatique), **GLO** (génie logiciel), **GIF** (génie informatique),
**IIG** (informatique et gestion), **STAT** (statistique et science des données), **GEL** (génie
électrique), and **MAT** (mathématiques).

## Data & method

- **Source:** the public **ULaval course catalogue** (`ulaval.ca/etudes/cours`), FSG *cheminement*
  grids, and the official academic calendar 2026–2027.
- Each course page lists its Fall-2026 sections; the tool reads the **day, time, room, delivery mode
  and capacity** of every fixed-time section. Asynchronous (no fixed time) sections are excluded.
- **Students** counts section capacity (seats), assuming classes are full — a comparative weight,
  not a headcount.
- **All courses** is an upper bound: it unions every scheduled elective; no single student takes them all.
- Ships as [`schedule-data.js`](schedule-data.js) (`window.SCHEDULE_DATA`) — a plain public data
  file, so `index.html` also works when opened directly (`file://`).

## Sharing a view

Change any control and the URL updates to a short opaque token. **Share** copies a link that restores
the exact view (programs, years, measure, course set, all/in-person). Works on GitHub Pages and locally.

## Running locally

No build, no server — download and **double-click `index.html`**.

## Disclaimer

Unofficial student tool, **not affiliated with or endorsed by Université Laval**. Built for the Club
d'intelligence artificielle (Université Laval). Schedules subject to change; verify critical dates.

## License

[MIT](LICENSE) © 2026 Ulysse Gagné.

---

## Deploying to GitHub Pages (manual)

**1.** Create an **empty** repo `schedule-heatmap` on github.com (no README/license).

**2.** In a terminal:

```bash
cd ~/Desktop/claude/schedule-heatmap
git init
git add .
git commit -m "A26 Schedule Heatmap — course-density tool (Fall 2026)"
git branch -M main
git remote add origin https://github.com/ulysseGagne/schedule-heatmap.git
git push -u origin main
```

**3.** Enable Pages: **Settings → Pages → Source: “Deploy from a branch” → Branch: `main` /
`/ (root)` → Save.** Live in ~1 min at **https://ulyssegagne.github.io/schedule-heatmap/**.
