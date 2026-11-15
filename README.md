# Mark's Tech Vlogs – link page

A one-page replacement for Linktree, hosted free on GitHub Pages at
**https://mytech.markstechblogs.co.uk**.

## Updating the page

Everything you edit is in the block marked `✏️ EVERYTHING YOU NEED TO EDIT` near the
bottom of `index.html`:

- `PRODUCTS`: one line per product. Copy a line, change the name, category and link.
  Plain Amazon links are fine: the Geniuslink script turns them into your affiliate links.
- `VIDEOS`: the "Popular on the channel" strip (YouTube video IDs).
- `FEATURED_APP`: the Pairbook card.
- `BRANDS`: the quick brand buttons under the search box.

Then commit and push. GitHub Pages updates in about a minute.

## First-time setup

1. Create an empty **public** repo on GitHub called `links` (no README).
2. In this folder, run:

   ```bash
   git init -b main
   git add .
   git commit -m "Link page"
   git remote add origin https://github.com/YOUR-USERNAME/links.git
   git push -u origin main
   ```

3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
4. The **Custom domain** box should already show `mytech.markstechblogs.co.uk` (from the
   `CNAME` file).
5. In **Cloudflare** (DNS for markstechblogs.co.uk), add a record:

   | Type  | Name     | Target                       | Proxy status          |
   |-------|----------|------------------------------|-----------------------|
   | CNAME | `mytech` | `YOUR-USERNAME.github.io`    | **DNS only** (grey cloud) |

   Keep it grey-clouded so GitHub can issue the HTTPS certificate.
6. Back in GitHub Pages settings, wait for the DNS check to pass, then tick
   **Enforce HTTPS**. This can take up to an hour.
7. Point your YouTube/Instagram bio links at https://mytech.markstechblogs.co.uk.

Until the domain is set up, the page also works at
`https://YOUR-USERNAME.github.io/links/`.

## Files

- `index.html`: the whole page
- `assets/`: avatar, logo, background, share image and Pairbook icon (web-sized copies of
  the originals in Movies/Youtube/YouTube)
- `CNAME`: the custom domain for GitHub Pages
- `.nojekyll`: tells GitHub to serve the files as they are
