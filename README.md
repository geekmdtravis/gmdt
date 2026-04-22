# gmdt

Source for [geekmd.io](https://geekmd.io), the personal site of Travis
Nesbit, MD (GeekMD). Built with [Hugo](https://gohugo.io/) and the
[PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## Stack

- **Hugo** (extended, latest) — static site generator.
- **PaperMod** — theme, pinned at `themes/papermod` as a git submodule.
- **GitHub Pages** — hosting, with `geekmd.io` as the custom domain
  (see `static/CNAME`).
- **GitHub Actions** — `.github/workflows/hugo.yml` builds and deploys
  on every push to `main`.

## Local development

```bash
git clone --recurse-submodules https://github.com/geekmdtravis/gmdt.git
cd gmdt
npm start          # hugo server, live reload on http://localhost:1313
npm run build      # hugo --minify, output in ./public
```

If you cloned without `--recurse-submodules`, pull the theme with:

```bash
git submodule update --init --recursive
```

## Adding a post

Posts live in `content/posts/<slug>.md`. Use `archetypes/default.md`
as the frontmatter template, or:

```bash
hugo new content posts/my-post.md
```

Keep slugs lowercase and hyphen-separated; the date goes in the
frontmatter, not the filename. Set `draft: false` to publish.

## Layout

```
content/          # Markdown pages and posts
  about.md
  posts/
hugo.yaml         # site config, menus, PaperMod params
static/           # static assets served at site root (includes CNAME)
archetypes/       # frontmatter templates for `hugo new`
themes/papermod/  # theme submodule — do not edit
.github/workflows/hugo.yml
```

## Deploys

Pushing to `main` triggers the Actions workflow. `public/` is built by
CI and is gitignored; nothing in it should be committed. The custom
domain is read from `static/CNAME` on every deploy — removing that
file reverts the site to the default `*.github.io` cert and breaks
HTTPS for `geekmd.io`.
