# Sattva Nation — AI Context

## Architecture
Static HTML site. No build step, no framework. Each page is a self-contained HTML file with inline CSS and vanilla JS.

```
Sattva/
├── index.html                 # Homepage (hero carousel, about, programmes preview, gallery, mentors, contact)
├── ai-content.md              # This file
├── about-us/
│   └── index.html             # Story, 8 dimensions, philosophy, values
├── programmes/
│   └── index.html             # 8 wellness dimensions with sticky tab nav
├── events/
│   └── index.html             # Upcoming events, past events, categories, newsletter
├── contact-us/
│   └── index.html             # Contact info cards, form, FAQ, map placeholder
├── founders/
│   └── index.html             # Vision, founder profiles, timeline, core team
├── blog/
│   └── index.html             # Wellness blog with featured post, grid, trending sidebar
├── gallery/
│   └── index.html            # Photo gallery with bento layout + lightbox, video section
└── assets/
    ├── sattvalogo.jpeg
    ├── sattvalogo12.png
    └── sattvalogo123.png
```

## Design System
- **Colors**: `--pink-deep: #c2185b`, `--pink-mid: #d4537e`, `--pink-soft: #f06292`, `--pink-light: #fce4ec`, `--pink-pale: #fdf0f5`, `--text-dark: #2d1a24`, `--text-mid: #6b3a50`, `--text-muted: #a06080`
- **Fonts**: Playfair Display (serif headings), DM Sans (sans body)
- **Patterns**: Glassmorphism nav (`backdrop-filter: blur(12px)`), gradient overlays, rounded corners (12px–50px), card hover lifts, bento grids, scroll-reveal animations

## Shared Patterns
- **Nav**: Fixed top, logo left, links right, CTA button. `active-page` class for current page highlight.
- **Page Hero**: `min-height: 52vh`, background image, gradient overlay, eyebrow label, breadcrumb.
- **Scroll Reveal**: `.reveal` class + IntersectionObserver (`threshold: 0.1`) toggles `.visible`.
- **Footer**: Dark background, logo, 5 links, copyright.
- **CTA Banner**: Pink background, decorative circles, heading + buttons.

## Changes This Session
- Created `events/index.html` — upcoming events grid, past events gallery, categories, newsletter
- Created `contact-us/index.html` — info cards, contact form, FAQ, map placeholder
- Created `founders/index.html` — vision quote, 2 founder profiles, journey timeline, values strip, core team
- Created `blog/index.html` — wellness blog with featured post, 6-post grid, trending sidebar widget, newsletter
- Created `gallery/index.html` — bento-grid photo gallery with lightbox, filter bar, video section
- Updated all internal links across all pages to use root-relative URLs (`/about-us/`, `/programmes/`, etc.)
- Updated footer on all 6 existing pages to include Blog and Gallery links
- Blog and Gallery pages are linked in footer only — NOT added to main navigation menu

## Conventions
- All CSS is inline within `<style>` in each HTML file (duplicated across pages)
- Images use Unsplash URLs (external)
- Logo loaded from external Netlify CDN URL in nav
- Forms use `onsubmit="return false;"` (no backend hooked up)
- Responsive breakpoints: `960px` and `640px`
- Mobile nav hides middle links (`li:not(:last-child):not(:first-child) { display: none; }`)

## Known Issues / TODO
- [ ] **CSS Duplication**: All 8 pages duplicate the same base CSS. Extract to a shared `assets/styles.css`.
- [ ] **No Mobile Hamburger**: Middle nav links simply hide on mobile; no toggle menu exists.
- [ ] **Forms Don't Submit**: Contact and newsletter forms are non-functional. Hook up to Formspree/Netlify Forms or add a backend.
- [ ] **External Images**: All photos are Unsplash hotlinks. Should be downloaded and optimized locally.
- [ ] **Map Placeholder**: Contact page has a decorative placeholder instead of an embedded map.
- [ ] **No Favicon**: `favicon.ico` is referenced but not present in `/assets`.
- [ ] **No OG/SEO Meta Tags**: Missing Open Graph tags, Twitter cards, structured data.
- [ ] **No 404 Page**: Not created.
- [ ] **Blog/Gallery Social Placeholders**: Blog article links and social media links still point to `#` — needs real content URLs.

## Next Recommended Steps
1. Extract shared CSS into `assets/styles.css` and link from all pages.
2. Add a mobile hamburger menu with toggle animation.
3. Hook up the contact form (Formspree, Netlify Forms, or EmailJS).
4. Download and optimize Unsplash images into `assets/images/`.
5. Add favicon and OG meta tags to all pages.
6. Add a testimonials/reviews section to the homepage.
7. Consider migrating to a static site generator (11ty, Vite) if page count grows.
