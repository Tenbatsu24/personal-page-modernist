# Modernist — Personal Academic Website

A Jekyll-powered personal website template for researchers and academics. Built on the original [Modernist theme](https://github.com/orderedlist/modernist) with blog, projects, and CV sections.

## Features

- **Dark/Light mode** — toggle with the button in the top-right corner; preference persists in your browser
- **Blog** — write posts in Markdown; they appear on the blog index and in the "Latest News" section on the homepage
- **Projects** — showcase your research projects with thumbnails, tags, and links
- **CV download** — link your CV PDF for easy sharing
- **Responsive** — works on desktop, tablet, and mobile
- **Syntax highlighting** — code blocks are highlighted automatically
- **Zero build step** — GitHub Pages builds it automatically

## Getting Started

### 1. Customize your site

Edit `_config.yml` with your information:

```yaml
title: Your Name
email: you@yourdomain.edu
author:
  name: Your Name
  twitter: yourtwitterhandle
  github: yourgithubusername
  linkedin: yourlinkedinhandle
```

### 2. Add your profile photo

Place your profile image at `assets/images/profile.jpg`.

### 3. Add a CV

Place your CV PDF at `cv/cv.pdf`.

### 4. Write a blog post

Create a file in `_posts/` named `YYYY-MM-DD-title.md`:

```markdown
---
layout: post
title: "My Post Title"
date: 2024-01-15 12:00:00 -0000
categories: announcement
---

Your content here...
```

### 5. Add a project

Create a file in `_projects/` named `project-name.md`:

```markdown
---
layout: project
name: "Project Name"
description: "A brief description"
date: 2024-01-01
tags: [ml, research]
thumbnail: "project_thumb.jpg"
links:
  - label: "GitHub"
    url: "https://github.com/"
---

Project content here...
```

### 6. Deploy to GitHub Pages

1. Push this repository to GitHub
2. Go to **Settings → Pages**
3. Under **Source**, select **Deploy from a branch** and choose your branch (e.g., `main`)
4. Your site will be live at `https://<username>.github.io/<repo>/`

## Directory Structure

```
├── _config.yml          # Site configuration
├── _layouts/            # Page layouts (base, homepage, post, project, CV)
├── _sass/               # SCSS source (compiled to CSS by Jekyll)
├── _posts/              # Blog posts
├── _projects/           # Project pages
├── assets/              # CSS, JS, images
├── blog/                # Blog index page
├── cv/                  # CV page
├── projects/            # Projects index page
├── stylesheets/         # Syntax highlighting (github-light, pygment_trac)
└── index.html           # Homepage (uses default layout)
```

## Customization

- **Colors & theme**: Edit `assets/css/main.css` (or `_sass/main.scss` if you have a Sass compiler)
- **Layout**: Edit the files in `_layouts/`
- **Navigation**: Edit the nav section in `_layouts/base.html`

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 3.0 Unported License](http://creativecommons.org/licenses/by-sa/3.0/).
Original theme by [Takeru Miyato](https://takerum.github.io/).
