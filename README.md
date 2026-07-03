# iee.smmiri.com

سند مرجع فارسی درباره **بورس انرژی ایران (IRENEX)** و **بازار برق**: ساختار بازارها،
تابلوها و نمادها، سلف موازی استاندارد، کشف قیمت، تسویه، کارمزد، مراحل ورود، ریسک‌ها،
مثال عددی و واژه‌نامه.

A single-page, self-contained Persian (RTL) reference on Iran Energy Exchange and its
electricity market. No build step: it is one static `index.html` with inline CSS/JS.

## Files

- `index.html` — the whole document (inline styles + a little JS for theme + active TOC).
- `CNAME` — custom domain `iee.smmiri.com`.
- `robots.txt`, `sitemap.xml`, `.nojekyll` — static hosting helpers.
- `.github/workflows/deploy-pages.yml` — GitHub Pages deploy (copies static files, no build).

## Local preview

This is a single static `index.html` with no build step, so there is nothing to install.
Run the dev server (uses Python's built-in static server, zero dependencies):

```bash
npm run dev
# then visit http://localhost:5173/
```

Or just open `index.html` directly in a browser, or serve the folder any other way:

```bash
python3 -m http.server 8080   # http://localhost:8080/
```

> Note: there is deliberately no bundler here. `npm run dev`, `npm start`, and
> `npm run preview` all just serve the folder over HTTP. If you later want Vite-style
> hot reload to match the sibling repos, ask and it can be swapped in.

## Deploy to iee.smmiri.com

This follows the same pattern as `rentorbuy.smmiri.com` (a separate GitHub Pages repo per
subdomain). Steps:

1. Create a new GitHub repo (for example `smmiri/iee`) and push this folder to `main`.

   ```bash
   git init
   git add .
   git commit -m "Iran Energy Exchange / electricity market reference"
   git branch -M main
   git remote add origin git@github.com:smmiri/iee.git
   git push -u origin main
   ```

2. Repo → **Settings → Pages → Build and deployment → Source: GitHub Actions**.
3. The `CNAME` file already sets the custom domain to `iee.smmiri.com`.
4. **Cloudflare DNS** (zone `smmiri.com`): add `CNAME  iee → smmiri.github.io`
   (DNS only / grey cloud). Do not touch the existing `rentorbuy` record.
5. After the DNS check passes and TLS is issued, enable **Enforce HTTPS**.
6. Optionally add `https://iee.smmiri.com/` to the apex `sitemap.xml` in the
   `smmiri.github.io` repo.

## Content notes

- Every important numeric, legal, or procedural claim is footnoted to a source listed at
  the bottom of the page.
- Fee tables, VAT rate, trading hours, and penalty coefficients change over time. Verify
  against the official sources before acting: `irenex.ir`, `seo.ir`, `igmc.ir`,
  `tavanir.org.ir`. Use `web.archive.org` if a page is unreachable.
- This site is not affiliated with IRENEX, the SEO, or any government body.
