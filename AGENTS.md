# Site guide (for people and AI agents)

Jekyll site on GitHub Pages, Minima 2.5 theme, served at meekflyer.net.

| To change… | Edit |
|---|---|
| Colors, fonts, spacing site-wide | Variables at top of `assets/main.scss` |
| Look of Projects + Posts lists | `.link-list` block in `assets/main.scss` |
| Add/edit a project | `_data/projects.yml` |
| Add a blog post | New file `_posts/YYYY-MM-DD-title.markdown` (lists update automatically) |
| Homepage text/sections | `index.markdown` |
| Header links (About, Contact) | `_includes/header.html` |
| Footer | `_includes/footer.html` |
| Contact form | `#contact` section in `index.markdown` (Formspree endpoint xqppowlr) |

Rules: prefer editing shared variables/classes over per-element styles; reuse `.link-list` for any new list of links.
Preview locally: `bundle exec jekyll serve --livereload` → http://localhost:4000
