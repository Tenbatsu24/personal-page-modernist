# Modernist — Personal Academic Website

A Jekyll-powered personal website template for researchers and academics. Built on the original [Modernist theme](https://github.com/orderedlist/modernist) with blog, projects, publications, and CV sections.

## Features

- **Dark/Light mode** — toggle in the top-right corner; preference persists in the browser
- **Blog** — write posts in Markdown; they appear on the blog index and "Latest News" on the homepage
- **Projects & Publications** — unified content system with thumbnails, tags, and external links
- **Featured items** — highlight key work on the homepage with a "view all" link to the full list
- **Sorting** — order projects and publications with a `rank` field
- **CV download** — link your CV PDF for easy sharing
- **Responsive** — works on desktop, tablet, and mobile
- **Zero build step** — GitHub Pages builds it automatically

## Getting Started

### 1. Configure your site

Edit `_config.yml` with your information:

```yaml
title: "Your Name"
email: "you@university.edu"
description: >-
  Your research description here.
baseurl: ""          # Set to "/repo-name" for project pages; leave empty for <username>.github.io
url: ""              # Set to "https://yourusername.github.io" when deploying

author:
  name: "Your Name"
  email: "you@university.edu"
  image: "assets/images/profile.png"  # Your profile photo
  github: "yourusername"              # Comment out to hide
  # Add social links: scholar, twitter, bluesky, linkedin, mastodon, orcid, website, cv
```

> **`baseurl` vs `url`**: Leave both empty for a user site (`username.github.io`). Set `baseurl` to `"/repo-name"` for a project site (`username.github.io/repo-name`).

### 2. Add your profile photo

Place your profile image at `assets/images/profile.png`.

### 3. Configure your homepage

All homepage content lives in `_data/profile.yml` — edit this file to set up your affiliation, research interests, education, and experience. Do not edit `_layouts/default.html`.

> **Publications moved**: Publications are now managed alongside projects in `_projects/` (see below). Remove the `publications` section from `_data/profile.yml`.

### 4. Add a CV

Place your CV PDF at the path you reference in `_config.yml` (e.g. `assets/files/cv.pdf`).

### 5. Write a blog post

Create a file in `_posts/` named `YYYY-MM-DD-title.md`:

```yaml
---
layout: post
title: "My Post Title"
date: 2024-01-15 12:00:00 -0000
categories: announcement
---

Your content here...
```

### 6. Add a project or publication

All items live in `_projects/`. Use `categories` to distinguish between them:

**Project** (standalone):

```yaml
---
layout: project
name: "Project Name"
description: "A brief description"
date: 2024-01-01
categories: [project]
tags: [ml, research]
featured: true
rank: 1
thumbnail: "project_thumb.jpg"
links:
  - label: "GitHub"
    url: "https://github.com/"
---

Project content here...
```

**Publication** (appears on both homepage and projects page):

```yaml
---
layout: project
name: "Paper Title"
description: "What it's about"
date: 2024-01-01
categories: [project, publication]
tags: [machine-learning]
featured: true
rank: 1
thumbnail: "pub_thumb.jpg"
citation: |
  <b><i>[Title]</i></b><br>
  Author et al.<br>
  Conference Name, Year<br>
  [<a href="[pdf]">PDF</a>] [<a href="[code]">code</a>]
links:
  - label: "PDF"
    url: "https://example.com/paper.pdf"
  - label: "Code"
    url: "https://github.com/"
---

Detailed description of your work...
```

**Key fields**:
- `categories` — use `[project]` for standalone projects, `[project, publication]` for papers
- `featured` — set to `true` to show on the homepage
- `rank` — numeric field for sorting (higher = more prominent); items sort in descending order
- `thumbnail` — image path under `assets/images/project/`
- `links` — external links (GitHub, PDF, project page, etc.)
- `citation` — formatted citation string shown on the homepage (optional)

## Building Locally

```bash
jekyll serve
# → http://localhost:4000
```

No local build is required for deployment — GitHub handles it automatically.

## Deploy on GitHub Pages

This repo includes a GitHub Actions workflow (`.github/workflows/deploy.yml`) that builds and deploys automatically on push to `main`.

1. Push to GitHub: `git remote add origin git@github.com:<username>/<repo>.git && git push -u origin main`
2. Go to **Settings → Pages** in your repository
3. Under **Build and deployment**, set **Source** to **GitHub Actions**
4. Your site is live at `https://<username>.github.io`

## Directory Structure

```
_config.yml          # Site settings
_data/profile.yml    # Homepage content (affiliation, education, etc.)
_layouts/           # Page templates
_posts/             # Blog posts
_projects/          # Projects & publications (unified)
assets/             # CSS, JS, images
cv/index.html       # CV page
projects/           # Full listing page
```

## License

[Creative Commons Attribution-ShareAlike 3.0 Unported](http://creativecommons.org/licenses/by-sa/3.0/). Original theme by [Takeru Miyato](https://takerum.github.io/).
