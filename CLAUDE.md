# frontend-architecture-slides

## Editing the deck

`index.notes.html` is the source of truth — the presenter deck, with every
`<aside class="notes">` speaker note inline. It is gitignored and never published.

`index.html` is **generated**. Never edit it directly; the edit will be wiped on the
next build and the note will be missing from the presenter copy.

Workflow for any slide change:

1. Edit `index.notes.html`
2. `python3 build.py`
3. Commit `index.html` (plus `build.py` / docs if those changed)

`python3 build.py --check` exits 1 when `index.html` is stale — run it before
committing.

## Checking the deck builds

There is no bundler. The equivalent of a build check is:

- `python3 build.py --check` — public deck in sync with the presenter deck
- HTML tag-balance parse over both files
- `node --check` on the extracted inline `<script>` of `index.html`
