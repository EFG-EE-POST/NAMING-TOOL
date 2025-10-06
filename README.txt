# EFG NA File Naming Tool — Static Site

This folder contains:
- `index.html` — the tool (fetches `efg-config.json`)
- `efg-config.json` — the dropdown lists (edit this to update options)

## Free + secure hosting options

### Option A — GitHub Pages (free, HTTPS, public)
1. Create a new repo, commit these two files.
2. In repo Settings > Pages, set Source to `main` and `/root`.
3. Your site will be served over HTTPS at `https://<org or user>.github.io/<repo>/`.
4. Edit `efg-config.json` in GitHub to update lists; clients see updates on reload.

Pros: free, fast CDN, no account sign-in needed.
Cons: config is publicly readable.

### Option B — Cloudflare Pages + Access (free, HTTPS, gated)
1. Import the repo into Cloudflare Pages.
2. Enable **Cloudflare Access** for the Pages domain and restrict to specific emails or your domain.
3. Update users are gated by SSO; JSON is not public to the world.

Pros: free tier, HTTPS, simple SSO gate to protect the config.
Cons: requires Cloudflare setup.

### Option C — Netlify (free, HTTPS, public) with password
1. Drag this folder to https://app.netlify.com/drop (Netlify Drop) or connect a repo.
2. Set a site-wide password in Site Settings > Identity > Netlify Access (or use Netlify Identity).
3. Update is just pushing a new `efg-config.json`.

Pros: free, quick deploys.
Cons: password is shared; not as strong as SSO.

### Using the config URL
If you split hosting (e.g., host HTML on Pages and JSON in a different repo), set in `index.html`:
```js
const CONFIG_URL = "https://<your-domain>/efg-config.json";
```

### CORS
GitHub Pages, Cloudflare Pages, and Netlify all send permissive CORS for static JSON, so `fetch()` will work from any HTTPS origin by default.

### Cache
The HTML app appends a `?t=<timestamp>` to the fetch to bypass caches so changes show immediately.
