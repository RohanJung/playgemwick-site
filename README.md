# Dream Big Quest website

Static site (plain HTML + one CSS file, no build step). Hosts the studio home page, a page per game,
privacy policies, terms, support and `app-ads.txt` for AdMob.

| URL | File | Used for |
|---|---|---|
| `/` | `index.html` | Studio home, list of games |
| `/gemwick/` | `gemwick/index.html` | Game page (Play Store "Website" field) |
| `/gemwick/privacy/` | `gemwick/privacy/index.html` | **Privacy policy URL** for Play Console and the AdMob consent message |
| `/privacy/` | `privacy/index.html` | Website privacy + links to each game's policy |
| `/terms/`, `/support/` | | Terms of use, contact + FAQ |
| `/app-ads.txt` | `app-ads.txt` | AdMob seller verification (must sit at the domain root) |

## Before going live
1. The domain is already set to https://playgemwick.site. Fill in the contact email:
   ```sh
   ./configure.sh support@playgemwick.site https://playgemwick.site
   ```
2. Deploy the folder (Cloudflare Pages: "Upload assets", or `npx wrangler pages deploy . --project-name dreambigquest`).
   `_headers` and `404.html` are picked up automatically by Cloudflare Pages and Netlify.
3. Connect the domain in the host's dashboard.

## When the game is live on Google Play
In `gemwick/index.html`, point the "Coming soon" button at
`https://play.google.com/store/apps/details?id=com.dreambigquest.boomblocks` and remove `aria-disabled`.
Then add the domain as the **Website** in the Play store listing so AdMob can find `app-ads.txt`.
