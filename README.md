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

Each file is self-contained — open it directly in a browser, host it on GitHub Pages, or paste it into any HTML page.

---

## 01 — Vertical Timeline Scroll

A fixed rail on the right edge of the viewport. As you scroll the page, a glowing gold dot moves down the rail, decade tick marks light up next to it, and a serif year readout (Y / Y+100) updates in real time. The rail hides on narrow viewports.

**Customisation tokens** (set on `:root`):

```css
--vts-accent : #e8c08c;   /* dot, ticks, year readout */
--vts-serif  : 'Recoleta', 'Cormorant Garamond', serif;
--vts-sans   : 'Inter', 'SF Pro Display', sans-serif;
