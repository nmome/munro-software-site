# munro-software-site

Single-page marketing, support, and privacy site for **FitnessAI** at
[munrosoftwarecompany.com](https://munrosoftwarecompany.com), built by Munro
Software.

This page exists to satisfy the App Store Connect URL fields:

| App Store Connect field | URL |
| --- | --- |
| Marketing URL (optional) | `https://munrosoftwarecompany.com` |
| Support URL (required) | `https://munrosoftwarecompany.com/#support` |
| Privacy Policy URL (required) | `https://munrosoftwarecompany.com/#privacy` |

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
- **Cloudflare bot protection** currently challenges automated clients on this
  zone (`Cf-Mitigated: challenge`). Fine for humans; consider allowlisting in
  case Apple's review tooling fetches the Support URL.

## Local preview

Open `index.html` in a browser, or:

```sh
python -m http.server 8000
```

then visit `http://localhost:8000`.

## Deploy

Cloudflare Pages is connected to this repo. Pushes to `main` deploy
automatically. Build command: *(none)*. Output directory: `/`.
