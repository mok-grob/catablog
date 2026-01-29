# Layout Customization Guide

## Easy-to-Modify Variables

All the key layout dimensions are controlled by CSS variables at the top of `custom.css`. Just change these numbers:

```css
:root {
  /* LAYOUT - MODIFY THESE */
  --content-max-width: 950px;      /* Max width of content area */
  --content-margin: 120px;         /* Left/right margins (desktop) */
  
  /* SEARCH BAR SIZING */
  --search-width-default: 200px;   /* Normal search bar width */
  --search-width-min: 140px;       /* Minimum search bar width */
  
  /* SPACING */
  --spacing-unit: 1rem;            /* Base spacing unit (16px) */
}
```

## How the Layout Works

### Three Containers:
1. **Navbar** (header.navbar) - Full page width
2. **Canvas** (main) - Full page width  
3. **Footer** (footer) - Full page width

### Each Contains Centered Content:
- **navbar-content** - Centered, max 950px
- **container** - Centered, max 950px
- **footer-content** - Centered, max 950px

### The Math:
```
Page max width = content-max-width + (content-margin × 2)
                = 950px + (120px × 2)
                = 1190px
```

## Visual Structure

```
┌─────────────────────────────────────────────┐
│ NAVBAR (full width, padding: 120px)        │
│ ┌─────────────────────────────────────┐    │
│ │ navbar-content (max 950px, centered)│    │
│ │ [title] [links...] [........search] │    │
│ └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
┌─────────────────────────────────────────────┐
│ CANVAS (full width, padding: 120px)        │
│ ┌─────────────────────────────────────┐    │
│ │ container (max 950px, centered)     │    │
│ │ [content goes here]                 │    │
│ └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
┌─────────────────────────────────────────────┐
│ FOOTER (full width, padding: 120px)        │
│ ┌─────────────────────────────────────┐    │
│ │ footer-content (max 950px, centered)│    │
│ │ [title - links] [social © ]         │    │
│ └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
```

## Responsive Behavior

The margins automatically adjust at breakpoints:

### Desktop (1190px+)
```css
--content-margin: 120px;  /* Full margins */
```

### Large tablet (951px - 1189px)
```css
--content-margin: 60px;   /* Reduced margins */
```

### Tablet (750px - 950px)
```css
--content-margin: 40px;   /* Smaller margins */
```

### Mobile (749px and below)
```css
--content-margin: 20px;   /* Minimal margins */
```

Plus at 749px:
- Blog title centers
- Nav links center below
- Search bar goes full width
- Catalog rows stack
- Footer stacks vertically

## Common Adjustments

### Want wider content area?
```css
--content-max-width: 1100px;  /* Instead of 950px */
```

### Want tighter margins?
```css
--content-margin: 80px;  /* Instead of 120px */
```

### Want more breathing room?
```css
--spacing-unit: 1.25rem;  /* Instead of 1rem */
```

### Want larger search bar?
```css
--search-width-default: 250px;  /* Instead of 200px */
```

## Key Alignment Principles

1. **Everything left-aligns** to the left edge of the content container
2. **Search bar right-aligns** to the right edge of the content container
3. **Content max-width** limits text wrapping for readability
4. **Margins are consistent** across navbar, canvas, and footer
5. **Mobile stacks center** while maintaining structure

## Testing Widths

To see the layout at different sizes:
- 1200px+ - Full desktop with maximum margins
- 1100px - Desktop with reduced margins
- 900px - Tablet with smaller margins  
- 700px - Mobile layout kicks in
- 375px - Narrow mobile

All adjustments cascade properly from the CSS variables.
