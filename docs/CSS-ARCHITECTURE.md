# CSS Architecture - Unparalleled Scholar

## Overview
The project now uses a modular CSS architecture with separate stylesheets for each page, improving maintainability and performance.

## CSS File Structure

```
client/css/
├── index.css              # Global styles (existing)
├── ui-enhancements.css    # UI components (existing)
├── courses.css            # Courses listing page (existing)
├── home.css               # Homepage specific styles (NEW)
├── about.css              # About page styles (NEW)
├── blog.css               # Blog listing page styles (NEW)
├── blog-post.css          # Individual blog post styles (NEW)
└── course-detail.css      # Course detail page styles (NEW)
```

## File Descriptions

### 1. **home.css** (Homepage)
- Hero section animations
- FAQ accordion styles
- Pillar cards hover effects
- Testimonial card animations
- CTA section styling
- Stats counter animations

### 2. **about.css** (About Page)
- About hero section
- Stats grid layout
- Core values cards
- Timeline styles
- Hover effects for value cards

### 3. **blog.css** (Blog Listing)
- Blog hero section
- Category filter buttons
- Blog card grid layout
- Featured post styling
- Pagination controls
- Newsletter section

### 4. **blog-post.css** (Individual Blog Post)
- Typography (prose styles)
- Reading progress bar
- Share buttons
- Author bio section
- Related posts grid
- Code block styling
- Table of contents

### 5. **course-detail.css** (Course Detail)
- Course hero section
- Curriculum accordion
- Sticky sidebar
- Instructor card
- Rating stars
- Enrollment button
- Progress bars
- Tab navigation

## How to Use

### Homepage (index.html)
```html
<link rel="stylesheet" href="../client/css/index.css">
<link rel="stylesheet" href="../client/css/ui-enhancements.css">
<link rel="stylesheet" href="../client/css/home.css">
```

### About Page (pages/about.html)
```html
<link rel="stylesheet" href="../../client/css/index.css">
<link rel="stylesheet" href="../../client/css/ui-enhancements.css">
<link rel="stylesheet" href="../../client/css/about.css">
```

### Blog Page (pages/blog.html)
```html
<link rel="stylesheet" href="../../client/css/index.css">
<link rel="stylesheet" href="../../client/css/ui-enhancements.css">
<link rel="stylesheet" href="../../client/css/blog.css">
```

### Blog Post (pages/blog-post.html)
```html
<link rel="stylesheet" href="../../client/css/index.css">
<link rel="stylesheet" href="../../client/css/ui-enhancements.css">
<link rel="stylesheet" href="../../client/css/blog-post.css">
```

### Course Detail (pages/course-detail.html)
```html
<link rel="stylesheet" href="../../client/css/index.css">
<link rel="stylesheet" href="../../client/css/ui-enhancements.css">
<link rel="stylesheet" href="../../client/css/course-detail.css">
```

### Courses Listing (pages/courses.html)
```html
<link rel="stylesheet" href="../../client/css/courses.css">
```

## Benefits

✅ **Modularity** - Each page has its own stylesheet
✅ **Performance** - Only load CSS needed for each page
✅ **Maintainability** - Easy to find and update styles
✅ **Scalability** - Add new pages without affecting existing ones
✅ **Organization** - Clear separation of concerns
✅ **Debugging** - Easier to identify style conflicts

## Common Styles

All pages share:
- `index.css` - Global typography, colors, utilities
- `ui-enhancements.css` - Reusable UI components (buttons, cards, etc.)

## Responsive Design

All CSS files include responsive breakpoints:
- Mobile: < 768px
- Tablet: 768px - 1024px
- Desktop: > 1024px

## Animation Classes

Common animations available across all pages:
- `.fade-in-up` - Fade in from bottom
- `.slide-in-left` - Slide in from left
- `.scale-up` - Scale up on hover
- `.bounce` - Bounce effect

## Color Palette

Primary colors used across all stylesheets:
- **Indigo**: #4f46e5 (Primary brand color)
- **Purple**: #7c3aed (Secondary brand color)
- **Teal**: #14b8a6 (Accent color)
- **Gray**: #64748b (Text color)

## Next Steps

To update the HTML files to use these new CSS files:
1. Update `<link>` tags in each HTML file
2. Remove inline `<style>` blocks
3. Test each page for styling consistency
4. Optimize CSS by removing unused styles

## Maintenance

When adding new features:
1. Add styles to the appropriate page-specific CSS file
2. If styles are reusable, add to `ui-enhancements.css`
3. Keep global styles in `index.css`
4. Document any new classes or components

---

**Built with ❤️ by Srijan Kumar | Srijanxi Technologies**
