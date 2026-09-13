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
├── _headers        Cloudflare response headers (security + caching)
└── wrangler.toml   Cloudflare Workers Builds project config
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

The site is a pure static bundle (no build step) deployed as a Cloudflare Worker with static
assets, project/Worker `openl1nked-com`. It's connected to this repository via Workers Builds
(Git integration) and redeploys automatically on every push to `main`; `[assets] directory = "."`
in [`wrangler.toml`](wrangler.toml) tells the build to serve the repository root as-is.

The `openl1nked.site` custom domain is attached from the Cloudflare dashboard under the
`openl1nked-com` Worker's **Settings → Domains & Routes**.

[`_headers`](_headers) sets security headers (CSP, frame protections) and edge/browser caching for
static assets — Workers static assets reads this file automatically at deploy time, using the
same format as Pages.

## Contributing

Issues and pull requests are welcome — typo fixes, content updates, accessibility and performance
improvements, and design refinements all help. For contributing to OpenL1nked itself (the desktop
app, mobile app, and protocol work), see the
[organization profile](https://github.com/OpenL1nked/.github).

## License

MIT — see [scrcpy-wrapper/LICENSE](https://github.com/OpenL1nked/scrcpy-wrapper/blob/main/LICENSE)
for the license OpenL1nked projects are published under.
