# munro-software-site

The site for **Munro Software Company LLC** at
[munrosoftwarecompany.com](https://munrosoftwarecompany.com).

- `index.html`: the business homepage (services, payment, refunds, terms,
  contact). Stripe verifies the business against this page, so the LLC name
  and what we sell must stay on it.
- `lead-follow-up/index.html`: the lead follow-up service page, served at
  `https://munrosoftwarecompany.com/lead-follow-up/`. Copy comes from the
  brain note `projects/money/site-copy.md`. It names no price: the quote is
  sized on the call. Showing "From $650" there is Nathan's call. Refund and
  terms wording is not repeated, the page links to the homepage for it.
- `templates/index.html`: the Lead Catch template page, served at
  `https://munrosoftwarecompany.com/templates/`. Copy comes from the brain
  notes `projects/money/template-listing.md` and `paid-template.md`. No price
  or buy link until the Gumroad listing is live: a comment marks the spot.
- `journey/index.html`: the journey page at `/journey/`, the only place the
  inward work (Jarvis, trading, clipping) appears. Published with Nathan's
  approved wording (2026-10-26), indexed, and linked from the homepage
  footer. Any wording change waits for him. No balances, P&L, net worth,
  personal life or day job on it.
- `404.html`: the branded not-found page. Cloudflare Pages serves it for
  any unknown path. It links the homepage, the three product pages and the
  homepage contact section. Uses `styles.css` as is.
- `sitemap.xml`: lists `/`, `/lead-follow-up/`, `/templates/`,
  `/fitnessai/` and `/journey/` for search engines. There is no `robots.txt` here because Cloudflare
  serves a managed one.
- `fitnessai/index.html`: the FitnessAI support and privacy page, for the
  App Store Connect URL fields:

| App Store Connect field | URL |
| --- | --- |
| Marketing URL (optional) | `https://munrosoftwarecompany.com/fitnessai/` |
| Support URL (required) | `https://munrosoftwarecompany.com/fitnessai/#support` |
| Privacy Policy URL (required) | `https://munrosoftwarecompany.com/fitnessai/#privacy` |

The old `/#support` and `/#privacy` links still work: a script on the
homepage forwards them to `/fitnessai/`.

Static HTML/CSS, no build step. Deployed to Cloudflare Pages on push to `main`.

## What the page currently claims

The copy is written against this architecture. If any of it changes, the page
has to change with it.

| Item | Provider | Notes |
| --- | --- | --- |
| AI inference | On-device, Apple Foundation Models | No cloud model. Coaching content never transmitted. |
| Hosting / backend | Cloud Firestore | Account backup and restore; trainer sharing only when the user links one. |
| Auth | Firebase Authentication | Email/password or Sign in with Apple. |
| Analytics | TelemetryDeck (opt-in), Apple MetricKit | No personal identifiers; diagnostics only. |
| Food lookups | USDA FoodData Central, Open Food Facts | Search text and barcodes only; no personal or health data. |

The page states a device floor of **iPhone 15 Pro or later**, which follows from
using Apple Intelligence rather than a bundled model. If the stack moves back to
MLX + Llama 3.2 3B, the floor returns to A15, and the page needs updating along
with the "Built with Llama" attribution and a `NOTICE.txt`.

## Still to do before submission

- **Account deletion must exist in-app** at `Settings > Account > Delete Account`.
  Apple guideline 5.1.1(v) requires it, the FAQ documents that exact path, and
  CCPA/GDPR deletion rights are real now that accounts exist. Local wipe is not
  enough.
- **Trainer unlink must exist** at `Settings > Trainer > Unlink`, as the FAQ says.
- **HealthKit consent screen.** Health-derived data reaching Firestore needs
  explicit consent, separate from the HealthKit permission itself, with a stated
  health-management purpose (App Review 5.1.3). It must not go to iCloud.
- **Confirm the FitnessAI name is available** in App Store Connect. There may be
  an existing iOS app using it.
- **Cloudflare bot protection** was turned off on 2026-10-22, because its
  challenge blocked Stripe's website check. Keep it off, or Stripe and Apple
  review cannot fetch the site.

## Local preview

Open `index.html` in a browser, or:

```sh
python -m http.server 8000
```

then visit `http://localhost:8000`.

## Deploy

Cloudflare Pages is connected to this repo. Pushes to `main` deploy
automatically. Build command: *(none)*. Output directory: `/`.
