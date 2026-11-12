# Personal website: vsella.com

Following are notes to self.

Personal academic website, built on the [al-folio](https://github.com/alshedivat/al-folio) Jekyll theme.
Local preview: `docker compose up` → http://localhost:8080. Pushing to `main` deploys.

## Where things live

| To add…             | Edit                              | Shows up on                                     |
| ------------------- | --------------------------------- | ----------------------------------------------- |
| Paper / preprint    | `_bibliography/papers.bib`        | /publications/ (and home page if `selected`)    |
| Paper on the PDF CV | `_data/cv.yml` (`publications:`)  | /cv/ (separate from papers.bib)                 |
| News item           | `_news/<anything>.md`             | home page "news"                                |
| Blog post           | `_posts/YYYY-MM-DD-slug.md`       | /blog/ and home page "latest posts"             |
| Project / demo page | `_projects/slug.md`               | /projects/                                      |
| Paper thumbnail     | `assets/img/publication_preview/` | referenced by `preview = {file.png}` in the bib |

## Adding a paper

Copy this into `_bibliography/papers.bib` and fill it in. Only `title`, `author`, `year`, and a venue are required.
Every link field (`pdf`, `arxiv`, `doi`, `html`, `code`, `demo`, `slides`, `poster`, `blog`) is optional
and turns into a button when present, so you can add links one line at a time as they become available.

```bibtex
@inproceedings{sella2027shortname,
  abbr        = {AIAA},
  bibtex_show = {true},
  title       = {Paper Title},
  author      = {Sella, Vignesh and Coauthor, First},
  booktitle   = {AIAA SciTech 2027 Forum},
  year        = {2027},
  note        = {Preprint, submitted.},
  pdf         = {https://www.researchgate.net/publication/...},
  preview     = {figure.png},
  abstract    = {...},
  selected    = {true}
}
```

**Typical preprint → published lifecycle (one-line edits each time):**

1. **Submitted:** entry as above, with `note = {Preprint, submitted.}` and the ResearchGate link in `pdf`.
2. **arXiv approved:** add `arxiv = {2611.01234},`. That adds an arXiv button. You can point `pdf` at `https://arxiv.org/pdf/2611.01234` instead of ResearchGate.
3. **Published:** add `doi = {10.2514/6.2027-XXXX},` and `html = {https://arc.aiaa.org/doi/...},`, then delete the `note` line.

Notes:

- Use `@article` with `journal = {...}` for journals, and `@inproceedings` with `booktitle = {...}` for conferences.
- `year` controls which year heading the entry appears under.
- Your name is bolded automatically (from `scholar.last_name`/`first_name` in `_config.yml`).
- Only the first 3 authors are shown until the reader clicks "more authors".
- `selected = {true}` puts the paper on the home page.
- `demo = {/projects/slug/}` (or any full URL) adds a Demo button.

## Adding a blog post

```markdown
---
layout: post
title: Post title
date: 2026-11-12
description: One-line summary shown in the list.
tags: [machine-learning]
related_publications: true # optional: enables {% cite key %} and a references list
---

Text, with $$math$$, images via {% include figure.liquid path="assets/img/x.png" %}, etc.
```

## Adding an interactive demo

Recommended structure: **one project page per demo**, linked from its paper.

1. Put the demo itself in its own folder as plain HTML/JS: `assets/demos/<name>/index.html` (plus any JS/CSS/data files).
   It can use any library (Plotly, D3, three.js, Pyodide, …) without affecting the rest of the site.
2. Create `_projects/<name>.md`:

   ```markdown
   ---
   layout: page
   title: Demo title
   description: One line for the project card.
   img: assets/img/publication_preview/figure.png
   category: research
   importance: 1
   related_publications: true
   ---

   Short explanation of what the demo shows and how to use it.

   {% include demo.liquid path="assets/demos/<name>/index.html" height="650px" %}

   Based on {% cite bibkey %}.
   ```

3. Add `demo = {/projects/<name>/},` to the paper's bib entry so it gets a Demo button.

For lighter-weight charts inside a post, al-folio can load libraries per page via front matter
(e.g. `chart: { plotly: true }` or `chart: { echarts: true }`); see the comments in `_config.yml`.
