# CSV Changelog Theme

A minimal, document-focused changelog theme for micro.blog that treats your blog as a functional source of documents.

## Design Philosophy

This theme reimagines a blog as a tabulated changelog with two primary views:

- **Catalog View**: A spreadsheet-like listing of posts for browsing and discovery
- **Record View**: Individual post pages for content engagement

The design emphasizes:
- Functional document presentation over stylistic flourish
- Quick scanning and navigation
- Consistent left-alignment anchored to the blog title
- Minimal formatting that respects readability best practices

## Features

### Catalog View (Homepage, Tags, Collections)
- Tabulated three-column layout: timestamp | title | tag
- Timestamps link to time-based archives (week/month/year)
- Text-forward, tidy rows with single-line height
- Responsive mobile layout stacks timestamp above title+tag
- Ellipsis text clipping for long titles

### Record View (Individual Posts)
- Clean, readable single-column layout
- Metadata pushed to periphery
- Annotations section for external links, attachments, cross-references
- Collections section for tags and project associations
- Max-width content area for optimal reading

### Navigation
- Simple text navbar with blog title as home link
- Right-justified pill-shaped search bar that expands on focus
- Quick access to projects and collections (tags)
- Mobile-responsive with stacked layout

### Footer
- Single-row layout with title, links, social icons, copyright
- Consistent left alignment
- Minimal height (~50px)

## Installation

### For Micro.blog

1. Download or clone this theme
2. In Micro.blog, go to Design → Edit Custom Themes
3. Click "New Theme" and upload the theme files
4. Activate the theme from Design → Edit Custom Themes

### Manual Installation

If you're running Hugo locally:

```bash
cd your-site
git clone https://github.com/yourusername/csv-changelog-theme themes/csv-changelog
```

Then update your `config.toml`:

```toml
theme = "csv-changelog"
```

## Configuration

Add these parameters to your site's `config.toml`:

```toml
[params]
  description = "Your blog description"
  
  # Optional social links
  twitter = "yourusername"
  github = "yourusername"
  mastodon = "https://mastodon.social/@yourusername"
  
  # Enable MicroPub (for Micro.blog)
  MicroPub = true
```

## Post Front Matter

### Standard Posts

```yaml
---
title: "Your Post Title"
date: 2026-01-28T10:00:00-07:00
tags:
  - tag1
  - tag2
---
```

### Posts with Annotations

```yaml
---
title: "Post with External Resources"
date: 2026-01-28T10:00:00-07:00
tags:
  - research
external_links:
  - title: "Source Article"
    url: "https://example.com/article"
  - title: "Related Study"
    url: "https://example.com/study"
attachments:
  - "/uploads/document.pdf"
related_posts:
  - "/posts/previous-post/"
---
```

### Project Posts

```yaml
---
title: "Your Project"
date: 2026-01-28T10:00:00-07:00
type: project
status: active
project: project-name
tags:
  - tag1
---
```

## Customization

### Colors and Typography

Edit `/static/css/custom.css` and modify the CSS variables:

```css
:root {
  --text-primary: #1a1a1a;
  --text-secondary: #666;
  --link-color: #0066cc;
  --border-subtle: #e0e0e0;
  --bg-primary: #ffffff;
  --font-body: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
  --font-mono: "SF Mono", Monaco, "Cascadia Code", "Roboto Mono", Consolas, monospace;
}
```

### Layout Spacing

Adjust the spacing variables:

```css
:root {
  --max-width: 1200px;
  --left-anchor: 2rem;
  --spacing-unit: 1rem;
}
```

## Pages Structure

The theme expects the following page structure:

```
content/
├── posts/           # Regular blog posts
├── projects/        # Project pages
└── pages/           # Static pages (about, etc.)
```

## Menu Configuration

Add pages to the navbar in your `config.toml`:

```toml
[[menu.main]]
  name = "About"
  url = "/about/"
  weight = 1

[[menu.main]]
  name = "Now"
  url = "/now/"
  weight = 2
```

## Ethos Alignment

This theme was designed with these principles:

1. **Be weird and avoid masking**: The design is functional, not fashionable
2. **Stay grounded in real observations**: Document-focused structure reflects how we actually organize information
3. **Continually undermine artifices**: No styling for styling's sake; everything serves function

## Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile responsive
- Progressive enhancement approach

## Credits

Based on the Bear theme by Micro.blog, redesigned as a functional document changelog.

## License

MIT License - see LICENSE file
