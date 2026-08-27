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

## Before submitting to Apple

Fill in every `[BRACKETED]` placeholder in `index.html`:

- The hero headline and lede
- The three feature bullets
- `[hosting and authentication provider]` and `[analytics and crash reporting provider]`
  in the privacy policy
- The **AI features** paragraph in the privacy policy: say whether inference runs
  on device or through a third-party model provider, and name the provider if so

If any user data is sent to a model provider, the "We do not share Apple Health
data with third parties" bullet has to be narrowed to match. Do not ship those
two claims in contradiction.

Also confirm the privacy policy matches what the app actually does. It currently
claims: email/password accounts, Apple Health read and write with explicit
permission, anonymized analytics and crash reporting, no data sales, no health
data shared with third parties, and account deletion within 30 days.

The support FAQ describes an in-app **Settings > Account > Delete Account** path.
Apple requires an in-app account deletion path (guideline 5.1.1(v)), so that
screen needs to exist and match the wording.

The brand color is one CSS variable: `--accent` / `--accent-strong` in
`styles.css`.

## Local preview

Open `index.html` in a browser, or:

```sh
python -m http.server 8000
```

then visit `http://localhost:8000`.

## Deploy

Cloudflare Pages is connected to this repo. Pushes to `main` deploy
automatically. Build command: *(none)*. Output directory: `/`.
