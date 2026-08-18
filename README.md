# Personal website

Built with [Quarto](https://quarto.org). Content that changes often (papers,
working papers, work in progress) lives in [`data/publications.csv`](data/publications.csv)
and is turned into the Research page by an R code chunk in
[`research.qmd`](research.qmd) — updating the site is usually just editing a
spreadsheet.

## Updating the site

1. Edit content:
   - Add/edit/remove a paper → edit `data/publications.csv`.
   - Edit bio/news → `index.qmd`.
   - Edit CV text or swap the PDF → `cv.qmd` / `files/cv.pdf`.
   - Edit teaching/contact → `teaching.qmd` / `contact.qmd`.
2. Preview locally (auto-reloads on save):
   ```
   export PATH="$HOME/.local/bin:$PATH"   # only needed if quarto isn't on your PATH already
   quarto preview
   ```
3. When you're happy, render the site (this also updates the `_freeze/`
   cache of R results that lets Netlify build without R installed):
   ```
   quarto render
   ```
4. Commit and push:
   ```
   git add -A
   git commit -m "Update publications"
   git push
   ```
   Netlify rebuilds and deploys automatically on push.

## One-time setup notes

- Quarto CLI was installed locally without admin rights, under `~/.local/opt`,
  symlinked at `~/.local/bin/quarto`. Add `export PATH="$HOME/.local/bin:$PATH"`
  to your shell profile (`~/.zshrc`) so `quarto` is always on your PATH.
- Replace `files/headshot.jpg` and `files/cv.pdf` with your real files (same
  filenames — the pages already link to them).
- Fill in the placeholder name/email/affiliation text in `_quarto.yml`,
  `index.qmd`, `cv.qmd`, `teaching.qmd`, and `contact.qmd`.
- Netlify: point your existing Netlify site at this repo/branch (or create a
  new Netlify site from this repo) — `netlify.toml` handles the build. No DNS
  changes needed since `www.liqing-li.com` stays on Netlify.
