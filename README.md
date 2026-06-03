# time-effects

Two drop-in scroll-driven timeline effects, built to evoke a **century of progress**. Originally designed for the WordPress.com 100-Year Plan and 100-Year Domain landing pages.

Both effects:

- Are **self-contained** single HTML files — paste the `<style>` + markup + `<script>` into any page.
- Use the visitor's **current year** as the starting point (`new Date().getFullYear()`) and span 100 years forward, automatically.
- Are **position: fixed** and appended/placed outside any transformed/overflow ancestor so they survive aggressive theme CSS (tested inside WordPress block themes).
- Have **no dependencies** — vanilla JS, no build step, no fonts required (Recoleta is preferred but falls back gracefully).

---

## 🌿 Vert-timeline-scroll

A vertical century rail pinned to the **right edge** of the viewport. A glowing accent dot and a serif year readout (`YEAR / 47 / OF 2126`) slide down the rail as the visitor scrolls. Decade ticks are labelled with absolute years. Hides itself below 1200px viewport width.

**Best for:** long editorial pages where the rail acts as a quiet "you are here in the century" indicator next to the main content.

📄 [`Vert-timeline-scroll.html`](./Vert-timeline-scroll.html)

---

## ➖ Horiz-timeline-scroll

A horizontal glass bar pinned to the **bottom** of the viewport. A centered serif year readout updates with scroll; a glowing dot and progress underline slide left → right across decade ticks labelled with absolute years.

**Best for:** product / marketing pages where the rail acts as a persistent status bar across all content sections.

📄 [`Horiz-timeline-scroll.html`](./Horiz-timeline-scroll.html)

---

## 📦 How to use

1. Open the effect's HTML file and copy:
   - The `<style id="vts-styles">` (or `hts-styles`) block — paste into `<head>`.
   - For the horizontal effect: the `<div class="hts-rail">…</div>` markup — paste just before `</body>`.
   - The `<script>` block — paste before `</body>`.
2. Make sure the page is **tall enough to scroll** (otherwise the dot stays at 0%).
3. That's it. The rail reads the current year on load and animates against `window.scrollY`.

### Customising the look

Both effects expose CSS custom properties at `:root`:

| Token            | Default                          | What it controls            |
|------------------|----------------------------------|-----------------------------|
| `--vts-accent` / `--hts-accent` | `#e8c08c` (warm gold) | Dot, ticks, readout colour |
| `--vts-serif` / `--hts-serif`   | `Recoleta, …, serif`  | Year readout typeface       |
| `--vts-sans` / `--hts-sans`     | `Inter, …, sans-serif`| Label typeface              |
| `--hts-bg-tint`                 | `10, 13, 15` (RGB triple) | Bottom-bar glass colour |

Override them in your own stylesheet:

```css
:root {
  --hts-accent: #3858E9;          /* swap warm gold for WP blue */
  --hts-serif: 'Playfair Display', serif;
}
