# Plan: Convert Modernist Theme to Jekyll Personal Website

## Context

The Modernist repository is a plain HTML/CSS template for a personal academic page. It has a broken build setup: `sass/styles.scss` uses the deprecated Compass framework, but the active CSS (`stylesheets/styles.css`) is hand-written and completely out of sync. The site is a single HTML file with no templating, no blog, no projects, and no CV section.

This plan converts it into a **Jekyll-based multi-page personal website** that deploys natively to GitHub Pages — zero build steps required, since GitHub Pages runs Jekyll automatically.

---

## What to Change

### Phase 1: Clean up and create directory structure

**Delete:**
- `sass/styles.scss` — Compass-based, deprecated, out of sync with active CSS
- `stylesheets/css.css` — unused Lato font-face declarations (active CSS uses JetBrains Mono)
- `config.rb` — Compass config, no longer needed

**Create directories:**
- `_layouts/` — Jekyll layout templates
- `_sass/` — SCSS source files (replaces `sass/`)
- `_posts/` — blog posts
- `_projects/` — project pages (Jekyll collection)
- `assets/css/` — compiled CSS output
- `assets/js/` — JavaScript
- `assets/images/` — images (profile, thumbnails, favicon)
- `cv/` — CV download directory

**Create files:**
- `_config.yml` — Jekyll configuration
- `.gitignore` — ignore `_site/`, `node_modules/`, etc.

### Phase 2: Jekyll configuration

**`_config.yml`** — Jekyll config for GitHub Pages:
- Site title, description, author, email
- Base URL and URL settings for GitHub Pages
- SCSS settings (Jekyll has native Sass/SCSS support)
- Collections configuration for projects
- Markdown parser (kramdown)
- Defaults for posts and projects

### Phase 3: CSS migration to SCSS

**Create `_sass/main.scss`:**
- Migrate the working `stylesheets/styles.css` into SCSS format
- Use SCSS variables (`$bg`, `$text`, etc.) instead of CSS custom properties for the base
- Keep CSS custom properties for runtime theme toggle
- Import syntax highlighting CSS files
- Proper `@import` chain

**Key improvements in the CSS:**
- Convert CSS variables to SCSS variables where appropriate
- Keep the two-column layout, publication cards, profile section
- Add hover animations, transitions
- Proper responsive breakpoints
- Add a theme toggle button (fixed position, top-right)

### Phase 4: Layout templates

**Create `_layouts/base.html`** — Base layout with:
- Meta tags (charset, viewport, theme-color, color-scheme)
- Open Graph + Twitter Card meta tags (with site-wide defaults)
- CSS imports (main.scss, github-light.css, pygment_trac.css)
- Favicon link
- Skip-to-content link
- Theme toggle button (JS-driven)
- Footer

**Create `_layouts/default.html`** — Homepage layout with:
- Profile section (name, photo, email with copy, links)
- Affiliation section
- Research interests
- Latest news (pulls from recent posts)
- Publications (static or data-driven)
- Education
- Experience
- Footer

**Create `_layouts/post.html`** — Blog post layout with:
- Post title, date, author
- Markdown content
- Back to home link
- Related posts sidebar

**Create `_layouts/project.html`** — Project page layout with:
- Project name, description
- Thumbnail image
- Links (code, paper, project page)
- Full content area

**Create `_layouts/cv.html`** — CV page layout with:
- Downloadable CV PDF link
- HTML version of CV (or embed)

### Phase 5: Homepage (`index.html`)

Convert the current `index.html` into a Jekyll page:
- Frontmatter with page title
- Use the `default` layout
- Profile section with placeholder content
- Links section (Google Scholar, GitHub, X, LinkedIn)
- Affiliation, research interests
- Latest news section (liquid loop over recent posts)
- Publications (static HTML or use a data file)
- Education, experience
- Footer

### Phase 6: Blog functionality

**Create `_posts/2024-01-01-sample-post.md`** — Sample blog post with:
- YAML frontmatter (title, date, category, summary)
- Markdown content

**Create `blog/index.html`** — Blog index page listing all posts:
- Loop through posts
- Show title, date, excerpt, read more link

### Phase 7: Projects section

**Create `_projects/sample-project.md`** — Sample project with:
- Frontmatter (name, description, date, tags, links)
- Markdown content

**Create `projects/index.html`** — Projects index page:
- Loop through projects collection
- Display as cards with thumbnails

### Phase 8: CV page

**Create `cv/index.html`** — CV page with:
- Download link for CV PDF
- HTML version of CV (or link to PDF)

### Phase 9: Theme toggle

**Create `assets/js/theme-toggle.js`:**
- Toggle button click handler
- Toggle `data-theme` attribute on `<html>`
- Store preference in `localStorage`
- Respect `prefers-color-scheme` on first visit

**Add to CSS:**
- Fixed position toggle button (top-right corner)
- Sun/moon icon using CSS or Unicode
- Smooth transition between themes

### Phase 10: Navigation

**Add to `base.html` header:**
- Navigation bar with links: Home, Blog, Projects, CV
- Active state styling
- Responsive: collapses to hamburger on mobile

### Phase 11: Final cleanup and documentation

- Update `README.md` with Jekyll setup instructions
- Add `404.html` for GitHub Pages
- Ensure all placeholder content is clearly marked
- Test with `jekyll build`
- Verify GitHub Pages compatibility

---

## Verification

1. Run `jekyll build` — should complete without errors
2. Open `_site/index.html` in browser — verify homepage renders correctly
3. Click through: Blog → Post, Projects → Project, CV page
4. Test theme toggle (light/dark) — should persist via localStorage
5. Test responsive layout at 1200px, 720px, 480px breakpoints
6. Verify syntax highlighting on code blocks
7. Verify email copy-to-clipboard still works
8. Deploy to GitHub Pages and verify live
