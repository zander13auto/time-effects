# Deploying Time Effects on WordPress

Each effect in this repository is a **single, self-contained HTML file** with no external dependencies — no libraries, no CDN calls, no build step. Three methods work reliably in WordPress.

---

## Method 1 — iframe from GitHub Pages *(recommended)*

GitHub Pages hosts this repository at:

```
https://zander13auto.github.io/time-effects/
```

In the WordPress block editor, add a **Custom HTML** block and paste:

```html
<!-- wp:html -->
<iframe
  src="https://zander13auto.github.io/time-effects/52week-grid.html"
  width="100%"
  height="900"
  style="border:none;display:block;"
  loading="lazy"
  title="52-Week Life Grid">
</iframe>
<!-- /wp:html -->
```

Swap the `src` for any other effect filename. Adjust `height` to taste.

**Pros:** Zero server setup; any update pushed to this repo appears automatically on your WordPress page.  
**Cons:** Requires the visitor's browser to reach GitHub Pages (almost always true on public sites).

---

## Method 2 — Self-host the file

1. Download the `.html` file from this repository.
2. Upload it to your server via SFTP, cPanel File Manager, or into `/wp-content/uploads/`.
3. Embed it with an `<iframe>` as above, using your own domain as `src`.

**Pros:** No third-party dependency; fully under your control.  
**Cons:** You must re-upload the file manually after each update.

---

## Method 3 — Paste HTML directly into a Custom HTML block

This embeds the effect as part of the page DOM rather than inside a frame.

1. Open the `.html` file in any text editor.
2. Copy the entire `<style>…</style>` block and paste it into **Appearance → Customize → Additional CSS** (or a plugin such as *Simple Custom CSS*).
3. Copy everything between (but not including) the `<body>` and `</body>` tags.
4. In the WordPress block editor, add a **Custom HTML** block and paste, wrapped exactly like this:

```html
<!-- wp:html -->
[paste content here]
<!-- /wp:html -->
```

> **Critical:** Always use the `<!-- wp:html -->` wrapper. Without it, WordPress's `wpautop` filter injects `<br>` and `<p>` tags inside `<script>` blocks and breaks the JavaScript.  
> Never paste into a Classic paragraph block.

**Pros:** Content is part of the page DOM; no iframe boundary.  
**Cons:** Most setup work; CSS must be managed separately; must re-paste on updates.

---

## Notes

- Each effect uses its own namespaced CSS custom properties (`--ac`, `--bg`, `--sf`, etc.) so multiple effects can coexist on the same page without collisions.
- The files contain **no tracking, no analytics, and no outbound requests** beyond links the user explicitly clicks.
- `localStorage` is used only in `52week-grid.html`, stored entirely in the visitor's own browser.
- For WordPress multisite or sites with a strict Content Security Policy, Method 1 (iframe) is the most reliable since the effect runs in its own browsing context.
