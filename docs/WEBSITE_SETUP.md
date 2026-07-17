# Website Setup

This repository is configured as a Jekyll site deployed by GitHub Actions.

## Local preview

1. Install Ruby 3.2 and Bundler.
2. Run `bundle install` in the repository root.
3. Run `bundle exec jekyll serve --source docs`.
4. Visit `http://localhost:4000/go1_gesture_tracking/`.

## GitHub Pages

In the repository's **Settings → Pages** menu, select **GitHub Actions** as the
source. The workflow in `.github/workflows/pages.yml` builds and deploys the site
after each push to `main`.

## Editing content

- Site identity and URLs: `docs/_config.yml`
- Main navigation: `docs/_data/nav.yml`
- Home page: `docs/index.md`
- Project pages: the Markdown files under `docs/`
- Images: `docs/_images/`
- Clemson theme styles: `docs/_sass/` and `docs/_css/main.scss`
