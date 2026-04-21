# CLAUDE.md

Guidance for Claude Code sessions working in this repo.

## What this is

A Hugo static site published at **https://geekmd.io**, the personal site
of Travis Nesbit (online handle **GeekMD**). Theme: PaperMod, pinned as
a git submodule at `themes/papermod`.

## Deploy flow

- Pushing to `main` triggers `.github/workflows/hugo.yml`, which builds
  with `hugo --minify` (extended, latest) and deploys to GitHub Pages.
- The custom domain `geekmd.io` is configured in the repo's Pages
  settings. If a `CNAME` file is needed in `static/`, add it there —
  `public/` is ignored by git.
- Do not push directly to `main` from a Claude session unless the user
  asks. Default branch for Claude work is
  `claude/create-geekmd-website-7kDQK`.

## Authoring a blog post (the common case)

The user's main workflow is: chat with Claude, get a post drafted and
pushed. To add a post:

1. Create `content/posts/<kebab-case-slug>.md`.
2. Use this frontmatter (mirrors `archetypes/default.md`):

   ```yaml
   ---
   title: "Post Title In Title Case"
   date: "YYYY-MM-DDTHH:MM:SS-07:00"   # -07:00 = Pacific; adjust if needed
   lastmod: "YYYY-MM-DD"
   draft: false                         # set true to stage without publishing
   author: "Travis Nesbit"
   description: "One-sentence meta description for search/social."
   summary: "One- or two-sentence summary shown on the list page."
   tags: ["tag-one", "tag-two"]
   categories: ["Category Name"]
   ---
   ```

3. Write the body in standard Markdown. PaperMod supports fenced code
   blocks with language hints, a TOC (enabled by default), reading time,
   and share buttons.
4. Do **not** commit to `main`. Commit to the claude working branch,
   push with `git push -u origin <branch>`, and let the user merge when
   they're ready.

### Slug / filename conventions

- Lowercase, hyphen-separated, no dates in the filename (date lives in
  frontmatter).
- Keep it short; it becomes the URL path: `/posts/<slug>/`.

### Draft vs. published

- `draft: true` posts are excluded from the production build
  (`buildDrafts: false` in `hugo.yaml`).
- `draft: false` is fine to push directly — the user reviews via the
  preview deploy / merge, not via a draft flag.

## Local smoke test (optional but recommended before pushing)

If `hugo` is available in the session:

```bash
git submodule update --init --recursive   # only if themes/papermod is empty
hugo --minify                              # builds into ./public
```

A clean exit with no `ERROR` lines means the deploy will succeed. The
workflow uses `hugo-version: latest` extended, so feature parity is
expected.

## Files worth knowing

- `hugo.yaml` — site config. Branding, menus, social links, PaperMod
  params. Asset paths (`favicon`, `apple_touch_icon`, etc.) and
  analytics verification tags are intentionally commented out until
  real values exist — do not re-add placeholder strings, PaperMod
  emits them verbatim into `<link>` / `<meta>` tags.
- `content/about.md` — the /about page.
- `content/posts/` — blog posts.
- `archetypes/default.md` — frontmatter template used by
  `hugo new content posts/foo.md`.
- `.github/workflows/hugo.yml` — CI build + Pages deploy.
- `themes/papermod/` — submodule, do not edit.

## House style for posts

- Voice: first-person, conversational, technical where it matters.
- Prefer concrete examples and code blocks over abstract prose.
- Include a `summary` in frontmatter so the posts list isn't dominated
  by auto-truncated first paragraphs.
- Tag consistently — check existing posts for tag reuse before
  inventing new ones.

## Things to NOT do

- Don't re-introduce placeholder strings in `hugo.yaml` (they render
  into production meta tags).
- Don't edit files under `themes/papermod/` — it's an upstream
  submodule.
- Don't add analytics / verification tags without a real value from the
  user.
- Don't create `README.md` or other doc files unless asked.
