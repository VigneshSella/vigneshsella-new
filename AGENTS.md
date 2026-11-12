# Agent Guidelines

Personal academic website built from the [al-folio](https://github.com/alshedivat/al-folio) Jekyll theme, served at https://www.vsella.com.

## Local development (Docker)

```bash
docker compose pull && docker compose up   # site at http://localhost:8080
docker compose up --build                  # rebuild after changing deps/Dockerfile
docker compose down
```

## Before every commit

1. Format: `npx prettier . --write` (first time: `npm install --save-dev prettier @shopify/prettier-plugin-liquid`)
2. Build locally and check http://localhost:8080 (navigation, pages, images, dark mode).

## Notes

- `_config.yml`: `url: https://www.vsella.com`, `baseurl:` empty. Quote YAML strings containing special characters.
- The /cv/ page is rendered from `_data/cv.yml`. The downloadable CV PDF is maintained separately on Google Drive (`cv_pdf` in `_data/socials.yml` and `_pages/cv.md`).
- Google Scholar citations are updated by `.github/workflows/update-citations.yml`.
- Commit conventions: see [.github/GIT_WORKFLOW.md](.github/GIT_WORKFLOW.md).
