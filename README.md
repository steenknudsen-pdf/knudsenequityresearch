# Knudsen Equity Research

A bare-bones static blog. No build step, no dependencies to install, free to host.
Everything is set in Times New Roman.

## Files

- `index.html` — home page (masthead, ethos, list of writing)
- `post.html` — the template that displays any single article
- `posts.json` — the list of articles (this is what builds the home page index)
- `posts/` — one Markdown file per article (this is where you write)
- `style.css` — all styling
- `CNAME` — your custom domain
- `.nojekyll` — tells GitHub Pages to serve the files as-is

## Publish on GitHub Pages (free)

1. Create a free account at github.com if you don't have one.
2. Create a new **public** repository named `knudsenequityresearch.com` (any name works, but this is tidy).
3. Upload every file in this folder to the repo (drag and drop works — include the `posts` folder, `CNAME`, and `.nojekyll`).
4. In the repo, go to **Settings → Pages**. Under "Build and deployment", set **Source: Deploy from a branch**, **Branch: main**, **Folder: / (root)**. Save.
5. Wait ~1 minute. Your site is live at `https://<your-username>.github.io/<repo>/`.

## Point your domain (knudsenequityresearch.com)

At your domain registrar, add these DNS records:

- Four `A` records for the apex domain, pointing to GitHub's IPs:
  - `185.199.108.153`
  - `185.199.109.153`
  - `185.199.110.153`
  - `185.199.111.153`
- One `CNAME` record for `www` pointing to `<your-username>.github.io`

Then in **Settings → Pages → Custom domain**, enter `knudsenequityresearch.com` and save.
Tick **Enforce HTTPS** once it becomes available (can take up to a few hours).
The `CNAME` file in this repo already holds your domain, so GitHub will recognize it.

## Write a new post (two steps)

1. Create a new Markdown file in `posts/`, e.g. `posts/nvda-thesis.md`. Write your article in
   plain Markdown — `##` for a section heading, blank lines between paragraphs, `**bold**`, `*italic*`,
   `>` for a pull quote, `-` for bullets, `[text](url)` for links.

2. Add one entry to the **top** of the `posts` list in `posts.json`:

   ```json
   {
     "posts": [
       { "slug": "nvda-thesis", "title": "The case for NVDA", "date": "August 2026" },
       { "slug": "first-note",  "title": "How I think about a position", "date": "July 2026" }
     ]
   }
   ```

   `slug` must match the file name (without `.md`). Use only lowercase letters, numbers, and hyphens.

Commit/upload both changes. The home page picks up the new post automatically. That's it.

## Note on previewing locally 

If you open `index.html` directly from your computer (file://), the post list may not load —
browsers block file reads for security. That's expected. It works correctly once the files are
on GitHub Pages (or any web server). To preview locally, run `python3 -m http.server` in this
folder and open `http://localhost:8000`.
