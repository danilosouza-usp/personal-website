# Academic website (Quarto)

A minimalist single-page academic site built with [Quarto](https://quarto.org).
Sans-serif, generous whitespace, one blue accent, hand-written publications.

## Files

- `index.qmd` — the homepage (header, bio, research, teaching, contact)
- `teaching/` — one `.qmd` per course page (e.g. `econ-crime-grad.qmd`
  becomes `yoursite.com/teaching/econ-crime-grad.html`)
- `custom.scss` — the look. The variables at the top control everything.
- `_quarto.yml` — site settings and the navbar
- `files/` — your `photo.jpg`, `cv.pdf`, reading lists, syllabi
- `.github/workflows/publish.yml` — auto-publishes on every push

## Adding a course page

1. Copy `teaching/econ-crime-grad.qmd` to a new name in the same folder.
2. Edit the header, description, meetings, assessment, syllabus and readings.
3. Link it from `index.qmd`, in the Teaching grid:
   `[[Syllabus](teaching/your-course.html)]{.course-link}`

Paths inside `teaching/` need `../` to reach the project root — for example
`../files/reading-list.pdf` and `../index.html#teaching`. Navbar links in
`_quarto.yml` do not: Quarto rewrites those for each page's depth.

## Run it locally

1. Install Quarto: <https://quarto.org/docs/get-started/>
2. From this folder, run:
   ```
   quarto preview
   ```
   Your browser opens with live reload. Edit `index.qmd` and watch it update.

## Make it yours

- Replace `files/photo.jpg` and `files/cv.pdf` with your own.
- Edit the text in `index.qmd` — it's plain Markdown. Each paper is a `::: {.pub}` block.
- Change the accent colour: edit `$accent` at the top of `custom.scss` (one line).
- Change the font: edit `$font-family-sans-serif` in `custom.scss` and the Google
  Fonts link in `_quarto.yml`.
- Add/remove navbar items in `_quarto.yml` under `navbar > right`.

## Publish to GitHub Pages

**Option 1 — automatic (recommended).** Push this repo to GitHub, then in
*Settings → Pages* set the source to the `gh-pages` branch. The included
GitHub Action renders and deploys on every push to `main`.

**Option 2 — manual.** Run `quarto render`, commit the generated `docs/`
folder, and in *Settings → Pages* set the source to `main` / `/docs`.

If your repo is named `yourusername.github.io`, the site lives at
`https://yourusername.github.io`. Update `site-url` in `_quarto.yml` to match.
