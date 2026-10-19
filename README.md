# WarLens

A bilingual English/Japanese Last War community intelligence website. Unofficial fan project.

## Run locally

```bash
npm install
npm run dev
```

Demo mode uses fictional player and alliance data. Switch between English and Japanese from the top-right language button.

## GitHub Pages

Open repository **Settings → Pages** and select **GitHub Actions** as the build source. Pushes to main invoke the deployment workflow. Once configured, the expected URL is https://notmuchapoet.github.io/lastwar/ .

## Real API integration

Frontend secrets are never secure. Deploy the separate Cloudflare Worker under `worker/` with Wrangler; set `LASTWAR_API_KEY` and `ALLOWED_ORIGIN=https://notmuchapoet.github.io` as Worker secrets. Then configure repository Actions variable `VITE_API_BASE_URL` with the Worker URL. The Worker is a starter proxy, not a production rate limiting solution. Configure Cloudflare WAF/rate limits before public use. **Live player search is intentionally unavailable** until upstream query parameters have been verified. Validate upstream response schemas before public launch.

Do not put the key in `VITE_` variables. No game-session credentials are required for mock mode.
