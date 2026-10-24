# polareyes.ai

Product website for **Polareyes**, the sovereign control point for AI agents.

The site is fully static: no server, no database, no cookies and no analytics. Fonts are self-hosted, so the page makes no third-party requests.

## Layout

| Path | What it is |
| --- | --- |
| `index.html`, `fonts/`, `og.png`, `favicon.svg`, `robots.txt`, `sitemap.xml` | The deployable site, served from the repository root |
| `src/index.html` | Editable source of the page |
| `src/build.py` | Builds the root files from the source: self-hosts fonts, adds metadata, renders the social card |
| `brand/` | Logo as vector (`polareyes-logo.svg`) and the original image |
| `DEPLOY.md` | Hosting steps for Cloudflare Pages or AWS |

## Editing

Change `src/index.html`, then rebuild:

```bash
pip install playwright && python -m playwright install chromium
python src/build.py
```

Commit the regenerated root files together with the source change.

## Content rules

Claims on the site are limited to capabilities shown in the product. Roadmap items are labelled as such: journal-backed file rollback, and approval of new tools at first contact. Framework coverage is an illustrative example estate and a technical mapping, not certification.
