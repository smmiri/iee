# بورس انرژی ایران و بازار برق · Iran Energy Exchange (IRENEX) reference

یک سند مرجع فارسی و راست‌به‌چپ درباره **بورس انرژی ایران (IRENEX)** با تمرکز ویژه بر **بازار برق**:
ساختار بازارها، تابلوها و نمادها، سلف موازی استاندارد، کشف قیمت، تسویه، کارمزد، مراحل ورود
فروشنده و خریدار، ریسک‌ها، یک مثال عددی و واژه‌نامه.

A single-page, self-contained Persian (RTL) reference on the Iran Energy Exchange and its
electricity market. It is one static `index.html` with inline CSS/JS: no build step and no
runtime dependencies.

**Live site:** https://iee.smmiri.com

## محتوا · What's inside

The document is organized into eleven sections with a sticky table of contents:

1. What IRENEX is: definition, purpose, legal status, and how it differs from the wholesale
   (grid-operated) electricity market and bilateral contracts.
2. Other electricity market mechanisms in Iran: the wholesale/balancing market (IGMC), bilateral
   contracts, renewables guaranteed purchase (SATBA), regulated retail tariffs (Tavanir/MoE),
   cross-border trade, and the mandatory-purchase / self-supply layer, each with a comparable
   schema (operator, pricing, settlement, participants, entry, data availability).
3. Overall market structure: physical, derivatives, secondary, and other-securities markets
   (non-electricity boards condensed).
4. Deep dive on the electricity market: normal vs green boards, load types (base / peak /
   mid-peak / off-peak), delivery periods, symbols, contract length, standard parallel salaf,
   price discovery, symbol open/close rules, trading hours, and roles.
5. Prerequisites and onboarding for sellers (power plants) and buyers, plus choosing a broker.
6. A step-by-step walkthrough of one trade, from trading code to physical delivery.
7. Settlement, guarantees, fees, taxes, and default penalties.
8. Risks and special electricity-market regulations.
9. A worked numerical example.
10. Glossary (Persian and English).
11. Sources.

## ویژگی‌ها · Tech

- Single static `index.html`, no bundler, works offline (the only external request is the
  Vazirmatn web font, which degrades gracefully to a system font stack).
- Light/dark theme with saved preference, print/PDF button, and scroll-synced table of contents.
- Every important numeric, legal, or procedural claim is footnoted to a numbered source.

## پیش‌نمایش محلی · Local preview

No install needed. The npm scripts just serve the folder over HTTP using Python's built-in
static server:

```bash
npm run dev
# then open http://localhost:5173/
```

You can also open `index.html` directly, or serve the folder any other way:

```bash
python3 -m http.server 8080   # http://localhost:8080/
```

> There is deliberately no bundler. `npm run dev`, `npm start`, and `npm run preview` all
> serve the same static files.

## استقرار · Deploy (GitHub Pages + custom subdomain)

The site ships with a `CNAME` and a GitHub Actions workflow
(`.github/workflows/deploy-pages.yml`) that publishes the static files to GitHub Pages.

1. Push this folder to a GitHub repo (for example `smmiri/iee`):

   ```bash
   git init
   git add .
   git commit -m "Iran Energy Exchange and electricity market reference"
   git branch -M main
   git remote add origin git@github.com:smmiri/iee.git
   git push -u origin main
   ```

2. In the repo, go to **Settings → Pages → Build and deployment** and set **Source: GitHub
   Actions**. The workflow runs on every push to `main`.
3. The `CNAME` file already points the site at `iee.smmiri.com`.
4. In your DNS provider, add a `CNAME` record: `iee` → `smmiri.github.io` (DNS only, no proxy).
   Leave any existing records intact.
5. Once the Pages domain check passes and TLS is issued, enable **Enforce HTTPS**.

## منابع و صحت · Sources and accuracy

- Claims are footnoted to reliable sources that themselves cite official directives from the
  Ministry of Energy, the Securities and Exchange Organization, and the Iran Grid Management
  Company.
- Fee tables, the VAT rate, trading hours, market price caps, feed-in and retail tariffs, and
  penalty coefficients change over time. Verify against the official sources before acting on
  anything: `irenex.ir`, `seo.ir`, `igmc.ir`, `tavanir.org.ir`, `satba.gov.ir`, and `moe.gov.ir`.
  Use `web.archive.org` if a page is unreachable.
- Corrections are welcome. If you find an outdated number or a better primary source, please
  open an issue or a pull request with a link.

## سلب مسئولیت · Disclaimer

This is an educational reference, not investment, legal, or tax advice. It is not affiliated
with IRENEX, the Securities and Exchange Organization, or any government body.

## License

MIT. See [`LICENSE`](./LICENSE).
