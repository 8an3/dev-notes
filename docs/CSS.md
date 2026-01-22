# THOR 

## tailwind.config.js

Creates a basic tailwind.config.js file pre configured with animations, etc.
### postcss.config.js, taiwlind.css
These files are created the same as the above mentioned files. While nothing can really be done for the postcss.config.js file, tailwind.css does host a number of modifications such as a themed scroll bar.

## tailwind.config preset ngin
Creates a config file that features optoins to customize font, theme and preset and controlling it with only 3 variables. Granting access to over 18,000 configurations all from one file.
The top of the file is where you will find the variables to set:

```javascript
// =====================================================================================================================================================
// ====================================================== SELECT A PRESET, FONT & THEME ================================================================ 
// PRESET - Change this to switch between design systems:
// 1. MODERN     - "MODERN SAAS" Refined & Professional, tight, clean, high-performance feel. (15% smaller spacing, tight layouts)  - Best paired font: Geist, Inter, Plus Jakarta Sans  
// 2. CREATIVE   - "CREATIVE STUDIO" Lots of breathing room and very round shapes. (Soft & Elegant)                                 - Best paired font: Outfit, Playfair Display, Montserrat
// 3. TECHNICAL  - Square corners, consistent spacing, "IDE" feel. (Precision & Focus)                                              - Best paired font: JetBrains Mono, Fira Code, Geist Mono
// 4. FINTECH    - "FINTECH DENSE" Maximum information density for dashboards. (Data Heavy)                                         - Best paired font: IBM Plex Mono (numbers), Roboto, Source Code Pro
// 5. LUXURY     - Characterized by extreme letter spacing, thin borders, and huge breathing room. (High-end & Sophisticated)       - Best paired font: Playfair Display, Lora, Montserrat (for subheaders)
// 6. BRUTALIST  - Thick borders, no rounding, and high-contrast sizing. (Bold, Raw, & Experimental)                                - Best paired font: Space Grotesk, IBM Plex Mono, Roboto Mono
// 7. EDITORIAL  - Focuses on vertical rhythm and classic typesetting. (The New Yorker / Magazine Style)                            - Best paired font: Source Serif 4, Merriweather, Libre Baskerville
// 8. PLAYFUL    - Thick "bouncy" borders and very round shapes. (Mobile-First / Duolingo Style)                                    - Best paired font: Nunito, Delius Swash Caps, Poppins     
const SELECTED_PRESET = 'MODERN'

// =================================================================== FONTS ============================================================================ 
// Sans-serif: Inter | Roboto | Geist | Poppins | Montserrat | Outfit | Plus Jakarta Sans | DM Sans | Nunito | Lato | Barlow | Gabriela | Delius Swash Caps | Barlow | Public Sans | Work Sans | Manrope | Urbanist | Figtree | Archivo
// Serif: Merriweather | Playfair Display | Lora | Source Serif 4 | Libre Baskerville | Space Grotesk | PT Serif | Fraunces | Cormorant Garamond | Crimson Pro | EB Garamond | Newsreader | DM Serif Display | Prata | Bodoni Moda | Young Serif
// Mono: JetBrains Mono | Fira Code | Geist Mono | IBM Plex Mono | Roboto Mono | Space Mono | Source Code Pro | Ubuntu Mono | Red Hat Mono | Nanum Gothic Coding | Cutive Mono
// Sand-Serif ( display & experimental ): Sora | Bricolage Grotesque | Clash Display | Syne | Unbounded | Cabinet Grotesk | Righteous | Lexend | Kanit
const SELECTED_FONT = 'Fira Code'

// ==================================================================== THEME =========================================================================== 
// Themes: marshmallow | art-deco | vs-code | spotify | summer | material-design | marvel | valorant | ghibli-studio | modern-minimal | nature | elegant-luxury | neo-brutalism | pastel-dreams | clean-slate | midnight-bloom | sunset-horizon | claude | caffeine | corporate | slack | perplexity | neutral | red | rose | orange | green | blue | yellow | violet | amber | lime | emerald | fuchsia | cyan | indigo | lime | darkBlue

// or if you would just like to include your own set the value to 'css' and you may set your own theme in the .css file
const SELECTED_THEME = 'blue'
```

## Plugins

Selecting any one of the plugins mentioned in the list will create a file with the desired plugin. Once created, you just need to install it in your tailwind.config.js file like so:

```javascript
export default {
	darkMode: ["class"],
	content: ["./app/**/*.{js,jsx,ts,tsx}"],
	theme: {
        ...options,
    },
	plugins: [
	    v3ToV4Plugin, // plugin
		require("tailwindcss-animate"),
		require("@tailwindcss/typography")
	]
} satisfies Config;
```

Current available plugins include: 
- Animation Library ........... One comprehensive solution
- AI/ML UI Patterns............ Modern UI patterns for AI interfaces 
- Framer Motion Helpers........ Tailwind utilities optimized for Framer Motion animations
- Radix UI Integration......... Pre-styled utilities for Radix UI primitives 
- Tailwind PlugIn for V3 Users . Complete v4 feature set in v3 - container queries, scroll animations, modern CSS, logical properties, its available for download, but I haven't had time to test yet, but will soon because tbh, I'm tired of switching things over from v4 to work in v3. docs but not tested 
- Scrollbar Styles ............ Customizable scrollbar utilities
- Bento Grid Plugin ........... Apple-style bento layouts
- Animated Gradient Borders ... Moving gradient borders (very trendy)
- Neumorphism Plugin .......... Soft UI / Neumorphism styles
- Spotlight Effect Plugin ..... Mouse-following spotlight (like on product pages)
- Glassmorphism ............... Frosted glass effect utilities
- Text Gradients .............. Gradient text utilities
- Custom Animations ........... Additional animation utilities
- Custom Shadows .............. Beautiful shadow utilities
- Background Gradient ......... Beautiful gradient backgrounds
- Aspect Ratios ............... Common aspect ratio utilities
- Glass & Surface Effects ..... Advanced backdrop blurs and reflective surface styles
- Modern Motion & Animation ... High-end animation utilities
- UI Comp Animations Plugin ... accordions, modals, dropdowns
- Attention Grabbers Plugin ... pulse, glow, bounce effects
- Loading States Plugin ....... shimmer, spin, progress
- Interaction Feedback Plugin . click, hover, drag
- Decorative Effects Plugin ... float, wiggle, sway
- Animations Plugin ........... gradients, particles
- Text Effects Plugin ......... typing, reveal, glitch
- Entrance/Exit Ani. Plugin ... accordions, modals, dropdowns
- Matrix/Rain Effect Plugin ... Welcome, Neo...
- Flip Card Plugin ............ Card tricks
- Heartbeat Plugin ............ Heartbeat utilities
- Marquee/Scroll Plugin ....... Marquee utilities
- Ken Burns Plugin ............ Ken Burns utilities zoom and pan
- Entrance Animations Plugin .. Entrance utilities
- Custom Shadows .............. Beautiful shadow utilities
- Background Gradients ........ Beautiful gradient backgrounds
- Aspect Ratios ............... Common aspect ratio utilities
- Border Utilities ............ Advanced border styles
- Scrollbar Plugin ............ Custom Styled scrollbar
- Theme Colors Plugin ......... Extended color palette
- Typography Styles Plugin .... Custom typography styles
- Typography Pro .............. Text balance and fluid headers
- Accordion Animations Plugin . Radix UI Accordion animations
- Caret Blink Plugin .......... Blinking cursor animation
- Glow Animations Plugin ...... Smooth floating animation
- Float Animation Plugin ...... Pulsing glow effects
- Shimmer & Shine Ani. Plugin . Loading shimmer effects
- Spin Animations Plugin ...... Rotation speed animations
- Fade Animations Plugin ...... Fade in/out animations
- Click Animation Plugin ...... Button press feedback
- Movement Animations Plugin .. Horizontal movement animations
- Gradient Flow Plugin ........ Animated gradient background
- Custom Easings Plugin ....... Additional easing functions curves
- Comprehensive Ani. Col. ..... Complete collefction of animations found within the library
- Custom Scrollbar ............ Themed scrollbar
- Skeleton/Placeholder Plugin . Pre-built skeleton components
- Micro-Interactions Plugin ... Subtle micro-interactions
- Spacing & Layout Helpers .... Modern spacing utilities
- Dark Mode Transitions ....... Smooth dark mode transitions plugin
- CSS Grid Helpers ............ Modern grid layouts
- Scroll Animations Plugin .... Scroll-triggered animations
- Focus States Plugin ......... Modern focus styles
- Clamp Utilities Plugin ...... Fluid responsive sizing
- Blend Mode Utilities ........ Modern blend modes
- Noise/Grain Texture Plugin .. Subtle texture overlays
- Container Queries Plugin .... Container query utilities
- 3D Transform Utilities ...... 3D perspective and transforms
- Backdrop Utilities .......... Extended backdrop filters
- CSS Shapes Plugin ........... Pre-made shapes
- Print Utilities ............. Print-specific styles
- Debug Utilities ............. Development helpers
- Architectural Layouts ....... Background patterns
- Masking & Cutouts Plugin .... Advanced CSS masking
- Mobile Safe Area Utilities .. Mobile-specific spacing
- Semantic Surface Depth ...... Inner glows and layered shadows
- Interaction Magnetism ....... Spring-loaded hover states
- Border Utilities ............ Advanced border styles

## CSS

> [!WARNING]
> Currently in testing
> Despite currently still in the testing phase, you are more than welcome to try it out.
> Initial and secondary tests were successful in remix-run and react-router platforms
> As this isn't platform dependant, any platform you currently use tailwind in should be able to use this without issue

### Features

✨ **JIT Compilation** - Only generates CSS for classes you actually use  
🎨 **Arbitrary Values** - Use any value with bracket notation: `w-[123px]`, `bg-[#ff0000]`, `text-[hsl(120_100%_50%)]`, `border-[rgb(0_0_255)]`  
⚡ **Lightning Fast** - Compiles in milliseconds  
👀 **Auto Watch Mode** - Automatically watches files in development  
🎯 **Config-Based** - Customize everything via `css.config.js`  **Not required**
🔥 **Zero Dependencies** - Minimal footprint  

### Installation

```bash
npm install @catalystsoftware/css-plus-plus --save-dev
pnpm install @catalystsoftware/css-plus-plus --save-dev
```

### app/styles/styles.css
```text
@css++;
```

#### postcss.config.js 

The one and only config I couldn't get rid of, since its due to a postcss requirement

```javascript
export default {
  plugins: {
    '@catalystsoftware/css-plus-plus/postcss': {},
  },
};

```

>Initial testing successful, did not have autoprefixer, postcss, or anything else style related installed. Just the single line css file and postcss-config.js with the above export, and ran perfectly. Will be conducting more thorough testing shortly.

### styles.css
To apply your own theme:
```css
@css++;

@layer css++ {
  :root {
    --background: #020817;
    --background-secondary: #111827;
    --foreground: #e2e8f0;
    --card: #020817;
    --card-foreground: #e2e8f0;
    --popover: #020817;
    --popover-foreground: #e2e8f0;
    --primary: #3b82f6;
    --primary-foreground: #111827;
    --secondary: #1e293b;
    --secondary-foreground: #e2e8f0;
    --muted: #1e293b;
    --muted-foreground: #94a3b8;
    --accent: #1e293b;
    --accent-foreground: #e2e8f0;
    --destructive: #7f1d1d;
    --destructive-foreground: #e2e8f0;
    --border: #1e293b;
    --input: #1e293b;
    --ring: #2563eb;
    --chart-1: #3b82f6;
    --chart-2: #10b981;
    --chart-3: #f59e0b;
    --chart-4: #a855f7;
    --chart-5: #ec4899;
    --radius: 0.0rem;
    --sidebar: 221 39% 11%;
    --sidebar-foreground: 220 20% 95%;
    --sidebar-primary: 217 91% 60%;
    --sidebar-primary-foreground: 220 20% 98%;
    --sidebar-accent: 220 30% 20%;
    --sidebar-accent-foreground: 220 20% 95%;
    --sidebar-border: 220 20% 25%;
    --sidebar-ring: 217 91% 60%;
    --special: 227 21% 8%;
    --special-muted-background: 240 10% 4%;
    --special-border: 240 4% 16%;
    --special-foreground: 240 5% 84%;
    --special-muted-foreground: 240 4% 46%;
  }

  .dark {
    /* Optional: Dark mode overrides */
    --background: #0a0a0a;
    --foreground: #ededed;
  }
}

/* User's custom styles below */
.my-custom-class {
  background: var(--primary);
  color: var(--foreground);
}
```

### Config Paths ( Not required )
- css.config.js
- css.config.mjs
- css.config.cjs
- csspp.config.js
- csspp.config.mjs
- csspp.config.cjs

### Quick Start - < 60 Seconds

#### For Remix Projects

```bash
# 1. Import CSS (app/root.tsx)
import styles from "~/styles/generated.css?url";

export const links = () => [
  { rel: "stylesheet", href: styles },
];

# 2. Done! Run dev server
npm run dev
```

**That's it!** CSS++ automatically:
- ✅ Creates `dist/generated.css`
- ✅ Watches for changes
- ✅ Hot-reloads instantly

---

#### For Next.js Projects

```bash
# 1. Import in layout (app/layout.tsx)
import './styles/generated.css';

# 2. Done! Run dev server
npm run dev
```

---

#### For Vite Projects

```bash
# 1. Import in main (src/main.js)
import './generated.css';

# 2. Done!
npm run dev
```

---

#### For Any Project (Manual)

```bash
# 1. Add script (package.json)
{
  "scripts": {
    "dev": "css++ & your-dev-command"
  }
}

# 2. Create config (css.config.js) - OPTIONAL!
export default {
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  output: "./dist/output.css",
};

# 3. Import CSS in HTML
<link rel="stylesheet" href="/dist/output.css">

# 4. Done!
npm run dev
```

---

#### Zero Config Mode

**No config file needed!** CSS++ uses smart defaults:

```javascript
// Automatic defaults
const defaultConfig = {
    darkMode: ["class"],
    content: [
        "./app/**/{**,.client,.server}/**/*.{js,jsx,ts,tsx}", // Remix
        "./src/**/*.{html,js,jsx,ts,tsx}", // Vite/CRA
        "./components/**/*.{js,jsx,ts,tsx}",
        "./pages/**/*.{js,jsx,ts,tsx}", // Next.js
    ],
    output: "./dist/generated.css",
    theme: {
        extend: {
            fontFamily: {
                sans: [
                    'Inter',
                    'ui-sans-serif',
                    'system-ui',
                    'sans-serif',
                    'Apple Color Emoji',
                    'Segoe UI Emoji',
                    'Segoe UI Symbol',
                    'Noto Color Emoji'
                ]
            },
            borderRadius: {
                lg: 'var(--radius)',
                md: 'calc(var(--radius) - 2px)',
                sm: 'calc(var(--radius) - 4px)'
            },
            colors: {
                border: "var(--border)",
                input: "var(--input)",
                ring: "var(--ring)",
                background: "var(--background)",
                foreground: "var(--foreground)",
                primary: {
                    DEFAULT: "var(--primary)",
                    foreground: "var(--primary-foreground)",
                },
                secondary: {
                    DEFAULT: "var(--secondary)",
                    foreground: "var(--secondary-foreground)",
                },
                destructive: {
                    DEFAULT: "var(--destructive)",
                    foreground: "var(--destructive-foreground)",
                },
                muted: {
                    DEFAULT: "var(--muted)",
                    foreground: "var(--muted-foreground)",
                },
                accent: {
                    DEFAULT: "var(--accent)",
                    foreground: "var(--accent-foreground)",
                },
                popover: {
                    DEFAULT: "var(--popover)",
                    foreground: "var(--popover-foreground)",
                },
                card: {
                    DEFAULT: "var(--card)",
                    foreground: "var(--card-foreground)",
                },
                sidebar: {
                    DEFAULT: "var(--sidebar)",
                    foreground: "var(--sidebar-foreground)",
                    primary: "var(--sidebar-primary)",
                    "primary-foreground": "var(--sidebar-primary-foreground)",
                    accent: "var(--sidebar-accent)",
                    "accent-foreground": "var(--sidebar-accent-foreground)",
                    border: "var(--sidebar-border)",
                    ring: "var(--sidebar-ring)",
                },
                chart: {
                    "1": "var(--chart-1)",
                    "2": "var(--chart-2)",
                    "3": "var(--chart-3)",
                    "4": "var(--chart-4)",
                    "5": "var(--chart-5)",
                },
                special: {
                    DEFAULT: "var(--special)",
                    "muted-background": "var(--special-muted-background)",
                    border: "var(--special-border)",
                    foreground: "var(--special-foreground)",
                    "muted-foreground": "var(--special-muted-foreground)",
                },
            },
            backgroundColor: {
                background: "var(--background)",
            },
            keyframes: {
                "accordion-down": {
                    from: { height: "0" },
                    to: { height: "var(--radix-accordion-content-height)" },
                },
                "accordion-up": {
                    from: { height: "var(--radix-accordion-content-height)" },
                    to: { height: "0" },
                },
                "caret-blink": {
                    "0%,70%,100%": { opacity: "1" },
                    "20%,50%": { opacity: "0" },
                },
                float: {
                    '0%, 100%': { transform: 'translateY(0px) scale(1)' },
                    '50%': { transform: 'translateY(-20px) scale(1.05)' },
                },
                "pulse-glow": {
                    '0%, 100%': { opacity: "0.3", transform: 'scale(1)' },
                    '50%': { opacity: "0.6", transform: 'scale(1.1)' },
                },
                shimmer: {
                    '0%': { backgroundPosition: '-200% 0' },
                    '100%': { backgroundPosition: '200% 0' },
                },
                "spin-slow": {
                    "0%": { transform: "rotate(0deg)" },
                    "100%": { transform: "rotate(360deg)" },
                },
                "spin-slower": {
                    "0%": { transform: "rotate(0deg)" },
                    "100%": { transform: "rotate(-360deg)" },
                },
                "matrix-fade": {
                    "0%, 100%": { opacity: "0" },
                    "50%": { opacity: "1" },
                },
                click: {
                    "0%, 100%": { transform: "scale(1)" },
                    "50%": { transform: "scale(0.95)" },
                },
            },
            animation: {
                "accordion-down": "accordion-down 0.2s ease-out",
                "accordion-up": "accordion-up 0.2s ease-out",
                "caret-blink": "caret-blink 1.25s ease-out infinite",
                "float": "float 6s ease-in-out infinite",
                "pulse-glow": "pulse-glow 4s ease-in-out infinite",
                "shimmer": "shimmer 2s infinite",
                "spin-slow": "spin-slow 3s linear infinite",
                "spin-slower": "spin-slower 6s linear infinite",
                matrix: "matrix-fade 0.5s ease-in-out infinite",
                click: "click 0.3s ease-in-out",
            },
            typography: {
                DEFAULT: {
                    css: {
                        h1: {
                            fontSize: "1.875rem",
                            fontWeight: "700",
                            lineHeight: "1.25",
                            letterSpacing: "-0.025em",
                            textAlign: "center",
                            "@media (min-width: 1024px)": { lineHeight: "1.1" },
                        },
                        h2: {
                            marginTop: "0.75rem",
                            color: "var(--muted-foreground)",
                            fontWeight: "300",
                            textAlign: "center",
                        },
                        h3: {
                            fontWeight: "600",
                            marginBottom: "1rem",
                            marginTop: "1rem",
                        },
                        h4: {
                            fontSize: "1.25rem",
                            fontWeight: "600",
                            marginBottom: "0.75rem",
                            marginTop: "0.75rem",
                        },
                        h5: {
                            fontSize: "1.125rem",
                            fontWeight: "500",
                            marginBottom: "0.5rem",
                            marginTop: "0.5rem",
                        },
                        p: {
                            textWrap: "balance",
                            fontWeight: "300",
                            color: "var(--foreground)",
                            fontSize: "0.875rem",
                        },
                    },
                },
            }
        },
    },
};
```

---

#### Usage Examples

```jsx
// Sizes
<div className="w-[300px] h-[200px]" />

// Colors
<div className="bg-[#ff0000] text-[rgb(255,255,255)] border-[hsl(120_100%_50%)]" />

// Spacing
<div className="p-[2rem] m-[10px] gap-[1.5rem]" />

// Borders
<div className="rounded-[16px] border-[2px]" />

// Everything!
<div className="
  w-[350px] 
  h-[75vh] 
  bg-[linear-gradient(to_right,#ff0000,#00ff00)]
  shadow-[0_4px_20px_rgba(0,0,0,0.1)]
  rotate-[45deg]
" />
```

---

#### With CSS Variables

```css
/* global.css */
:root {
  --primary: #3b82f6;
  --radius: 0.5rem;
}
```

```jsx
<div className="bg-[var(--primary)] rounded-[var(--radius)]" />
```

---

#### Custom Animations

**css.config.js**:
```javascript
export default {
  theme: {
    extend: {
      keyframes: {
        fadeIn: {
          "0%": { opacity: "0" },
          "100%": { opacity: "1" },
        },
      },
      animation: {
        "fade-in": "fadeIn 0.3s ease-in",
      },
    },
  },
};
```

**Usage**:
```jsx
<div className="animate-fade-in" />
```

---

#### FAQ

**Q: Do I need a config file?**  
A: No! Works out of the box.

**Q: Does it auto-watch?**  
A: Yes! In development mode.

**Q: Works with TypeScript?**  
A: Yes! Scans `.ts` and `.tsx` files.

**Q: Works with CSS-in-JS?**  
A: Yes! Detects classes in `className={}`.

**Q: Production builds?**  
A: Set `NODE_ENV=production` for minified output.

**Q: File size?**  
A: Only generates CSS you use (~5KB typical).

---


