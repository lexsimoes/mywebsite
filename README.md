# lexsimoes.dev

Source of my personal site — **[lexsimoes.dev](https://lexsimoes.dev)**.

It's a portfolio for the AI systems I build: autonomous editorial pipelines, multi-tenant
agent platforms and document generators, presented as case studies with the engineering
decisions behind each one.

## How it's built

One file. `index.html` is the entire site — markup, CSS, JavaScript and images. No build
step, no framework, no dependencies to install. Open it in a browser and it runs.

The only external request is the Google Fonts stylesheet (Jost + JetBrains Mono).
Both photographs are embedded as base64 data URIs, so the page has no image requests
and no broken-asset risk. Total weight is about 130 KB.

### Design system

Colours come from the palette the previous version of this site used — orange `#FF621A`,
amber, mint, peach, periwinkle, sage, lavender — reorganised into Material 3 Expressive
roles and exposed as CSS custom properties. Everything derives from those tokens, so light
and dark themes are the same rules with a different token block.

A few decisions worth knowing before editing:

- **Two oranges.** `--brand` (`#FF621A`) is for large display type and graphics only; it
  fails WCAG AA at body size. `--accent` (`#C93E00`) is for text and filled controls.
- **Hairlines carry the structure.** Stats, principles, stack, experience and education are
  rule-separated rows. The seven case studies are the only cards on the page — that's what
  makes them read as the primary content.
- **Motion is spring-based**, via a `linear()` easing token, matching Material 3 Expressive.
  Shapes morph on hover rather than merely lifting. All of it collapses under
  `prefers-reduced-motion`.
- **Type has two voices.** Jost for everything human; JetBrains Mono for anything that is a
  machine record — metrics, dates, statuses, identifiers.

### The hero figure

The canvas on the right of the hero draws a dense field of unfiltered observations, a gate,
and the few marks that make it through — the thesis of
[noiseOff.today](https://noiseoff.vercel.app) rendered as an ambient graphic. It reads its
colours from the CSS tokens at draw time, so it repaints correctly when the theme changes,
and it renders a static composition when reduced motion is requested.

### Accessibility

Semantic landmarks, visible focus states, `<details>`/`<summary>` for the case-study
accordion so it works without JavaScript, AA contrast on body text, and content that is
never trapped behind a scroll observer — the reveal animation only applies once JavaScript
has confirmed it can undo itself.

## Editing

```
# there is no toolchain — just open it
open index.html
```

Commit to `main` and GitHub Pages redeploys within a minute.

## Deployment

| | |
|---|---|
| Host | GitHub Pages, `main` branch, root |
| Domain | `lexsimoes.dev`, set by the `CNAME` file |
| Registrar | Squarespace Domains (formerly Google Domains) |
| DNS | Google Cloud DNS |
| Redirect | `lexsimoes.com` → `lexsimoes.dev` (301, at the registrar) |

## Legacy files

`contact.html`, `portfolio.html`, `service.html` and `assets/` are from the 2022 version of
this site. They are still served at their old paths and still describe me as a full-stack
developer. They should be deleted once nothing links to them.

## Licence

The code is free to learn from. The photographs, written content and CV details are mine.
