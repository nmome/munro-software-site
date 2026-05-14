# munro-software-site

Single-page credibility site for **Munro Software** at
[munrosoftwarecompany.com](https://munrosoftwarecompany.com).

Static HTML/CSS, no build step. Deployed to Cloudflare Pages on push to `main`.

## Local preview

Open `index.html` in a browser, or:

```sh
python -m http.server 8000
```

then visit `http://localhost:8000`.

## Deploy

Cloudflare Pages is connected to this repo. Pushes to `main` deploy automatically.
Build command: *(none)*. Output directory: `/`.
