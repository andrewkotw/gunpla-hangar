# GUNPLA HANGAR

A responsive personal Gunpla wishlist and collection archive, built with plain HTML, CSS and JavaScript. Visit the [live site](https://andrewkotw.github.io/gunpla-hangar/).

## Features

- Toggle between a photo grid and compact ranked list for all **15** wishlist entries. Your view choice is saved in the browser.
- See each kit's regular retail or Premium Bandai release channel, with a sourced reprint or restock record and its evidence type.
- English and Traditional Chinese product names appear together; wishlist search matches either name.
- Dedicated, shareable HTML page for each kit, including the **8** collection entries.
- Search by kit name, series, pilot or grade; filter by series and availability; sort by rank, price, newest or name.
- Product photo galleries with original-source credits, lightbox, keyboard arrows and Esc.
- Straight-build assessments, sticker concerns, joint notes, reviews, release dates and indicative Taiwan prices.
- Separate collection and ranking-method pages.
- Mouse-only targeting cursor with a short trail and four corners that tighten on click; form fields, touch devices and reduced-motion settings use the native cursor.
- Responsive layout for desktop, tablet and mobile. No framework, build step, authentication or database required.

## Preview locally

You can open `index.html` directly in a browser. For a more realistic preview, run:

```bash
cd gunpla-hangar
python3 -m http.server 8000
```

Open <http://localhost:8000>.

## GitHub Pages

The site is published from the `main` branch root at <https://andrewkotw.github.io/gunpla-hangar/>. Pushes to `main` trigger a new deployment.

All navigation is relative, so it works at a project subpath and on a custom domain. No fixed hostname is embedded.

## Updating kit data

- Edit **`data/models.json`**, the canonical source containing `wishlist` and `collection` arrays.
- Set `nameZh` to the kit's Traditional Chinese shopping name; it appears below the English name and is searchable on the wishlist.
- `rank` determines personal ranking; `priceMin` is used when sorting by price.
- `priceEvidence` records the source listings, JPY sample range, conversion rate and check date for marketplace estimates.
- `releaseChannel` records the kit's original sales channel (`Regular retail` or `Premium Bandai`). `latestReprint` stores the newest dated evidence found, its source, and an `evidenceLabel` describing what was actually observed. This is not a complete production history: a retailer restock, buyback listing, or overseas arrival does not establish the factory's production month or prove there was no later run. `nextReprint` stores a separate, tentative retailer-listed future batch where available.
- `photos` contain external image URLs and credit links. Each image is an object with `url`, `label`, `type`, `source`.
- External links should be verified and only photographs you have permission to reuse should be hosted locally.
- Run **`python3 build.py`** after changing the JSON. It updates `assets/data.js` and creates per-kit `models/slug/index.html` pages. Commit all generated changes.

**Important**: Edit `data/models.json`, not the generated `assets/data.js`. The build script loads the JSON if it exists and will not overwrite it. Existing model pages are simple wrappers and do not need regeneration for updates to current entries.

## Photography policy & known limitation

- External image URLs are used to avoid shipping copied proprietary photos. The photographs remain the property of Bandai, reviewers, and their respective original publishers.
- **Some links may fail to load** due to anti-hotlink rules, missing/unpublished variants, or changes to a third-party site's image filenames. The gallery hides broken thumbnails automatically and keeps source-review links available.
- Some kits have fewer than five sourced images. The UI shows only available images; it does not pretend to have straight-build pictures when only painted examples are known.
- Before public deployment, consider replacing uncertain/third-party externally linked image URLs with **your own photographs or images you have permission to publish** and keep their credits.

## Price disclaimer

Prices are rough references, not live offers or amounts paid. The eight entries that lacked a price reference now use Mercari Japan kit listings, except the unreleased Ryusei-Go (Graze Custom III), which uses [Bandai's ¥2,750 preorder price](https://www.bandaispirits.co.jp/products/search/detail.php?grp_id=5325&prd_id=4580886844968000). Each updated kit page links its sample listings.

JPY estimates use the [Bank of Taiwan](https://rate.bot.com.tw/xrt) spot selling rate of **¥1 = NT$0.2085** checked 30 October 2026. Ranges are rounded and exclude Taiwan proxy fees, international shipping and taxes. Listing condition, availability and exchange rates can change; older Taiwan price references elsewhere in the catalog were not refreshed.

## Technologies

Pure HTML/CSS/JavaScript, Google Fonts (optional with system fallbacks), relative links, SVG favicon.
