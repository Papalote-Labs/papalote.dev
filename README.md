# papalote.dev

Coming soon page for [Papalote Labs](https://papalote.dev).

## Development

Serve the `public/` directory locally, e.g.:

```bash
python3 -m http.server -d public 8787
# then open http://127.0.0.1:8787/
```

Or just open `public/index.html` directly in a browser.

## Deployment

Deployed via **Cloudflare Pages** (project `papalote-dev`), auto-deploying on push
to `main`. No build step — Pages serves the site straight from the output directory.

**Build output directory: `public`**, set via `pages_build_output_dir` in
`wrangler.toml` (the source of truth for the git-connected project — it overrides
the dashboard build settings). Only the contents of `public/` are published, which
keeps `.git`, `.github`, `wrangler.toml`, and other repo files off the live site.

Caching is controlled by `public/_headers`, which forces revalidation
(`Cache-Control: public, max-age=0, must-revalidate`) so redeploys are visible
immediately instead of being masked by a stale cache. For this to be honored, the
zone's **Browser Cache TTL** (Caching → Configuration) must be set to
**"Respect Existing Headers"**.

## Structure

```
papalote.dev/
├── public/                      # ← Pages build output directory (published)
│   ├── index.html               # Coming soon page
│   ├── wick-and-wax-privacy.html
│   ├── _headers                 # Cloudflare Pages cache headers
│   ├── assets/
│   │   ├── papalote-kite.svg            # Kite brand mark (color, transparent)
│   │   ├── papalote-kite-node.svg       # Dark-background variant
│   │   ├── papalote-kite-mono.svg       # Single-color variant
│   │   ├── papalote-kite-currentcolor.svg  # Inherits text color
│   │   ├── papalote-icon.svg            # App-icon / favicon
│   │   └── papalote-icon.png            # PNG favicon fallback
│   └── styles/
│       └── main.css
├── wrangler.toml                # Pages build config (pages_build_output_dir)
└── README.md
```

## Brand

- **Iron Slate** `#2F3E46` — ground / wordmark
- **Solar Tangerine** `#FF8C42` — kite body, spark / action
- **Electric Violet** `#7067CF` — "Labs" wordmark, kite tail (logic layer)
- **Violet Glow** `#8E86E6` — dark-mode tail
- Wordmark set in **Poppins SemiBold**
