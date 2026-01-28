# Quick Implementation Guide

## Immediate Steps

1. **Upload Custom CSS**
   - Go to Micro.blog → Design → Edit CSS
   - Copy and paste the contents of `static/css/custom.css`
   - Save changes

2. **Update Your Theme Templates**
   
   Since you're using the Bear theme, you can customize it by:
   
   - Design → Edit Custom Templates
   - Create custom versions of:
     - `baseof.html` (navbar + footer)
     - `index.html` (homepage catalog)
     - `single.html` (post records)
     - `tags/terms.html` (collections browser)
     - `tags/taxonomy.html` (tag pages)

## Post Front Matter Examples

### Simple Blog Post

```yaml
---
title: "Reflections on meaning-making systems"
date: 2026-01-28T14:30:00-07:00
tags:
  - consciousness
  - philosophy
---

Your content here...
```

### Post with External Links and Annotations

```yaml
---
title: "Research on emergent complexity"
date: 2026-01-28T14:30:00-07:00
tags:
  - systems complexity
  - research
external_links:
  - title: "Source Paper"
    url: "https://arxiv.org/example"
  - title: "Related Discussion"
    url: "https://example.com/discussion"
---

Your content here...
```

### Project Post

```yaml
---
title: "CSV Micro.blog Theme"
date: 2026-01-28T14:30:00-07:00
type: project
status: active
project: csv-theme
tags:
  - web design
  - tools
---

Your project description...
```

## Hybrid Approach (If Full Theme Switch Is Too Much)

If you want to test this gradually:

1. **Start with CSS only**: Add the custom CSS to your current Bear theme
2. **Test on a few posts**: Add the new front matter fields to a few posts
3. **Gradually adopt templates**: Switch templates one at a time
4. **Iterate**: Adjust based on what feels right

## Timestamp Link Behavior

The catalog view timestamps are interactive:

- Click **Mon** → Shows that week's posts
- Click **Jan** → Shows that month's posts  
- Click **02 2026** → Shows that year's posts
- Time (15:04) → Non-clickable, just for reference

## Collections vs Tags

- **Tags** = Your existing micro.blog tags
- **Collections** = The tag browser page
- **Projects** = Special posts with `type: project`

## Mobile View Changes

On mobile devices:
- Timestamp moves to its own row above title
- Title and tag share a row
- Tag stays right-aligned
- Title clips with margin

## Customization Tips

### Want wider content?
Change `--max-width: 1200px;` to your preference

### Want tighter spacing?
Reduce `--spacing-unit: 1rem;` to `0.75rem`

### Want different fonts?
Update `--font-body` and `--font-mono` variables

### Want different colors?
All colors are in CSS variables at the top of custom.css

## Content Strategy

Given your range of disciplines, consider:

- **Consciousness** posts → tag: consciousness
- **Economics** posts → tag: economics  
- **Poetry** work → tag: poetry
- **Systems** thinking → tag: systems complexity

Create project pages for:
- Long-term research threads
- Book/writing projects
- Tool development
- Course/teaching materials

## Integration with Your Channels

- **csv.micro.blog** → Primary content source (this theme!)
- **newstate website** → Link from footer or navbar
- **notion profile** → Link from projects page
- **gumroad** → Link templates from relevant posts
- **youtube** → Embed videos in posts, link from navbar

## Next Actions

1. Review the CSS and adjust colors/spacing to taste
2. Create 2-3 test posts with different front matter
3. View on mobile to ensure responsive design works
4. Adjust catalog column widths if needed
5. Start writing!

## Philosophy Alignment

Remember: "Websites are stacks of documents arranged for discovery and reference"

This theme embodies that by:
- Making discovery easy (catalog view)
- Making reference accessible (record view)
- Avoiding style theater (functional design)
- Staying grounded (plain text, simple structure)
