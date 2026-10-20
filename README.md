# whoisgreed.com

Greed's artist website: bookings, electronic press kit, SoundCloud mixes, and performance archive.

## Deployment

The existing Cloudflare deployment was shown as a Worker named `djgreed`. To retain it and its domain, open that Worker → Settings → Build → Connect Git repository, select this repo, set production branch `main`, leave build command blank, and use `npx wrangler deploy` as the deploy command. The included `wrangler.jsonc` serves `public/` without a Worker script. No paid plan or app secrets are required for static assets.


Site files live in `public/`. No dependencies or build step are needed.

### Cloudflare Pages Git integration

- Repository: `brandondaugherty/whoisgreed`
- Production branch: `main`
- Framework preset: None
- Build command: leave blank
- Build output directory: `public`
- Root directory: repository root

Connect this repository in Cloudflare Workers & Pages → Create application → Pages → Connect to Git. After the first deployment succeeds, add `whoisgreed.com` under Custom domains. Keep all Purelymail email DNS records in place.

The previous upload-based deployment remains live until the custom domain is moved. A Pages Direct Upload project needs a new Git-integrated project. If the existing deployment is a Worker, its Git integration can instead use the included `wrangler.jsonc` with deploy command `npx wrangler deploy` and no build command. Confirm that the existing Worker is named `djgreed` before using that configuration.

Pushing changes to `main` triggers production deployment once Cloudflare Git integration is connected. Other branches can produce previews in Pages. Check Cloudflare's deployment status before calling a change live.

## Editing

- `public/index.html`: copy, show history, links, and embeds
- `public/style.css`: appearance and responsive layout
- `public/app.js`: booking email preparation and browser interactions
- `public/assets/`: logos, portraits, textures, and flyers

The booking form opens the visitor's email app with an inquiry addressed to `me@whoisgreed.com`. It does not submit or store inquiries on a server.

## Local preview

Run `python3 -m http.server 4173 --directory public`, then open http://localhost:4173.
