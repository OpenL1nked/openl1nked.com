# openl1nked.com

The official marketing site for [OpenL1nked](https://github.com/OpenL1nked) — an open-source,
cross-platform bridge between your desktop and mobile devices.

**Live at:** [openl1nked.site](https://openl1nked.site)

## About

This is a static, dependency-free landing page introducing the OpenL1nked project: its mission,
planned feature set, technology stack, and roadmap, along with links to the organization's
repositories and ways to get involved as a contributor.

The visual design mirrors the glassmorphic, dark-themed UI of the
[desktop client](https://github.com/OpenL1nked/openl1nked-Windows) so the site and the product
feel like one brand.

## Structure

```
.
├── index.html      Single-page site markup
├── css/style.css   Styles (dark theme, responsive, no build step)
├── js/script.js    Small progressive-enhancement script (mobile nav toggle)
├── _headers        Cloudflare Pages response headers (security + caching)
└── wrangler.toml   Cloudflare Pages project config
```

## Local development

No build tooling is required. Serve the directory with any static file server, for example:

```bash
python3 -m http.server 8080
# or
npx serve .
```

Then open `http://localhost:8080`.

## Deployment

The site is a pure static bundle (no build step) deployed on **Cloudflare Pages**, project
`openl1nked-com`. The project is connected to this repository's Git integration and redeploys
automatically on every push to `main`, running `npx wrangler pages deploy` per its configured
build settings; `pages_build_output_dir = "."` in [`wrangler.toml`](wrangler.toml) tells it to
serve the repository root as-is (no build step).

The `openl1nked.site` custom domain is attached from the Cloudflare dashboard under the
`openl1nked-com` Pages project's **Custom domains** settings, not through `wrangler.toml` (Pages
custom domains aren't configured via the `routes`/`custom_domain` keys — those are Workers-only).

[`_headers`](_headers) sets security headers (CSP, frame protections) and edge/browser caching for
static assets — Cloudflare Pages reads this file automatically at deploy time, no extra config
needed.

## Contributing

Issues and pull requests are welcome — typo fixes, content updates, accessibility and performance
improvements, and design refinements all help. For contributing to OpenL1nked itself (the desktop
app, mobile app, and protocol work), see the
[organization profile](https://github.com/OpenL1nked/.github).

## License

MIT — see [scrcpy-wrapper/LICENSE](https://github.com/OpenL1nked/scrcpy-wrapper/blob/main/LICENSE)
for the license OpenL1nked projects are published under.
