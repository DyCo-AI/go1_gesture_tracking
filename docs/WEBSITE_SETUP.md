# Website Setup

This repository is configured as a Jekyll site deployed by GitHub Actions.

## Local preview

The local website toolchain is isolated in the `go1-website` Conda
environment. It includes Ruby 3.3, Bundler, Jekyll, and the native build tools
required by the locked gems.

1. Run `conda activate go1-website`.
2. Run `bundle check` in the repository root.
3. Run `bundle exec jekyll serve --source docs`.
4. Visit `http://localhost:4000/go1_gesture_tracking/`.

After changing `Gemfile`, run `bundle install` inside the activated environment.

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
