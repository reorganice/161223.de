# 161223.de Website Rebuild - Claude Code Documentation

## 🎯 Project Overview
Complete rebuild of 161223 interior design portfolio website from SCSS/SvelteKit 1.x to modern TailwindCSS/SvelteKit 2.x stack.

## 📋 Migration Goals
- **Remove SCSS** → Replace with TailwindCSS + CSS Custom Properties
- **Upgrade SvelteKit** 1.x → 2.x with modern best practices
- **Fix amateur slideshow** → Professional implementation with touch support
- **Replace svelte-scroller** → Native Intersection Observer
- **Optimize fonts** → Variable fonts, local hosting, performance
- **Modern image handling** → AVIF/WebP with responsive srcset
- **Dark mode preparation** → CSS custom properties structure

## 🚀 Deployment Target
- **Platform**: Hetzner CAX31 VPS
- **Git**: Gitea (self-hosted)
- **Deploy**: Coolify (self-hosted)
- **Adapter**: Node.js for VPS compatibility

## 🛠 Technology Stack

### Current (Old)
```
SvelteKit 1.x + Vite
SCSS with global variables
@sveltejs/svelte-scroller
Local fonts + @fontsource (redundant)
ImageKit CDN (unused)
```

### Target (New) ✅
```
SvelteKit 2.x + Vite + TypeScript
TailwindCSS + CSS Custom Properties
Native Intersection Observer
Variable fonts (local)
Modern image formats (AVIF/WebP)
Playwright + Vitest (Testing)
ESLint + Prettier (Code Quality)
```

## 📁 Project Structure (Actual)
```
161223.de/
├── src/
│   ├── app.html
│   ├── app.d.ts
│   ├── app.css
│   ├── routes/
│   │   ├── +layout.svelte
│   │   └── +page.svelte
│   └── lib/
│       └── assets/
├── static/
│   └── robots.txt
├── e2e/
├── package.json
├── svelte.config.js
├── vite.config.ts
├── playwright.config.ts
├── eslint.config.js
├── tsconfig.json
└── CLAUDE.md
```

## 🎨 Design System

### Colors (CSS Custom Properties)
```css
:root {
  --color-primary: #000000;
  --color-secondary: #ffffff;
  --color-background: #ffffff;
  --color-foreground: #000000;
}

[data-theme="dark"] {
  --color-primary: #ffffff;
  --color-secondary: #000000;
  --color-background: #000000;
  --color-foreground: #ffffff;
}
```

### Typography
```css
:root {
  --font-family: 'CourierPrime', 'Courier New', monospace;
  --font-size-headline: 1.6rem;
  --font-size-headline-sm: 1.2rem;
  --font-size-body: 1rem;
  --font-size-body-sm: 0.7rem;
  --line-height: 1.2;
}
```

### Layout
```css
:root {
  --padding-inline: 0.5rem;
  --margin-block: 1rem;
  --section-height: 77vh;
  --breakpoint: 819px;
  --opacity-reduced: 0.77;
}
```

## 🖼 Portfolio Data Structure
```javascript
export const projects = [
  {
    id: 0,
    type: 'interior design',
    materials: 'glass-mirror-resin-crystal',
    displayName: 'ÆVE',
    slug: 'aeve',
    year: '2023',
    location: 'berlin',
    images: {
      total: 7,
      formats: ['avif', 'webp', 'jpg'],
      sizes: [360, 480, 960, 1440, 2500]
    }
  }
  // ... other projects
];
```

## 🔧 Build Commands
```bash
npm run dev          # Development server
npm run build        # Production build
npm run preview      # Preview build
npm run check        # Type checking
npm run lint         # ESLint + Prettier
npm test             # Run Vitest unit tests
npm run test:e2e     # Run Playwright E2E tests
```

## 📱 Features Implementation

### Scroll System
- Native Intersection Observer
- Smooth section transitions
- Performance optimized
- No external dependencies

### Slideshow System
- Touch/swipe support for mobile
- Keyboard navigation (arrow keys, space)
- Auto-play with pause controls
- Accessible (ARIA labels, focus management)
- Memory leak prevention

### Image System
- Modern formats: AVIF → WebP → JPG fallback
- Responsive srcset for all screen sizes
- Lazy loading for performance
- Optimized for Core Web Vitals

## 🎯 Identified Issues in Old Code

### Slideshow Problems
- Duplicate keyboard handlers (ImageSlides.svelte + Images.svelte)
- Inconsistent autoplay logic with memory leaks
- Unused/commented UI elements
- Confusing state management between components

### Font Problems
- Redundant font loading (@fontsource AND local @font-face)
- Outdated font-face paths (./fonts/ instead of /fonts/)
- Missing variable font optimization

### Image Problems
- ImageKit CDN commented out but local images used
- No modern image formats (WebP/AVIF)
- Suboptimal responsive images

### SCSS Problems
- Overcomplicated SCSS setup for simple variables
- Hardcoded values instead of CSS custom properties
- No dark mode preparation

## 🚀 Deployment Notes

### Coolify Configuration
- Build command: `npm run build`
- Start command: `node build`
- Port: 3000 (default SvelteKit)
- Environment: NODE_ENV=production

### Performance Targets
- Lighthouse Score: 95+ (all categories)
- First Contentful Paint: < 1.5s
- Largest Contentful Paint: < 2.5s
- Cumulative Layout Shift: < 0.1

## 📝 Development Log

### 2025-01-13 - Project Initialization
- ✅ Git repository initialized in 161223.de/ (main branch)
- ✅ SvelteKit 2.x project created with TypeScript, ESLint, Prettier, Playwright, Vitest
- ✅ CLAUDE.md documentation created
- 🔄 Starting TailwindCSS configuration

### Next Steps
1. Configure TailwindCSS with CSS custom properties
2. Copy & optimize fonts from old project
3. Copy & optimize images from old project
4. Implement variable fonts system
5. Create native Intersection Observer scroll system
6. Rebuild slideshow with modern approach
7. Implement modern image system

---
*Generated with Claude Code - Interior Design Portfolio Rebuild*