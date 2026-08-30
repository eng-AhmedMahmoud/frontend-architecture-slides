# frontend-architecture-slides

## Editing the deck

`index.notes.html` is the source of truth — the presenter deck, with every
`<aside class="notes">` speaker note inline. It is gitignored and never published.

`index.html` is **generated**. Never edit it directly; the edit will be wiped on the
next build and the note will be missing from the presenter copy.

Workflow for any slide change:

1. Edit `index.notes.html`
2. `python3 ../../brand/apply_brand.py` — re-stamps the Catalyst chrome and renumbers pages
3. `python3 build.py`
4. Commit `index.html` (plus `build.py` / docs if those changed)

Step 2 matters whenever a slide is added, removed or reordered: the `MODULE X · VIDEO Y`
chip and the `07 / 49` page number are baked into each `<section class="slide">`, so a new
slide leaves every number after it wrong until the brand script runs.

`python3 build.py --check` exits 1 when `index.html` is stale — run it before
committing.

## Checking the deck builds

There is no bundler. The equivalent of a build check is:

- `python3 ../../brand/apply_brand.py --check` — brand chrome present and page numbers correct
- `python3 build.py --check` — public deck in sync with the presenter deck
- HTML tag-balance parse over both files
- `node --check` on the extracted inline `<script>` of `index.html`
