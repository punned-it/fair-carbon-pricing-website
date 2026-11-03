# fair-carbon-pricing-website

Quartz/Obsidian website for [faircarbonpricing.org](https://faircarbonpricing.org).

Every push to `main` rebuilds and publishes the site automatically (see `.github/workflows/deploy.yml`).

## Where things go

```
content/
  index.md      homepage
  articles/     long-form articles
  terms/        short definitions, one file per term
  figures/      images and diagrams (PNG, JPG, SVG)
  templates/    starting points for new pages (not published)
```

Everything else in the repo is Quartz itself. You rarely need to touch it, except `quartz.config.yaml` for site settings (title, colours, fonts, features).

## Writing

### Set up Obsidian (once)

1. Install [Obsidian](https://obsidian.md) and clone this repo to your computer (GitHub Desktop is the easiest way).
2. In Obsidian, choose **Open folder as vault** and pick the repo's `content` folder.
3. **Settings → Files and links**:
   - *Default location for new notes*: **In the folder specified below** → `terms`
   - *New link format*: **Shortest path when possible**
   - *Use [[Wikilinks]]*: on
   - *Default location for new attachments*: **In the folder specified below** → `figures`
4. **Settings → Core plugins**: turn on **Templates**, then in its settings set the template folder to `templates`.

### Day to day

- **Link a term:** type `[[Term name]]`. Clicking a link to a page that doesn't exist yet creates it in `terms/`; use **Insert template → Term** to fill in the skeleton.
- **New article:** create a note in `articles/` and insert the **Article** template.
- **Drafts:** pages with `draft: true` in their frontmatter are not published. Change it to `false` when ready.
- **Alternative names:** add them under `aliases:` so `[[carbon prices]]` and `[[Carbon price]]` reach the same page.
- **Figures:** drag an image into the note; it lands in `figures/` and is embedded as `![[name.png]]`.
- **Diagrams:** write a ```` ```mermaid ```` code block. See the example article.
- **Google Sheets:** use the snippet in `templates/Article.md` (embed plus "Make a copy" link). The sheet must be shared as *Anyone with the link → Viewer* and published to the web.

### Publishing

Commit and push your changes (GitHub Desktop, or the Obsidian Git plugin). The site updates a minute or two later. Progress is visible on the repo's **Actions** tab.

## Previewing locally (optional)

Requires Node.js 22 or later.

```bash
npm ci
npx quartz plugin install --from-config
npx quartz build --serve
```

Then open http://localhost:8080.
