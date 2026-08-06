# Ginevra Cerri — resume site

A single-page resume site. Static HTML and CSS, no build step and no dependencies.

```
index.html    the page
styles.css    all styling
uploads/      the downloadable CV (see below)
```

## Running it

Open `index.html` directly, or serve it:

```sh
python3 -m http.server 8000
# → http://localhost:8000
```

Use a server rather than `file://` if you want the YouTube embed in the hero to
play — YouTube rejects embeds from `file://` origins with "Error 153".

## Deploying

Any static host works — GitHub Pages, Netlify, Cloudflare Pages, S3. There is
nothing to compile; publish the directory as-is.

## The CV download

The **Download CV** button links to `uploads/CerriG_Resume.pdf`, which is **not
in this repo yet** — the file has to be added by hand. Until it is, that button
404s.

To change which file it points at, edit the one link in `index.html`:

```html
<a class="btn btn--cv" href="uploads/CerriG_Resume.pdf" download="Ginevra-Cerri-CV.pdf">
```

## Origin

Implemented from the `Resume Site.dc.html` design in the "Ginevra Cerri resume
redesign" Claude Design project. Two deliberate departures from that source:

- **Hover states are real.** The design expressed them as `style-hover`
  attributes, which its runtime (`support.js`) never implemented — they are CSS
  `:hover` rules here.
- **The page is responsive.** The design is desktop-only with no breakpoints.
  Rendering above 1024px is unchanged; below that, breakpoints at 1024/820/560px
  collapse the multi-column grids. A `prefers-reduced-motion` block disables the
  CV button's pulsing glow and smooth scrolling.

Design tokens (colour, type, spacing) are CSS custom properties at the top of
`styles.css`, carried over verbatim from the source.
