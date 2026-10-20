# 🌐 Błażej Stanisz — Personal Homepage

> **🌐 Live site:** <https://blazej-stanisz.github.io/>
>
> **▶️ Google Play:** <https://play.google.com/store/apps/developer?id=B%C5%82a%C5%BCej+Stanisz> — all my Android apps

The personal homepage of **Błażej Stanisz**, served by **GitHub Pages** from the root of this repository.
It's a single static page — one `index.html`, no build step, no dependencies, no backend.

## What's on the page

| Section | Anchor | Content |
|---|---|---|
| Nav | — | Sticky pill navigation: monogram, section links, GitHub button |
| Hero | `#top` | Headline claim, two actions, and a "Live apps" panel |
| Selected work | `#work` | The three public apps, each with a description, tags and **Live** / **Source** links |
| Explore | `#explore` | "What you'll find here" — four items as an accordion |
| About | `#about` | Statement paragraph |
| Get in touch | `#contact` | Inverted (light) call-to-action card |
| Footer | — | Copyright, links, hosting note |

Project entries link to real, live apps, so the section stays honest as long as those apps stay up:

- [3000 Words](https://blazej-stanisz.github.io/3000words/) — English vocabulary trainer ([repo](https://github.com/blazej-stanisz/3000words))
- [PSM I — Practice Tests](https://blazej-stanisz.github.io/PSM-I-Practice-Tests/) ([repo](https://github.com/blazej-stanisz/PSM-I-Practice-Tests))
- [AZ-900 — Practice Tests](https://blazej-stanisz.github.io/AZ-900-Practice-Tests/) ([repo](https://github.com/blazej-stanisz/AZ-900-Practice-Tests))

## Design

The visual language is dark, minimal and typographic, borrowed in spirit from [cleanmeter.app](https://www.cleanmeter.app/):
a near-black canvas, generous whitespace, hairline dividers, oversized headings with tight tracking, and pill-shaped
controls.

- **Type:** Inter (300–700) from Google Fonts, falling back to the system UI stack
- **Tokens:** all in `:root` at the top of the `<style>` block — ink `#f4f5f7`, muted `#9aa0ab`, accent `#38bdf8`,
  background `#0c111d`, surface `#161b26`, hairlines `rgba(255,255,255,.085)`, pill radius `50px`
- **Backdrop:** one soft accent glow plus a faint fading grid, both in the `.bg` layer
- **Motion:** scroll-reveal (`IntersectionObserver`) and the accordion; everything is disabled under
  `prefers-reduced-motion`
- **JS-off safe:** the reveal animation only hides content when the `js` class is present on `<html>`, so the page
  renders fully without JavaScript

## Editing

Everything lives in `index.html`:

- copy — plain HTML in the `main` block
- colours, spacing and radii — the `:root` custom properties
- reveal timing — the `--d` inline custom property on each `[data-reveal]` element (ms)
- links — hero panel, project rows, CTA and footer each carry their own `href`s

## Local preview

Open `index.html` in a browser, or serve the folder:

```bash
python -m http.server 8000
```

## Deploying

Push to `main`. GitHub Pages publishes the repository root, so `index.html` is live within a minute.
`app-ads.txt` also lives at the root and must stay there — it is read by ad networks, not by the page itself.
