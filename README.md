# indaiatech-site

## Running

one-time setup:
```sh
mise use -g bun@latest
bun install
```

running:
```sh
bun dev
```

## Structure

- `/` — site institucional
- `/ai-assistant` — site do produto AI Assistant (chat)

## Deploy

GitHub Pages via GitHub Actions (`.github/workflows/deploy.yml`), adapter estático,
domínio próprio `indaia.tech` (CNAME). DNS do registrante:

- `A @` → `185.199.108.153` `185.199.109.153` `185.199.110.153` `185.199.111.153`
- `CNAME www` → `indaiatech.github.io.`

## Other resources

to get images:
https://www.pexels.com/search/videos/using%20app/
