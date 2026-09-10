# SweetPeeps — Local Website

A responsive HTML presentation of a redesigned SweetPeeps jewelry storefront, featuring an ivory-and-blush design and a locally stored snapshot of the original store's public catalog.

## Getting started

Double-click **index.html** or **OPEN WEBSITE.cmd** in the project folder. No installation is required. Open the website in Chrome or Edge, and keep the `dist` folder and its assets together.

### Optional local server

With Node.js installed, run this command from the project folder:

```sh
node preview-server.cjs
```

Then open [http://127.0.0.1:4173](http://127.0.0.1:4173). The server is accessible only from the same computer.

## Features

- Responsive homepage with a compact header and original product photography in the main banner.
- Catalog snapshot with **1,260 products** and **25 collections**, including imported USD prices, variants, full galleries and descriptions.
- Search, finish/price/stock filters, sorting, pagination and grid/list views.
- Product quick view, image zoom, and sizing and care information.
- Device-local wishlist, recently viewed products and comparison of up to four products.
- Shopping bag with variant selection, quantity controls, removal and a locally saved gift note.
- **10 information pages** and **40 publicly rendered customer reviews** imported from the original store.
- Original brand film and links to the original social reels.
- Original-store links for newsletter subscriptions, region selection, accounts and checkout.

## Local preview vs. live store

This project is a local presentation, not a live commerce backend.

- The catalog was imported on **September 9, 2026** and does not synchronize automatically.
- The cart and wishlist use browser local storage on the current device.
- The newsletter preview does not subscribe anyone; it directs visitors to the original store.
- Account credentials and payments are not collected by the local website.
- Checkout opens the original Shopify store with the selected variant IDs. Review current prices, stock, shipping and gift eligibility there before purchasing.
- Gift notes do not transfer automatically to the original checkout.
- The imported policy allows exchanges rather than returns. Refer to the original store for the current policy.
- Conflicting shipping promotions were not reproduced as an unconditional shipping promise.

## Project structure

```text
index.html             Entry page that opens dist/index.html
OPEN WEBSITE.cmd       Windows launcher
preview-server.cjs     Optional Node.js local server
README.md              GitHub documentation
README.txt             Plain-text copy of this documentation
dist/index.html        Main HTML document
dist/styles.css        Responsive styling
dist/app.js            Local routes and interactions
dist/data.js           Product and collection snapshot
dist/pages.js          Information pages and reviews
dist/assets/           Local images, size chart and brand film
work/                  Import scripts, source snapshots and validation
```

The `work` folder is not required to present the website. Some development scripts contain machine-specific paths; the static website can be opened from another folder as long as its files remain together.

## Imagery

Product photographs and the original brand film were sourced from [shopsweetpeeps.com](https://shopsweetpeeps.com/).

The active homepage banner uses the original **Margo Celestial Charm Necklace** photograph at `dist/assets/p-8650690232478-1.jpg`.

The brand-story image at `dist/assets/story.png` is an AI-generated editorial concept. The earlier generated hero at `dist/assets/hero.png` remains in the assets folder but is no longer used as the active banner.

Generated assets were created with the built-in `image_gen` tool using these briefs:

- **Earlier hero:** An adult woman's collarbone and hand, layered gold necklaces, a heart ring, ivory knit clothing, warm daylight, realistic texture, and no text or logos.
- **Brand story:** Gold jewelry, pearl earrings and a blush suede box on ivory linen, soft sunlight, realistic still-life photography, and no text or logos.

Generated editorial imagery is illustrative and should not be treated as exact product photography.

## Verification

JavaScript syntax, catalog and asset integrity, and scripted local shopping logic checks were run. Results are recorded in `work/validation-report.json`.

Browser visual QA and live payment/checkout transaction testing were not performed.

## Latest design update

**September 10, 2026:** Replaced the generated homepage banner with original product photography, reduced the header height, and standardized product names, prices and spacing.

## Deploying to Vercel

This is a static HTML/CSS/JavaScript website. The root `vercel.json` configures Vercel to serve `dist` directly without an install or build step.

1. Upload or commit `vercel.json` and the complete `dist` folder, including its assets, to your GitHub repository.
2. In Vercel, select the directory containing both `vercel.json` and `dist` as the Root Directory. If they are at the repository root, leave Root Directory at its default. Do not select `dist` as Root Directory when using this configuration.
3. Use the **Other** framework preset. The configuration sets the Output Directory to `dist` and leaves the Build and Install Commands empty.
4. Deploy the updated commit. Redeploying an older commit will not include the new configuration.
5. Open the deployment's base URL, not `/dist/index.html`.

The application uses hash routes such as `/#collection/new`, so a catch-all rewrite is not required. The local `preview-server.cjs` is not used by Vercel.

If `404: NOT_FOUND` persists, check that the selected GitHub branch contains `dist/index.html`, the deployment finished successfully, and the domain points to that deployment. The local configuration alone cannot verify your remote project settings.

Reference: https://vercel.com/docs/builds/configure-a-build
