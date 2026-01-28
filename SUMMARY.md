# CSV Changelog Theme - Implementation Summary

## What You're Getting

A complete micro.blog theme that transforms your blog into a functional document archive with a tabulated changelog aesthetic. This design aligns with your ethos of avoiding artifice and staying grounded in function.

## Core Components Delivered

### 1. Stylesheet (`static/css/custom.css`)
- **Catalog styling**: Three-column tabulated layout for browsing posts
- **Record styling**: Clean single-post view optimized for reading
- **Navbar**: Simple text-based navigation with expanding search
- **Footer**: Minimalist single-row footer
- **Responsive**: Mobile-first with intelligent stacking
- **Variables**: Easy customization via CSS custom properties

### 2. Base Template (`layouts/_default/baseof.html`)
- HTML structure and head meta tags
- Navbar with blog title, menu links, and search bar
- Footer with links, social icons, copyright
- Simple client-side search functionality

### 3. Homepage (`layouts/index.html`)
- Catalog view of recent posts
- Three columns: timestamp | title | tag
- Interactive timestamp links to week/month/year archives
- Pagination support

### 4. Single Post Template (`layouts/_default/single.html`)
- Record view for individual posts
- Timestamp and title header
- Content area with max-width for readability
- Optional annotations section (external links, attachments)
- Optional collections section (project + tags)

### 5. Collections Browser (`layouts/tags/terms.html`)
- Alphabetical list of all tags
- Post counts per tag
- Clean, scannable layout

### 6. Tag Pages (`layouts/tags/taxonomy.html`)
- Catalog view filtered by tag
- Same three-column layout as homepage
- Page header with tag name and count

### 7. Projects Browser (`layouts/section/projects.html`)
- Catalog view of project pages
- Special handling for posts with `type: project`
- Status indicator in third column

### 8. Documentation
- **README.md**: Complete theme documentation
- **IMPLEMENTATION.md**: Quick start guide and practical tips
- **theme.toml**: Theme metadata and configuration

## Key Design Decisions

### Catalog as Discovery Tool
The catalog view (homepage, tag pages, project pages) is optimized for scanning and navigation, not content consumption. Each row is a single line that provides just enough information to decide whether to click through.

### Record as Content Arena  
The record view (individual posts) pushes metadata to the periphery and centers the content. This is where readers engage with your writing, watch videos, view images.

### Interactive Timestamps
Timestamps aren't just decoration—they're navigation tools. Each component (day, month, year) links to time-based archives, turning temporal metadata into discovery paths.

### Minimal Formatting Philosophy
No unnecessary bold text, no excessive headers, no bullet points unless essential. Text flows naturally in paragraphs. This respects your directive to "avoid engineering a persona" and keep things "simple and functional."

### Consistent Left Anchoring
Everything aligns to the same left margin as your blog title, creating a strong vertical rhythm and making the interface feel anchored and stable.

### Annotations & Collections
These sections only appear when relevant, keeping the interface clean. They present metadata as plain text, comma-separated lists—reinforcing the "documents in a database" metaphor.

## How It Maps to Your Content Channels

This theme serves as your **primary content source** (csv.micro.blog), while integrating with your other channels:

- **Newstate website**: Link from navbar or footer for commercialization
- **Notion profile**: Link templates from project pages or posts
- **Gumroad**: Reference products in post annotations
- **YouTube**: Embed videos directly in posts, or link channel from navbar

## Alignment with Your Ethos

### "Be weird and avoid masking"
The tabulated changelog aesthetic is unusual for a blog—it's more database than magazine. But it's weird in service of function, not style theater.

### "Stay grounded in real observations"
This design treats your blog like what it actually is: a chronological database of documents. The catalog/record metaphor makes this explicit.

### "Continually undermine artifices"
No hero images, no fancy animations, no "brand identity." Just clean typography, functional layout, and direct access to content. The theme itself is almost invisible—as it should be.

## Implementation Path

### Option 1: Full Theme Install (Recommended)
Upload all files to micro.blog as a custom theme. This gives you complete control.

### Option 2: CSS-Only Start
Just add the custom CSS to your existing Bear theme as a test. You'll get the visual design without changing templates.

### Option 3: Gradual Migration  
Start with CSS, then switch templates one at a time (homepage first, then singles, then tags).

## What to Customize

Likely candidates for adjustment:
- **Colors**: All in CSS variables at top of stylesheet
- **Spacing**: Adjust `--spacing-unit` and `--left-anchor`
- **Max width**: Change `--max-width` if you want wider/narrower
- **Timestamp format**: Modify the date formatting in templates
- **Column proportions**: Adjust grid template columns in `.catalog-row`

## Front Matter Structure

The theme expects posts with this structure:

```yaml
---
title: "Your Title"
date: 2026-01-28T14:30:00-07:00
tags:
  - tag1
  - tag2
project: project-name  # optional
external_links:        # optional
  - title: "Link Title"
    url: "https://..."
attachments:           # optional
  - "/uploads/file.pdf"
related_posts:         # optional
  - "/posts/other-post/"
---
```

## Mobile Responsive Behavior

On screens under 768px wide:
- Navbar stacks vertically
- Search bar goes full width
- Catalog rows become two-row grid:
  - Row 1: Full-width timestamp
  - Row 2: Title (left, clips) + Tag (right)
- Footer stacks into single column

## Browser Compatibility

Built with modern CSS (Grid, CSS variables) but degrades gracefully:
- Chrome/Edge: Full support
- Firefox: Full support  
- Safari: Full support
- Mobile browsers: Full support

## File Structure

```
csv-changelog-theme/
├── layouts/
│   ├── _default/
│   │   ├── baseof.html      # Base template with navbar/footer
│   │   └── single.html      # Individual post record view
│   ├── index.html           # Homepage catalog view
│   ├── section/
│   │   └── projects.html    # Projects browser
│   └── tags/
│       ├── terms.html       # All tags (collections browser)
│       └── taxonomy.html    # Individual tag pages
├── static/
│   └── css/
│       └── custom.css       # All styles
├── IMPLEMENTATION.md        # Quick start guide
├── README.md               # Full documentation
└── theme.toml              # Theme configuration
```

## Next Steps

1. Review the files and adjust any colors/spacing to your taste
2. Choose your implementation path (full theme, CSS-only, or gradual)
3. Create 2-3 test posts with different front matter configurations
4. Check responsive behavior on mobile
5. Start writing

## Philosophy in Practice

This theme embodies your statement: "websites are stacks of documents arranged for discovery and reference."

- **Discovery** = Catalog view with scannable rows
- **Reference** = Record view with readable content
- **Documents** = Individual posts, properly formatted
- **Stacks** = Chronological ordering, time-based archives
- **Arranged** = Navigation via timestamps, tags, projects

The whole interface serves these functions without pretense. It's a tool for organizing meaning-making, not a performance of web design.

---

## Technical Notes

- Built on Hugo templating (micro.blog's static site generator)
- Uses CommonMark for markdown rendering
- CSS Grid for layouts (no framework dependencies)
- Progressive enhancement approach
- Semantic HTML throughout
- ARIA labels on icons for accessibility

## License

MIT License - use, modify, share freely.
