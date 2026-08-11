# CEO Sidekick — public site

Three static pages, no build step:

| Page | Purpose |
|---|---|
| `index.html` | Homepage. Google OAuth verification requires a homepage that describes the app and links to the privacy policy. |
| `privacy.html` | Privacy policy. Required by **both** Google OAuth verification and App Store Connect. |
| `terms.html` | Terms of service. |

## Why this is a separate repo

GitHub Pages needs a public repo on a free plan. The app repo contains a `.env`
with live credentials, so the site is kept entirely apart from it — there is no
path from here back to application source.

## Deploying

Pushing to `main` publishes automatically via GitHub Pages.

## Custom domain

Google OAuth verification wants a homepage on a domain you demonstrably own.
`*.github.io` is owned by GitHub, so for verification, point a subdomain here:

1. Add a `CNAME` file to this repo containing the bare hostname, e.g.
   `ceosidekick.formadinnerware.com`
2. At your DNS provider, add a `CNAME` record for that subdomain pointing to
   `formatableware.github.io`
3. Repo **Settings → Pages → Custom domain**, enter the same hostname, and tick
   **Enforce HTTPS** once the certificate is issued
4. Verify the domain in [Google Search Console](https://search.google.com/search-console)
   using the same Google account that owns the Cloud project

## Editing

Colours in `style.css` mirror `src/constants/theme.js` in the app repo. If the
brand palette changes there, change it here too.

## Before submitting to Google or Apple

1. Replace `support@example.com` throughout (10 occurrences across the three pages).
2. Remove the `<meta name="robots" content="noindex">` tag from all three pages —
   it is only there to keep the placeholder-contact version out of search results.
