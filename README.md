# AI News Short Factory — TikTok Review Site

Static public website for TikTok Developer Platform app review.

AI News Short Factory is a creator workflow tool that helps an authorized creator prepare short-form AI news videos and upload completed videos to the creator’s TikTok inbox/upload flow for manual review and publishing.

The system does **not** auto-publish public posts.

## Files

| File                  | Purpose                                                                                     |
| --------------------- | ------------------------------------------------------------------------------------------- |
| `index.html`          | Homepage — tool overview, workflow, and “no auto-publish” policy                            |
| `privacy.html`        | Privacy Policy — data collected, TikTok token handling, no data sale, deletion instructions |
| `terms.html`          | Terms of Service — authorized use, no auto-publish, no spam/abuse, creator responsibility   |
| `oauth-callback.html` | OAuth redirect target — displays success/error state after TikTok authorization             |
| `README.md`           | Deployment and TikTok app configuration notes                                               |

## Messaging summary

AI News Short Factory is a creator workflow tool, not a bot.

It may upload completed videos to the authorized creator’s TikTok inbox/upload flow using TikTok’s Content Posting API. The creator manually reviews, edits, and publishes inside TikTok.

The system:

* Does not auto-publish to a public audience
* Does not schedule public posts
* Does not change video visibility to public
* Does not sell user data
* Stores TikTok tokens and pipeline outputs locally under the creator’s control
* Uses TikTok access only for the authorized creator account

## Deployment

This review site is deployed with GitHub Pages.

Live URLs:

| Field                | URL                                                                             |
| -------------------- | ------------------------------------------------------------------------------- |
| Website URL          | `https://rivedu-droid.github.io/ai-news-short-factory-site/`                    |
| Privacy Policy URL   | `https://rivedu-droid.github.io/ai-news-short-factory-site/privacy.html`        |
| Terms of Service URL | `https://rivedu-droid.github.io/ai-news-short-factory-site/terms.html`          |
| OAuth Redirect URI   | `https://rivedu-droid.github.io/ai-news-short-factory-site/oauth-callback.html` |

## TikTok app configuration

Use the URLs above in the TikTok Developer Portal.

Recommended setup:

* App type: Web
* Product: Content Posting API
* Requested scope: `video.upload`
* Do not request `video.publish` for this workflow
* Redirect URI: use the hosted HTTPS OAuth callback URL above, or any other redirect URI explicitly registered in the TikTok app configuration

## OAuth and token handling

TikTok OAuth tokens are not stored in this repository.

Tokens are stored locally by the creator in environment variables or local-only token files. These files are excluded from Git and are never published to GitHub Pages.

No client secrets, access tokens, refresh tokens, API keys, or authorization headers should be committed to this repository.

## Public publishing policy

The tool may prepare and upload content for manual creator review, but the creator remains responsible for final publishing decisions.

The tool must not:

* Publish public TikTok posts automatically
* Schedule public posts
* Set video visibility to public through the API
* Use TikTok Direct Post functionality
* Post spam, abusive, misleading, or unauthorized content

## Before submitting to TikTok

Confirm:

* Homepage loads over HTTPS
* Privacy Policy loads over HTTPS
* Terms of Service loads over HTTPS
* OAuth callback page loads over HTTPS
* Contact email is visible in the Privacy Policy and Terms
* No secrets or internal credentials are present in this repository
* The TikTok app requests `video.upload`, not `video.publish`
* The app description clearly states that the creator manually reviews and publishes content inside TikTok
