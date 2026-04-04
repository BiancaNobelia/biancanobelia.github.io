# biancanobelia.github.io

Personal portfolio website for **Bianca Surya Nobelia** — Mechanical & Robotics Engineer.  
Built with Jekyll and hosted on GitHub Pages.

🌐 **Live site:** [biancanobelia.github.io](https://biancanobelia.github.io)

---

## 🚀 Local Development

1. Install dependencies:
   ```bash
   bundle install
   ```

2. Run the development server:
   ```bash
   bundle exec jekyll serve
   ```

3. Visit `http://localhost:4000` in your browser

---

## 📁 Project Structure

```
.
├── _config.yml          # Jekyll configuration
├── _layouts/            # Page layouts
│   ├── default.html     # Base layout (navbar & footer)
│   ├── page.html        # Regular pages
│   └── project.html     # Project detail pages (gallery, lightbox, video)
├── _includes/           # Reusable components
│   └── navbar.html      # Navigation menu
├── _projects/           # Project collection (.md files)
├── assets/
│   └── css/
│       └── style.css    # Main stylesheet
├── pictures/            # Project images
├── index.md             # Home page
├── projects.md          # Projects listing page
├── achievements.md      # Achievements & awards page
├── resume.md            # Resume page
└── contact.md           # Contact page
```

---

## 📝 Adding a New Project

Create a new `.md` file in `_projects/`:

```yaml
---
title: Project Title
description: Short description for the project card
cover_image: /pictures/your-image.png
tags: [Tag1, Tag2, Tag3]
featured: true            # show on homepage
project_type: full-time   # full-time | internship | research
demo_url: https://...     # optional video demo link
repo_url:                 # optional GitHub link
date: 2024-01-01
gallery:
  - image: /pictures/img1.png
    caption: Caption here
---

## Project Overview
Write your content here...
```

### Front Matter Reference

| Field | Description |
|-------|-------------|
| `title` | Project name |
| `description` | Short description shown on card |
| `cover_image` | Path to cover image in `/pictures/` |
| `tags` | Array of technology tags |
| `featured` | `true` to show on homepage |
| `project_type` | `full-time`, `internship`, or `research` |
| `demo_url` | Video demo link (Google Drive `/preview`) |
| `repo_url` | GitHub repository link |
| `gallery` | Array of `{image, caption}` for the gallery grid |
| `date` | Project date for sorting |

---

## 🔧 Troubleshooting

**Port already in use:**
```bash
bundle exec jekyll serve --port 4001
```

**Changes not showing:**  
Hard refresh with `Ctrl + Shift + R`
