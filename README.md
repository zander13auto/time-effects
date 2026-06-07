# time-effects

A small collection of standalone, dependency-free HTML files that turn page scroll into a sense of time passing. Drop one into any project, swap the CSS custom properties to match your brand, and replace the dataset.

**Live gallery:** [zander13auto.github.io/time-effects](https://zander13auto.github.io/time-effects/)

---

## What's in here

| # | Effect | File | Best for |
|---|---|---|---|
| 01 | Vertical Timeline Scroll | [`Vert-timeline-scroll.html`](./Vert-timeline-scroll.html) | Long-form pages where the destination is "the end of the century." |
| 02 | Horizontal Timeline Scroll | [`Horiz-timeline-scroll.html`](./Horiz-timeline-scroll.html) | Hero-video pages and full-bleed layouts where a side rail would compete with content. |
| 03 | Date Magnify Scroll | [`Date-magnify-scroll.html`](./Date-magnify-scroll.html) | Dense chronologies (days of a year, sprint days, life milestones) where each individual date matters. |
| 04 | 52-Week Life Grid | [`52week-grid.html`](./52week-grid.html) | Visualising a life (or any multi-year span) as a grid of weeks with per-week notes and calendar import/export. |

Each file is self-contained — open it directly in a browser, host it on GitHub Pages, or paste it into any HTML page.

---

## 01 — Vertical Timeline Scroll

A fixed rail on the right edge of the viewport. As you scroll the page, a glowing gold dot moves down the rail, decade tick marks light up next to it, and a serif year readout (Y / Y+100) updates in real time. The rail hides on narrow viewports.

**Customisation tokens** (set on `:root`):

```css
--vts-accent : #e8c08c;   /* dot, ticks, year readout */
--vts-serif  : 'Recoleta', 'Cormorant Garamond', serif;
--vts-sans   : 'Inter', 'SF Pro Display', sans-serif;
```

---

## 04 — 52-Week Life Grid

An interactive grid showing every week of a configurable span (default: 100 years). Each cell represents one ISO week. Hover to preview; click to add or view an entry.

### Features

- **Editable span** — change start year and number of years via the meta bar; grid rebuilds instantly.
- **Fit to entries** — click "fit to entries" next to the Span edit button to automatically set the start year and year count to exactly cover the earliest and latest weeks that have entries.
- **Per-week entries** — each cell stores a text note and an optional URL, persisted in `localStorage`.
- **Google Calendar link** — the hover lens and entry modal both link directly to that week's view in Google Calendar.
- **Import** — populate the grid from exported calendar files (see formats below).
- **Export** — download all entries as a CSV file importable back into Google Calendar or Outlook.
- **Reset** — clear all saved entries with a confirmation step.

---

## Calendar import / export formats

### Import formats accepted

The **↑ Import** button accepts two formats:

#### iCalendar (.ics)

The standard cross-platform calendar format defined in [RFC 5545](https://www.rfc-editor.org/rfc/rfc5545).

| Application | How to export |
|---|---|
| **Google Calendar** | Settings → Import & export → Export. Downloads a `.zip` containing one `.ics` per calendar. | 
| **Apple Calendar** | File → Export → Export… Saves a `.ics` file. |
| **Microsoft Outlook** | File → Open & Export → Import/Export → Export to a file → iCalendar Format (.ics). |

Google's export guide: [support.google.com/calendar/answer/37111](https://support.google.com/calendar/answer/37111)

#### CSV (.csv) — Google Calendar / Microsoft Outlook format

A comma-separated file with at minimum a `Subject` column and a `Start Date` column (formatted `MM/DD/YYYY` or `YYYY-MM-DD`).

| Application | How to export |
|---|---|
| **Google Calendar** | Settings → Import & export → Export (choose CSV option if available, otherwise use .ics). |
| **Microsoft Outlook** | File → Open & Export → Import/Export → Export to a file → Comma Separated Values. |

Google CSV format reference: [support.google.com/calendar/answer/37118](https://support.google.com/calendar/answer/37118)  
Microsoft Outlook CSV reference: [support.microsoft.com — Import and export Outlook email, contacts, and calendar](https://support.microsoft.com/en-us/office/import-and-export-outlook-email-contacts-and-calendar-92577192-3881-4502-b79d-c3bbada6c8ef)

**Import behaviour:** events are grouped by ISO week. All event titles for a given week are joined with newlines and merged into that week's entry. Existing entry text is preserved — new titles are appended.

---

### Export format

The **↓ Export** button downloads `life-grid-entries.csv` — a standard Google Calendar–compatible CSV with one all-day event per saved entry spanning the full Monday–Sunday of that ISO week.

It can be imported directly into:
- **Google Calendar** via Settings → Import & export → Import.
- **Microsoft Outlook** via File → Open & Export → Import/Export → Import from another program or file → Comma Separated Values.

---

## Deploying on WordPress

See [WORDPRESS-DEPLOY.md](./WORDPRESS-DEPLOY.md) for three methods: iframe embed from GitHub Pages, self-hosting, and pasting HTML directly into a Custom HTML block.

---

## License

[GPL-3.0](./LICENSE)
