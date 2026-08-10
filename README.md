# Frontend Architecture — Slides

The 30-minute lesson: Monoliths → Monorepos → Micro-Frontends.

**Live:** https://eng-ahmedmahmoud.github.io/frontend-architecture-slides/

- `index.html` — the student deck, generated (arrow keys to reveal/move, `M` slide menu, `C` code exercise, `F` fullscreen, `P` print)
- `index.notes.html` — the presenter deck, same slides plus speaker notes on `S`. Local only, gitignored
- `cheatsheet.html` — one-page speaker cheat-sheet
- `curriculum.html` — the curriculum proposal deck

## Two decks, one source

Edit **`index.notes.html`** — it is the source of truth. Then:

```sh
python3 build.py          # regenerate index.html
python3 build.py --check  # verify index.html is in sync (exit 1 if stale)
```

The build strips every `<aside class="notes">` block, drops the `S` hint from the
footer, and disables the notes toggle, so the published deck carries no speaker
notes at all — not hidden, not in view-source.

Because `index.notes.html` is gitignored, the notes exist **only on this machine**.
If it ever goes missing, the last committed copy of the deck that still had notes
inline is `4d74a98`:

```sh
git show 4d74a98:index.html > index.notes.html
```
