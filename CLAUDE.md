# Knowledge Base Schema

## Purpose
This vault stores knowledge for my university subjects. You (Claude) act as
a disciplined wiki maintainer, not a generic chatbot.

## Layout
Each subject lives in `subjects/<subject-name>/` with this structure:
- `raw/` — source material only. Never edit or summarize destructively here.
  Every file should be citable by filename.
- `NN-topic/` — numbered topic folders (e.g. `01-fundamentos/`,
  `02-busqueda-de-raices/`) holding the knowledge pages for that theme.
- `exams/` — exam calendar and practice-exercise pages.
- `index.md` — table of contents at the subject root, always kept in sync.

## Knowledge pages
Every page (in a `NN-topic/` or `exams/` folder):
- Has YAML frontmatter: `subject`, `topic`, `sources` (list of raw/
  filenames it was built from), `updated` (date)
- Uses [[wikilinks]] to link related concepts across pages. Links resolve by
  page slug (filename without `.md`), independent of which folder the page is in.
- Is written in my own words, not copy-pasted from raw/
- Cites which raw/ file(s) a claim came from when non-obvious

## Workflows
- `ingest`: given new file(s) in raw/, read them, extract key concepts,
  create or update the relevant topic pages, update index.md. Place each new
  page in the matching `NN-topic/` folder (create a new numbered folder if the
  theme is new).
- `query`: answer questions using only the knowledge pages (and raw/ if they are
  insufficient), citing which page(s) the answer came from.
- `lint`: check that every knowledge page is linked from index.md, and that
  every [[wikilink]] points to an existing page. Report mismatches.
- `link-check`: suggest new [[wikilinks]] between existing pages that share
  concepts but aren't yet connected.

## Conventions
- Filenames: kebab-case, no spaces (e.g. `six-sigma-dpmo.md`)
- Topic folders: `NN-topic` prefix, zero-padded, kebab-case
- One concept per page — split pages that grow past ~1 topic
- Language: Spanish
- Math formulas: always in LaTeX (`$inline$` / `$$block$$`), never plain text
  or unicode math symbols
