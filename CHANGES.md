# Change Log — Automated Edits (2026-08-04)

> **Read this first.** The edits described below were made by an automated
> background task, **not** explicitly requested change-by-change. They have been
> **kept** by decision of the site owner, with this file serving as the record so
> they can be reverted if anything looks wrong.

## How to revert

The last clean committed state is:

```
ed94041  Initial commit: Sattva Nation static site (2026-08-03 10:57:03 +0530)
full SHA: ed9404176856f3ca43e3b71b6d6ea88b59cbf846
```

**Revert everything back to that commit (discards ALL the edits below):**

```bash
git restore --source=ed94041 --worktree -- .
# restore the renamed image and remove the added copy
git checkout ed94041 -- "assets/mentors/Dr. Blossom Kochar.jpg"
rm -f "assets/mentors/Dr. Blossom Kochhar.jpg"
```

**Revert a single file** (example: the homepage):

```bash
git checkout ed94041 -- index.html
```

**See exactly what changed in a file before deciding:**

```bash
git diff ed94041 -- index.html
```

**Discard this whole batch quickly** (nuclear option — wipes ALL uncommitted
changes in the working tree, including this file):

```bash
git stash --include-untracked      # tuck away, recoverable via `git stash pop`
# or, to throw them away permanently:
git checkout -- . && git clean -fd
```

---

## Files changed

Diff stat vs. commit `ed94041`:

| File | Lines changed |
|------|---------------|
| `index.html` | +219 / heavy |
| `gallery/index.html` | +384 / heavy |
| `blog/index.html` | +166 |
| `contact-us/index.html` | +94 |
| `events/index.html` | +79 |
| `founders/index.html` | +59 |
| `programmes/index.html` | +40 |
| `about-us/index.html` | +22 |
| `assets/mentors/Dr. Blossom Kochar.jpg` | **deleted** (renamed) |
| `assets/mentors/Dr. Blossom Kochhar.jpg` | **added** (renamed copy, corrected spelling) |

---

## What was changed (per the automated task's own report)

> ⚠️ These descriptions come from the automated task. They have **not been
> independently verified line-by-line.** Preview the pages in a browser before
> relying on them.

### index.html (homepage)
- **Mentors:** replaced 4 generic Unsplash stock faces + invented names with 7 real
  named headshots from `assets/mentors/` (Dr. Mickey Mehta, Dr. Mukesh Batra,
  Dr. Blossom Kochhar, Dr. Deepa Malik, Dr. Niranjan Hiranandani, Dr. Seema Midha,
  Gurmit Singh Arora). Switched from `background-image` divs to `<img alt>` tags.
- **Gallery strip:** now pulls from the real Awards 1.0/2.0/3.0 and college-workshop
  image libraries instead of stock photos.
- **Deduped About:** the two stacked "Love. Refine. Empower." sections no longer
  share a heading — the second is now "A Festival to Celebrate Life."
- **Nav:** added Blog + Gallery links; changed mobile breakpoint 900px → 960px to
  match the other pages.
- **Anchors:** gallery section `id="events"` → `id="gallery"`; "View Events" now
  points to `/events/`; `#about` now targets the About section.
- **Contact form:** added `aria-label`s, `novalidate`, email-format validation.
- **Responsive:** added mobile breakpoints for mentors, programmes, gallery,
  what-we-do, about, contact. Added `:focus-visible` outlines and
  `scroll-padding-top`.

### gallery/index.html
- Relabeled filter bar "Filter by" → "Jump to" with accurate labels; fixed the
  mismatched JS section map; added an `id` to the video section.
- Converted all relative `../SATTVA…` image paths to absolute `/SATTVA…`.
- Added `:focus-visible` + `scroll-padding-top`.

### contact-us/index.html
- Added Blog + Gallery to the nav; breadcrumb separator `–` → `|`; added
  `rel="noopener"` on the Instagram link; added `:focus-visible` + `scroll-padding-top`.

### blog/index.html
- Fixed author inconsistency (featured post "Priya Sharma" → "Priya Kapoor").
- Converted 6 post-card titles from `<div>` to semantic `<h3>` (with margin reset).
- Added `:focus-visible` + `scroll-padding-top`.

### events / founders / about-us / programmes
- Modified as part of the same batch (nav / consistency / responsive / accessibility
  tweaks). Review individual diffs with `git diff ed94041 -- <file>`.

---

## Addendum — additional edits landed after this file was first written

The same automated task continued running and made **further edits** beyond the
list above. Confirmed on disk:

- **`index.html` and `contact-us/index.html`:** mobile-menu breakpoint changed
  again from `960px` → **`1024px`** (to stop the expanded 8-item nav from
  overlapping the logo around 961–1024px width).
- The task also *reported* (not yet independently confirmed here) a **UTF-8 BOM**
  present on `blog`, `contact-us`, and `events` — it said it did **not** strip it.

Because this task mutated files unpredictably over several runs, treat the
per-file `git diff` as the source of truth, **not** the descriptions in this file:

```bash
git diff ed94041 -- <file>          # exact changes in one file
git diff ed94041 --stat             # overview of everything changed
```

Note the breakpoint is now inconsistent across pages: `index.html` and
`contact-us` use `1024px`, while `about-us` uses `900px` and blog/gallery/events/
programmes/founders use `960px`. Worth unifying if you keep the changes.

## Known item left unchanged (intentional)

The contact form and the blog newsletter form still POST to the **same Formspree
endpoint** (`mvgqzdrl`). Contact messages and newsletter sign-ups will land in one
shared inbox. This is a business decision — if you want them separated, create a
second Formspree form and point the newsletter at it.
