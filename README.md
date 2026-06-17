# AI News Short Factory — TikTok Review Site

Static website package for TikTok Developer Platform app review.

## Files

| File | Purpose |
|---|---|
| `index.html` | Homepage — tool overview, workflow, "no auto-publish" callout |
| `privacy.html` | Privacy Policy — data collected, TikTok tokens, no data sale, deletion instructions |
| `terms.html` | Terms of Service — authorized use, no auto-publish, no spam, creator responsibility |
| `oauth-callback.html` | OAuth redirect target — shows success/error state after TikTok authorization |

## Messaging summary

- AI News Short Factory is a **creator workflow tool**, not a bot.
- It **uploads completed videos as private drafts** using TikTok's Content Posting API.
- The creator **manually reviews and publishes** inside TikTok.
- It **never auto-publishes** to a public audience.
- It **never schedules** public posts.
- It **never changes** video visibility to public.
- It **does not sell** user data.
- All data (tokens, pipeline outputs) is stored **locally on the creator's machine**.

## Deployment recommendation — GitHub Pages

GitHub Pages is the right choice for this review site:

- Free, HTTPS by default (TikTok requires HTTPS for redirect URIs).
- Custom domain support (`yourdomain.com`) if needed for brand consistency.
- No server to maintain — purely static, no attack surface.
- Easy to update via git push.

### Steps to deploy

1. Create a new public GitHub repo (e.g., `ai-news-short-factory-site`).
2. Copy this directory's files into the repo root (or a `docs/` subfolder).
3. In repo Settings → Pages → Source, select `main` branch / `root` (or `/docs`).
4. GitHub assigns a URL: `https://<username>.github.io/ai-news-short-factory-site/`
5. Optionally add a custom domain under Settings → Pages → Custom domain.

### TikTok app configuration

Once deployed, use these URLs in your TikTok Developer app:

| Field | Value |
|---|---|
| **Website URL** | `https://<your-pages-url>/` |
| **Privacy Policy URL** | `https://<your-pages-url>/privacy.html` |
| **Terms of Service URL** | `https://<your-pages-url>/terms.html` |
| **Redirect URI** | `https://<your-pages-url>/oauth-callback.html` (for review) |

> **Note:** The production redirect URI should point to `http://localhost:8080/oauth/callback`
> (the local auth server). The hosted `oauth-callback.html` serves as the registered
> HTTPS URI that TikTok requires for review; the local server handles actual token exchange.

## What to do before submitting to TikTok

- [ ] Deploy to GitHub Pages and confirm all four pages load over HTTPS.
- [ ] Replace `<your-pages-url>` placeholders in the TikTok app config with the real URLs.
- [ ] Add your real contact email to Privacy Policy §10 and Terms §9 (currently says "listed in README").
- [ ] Review TikTok's Content Posting API scope requirements and confirm the use-case description matches.
- [ ] Do **not** add credentials, API keys, or secrets to these files.
