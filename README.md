# wongmanchun.github.io

## Overview

Static portfolio site for WONG Man Chun showcasing technical projects, professional experience, leadership roles, and certifications. The site emphasizes data analytics, optimization, and supply chain engineering projects crafted during undergraduate studies.

## What changed recently

- Standardized project pages to a consistent structure: Problem → Approach → Tech stack → Results → Impact.
- Synchronized project tag ribbons on the homepage with each detailed project page for clearer recruiter context.
- Added shared `.project-tag` styling in `styles.css` and improved CTAs on the homepage.

## Key Files

- `index.html` — homepage with project previews and interactive experience panels
- `styles.css` — shared stylesheet for pages
- `project-*.html` — detailed project pages
- `resume.pdf` — downloadable resume linked from the site

## Tech Stack

- HTML5, CSS3
- Vanilla JavaScript for small interactive components
- Google Fonts (Inter)

## How to run locally

Open `index.html` directly in your browser, or run a minimal server in the repository root:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

## Deployment

The site is static — deploy on GitHub Pages, Netlify, or any static host. For GitHub Pages, push this repo to a GitHub account and enable Pages in repository settings (branch: `main` or `gh-pages`).

## Contributing

Small content or styling fixes are welcome. Suggested workflow:

1. Fork the repository
2. Create a feature branch
3. Make edits and test locally
4. Open a pull request with a clear summary of changes

If you want me to add screenshots, GitHub repo links on each project page, or a custom domain setup guide, request the step and I’ll scaffold it.

## Suggested next steps

- Add project screenshots (`/assets/screenshots/`) and reference them from project cards to improve visual storytelling.
- Add a `projects.json` manifest if you plan to programmatically build project lists or migrate to a static site generator.

## Contact

Email: matthew20041120@gmail.com
LinkedIn: https://linkedin.com/in/matthew-wmc

---
_Generated edits: synchronized tags and standardized project pages on May 16, 2026._

