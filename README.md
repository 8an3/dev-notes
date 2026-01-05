# TAILWIND_NGIN

<pre>
/ DEVSTACK_SYSTEM_ROOT/
├── 📂 TABLE_OF_CONTENTS/
└── 📍 TAILWIND_NGIN/
    ├── 📄 <a href="#tailwind-preset-ngin">Tailwind Plugin Ngin</a>
    ├── 📄 <a href="#tailwind-config">Tailwind Config</a> ................. Creates a basic config file to start your project off, if you for some can't use the other available options
    ├── 📄 <a href="#tailwind-preset-ngin">Tailwind Preset Ngin</a> ............... Over 525+ configurations available, but ZERO added work in order to use it, it actually reduces your implementation of tailwind in comparison to what you are currently doing. Click create, fill in the 3 variables at the top of the config... that's it!
    ├── 📄 <a href="#tailwind-css">Tailwind CSS</a>....................... Creates a pre-configured .css file to start your project off with
    ├── 📄 <a href="#postcss-config">Postcss Config</a> .................. Creating a basic postcss file, meeting tailwinds requirements
    └── 📄 <a href="https://github.com/8an3/DevStack">DEVSTACK_WEB_UI</a> ................ For other tools that also fit in this category, the provided link will take you to view them
</pre>

## Overview

Access all features via the **DevStack** status bar menu → **Tailwind** option.

---

### Tailwind CSS
**Command:** `ocrmnavigator.tailwind.file.css.create`

Creates a complete `tailwind.css` file at `app/routes/styles/tailwind.css` with:
- Base Tailwind directives (`@tailwind base/components/utilities`)
- Comprehensive CSS variable system (525+ tokens)
- Dark mode support with HSL color variables
- Custom utility classes and animations
- Pre-configured component styles (markdown, tables, scrollbars)

**Perfect for:** Starting a new project with a production-ready design system


#### 🎨 What's Included in the CSS File

The generated `tailwind.css` includes:

##### CSS Variables (525+ tokens):
- Complete color system with HSL values
- Background/foreground variants
- UI component colors (card, popover, sidebar)
- Chart colors (5 variants)
- Special utility colors
- Border and ring colors

##### Custom Animations:
- `glimmer` - Pulsing opacity effect
- `gradient-rotate` - Rotating gradient backgrounds
- Accordion animations
- Caret blink for text cursors
- Float, pulse-glow, shimmer effects
- Matrix fade, click, move, shine

#### Pre-styled Components:
- **Markdown rendering** with syntax highlighting
- **Tables** with proper borders and hover states
- **Checkboxes** with custom checked states
- **Scrollbars** with themed styling
- **Mermaid diagrams** with dark mode support
- **Code blocks** with proper formatting

##### Utility Classes:
- `.no-select` - Prevent text selection
- `.dimmed-line` / `.focused-line` - Focus mode styling
- `.prose` typography enhancements
- Theme overlay system (z-index managed)


---

### Tailwind Config 
**Command:** `ocrmnavigator.tailwind.file.config.base.create`

Generates a minimal `tailwind.config.js` with essential configurations:
- Content paths configured for Remix/React projects
- Extended color system using CSS variables
- Custom font family support
- Border radius tokens
- Animation utilities
- Typography plugin integration

**Perfect for:** Quick prototyping or learning Tailwind

---

### Tailwind Preset Ngin
**Command:** `ocrmnavigator.tailwind.file.config.create`

Creates the **ultimate Tailwind configuration** with 525+ pre-configured settings and **zero additional implementation work**. Simply set 3 variables at the top:

```typescript
// 1. Select a Design System Preset
const SELECTED_PRESET = 'MODERN' // or CREATIVE, TECHNICAL, FINTECH, LUXURY, BRUTALIST, EDITORIAL, PLAYFUL

// 2. Choose Your Font
const SELECTED_FONT = 'Geist' // 60+ Google Fonts available

// 3. Pick a Theme
const SELECTED_THEME = 'blue' // 40+ pre-built themes
```

**That's it!** Your entire design system is configured.


#### Available Presets:

| Preset | Description | Best For | Recommended Fonts |
|--------|-------------|----------|-------------------|
| **MODERN** | Refined, tight, high-performance feel (15% tighter spacing) | SaaS apps, dashboards | Geist, Inter, Plus Jakarta Sans |
| **CREATIVE** | Maximum breathing room, very round shapes | Creative portfolios, agencies | Outfit, Playfair Display, Montserrat |
| **TECHNICAL** | Square corners, IDE-like precision | Developer tools, documentation | JetBrains Mono, Fira Code, Geist Mono |
| **FINTECH** | Maximum information density | Trading platforms, analytics | IBM Plex Mono, Roboto, Source Code Pro |
| **LUXURY** | Extreme letter spacing, thin borders, huge whitespace | High-end brands, fashion | Playfair Display, Lora, Bodoni Moda |
| **BRUTALIST** | Thick borders, zero rounding, raw aesthetic | Experimental sites, art projects | Space Grotesk, IBM Plex Mono |
| **EDITORIAL** | Vertical rhythm, classic typesetting | Magazines, blogs, longform content | Source Serif 4, Merriweather, EB Garamond |
| **PLAYFUL** | Thick bouncy borders, mobile-first | Gaming, education apps, kids' sites | Nunito, Poppins, Delius Swash Caps |

#### Available Fonts (57):
#### Available Themes (57):
`marshmallow` | `art-deco` | `vs-code` | `spotify` | `summer` | `material-design` | `marvel` | `valorant` | `ghibli-studio` | `modern-minimal` | `nature` | `elegant-luxury` | `neo-brutalism` | `pastel-dreams` | `clean-slate` | `midnight-bloom` | `sunset-horizon` | `claude` | `caffeine` | `corporate` | `slack` | `perplexity` | `neutral` | `red` | `rose` | `orange` | `green` | `blue` | `yellow` | `violet` | `amber` | `lime` | `emerald` | `fuchsia` | `cyan` | `indigo` | `darkBlue`

**Or use:** `SELECTED_THEME = 'css'` to define your own theme in the CSS file

#### Quick Reference by Use Case

##### **Best for SaaS/Dashboards**
- Inter, Geist, DM Sans, IBM Plex Sans, Manrope

##### **Best for Marketing/Landing Pages**
- Poppins, Montserrat, Plus Jakarta Sans, Outfit, Urbanist

##### **Best for Luxury/Fashion**
- Playfair Display, Bodoni Moda, Cormorant Garamond, Prata

##### **Best for Editorial/Blogs**
- Merriweather, Lora, Newsreader, Source Serif 4

##### **Best for Code/Developer Tools**
- JetBrains Mono, Fira Code, Geist Mono, Source Code Pro

##### **Best for Playful/Creative**
- Nunito, Outfit, Delius Swash Caps, Righteous, Space Grotesk

##### **Best for Traditional/Professional**
- Libre Baskerville, PT Serif, EB Garamond, Lato

##### **Best for Accessibility**
- Lexend, Open Sans, Public Sans, Atkinson Hyperlegible

---
 

#### Sans-Serif Fonts (Modern & Professional)

| Font Name | Type | Description | Best For |
|-----------|------|-------------|----------|
| **Inter** | sans-serif | Clean, highly legible with excellent metrics optimization | UI design, dashboards, modern apps |
| **Roboto** | sans-serif | Google's flagship font, mechanical yet friendly | Android apps, Google-style interfaces |
| **Open Sans** | sans-serif | Neutral, humanist design with excellent readability | Body text, long-form content |
| **Poppins** | sans-serif | Geometric with friendly rounded terminals | Headlines, modern marketing sites |
| **Montserrat** | sans-serif | Urban, geometric letterforms inspired by Buenos Aires | Logos, headlines, bold statements |
| **Outfit** | sans-serif | Rounded, approachable geometric sans | Creative portfolios, friendly brands |
| **Plus Jakarta Sans** | sans-serif | Geometric humanist with Indonesian influence | Modern SaaS, startup branding |
| **DM Sans** | sans-serif | Low-contrast geometric, optimized for UI | Interface text, design systems |
| **IBM Plex Sans** | sans-serif | Corporate grotesque with warmth | Enterprise apps, IBM-style interfaces |
| **Nunito** | sans-serif | Rounded, playful terminals | Children's apps, friendly UI |
| **Lato** | sans-serif | Warm, stable humanist sans | Professional sites, body text |
| **Geist** | sans-serif | Vercel's font, optimized for code/UI hybrid | Developer tools, technical content |
| **Barlow** | sans-serif | Slightly rounded, highway signage-inspired | Navigation, wayfinding, modern UI |
| **Public Sans** | sans-serif | U.S. government design system font | Government sites, accessible design |
| **Work Sans** | sans-serif | Optimized for screen display | Body text, UI elements |
| **Manrope** | sans-serif | Modern geometric with open apertures | Minimalist designs, clean interfaces |
| **Urbanist** | sans-serif | Geometric with contemporary feel | Urban/city branding, modern apps |
| **Figtree** | sans-serif | Friendly, geometric with personality | Creative projects, approachable brands |
| **Archivo** | sans-serif | Grotesque style, great for headlines | Editorial, bold typography |

---

#### Serif Fonts (Luxury & Editorial)

| Font Name | Type | Description | Best For |
|-----------|------|-------------|----------|
| **Merriweather** | serif | Designed for screens, highly readable | Blogs, long-form reading, Medium-style |
| **Playfair Display** | serif | High-contrast, transitional design | Luxury brands, fashion, elegance |
| **Lora** | serif | Brushed curves, calligraphic roots | Editorial content, sophisticated blogs |
| **Source Serif 4** | serif | Adobe's readable serif for body text | Documentation, technical writing |
| **Libre Baskerville** | serif | Web-optimized Baskerville revival | Traditional publishing, books |
| **Space Grotesk** | sans-serif* | Geometric grotesque (technically sans) | Futuristic, tech branding |
| **PT Serif** | serif | Traditional, harmonious proportions | Russian/Cyrillic content, classic design |
| **Fraunces** | serif | Old-style with wonky charm | Quirky brands, artisanal products |
| **Cormorant Garamond** | serif | Display serif with Garamond influence | High fashion, luxury editorial |
| **Crimson Pro** | serif | Inspired by old-style classics | Literary sites, book publishing |
| **EB Garamond** | serif | Digital revival of Claude Garamont | Classic typography, academic |
| **Newsreader** | serif | Modern news typography | News sites, journalism, magazines |
| **DM Serif Display** | serif | Low-contrast display serif | Headers, editorial design |
| **Prata** | serif | Elegant, refined display typeface | Upscale brands, sophisticated design |
| **Bodoni Moda** | serif | High-contrast Bodoni revival | Fashion, luxury, dramatic headlines |
| **Young Serif** | serif | Contemporary serif with character | Modern editorial, creative projects |

---

#### Monospace Fonts (Technical & Code)

| Font Name | Type | Description | Best For |
|-----------|------|-------------|----------|
| **JetBrains Mono** | monospace | Developer-focused with ligatures | Code editors, IDEs, developer tools |
| **Fira Code** | monospace | Monospaced with programming ligatures | VS Code, coding tutorials |
| **Geist Mono** | monospace | Vercel's monospace, matches Geist Sans | Technical documentation, code blocks |
| **IBM Plex Mono** | monospace | Corporate mono with personality | Enterprise code, technical specs |
| **Roboto Mono** | monospace | Google's monospace companion | Android development, terminal |
| **Space Mono** | monospace | Quirky, retro-futuristic | Creative coding, space themes |
| **Source Code Pro** | monospace | Adobe's coding font | Programming, technical writing |
| **Inconsolata** | monospace | Humanist monospace, highly legible | Code snippets, terminal emulators |
| **Ubuntu Mono** | monospace | Ubuntu's system monospace | Linux apps, terminal interfaces |
| **Red Hat Mono** | monospace | Red Hat's enterprise monospace | Enterprise dev tools, documentation |
| **Nanum Gothic Coding** | monospace | Korean-optimized coding font | Korean language coding, CJK support |
| **Cutive Mono** | monospace | Typewriter-inspired | Retro coding themes, vintage tech |

---

#### Display & Experimental Fonts (Brutalist & Playful)

| Font Name | Type | Description | Best For |
|-----------|------|-------------|----------|
| **Gabriela** | serif | Decorative serif with ornate details | Poetry, artistic projects |
| **Delius Swash Caps** | cursive | Playful handwriting with swashes | Children's content, playful branding |
| **Sora** | sans-serif | Geometric with unique character | Modern tech, crypto projects |
| **Bricolage Grotesque** | sans-serif | Quirky, irregular letterforms | Experimental design, art projects |
| **Clash Display** | sans-serif | Bold, display-focused geometric | Hero sections, impact headlines |
| **Syne** | sans-serif | Variable, modern with personality | Tech startups, contemporary brands |
| **Unbounded** | sans-serif | Rounded, futuristic geometric | Gaming, metaverse, Web3 |
| **Cabinet Grotesk** | sans-serif | Neo-grotesque with character | Design studios, creative agencies |
| **Righteous** | cursive | Geometric display with flair | Logos, badges, bold statements |
| **Lexend** | sans-serif | Optimized for reading efficiency | Accessibility-focused, dyslexia-friendly |
| **Kanit** | sans-serif | Thai-influenced geometric | International brands, Thai language |
 

---

### Postcss Config
**Command:** `ocrmnavigator.tailwind.file.postcss.create`

Generates `postcss.config.js` with Tailwind CSS integration.

**Perfect for:** Completing your Tailwind setup for build processes

---

### Tailwind Plugin Ngin

Add powerful utility classes through custom plugins. All plugins can be added as **separate files** or **inline** in your config.

#### How to Add Plugins

1. Open DevStack menu → Tailwind
2. Select a plugin from the list
3. Choose installation method:
   - **Separate File**: Creates `plugins/{pluginName}.ts` and auto-imports
   - **Inline**: Adds directly to `tailwind.config.js`

#### Available Plugins:

##### Tailwind V4 Plug-in
It's just plug and play, and drop a v4 configured component into your project.

Key Features This Plugin Adds:
1. Full V4 Spacing Scale - 0.25rem increments (0.25rem to 25rem)
2. Logical Properties - Complete RTL/LTR support with ms, me, start, end, etc.
3. Container Queries - Full @container syntax with size variants
4. OKLCH Color System - V4's new color palette with proper color-mix
5. Scroll-Driven Animations - animate-on-scroll, view-timeline
6. Modern CSS - Subgrid, anchor positioning, text-balance, starting styles
7. All V4 Variants - has-*, not-*, @container, forced-colors, etc.
8. 3D Transforms - rotate-x, rotate-y, perspective, transform-3d
9. Viewport Units - All dynamic viewport units (dvw, dvh, svw, etc.)
10. Form Features - field-sizing, input spinners, modern form states

##### **Animated Gradient Borders**
Moving gradient borders for modern, eye-catching UI elements.

```html
<div class="border-gradient-animated">Animated border</div>
<div class="border-gradient-glow">Glowing border</div>
```

**Use cases:** Hero sections, CTAs, featured cards

---

##### **Neumorphism Plugin**
Soft UI styles with realistic light/shadow effects.

```html
<div class="neu">Raised element</div>
<div class="neu-dark">Dark mode raised</div>
<div class="neu-inset">Pressed appearance</div>
<div class="neu-floating">Hoverable card</div>
```

**Classes available:**
- `.neu` - Standard raised (light mode)
- `.neu-dark` - Dark mode version
- `.neu-inset` - Pressed/inset appearance
- `.neu-inset-dark` - Dark inset
- `.neu-flat` - Subtle flat version
- `.neu-pressed` - Active/clicked state
- `.neu-floating` - Elevated with hover effect

**Use cases:** Modern dashboards, settings panels, form controls

---

##### **Spotlight Effect Plugin**
Mouse-following spotlight effects for interactive product pages.

```html
<div class="spotlight">Subtle spotlight</div>
<div class="spotlight-strong">Strong spotlight</div>
<div class="spotlight-colored">Colored spotlight</div>
<div class="spotlight-border">Border spotlight</div>
```

**JavaScript required for mouse tracking:**
```javascript
element.addEventListener('mousemove', (e) => {
  const rect = e.currentTarget.getBoundingClientRect();
  const x = e.clientX - rect.left;
  const y = e.clientY - rect.top;
  e.currentTarget.style.setProperty('--spotlight-x', `${x}px`);
  e.currentTarget.style.setProperty('--spotlight-y', `${y}px`);
});
```

**Use cases:** Product showcases, pricing tables, feature cards

---

### Tailwind Plugin Library (Ngin) - Documentation

#### Overview

The **Tailwind Plugin Ngin** is a comprehensive collection of 60+ production-ready Tailwind CSS plugins accessible through VS Code. These plugins add powerful utility classes for modern UI effects, animations, and interactions.

---

#### 🚀 How to Add Plugins

##### Via DevStack Menu:
1. Click **DevStack** in the status bar
2. Select **Tailwind**
3. Choose **Tailwind Plugin Ngin**
4. Browse and select a plugin
5. Choose installation method:
   - **Create plugin file**: Saves as `plugins/{name}.ts` and auto-imports into your config
   - **Add inline to config**: Adds directly to `tailwind.config.js`

##### What Happens Automatically:
- Plugin file is created (if file method chosen)
- Import statement added to your Tailwind config
- Plugin registered in the `plugins` array
- File opened in VS Code for immediate review

---

#### 📚 Plugin Categories

##### 🎨 Visual Effects

##### **Glassmorphism**
Frosted glass effects for modern, layered UIs.

```html
<div class="glass">Standard glass effect</div>
<div class="glass-dark">Dark mode glass</div>
<div class="glass-strong">Stronger blur</div>
<div class="glass-morphic">Premium glassmorphic</div>
<div class="surface-reflection">Reflective surface</div>
```

**Use cases:** Modals, overlays, navigation bars, cards

---

##### **Neumorphism**
Soft UI styles with realistic light/shadow effects.

```html
<div class="neu">Raised element</div>
<div class="neu-dark">Dark mode raised</div>
<div class="neu-inset">Pressed appearance</div>
<div class="neu-floating">Hoverable card</div>
```

**Use cases:** Modern dashboards, settings panels, form controls

---

##### **Spotlight Effect**
Mouse-following spotlight for interactive product pages.

```html
<div class="spotlight">Subtle spotlight</div>
<div class="spotlight-strong">Strong spotlight</div>
<div class="spotlight-colored">Colored (purple)</div>
<div class="spotlight-border">Border spotlight</div>
```

**Requires JavaScript** for mouse tracking:
```javascript
element.addEventListener('mousemove', (e) => {
  const rect = e.currentTarget.getBoundingClientRect();
  const x = e.clientX - rect.left;
  const y = e.clientY - rect.top;
  e.currentTarget.style.setProperty('--spotlight-x', `${x}px`);
  e.currentTarget.style.setProperty('--spotlight-y', `${y}px`);
});
```

---

##### **Text Gradients**
Beautiful gradient text effects.

```html
<h1 class="text-gradient">Gradient Text</h1>
<h1 class="text-gradient-rainbow">Rainbow Text</h1>
<h1 class="text-gradient-sunset">Sunset Text</h1>
```

---

##### **Custom Shadows**
Beautiful pre-configured shadow utilities.

```html
<div class="shadow-soft">Soft shadow</div>
<div class="shadow-brutal">Hard shadow</div>
<div class="shadow-glow">Glowing shadow</div>
```

---

##### 🎬 Animations

##### **Comprehensive Animation Collection**
60+ animations organized by category. The most complete animation library for Tailwind.

**Categories included:**
- **UI Component Animations**: Accordions, modals, dropdowns
- **Attention Grabbers**: Pulse, glow, bounce effects
- **Loading States**: Shimmer, spin, progress bars
- **Interaction Feedback**: Click, hover, drag responses
- **Decorative Effects**: Float, wiggle, sway
- **Background Animations**: Gradients, particles, borders
- **Text Effects**: Typing, reveal, glitch
- **Entrance/Exit Animations**: Fade, slide, zoom

**Examples:**
```html
<!-- Loading skeleton -->
<div class="animate-shimmer">Loading...</div>

<!-- Attention-grabbing button -->
<button class="animate-pulse-ring hover:animate-bounce-subtle">
  Click me!
</button>

<!-- Floating hero element -->
<div class="animate-float">
  <img src="hero.png" />
</div>

<!-- Entrance animation -->
<div class="animate-fade-in-up">Welcome!</div>

<!-- Interactive feedback -->
<button class="active:animate-tap">Press me</button>

<!-- Gradient background -->
<div class="bg-gradient-to-r from-purple-500 to-pink-500 animate-gradient-flow">
  Beautiful gradient
</div>
```

---

##### **Animated Gradient Borders**
Moving gradient borders for modern, eye-catching UI.

```html
<div class="border-gradient-animated">Animated border</div>
<div class="border-gradient-glow">Glowing border</div>
```

---

##### **Matrix/Rain Effect**
Iconic Matrix-style falling characters effect.

```html
<div class="matrix-rain">Welcome, Neo...</div>
```

---

##### **Flip Card**
3D card flip animations.

```html
<div class="flip-card">
  <div class="flip-card-front">Front</div>
  <div class="flip-card-back">Back</div>
</div>
```

---

##### **Heartbeat**
Pulsing heartbeat animation.

```html
<button class="animate-heartbeat">♥</button>
```

---

##### **Marquee/Scroll**
Infinite scrolling text or content.

```html
<div class="marquee">
  <span>Scrolling text...</span>
</div>
```

---

##### **Ken Burns (Zoom + Pan)**
Cinematic zoom and pan effects for images.

```html
<img src="photo.jpg" class="ken-burns" />
```

---

##### 🎯 UI Components

##### **Scrollbar Styles**
Customizable scrollbar utilities that match your design system.

```html
<div class="scrollbar">Standard scrollbar</div>
<div class="scrollbar-thin">Thin scrollbar</div>
<div class="scrollbar-none">Hidden scrollbar</div>
```

**Uses CSS variables** for automatic theming with light/dark mode.

---

##### **Bento Grid**
Apple-style bento box layouts for modern dashboards.

```html
<div class="bento-grid">
  <div class="bento-item">Card 1</div>
  <div class="bento-item-large">Card 2</div>
  <div class="bento-item">Card 3</div>
</div>
```

---

##### **Skeleton/Placeholder**
Pre-built skeleton components for loading UIs.

```html
<div class="skeleton-text"></div>
<div class="skeleton-avatar"></div>
<div class="skeleton-card"></div>
```

---

##### 🎨 Backgrounds & Gradients

##### **Background Gradients**
Beautiful pre-configured gradient backgrounds.

```html
<div class="bg-gradient-purple">Purple gradient</div>
<div class="bg-gradient-sunset">Sunset gradient</div>
<div class="bg-gradient-ocean">Ocean gradient</div>
```

---

##### **Architectural Layout Patterns**
Subtle background patterns like dots, grids, and plus signs.

```html
<div class="pattern-dots">Dot pattern</div>
<div class="pattern-grid">Grid pattern</div>
<div class="pattern-plus">Plus sign pattern</div>
```

---

##### **Noise/Grain Texture**
Subtle texture overlays for depth.

```html
<div class="noise">Grainy texture</div>
<div class="noise-subtle">Subtle grain</div>
```

---

##### 🔧 Layout & Utilities

##### **Aspect Ratios**
Common aspect ratio utilities.

```html
<div class="aspect-video">16:9</div>
<div class="aspect-square">1:1</div>
<div class="aspect-portrait">3:4</div>
```

---

##### **CSS Grid Helpers**
Modern grid layouts made easy.

```html
<div class="grid-auto-fit">Auto-fitting grid</div>
<div class="grid-auto-fill">Auto-filling grid</div>
```

---

##### **Spacing & Layout Helpers**
Modern spacing utilities.

```html
<div class="stack-4">Vertical stack with gap-4</div>
<div class="cluster">Horizontal cluster</div>
<div class="center">Perfect centering</div>
```

---

##### **Container Queries**
Container query utilities (modern CSS).

```html
<div class="@container">
  <div class="@sm:text-lg">Responsive to container</div>
</div>
```

---

##### **Clamp Utilities**
Fluid, responsive sizing with CSS clamp().

```html
<h1 class="text-clamp-lg">Fluid text</h1>
<div class="w-clamp">Fluid width</div>
```

---

##### 🎭 Advanced Effects

##### **Masking & Cutouts**
Advanced CSS masking for smooth edge-fading.

```html
<div class="mask-fade-bottom">Fades at bottom</div>
<div class="mask-circular">Circular cutout</div>
```

---

##### **3D Transform Utilities**
3D perspective and transforms.

```html
<div class="perspective-1000">
  <div class="rotate-3d">3D rotation</div>
</div>
```

---

##### **Backdrop Utilities**
Extended backdrop filter options.

```html
<div class="backdrop-blur-sm">Subtle blur</div>
<div class="backdrop-saturate-150">Saturated</div>
```

---

##### **Blend Mode Utilities**
Modern blend modes for overlays.

```html
<div class="mix-blend-multiply">Multiply blend</div>
<div class="mix-blend-screen">Screen blend</div>
```

---

##### ♿ Accessibility & UX

##### **Focus States**
Modern, accessible focus styles.

```html
<button class="focus-ring">Accessible button</button>
<input class="focus-border">Accessible input</input>
```

---

##### **Micro-Interactions**
Subtle micro-interactions for modern UIs.

```html
<button class="micro-lift">Lifts on hover</button>
<button class="micro-press">Press feedback</button>
```

---

##### **Mobile Safe Area Utilities**
Handles notches and home indicators for iOS/Android.

```html
<div class="safe-top">Safe area top</div>
<div class="safe-bottom">Safe area bottom</div>
```

---

##### 🎨 Typography

##### **Typography Pro**
Utilities for text balance, fluid headers, and advanced clamp-based sizing.

```html
<h1 class="text-balance">Balanced text</h1>
<h1 class="text-fluid-2xl">Fluid heading</h1>
```

---

##### **Typography Styles**
Custom typography styles for `@tailwindcss/typography` plugin.

```html
<article class="prose prose-custom">
  <h1>Styled heading</h1>
  <p>Styled paragraph</p>
</article>
```

---

##### 🎬 Specialized Animations

##### **Dark Mode Transitions**
Smooth transitions when switching themes.

```html
<div class="dark-mode-transition">
  Content transitions smoothly
</div>
```

---

##### **Scroll Animations**
Intersection Observer scroll-triggered animations.

```html
<div class="scroll-fade-in">Fades in on scroll</div>
<div class="scroll-slide-up">Slides up on scroll</div>
```

---

##### **Interaction Magnetism**
Subtle spring-loaded hover and active states.

```html
<button class="magnetic">Magnetic button</button>
<button class="magnetic-strong">Strong magnetic</button>
```

---

##### 🎨 Design System

##### **Theme Colors Extension**
Extends Tailwind's color palette with design system colors using CSS variables.

```html
<div class="bg-primary">Primary color</div>
<div class="text-accent">Accent text</div>
```

**Automatically supports light/dark mode** through CSS variables.

---

##### **Semantic Surface Depth**
Inner glows and layered shadows for physically nested components.

```html
<div class="surface-1">Level 1 surface</div>
<div class="surface-2">Level 2 surface</div>
<div class="surface-inset">Inset surface</div>
```

---

##### 🛠️ Development Tools

##### **Border Utilities**
Advanced border styles beyond Tailwind defaults.

```html
<div class="border-dashed-custom">Custom dashed</div>
<div class="border-gradient">Gradient border</div>
```

---

##### **CSS Shapes**
Pre-made shapes for quick prototyping.

```html
<div class="shape-triangle">Triangle</div>
<div class="shape-hexagon">Hexagon</div>
<div class="shape-star">Star</div>
```

---

##### **Print Utilities**
Print-specific styles.

```html
<div class="print:hidden">Hidden in print</div>
<div class="print:text-black">Black text in print</div>
```

---

##### **Debug Utilities**
Development helpers for debugging layouts.

```html
<div class="debug-grid">Shows grid overlay</div>
<div class="debug-outlines">Shows all outlines</div>
```

---

#### 🎯 Plugin Installation Methods Compared

##### **Separate File** (Recommended)
✅ Better organization  
✅ Easier to update  
✅ Can be shared across projects  
✅ Keeps config file clean  

```
project/
├── plugins/
│   ├── glassmorphism.ts
│   ├── animations.ts
│   └── scrollbar.ts
└── tailwind.config.js (imports from plugins/)
```

##### **Inline**
✅ Everything in one file  
✅ No extra files to manage  
❌ Config file gets large  
❌ Harder to maintain  

 
---

#### 🚀 Quick Start Examples

##### Modern SaaS Landing Page
```html
<section class="glass spotlight animate-fade-in-up">
  <h1 class="text-gradient-sunset text-fluid-2xl">
    Welcome to the Future
  </h1>
  <button class="neu-floating animate-pulse-ring">
    Get Started
  </button>
</section>
```

##### Dashboard Card
```html
<div class="glass-morphic scrollbar hover:animate-lift">
  <div class="skeleton-text animate-shimmer"></div>
</div>
```

##### Interactive Product Card
```html
<div class="spotlight-strong neu-floating">
  <img src="product.jpg" class="ken-burns" />
  <button class="active:animate-tap">Add to Cart</button>
</div>
```

---

#### 📊 Plugin Count by Category

- **Animations**: 25+ plugins
- **Visual Effects**: 10+ plugins
- **Layout Utilities**: 8+ plugins
- **Typography**: 3+ plugins
- **Accessibility**: 4+ plugins
- **Development Tools**: 5+ plugins
- **Backgrounds**: 6+ plugins
- **3D/Advanced**: 4+ plugins

**Total: 60+ production-ready plugins**

---

#### 🔄 Updates & Maintenance

All plugins are:
- ✅ TypeScript-ready
- ✅ Dark mode compatible
- ✅ Purge-safe (no unused CSS)
- ✅ Modern browser compatible
- ✅ Accessibility-friendly

---
 
## Overview

Access all features via the **DevStack** status bar menu → **Tailwind** option.

---

### Tailwind CSS
**Command:** `ocrmnavigator.tailwind.file.css.create`

Creates a complete `tailwind.css` file at `app/routes/styles/tailwind.css` with:
- Base Tailwind directives (`@tailwind base/components/utilities`)
- Comprehensive CSS variable system (525+ tokens)
- Dark mode support with HSL color variables
- Custom utility classes and animations
- Pre-configured component styles (markdown, tables, scrollbars)

**Perfect for:** Starting a new project with a production-ready design system


#### 🎨 What's Included in the CSS File

The generated `tailwind.css` includes:

##### CSS Variables (525+ tokens):
- Complete color system with HSL values
- Background/foreground variants
- UI component colors (card, popover, sidebar)
- Chart colors (5 variants)
- Special utility colors
- Border and ring colors

##### Custom Animations:
- `glimmer` - Pulsing opacity effect
- `gradient-rotate` - Rotating gradient backgrounds
- Accordion animations
- Caret blink for text cursors
- Float, pulse-glow, shimmer effects
- Matrix fade, click, move, shine

#### Pre-styled Components:
- **Markdown rendering** with syntax highlighting
- **Tables** with proper borders and hover states
- **Checkboxes** with custom checked states
- **Scrollbars** with themed styling
- **Mermaid diagrams** with dark mode support
- **Code blocks** with proper formatting

##### Utility Classes:
- `.no-select` - Prevent text selection
- `.dimmed-line` / `.focused-line` - Focus mode styling
- `.prose` typography enhancements
- Theme overlay system (z-index managed)


---

### Tailwind Config 
**Command:** `ocrmnavigator.tailwind.file.config.base.create`

Generates a minimal `tailwind.config.js` with essential configurations:
- Content paths configured for Remix/React projects
- Extended color system using CSS variables
- Custom font family support
- Border radius tokens
- Animation utilities
- Typography plugin integration

**Perfect for:** Quick prototyping or learning Tailwind

---

### Tailwind Preset Ngin
**Command:** `ocrmnavigator.tailwind.file.config.create`

Creates the **ultimate Tailwind configuration** with 525+ pre-configured settings and **zero additional implementation work**. Simply set 3 variables at the top:

```typescript
// 1. Select a Design System Preset
const SELECTED_PRESET = 'MODERN' // or CREATIVE, TECHNICAL, FINTECH, LUXURY, BRUTALIST, EDITORIAL, PLAYFUL

// 2. Choose Your Font
const SELECTED_FONT = 'Geist' // 60+ Google Fonts available

// 3. Pick a Theme
const SELECTED_THEME = 'blue' // 40+ pre-built themes
```

**That's it!** Your entire design system is configured.

#### Available Presets:

| Preset | Description | Best For | Recommended Fonts |
|--------|-------------|----------|-------------------|
| **MODERN** | Refined, tight, high-performance feel (15% tighter spacing) | SaaS apps, dashboards | Geist, Inter, Plus Jakarta Sans |
| **CREATIVE** | Maximum breathing room, very round shapes | Creative portfolios, agencies | Outfit, Playfair Display, Montserrat |
| **TECHNICAL** | Square corners, IDE-like precision | Developer tools, documentation | JetBrains Mono, Fira Code, Geist Mono |
| **FINTECH** | Maximum information density | Trading platforms, analytics | IBM Plex Mono, Roboto, Source Code Pro |
| **LUXURY** | Extreme letter spacing, thin borders, huge whitespace | High-end brands, fashion | Playfair Display, Lora, Bodoni Moda |
| **BRUTALIST** | Thick borders, zero rounding, raw aesthetic | Experimental sites, art projects | Space Grotesk, IBM Plex Mono |
| **EDITORIAL** | Vertical rhythm, classic typesetting | Magazines, blogs, longform content | Source Serif 4, Merriweather, EB Garamond |
| **PLAYFUL** | Thick bouncy borders, mobile-first | Gaming, education apps, kids' sites | Nunito, Poppins, Delius Swash Caps |

#### Available Fonts (57):
#### Available Themes (57):
`marshmallow` | `art-deco` | `vs-code` | `spotify` | `summer` | `material-design` | `marvel` | `valorant` | `ghibli-studio` | `modern-minimal` | `nature` | `elegant-luxury` | `neo-brutalism` | `pastel-dreams` | `clean-slate` | `midnight-bloom` | `sunset-horizon` | `claude` | `caffeine` | `corporate` | `slack` | `perplexity` | `neutral` | `red` | `rose` | `orange` | `green` | `blue` | `yellow` | `violet` | `amber` | `lime` | `emerald` | `fuchsia` | `cyan` | `indigo` | `darkBlue`

**Or use:** `SELECTED_THEME = 'css'` to define your own theme in the CSS file

---

### Postcss Config
**Command:** `ocrmnavigator.tailwind.file.postcss.create`

Generates `postcss.config.js` with Tailwind CSS integration.

**Perfect for:** Completing your Tailwind setup for build processes

---

### Tailwind Plugin Ngin

Add powerful utility classes through custom plugins. All plugins can be added as **separate files** or **inline** in your config.

#### How to Add Plugins

1. Open DevStack menu → Tailwind
2. Select a plugin from the list
3. Choose installation method:
   - **Separate File**: Creates `plugins/{pluginName}.ts` and auto-imports
   - **Inline**: Adds directly to `tailwind.config.js`

#### Available Plugins:

##### **Animated Gradient Borders**
Moving gradient borders for modern, eye-catching UI elements.

```html
<div class="border-gradient-animated">Animated border</div>
<div class="border-gradient-glow">Glowing border</div>
```

**Use cases:** Hero sections, CTAs, featured cards

---

##### **Neumorphism Plugin**
Soft UI styles with realistic light/shadow effects.

```html
<div class="neu">Raised element</div>
<div class="neu-dark">Dark mode raised</div>
<div class="neu-inset">Pressed appearance</div>
<div class="neu-floating">Hoverable card</div>
```

**Classes available:**
- `.neu` - Standard raised (light mode)
- `.neu-dark` - Dark mode version
- `.neu-inset` - Pressed/inset appearance
- `.neu-inset-dark` - Dark inset
- `.neu-flat` - Subtle flat version
- `.neu-pressed` - Active/clicked state
- `.neu-floating` - Elevated with hover effect

**Use cases:** Modern dashboards, settings panels, form controls

---

##### **Spotlight Effect Plugin**
Mouse-following spotlight effects for interactive product pages.

```html
<div class="spotlight">Subtle spotlight</div>
<div class="spotlight-strong">Strong spotlight</div>
<div class="spotlight-colored">Colored spotlight</div>
<div class="spotlight-border">Border spotlight</div>
```

**JavaScript required for mouse tracking:**
```javascript
element.addEventListener('mousemove', (e) => {
  const rect = e.currentTarget.getBoundingClientRect();
  const x = e.clientX - rect.left;
  const y = e.clientY - rect.top;
  e.currentTarget.style.setProperty('--spotlight-x', `${x}px`);
  e.currentTarget.style.setProperty('--spotlight-y', `${y}px`);
});
```

**Use cases:** Product showcases, pricing tables, feature cards

---

### Tailwind Plugin Library (Ngin) - Documentation

#### Overview

The **Tailwind Plugin Ngin** is a comprehensive collection of 60+ production-ready Tailwind CSS plugins accessible through VS Code. These plugins add powerful utility classes for modern UI effects, animations, and interactions.

---

#### 🚀 How to Add Plugins

##### Via DevStack Menu:
1. Click **DevStack** in the status bar
2. Select **Tailwind**
3. Choose **Tailwind Plugin Ngin**
4. Browse and select a plugin
5. Choose installation method:
   - **Create plugin file**: Saves as `plugins/{name}.ts` and auto-imports into your config
   - **Add inline to config**: Adds directly to `tailwind.config.js`

##### What Happens Automatically:
- Plugin file is created (if file method chosen)
- Import statement added to your Tailwind config
- Plugin registered in the `plugins` array
- File opened in VS Code for immediate review

---

#### 📚 Plugin Categories

##### 🎨 Visual Effects

##### **Glassmorphism**
Frosted glass effects for modern, layered UIs.

```html
<div class="glass">Standard glass effect</div>
<div class="glass-dark">Dark mode glass</div>
<div class="glass-strong">Stronger blur</div>
<div class="glass-morphic">Premium glassmorphic</div>
<div class="surface-reflection">Reflective surface</div>
```

**Use cases:** Modals, overlays, navigation bars, cards

---

##### **Neumorphism**
Soft UI styles with realistic light/shadow effects.

```html
<div class="neu">Raised element</div>
<div class="neu-dark">Dark mode raised</div>
<div class="neu-inset">Pressed appearance</div>
<div class="neu-floating">Hoverable card</div>
```

**Use cases:** Modern dashboards, settings panels, form controls

---

##### **Spotlight Effect**
Mouse-following spotlight for interactive product pages.

```html
<div class="spotlight">Subtle spotlight</div>
<div class="spotlight-strong">Strong spotlight</div>
<div class="spotlight-colored">Colored (purple)</div>
<div class="spotlight-border">Border spotlight</div>
```

**Requires JavaScript** for mouse tracking:
```javascript
element.addEventListener('mousemove', (e) => {
  const rect = e.currentTarget.getBoundingClientRect();
  const x = e.clientX - rect.left;
  const y = e.clientY - rect.top;
  e.currentTarget.style.setProperty('--spotlight-x', `${x}px`);
  e.currentTarget.style.setProperty('--spotlight-y', `${y}px`);
});
```

---

##### **Text Gradients**
Beautiful gradient text effects.

```html
<h1 class="text-gradient">Gradient Text</h1>
<h1 class="text-gradient-rainbow">Rainbow Text</h1>
<h1 class="text-gradient-sunset">Sunset Text</h1>
```

---

##### **Custom Shadows**
Beautiful pre-configured shadow utilities.

```html
<div class="shadow-soft">Soft shadow</div>
<div class="shadow-brutal">Hard shadow</div>
<div class="shadow-glow">Glowing shadow</div>
```

---

##### 🎬 Animations

##### **Comprehensive Animation Collection**
60+ animations organized by category. The most complete animation library for Tailwind.

**Categories included:**
- **UI Component Animations**: Accordions, modals, dropdowns
- **Attention Grabbers**: Pulse, glow, bounce effects
- **Loading States**: Shimmer, spin, progress bars
- **Interaction Feedback**: Click, hover, drag responses
- **Decorative Effects**: Float, wiggle, sway
- **Background Animations**: Gradients, particles, borders
- **Text Effects**: Typing, reveal, glitch
- **Entrance/Exit Animations**: Fade, slide, zoom

**Examples:**
```html
<!-- Loading skeleton -->
<div class="animate-shimmer">Loading...</div>

<!-- Attention-grabbing button -->
<button class="animate-pulse-ring hover:animate-bounce-subtle">
  Click me!
</button>

<!-- Floating hero element -->
<div class="animate-float">
  <img src="hero.png" />
</div>

<!-- Entrance animation -->
<div class="animate-fade-in-up">Welcome!</div>

<!-- Interactive feedback -->
<button class="active:animate-tap">Press me</button>

<!-- Gradient background -->
<div class="bg-gradient-to-r from-purple-500 to-pink-500 animate-gradient-flow">
  Beautiful gradient
</div>
```

---

##### **Animated Gradient Borders**
Moving gradient borders for modern, eye-catching UI.

```html
<div class="border-gradient-animated">Animated border</div>
<div class="border-gradient-glow">Glowing border</div>
```

---

##### **Matrix/Rain Effect**
Iconic Matrix-style falling characters effect.

```html
<div class="matrix-rain">Welcome, Neo...</div>
```

---

##### **Flip Card**
3D card flip animations.

```html
<div class="flip-card">
  <div class="flip-card-front">Front</div>
  <div class="flip-card-back">Back</div>
</div>
```

---

##### **Heartbeat**
Pulsing heartbeat animation.

```html
<button class="animate-heartbeat">♥</button>
```

---

##### **Marquee/Scroll**
Infinite scrolling text or content.

```html
<div class="marquee">
  <span>Scrolling text...</span>
</div>
```

---

##### **Ken Burns (Zoom + Pan)**
Cinematic zoom and pan effects for images.

```html
<img src="photo.jpg" class="ken-burns" />
```

---

##### 🎯 UI Components

##### **Scrollbar Styles**
Customizable scrollbar utilities that match your design system.

```html
<div class="scrollbar">Standard scrollbar</div>
<div class="scrollbar-thin">Thin scrollbar</div>
<div class="scrollbar-none">Hidden scrollbar</div>
```

**Uses CSS variables** for automatic theming with light/dark mode.

---

##### **Bento Grid**
Apple-style bento box layouts for modern dashboards.

```html
<div class="bento-grid">
  <div class="bento-item">Card 1</div>
  <div class="bento-item-large">Card 2</div>
  <div class="bento-item">Card 3</div>
</div>
```

---

##### **Skeleton/Placeholder**
Pre-built skeleton components for loading UIs.

```html
<div class="skeleton-text"></div>
<div class="skeleton-avatar"></div>
<div class="skeleton-card"></div>
```

---

##### 🎨 Backgrounds & Gradients

##### **Background Gradients**
Beautiful pre-configured gradient backgrounds.

```html
<div class="bg-gradient-purple">Purple gradient</div>
<div class="bg-gradient-sunset">Sunset gradient</div>
<div class="bg-gradient-ocean">Ocean gradient</div>
```

---

##### **Architectural Layout Patterns**
Subtle background patterns like dots, grids, and plus signs.

```html
<div class="pattern-dots">Dot pattern</div>
<div class="pattern-grid">Grid pattern</div>
<div class="pattern-plus">Plus sign pattern</div>
```

---

##### **Noise/Grain Texture**
Subtle texture overlays for depth.

```html
<div class="noise">Grainy texture</div>
<div class="noise-subtle">Subtle grain</div>
```

---

##### 🔧 Layout & Utilities

##### **Aspect Ratios**
Common aspect ratio utilities.

```html
<div class="aspect-video">16:9</div>
<div class="aspect-square">1:1</div>
<div class="aspect-portrait">3:4</div>
```

---

##### **CSS Grid Helpers**
Modern grid layouts made easy.

```html
<div class="grid-auto-fit">Auto-fitting grid</div>
<div class="grid-auto-fill">Auto-filling grid</div>
```

---

##### **Spacing & Layout Helpers**
Modern spacing utilities.

```html
<div class="stack-4">Vertical stack with gap-4</div>
<div class="cluster">Horizontal cluster</div>
<div class="center">Perfect centering</div>
```

---

##### **Container Queries**
Container query utilities (modern CSS).

```html
<div class="@container">
  <div class="@sm:text-lg">Responsive to container</div>
</div>
```

---

##### **Clamp Utilities**
Fluid, responsive sizing with CSS clamp().

```html
<h1 class="text-clamp-lg">Fluid text</h1>
<div class="w-clamp">Fluid width</div>
```

---

##### 🎭 Advanced Effects

##### **Masking & Cutouts**
Advanced CSS masking for smooth edge-fading.

```html
<div class="mask-fade-bottom">Fades at bottom</div>
<div class="mask-circular">Circular cutout</div>
```

---

##### **3D Transform Utilities**
3D perspective and transforms.

```html
<div class="perspective-1000">
  <div class="rotate-3d">3D rotation</div>
</div>
```

---

##### **Backdrop Utilities**
Extended backdrop filter options.

```html
<div class="backdrop-blur-sm">Subtle blur</div>
<div class="backdrop-saturate-150">Saturated</div>
```

---

##### **Blend Mode Utilities**
Modern blend modes for overlays.

```html
<div class="mix-blend-multiply">Multiply blend</div>
<div class="mix-blend-screen">Screen blend</div>
```

---

##### ♿ Accessibility & UX

##### **Focus States**
Modern, accessible focus styles.

```html
<button class="focus-ring">Accessible button</button>
<input class="focus-border">Accessible input</input>
```

---

##### **Micro-Interactions**
Subtle micro-interactions for modern UIs.

```html
<button class="micro-lift">Lifts on hover</button>
<button class="micro-press">Press feedback</button>
```

---

##### **Mobile Safe Area Utilities**
Handles notches and home indicators for iOS/Android.

```html
<div class="safe-top">Safe area top</div>
<div class="safe-bottom">Safe area bottom</div>
```

---

##### 🎨 Typography

##### **Typography Pro**
Utilities for text balance, fluid headers, and advanced clamp-based sizing.

```html
<h1 class="text-balance">Balanced text</h1>
<h1 class="text-fluid-2xl">Fluid heading</h1>
```

---

##### **Typography Styles**
Custom typography styles for `@tailwindcss/typography` plugin.

```html
<article class="prose prose-custom">
  <h1>Styled heading</h1>
  <p>Styled paragraph</p>
</article>
```

---

##### 🎬 Specialized Animations

##### **Dark Mode Transitions**
Smooth transitions when switching themes.

```html
<div class="dark-mode-transition">
  Content transitions smoothly
</div>
```

---

##### **Scroll Animations**
Intersection Observer scroll-triggered animations.

```html
<div class="scroll-fade-in">Fades in on scroll</div>
<div class="scroll-slide-up">Slides up on scroll</div>
```

---

##### **Interaction Magnetism**
Subtle spring-loaded hover and active states.

```html
<button class="magnetic">Magnetic button</button>
<button class="magnetic-strong">Strong magnetic</button>
```

---

##### 🎨 Design System

##### **Theme Colors Extension**
Extends Tailwind's color palette with design system colors using CSS variables.

```html
<div class="bg-primary">Primary color</div>
<div class="text-accent">Accent text</div>
```

**Automatically supports light/dark mode** through CSS variables.

---

##### **Semantic Surface Depth**
Inner glows and layered shadows for physically nested components.

```html
<div class="surface-1">Level 1 surface</div>
<div class="surface-2">Level 2 surface</div>
<div class="surface-inset">Inset surface</div>
```

---

##### 🛠️ Development Tools

##### **Border Utilities**
Advanced border styles beyond Tailwind defaults.

```html
<div class="border-dashed-custom">Custom dashed</div>
<div class="border-gradient">Gradient border</div>
```

---

##### **CSS Shapes**
Pre-made shapes for quick prototyping.

```html
<div class="shape-triangle">Triangle</div>
<div class="shape-hexagon">Hexagon</div>
<div class="shape-star">Star</div>
```

---

##### **Print Utilities**
Print-specific styles.

```html
<div class="print:hidden">Hidden in print</div>
<div class="print:text-black">Black text in print</div>
```

---

##### **Debug Utilities**
Development helpers for debugging layouts.

```html
<div class="debug-grid">Shows grid overlay</div>
<div class="debug-outlines">Shows all outlines</div>
```

---

#### 🎯 Plugin Installation Methods Compared

##### **Separate File** (Recommended)
✅ Better organization  
✅ Easier to update  
✅ Can be shared across projects  
✅ Keeps config file clean  

```
project/
├── plugins/
│   ├── glassmorphism.ts
│   ├── animations.ts
│   └── scrollbar.ts
└── tailwind.config.js (imports from plugins/)
```

##### **Inline**
✅ Everything in one file  
✅ No extra files to manage  
❌ Config file gets large  
❌ Harder to maintain  

 
---

#### 🚀 Quick Start Examples

##### Modern SaaS Landing Page
```html
<section class="glass spotlight animate-fade-in-up">
  <h1 class="text-gradient-sunset text-fluid-2xl">
    Welcome to the Future
  </h1>
  <button class="neu-floating animate-pulse-ring">
    Get Started
  </button>
</section>
```

##### Dashboard Card
```html
<div class="glass-morphic scrollbar hover:animate-lift">
  <div class="skeleton-text animate-shimmer"></div>
</div>
```

##### Interactive Product Card
```html
<div class="spotlight-strong neu-floating">
  <img src="product.jpg" class="ken-burns" />
  <button class="active:animate-tap">Add to Cart</button>
</div>
```

---

#### 📊 Plugin Count by Category

- **Animations**: 25+ plugins
- **Visual Effects**: 10+ plugins
- **Layout Utilities**: 8+ plugins
- **Typography**: 3+ plugins
- **Accessibility**: 4+ plugins
- **Development Tools**: 5+ plugins
- **Backgrounds**: 6+ plugins
- **3D/Advanced**: 4+ plugins

**Total: 60+ production-ready plugins**

---

#### 🔄 Updates & Maintenance

All plugins are:
- ✅ TypeScript-ready
- ✅ Dark mode compatible
- ✅ Purge-safe (no unused CSS)
- ✅ Modern browser compatible
- ✅ Accessibility-friendly

---
 