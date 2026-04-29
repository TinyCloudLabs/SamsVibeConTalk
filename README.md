# The Anatomy of Interoperable Apps

A 15-minute talk by Sam Gbafa, co-founder of TinyCloud. April 29, 2026.

## To edit the deck

**`anatomy-talk.md` is the only file you edit.** It's a [Slidev](https://sli.dev) markdown file — each `---` is a new slide.

```bash
bun install        # one-time
bun run dev        # http://localhost:3033 — hot reloads as you save
bun run export     # rebuilds anatomy-talk.pdf
```

The dev server hot-reloads, so save and refresh.

## What's in here

| path | what it is | edit it? |
| --- | --- | --- |
| `anatomy-talk.md` | the deck source | **yes — this is the deck** |
| `styles/index.css` | layout classes the markdown depends on | only if you need new layouts |
| `public/anatomy-talk/*.png` | the 10 illustrations the slides reference at `/anatomy-talk/...` | replace files in place to swap illustrations |
| `package.json` | Slidev + theme deps | shouldn't need to |
| `anatomy-talk.pdf` | full PDF export — regenerate with `bun run export` | no — output |
| `slides/slide-NN.png` | per-slide PNG export — regenerate with `slidev export anatomy-talk.md --format png --output slides` | no — output |
| `illustrations/` | clean copies of the 10 deployed illustrations (same files as `public/anatomy-talk/`, mirrored here for browsing) | no — reference |
| `illustrations/alternates/` | every other render generated during iteration (originals before cropping, v2–v4 attempts, raw Gemini outputs) | no — archive |

## Slide / illustration map

| slide | topic | illustration |
| --- | --- | --- |
| 1 | Title | — |
| 2 | Cold open: medical silos | `02-medical-silos.png` |
| 3 | Diagnosis: every app starts cold | `03-fragmented-islands.png` |
| 4 | A clue: local agents | `04-local-agent.png` |
| 5 | The four-part frame | `01-stack-hero.png` |
| 6 | Identity (passkey) | `05-identity-passkey.png` |
| 7 | A place (space) | `06-place-space.png` |
| 8 | A contract (manifest) | `07-contract-manifest.png` |
| 9 | Discovery (registry) | `08-discovery-registry.png` |
| 10 | Demo intro | — |
| 11 | Demo punchline | `09-emergent-app.png` |
| 12 | The bigger bet | `10-bigger-bet.png` |
| 13 | Where TinyCloud fits | — |
| 14 | Thank you / contact | — |
