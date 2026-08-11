# THOR

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Vanilla Tailwind

```
/* 
╭─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│                                              Vanilla Tailwind Ngin                                                  │
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│  A fully configured Tailwind engine providing access to 46,060+ design combinations. By adjusting just three        │ 
│  values, you can transform the entire visual identity of your application.                                          │ 
│                                                                                                                     │ 
│  1. THEME:  Sets the core color palette with 47 to choose from (Brand, Semantic, and Accent colors).                │ 
│  2. PRESET: Defines the "feel"—adjusting spacing, margins, and border-radius across 15 distinct systems.            │ 
│  3. FONT:   Select from 70+ curated typefaces optimized for readability and style.                                  │ 
│                                                                                                                     │  
│  Only selected assets are bundled into your build, ensuring maximum performance with zero runtime bloat.            │ 
│  Other values that can be, but are not required to configure:                                                       │  
│  4. USE_CUSTOM_TYPOGRAPHY & TYPOGRAPHY                                                                              │
│  4. USE_FONT_WEIGHTS & FONT_WEIGHTS                                                                                 │
│  5. ENVIROMENT                                                                                                      │  
│  6. COLORS & CUSTOM_THEME                                                                                           │  
│                                                                                                                     │  
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                                     │ 
│  Please select each of the following:                                                                               │ 
│  1. Theme                                                                                                           │ 
│  2. Preset                                                                                                          │ 
│  3. Font ( Not required, if left blank will default to the themes default )                                         │ 
│                                                                                                                     │ 
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                    PRESET                                                           │ 
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ 1. MODERN                       - Refined & Professional, tight, clean, high-performance feel.                      │ 
│                                 - 15% smaller spacing, tight layouts - Geist, Inter, Plus Jakarta Sans              │ 
│                                                                                                                     │ 
│ 2. CREATIVE                     - Lots of breathing room and very round shapes.                                     │ 
│                                 - Soft & Elegant - Outfit, Playfair Display, Montserrat                             │ 
│                                                                                                                     │ 
│ 3. TECHNICAL                    - Square corners, consistent spacing, "IDE" feel.                                   │ 
│                                 - Precision & Focus - JetBrains Mono, Fira Code, Geist Mono                         │ 
│                                                                                                                     │ 
│ 4. FINTECH                      - Maximum information density for dashboards.                                       │ 
│                                 - Data Heavy - IBM Plex Mono (numbers), Roboto, Source Code Pro                     │ 
│                                                                                                                     │ 
│ 5. LUXURY                       - Characterized by extreme letter spacing, thin borders, and huge breathing room.   │ 
│                                 - High-end & Sophisticated - Playfair Display, Lora, Montserrat (for subheaders)    │ 
│                                                                                                                     │ 
│ 6. BRUTALIST                    - Thick borders, no rounding, and high-contrast sizing.                             │ 
│                                 - Bold, Raw, & Experimental - Space Grotesk, IBM Plex Mono, Roboto Mono             │ 
│                                                                                                                     │ 
│ 7. EDITORIAL                    - Focuses on vertical rhythm and classic typesetting.                               │ 
│                                 - The New Yorker / Magazine Style - Source Serif 4, Merriweather, Libre Baskerville │ 
│                                                                                                                     │ 
│ 8. PLAYFUL                      - Thick "bouncy" borders and very round shapes.                                     │ 
│                                 - Mobile-First / Duolingo Style - Nunito, Delius Swash Caps, Poppins                │ 
│                                                                                                                     │ 
│ 9. MINIMALIST                   - Ultra-clean with subtle refinements, maximum clarity.                             │ 
│                                 - Calm & Spacious - SF Pro Display, Helvetica Neue, Inter                           │ 
│                                                                                                                     │ 
│ 10. GAMING                      - Aggressive sizing with heavy weights, cinematic impact.                           │ 
│                                 - Bold & Energetic - Rajdhani, Orbitron, Teko                                       │ 
│                                                                                                                     │ 
│ 11. MEDICAL                     - Clean, trustworthy, optimized for clinical readability.                           │ 
│                                 - Professional & Reliable - Source Sans Pro, Open Sans, Lato                        │ 
│                                                                                                                     │ 
│ 12. ECOMMERCE                   - Product-focused with strong visual hierarchy for pricing and CTAs.                │ 
│                                 - Conversion Optimized - Proxima Nova, Avenir, Work Sans                            │ 
│                                                                                                                     │ 
│ 13. CORPORATE                   - Conservative spacing with traditional letter-spacing for enterprise trust.        │ 
│                                 - Authoritative & Traditional - Calibri, Arial, Segoe UI                            │ 
│                                                                                                                     │ 
│ 14. RETRO                       - Squared-off with chunky weights, arcade and 80s computing aesthetics.             │ 
│                                 - Nostalgic & Pixel-Perfect - Press Start 2P, VT323, Courier Prime                  │
│                                                                                                                     │ 
│*/                                             PRESET = 'MODERN'                                                   /*│ 
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                       FONT                                                          │ 
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ SANS-SERIF     - Inter, Roboto, Geist, Poppins, Montserrat, Outfit, Plus Jakarta Sans, DM Sans, Urbanist,           │ 
│                  Nunito, Lato, Barlow, Gabriela, Delius Swash Caps, Public Sans, Work Sans, Manrope, Figtree,       │ 
│                  Archivo                                                                                            │ 
│                                                                                                                     │ 
│ SERIF          - Merriweather, Playfair Display, Lora, Source Serif 4, Libre Baskerville, Space Grotesk,            │ 
│                  PT Serif, Fraunces, Cormorant Garamond, Crimson Pro, EB Garamond, Newsreader, DM Serif Display,    │ 
│                  Prata, Bodoni Moda, Young Serif                                                                    │ 
│                                                                                                                     │ 
│ MONO           - JetBrains Mono, Fira Code, Geist Mono, IBM Plex Mono, Roboto Mono, Space Mono,                     │ 
│                  Source Code Pro, Ubuntu Mono, Red Hat Mono, Cutive Mono, Nanum Gothic Coding                       │ 
│                                                                                                                     │ 
│ DISPLAY        - Sora, Bricolage Grotesque, Clash Display, Syne, Unbounded, Cabinet Grotesk, Righteous,             │ 
│                  Lexend, Kanit                                                                                      │ 
│                                                                                                                     │ 
│*/                                                FONT = 'Geist'                                                   /*│ 
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                        THEME                                                        │ 
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                                     │ 
│                     Cirrus-Float                  Synthwave-Neon                        Geek-Blue                   │
│                  Metropolis-Sky-Scape                Solar-Flare                       Desert-Night                 │
│                   Mainframe-Terminal                Amazon-Jungle                    Cyber-Industrial               │
│                      Sonic-Pulse                     Cobalt-Ice                        Forest-Tech                  │
│                     Solstice-Heat                   Midas-Touch                       Oceanic-Sunset                │
│                      Polymer-Flow                  Amethyst-Stone                      Deep-Emerald                 │
│                    Vanguard-Strike                 Smoldering-Ember                  Deep-Sea-Navigator             │
│                     Tactical-Ops                     Acid-Trip                         Glacier-Blue                 │
│                     Meadow-Whisper                      Loki                        High-Alert-Crimson              │
│                    Studio-Apartment                   Silk-Petal                        Cyber-Pop                   │ 
│                      Terra-Verde                    Aqua-Glacier                       Forest-Tech-2                │
│                   Black-Velvet-Luxe                Nightshade-Venom                    Frozen-Deep                  │
│                     Blueprint-Grid                Another-Acid-Trip                    Pastel-Sorbet                │
│                     Sorbet-Swirl                      Deep-Abyss                       Modern-Retro                 │
│                     Office-Paper                  Fifth-Element-Aether                 Obsidian-Wine                │
│                    Twilight-Bloom                    True-Veridian                     Mineral-Forest               │
│                    Afterglow-Fade                     Deep-Teal                          Deep-Ocean                 │
│                  Monet-Impressionism              Interstellar-Nebula                   Retro-Arcade                │
│                     Espresso-High                    Granite-Top                       Vintage-Heritage             │
│                    Executive-Level                  Ti-Titanium-22                     Oceanic-Gradient             │
│                   Workplace-Chatter             Graphite-Neutron-Moderator              Crystal-Quartz              │
│                     Oracle-Vision                   Concrete-slab                         Deep-Void                 │
│                   Middle-Field-Canvas                 C-Carbon-6                         Dark-Crimson               │
│                                                                                                                     │ 
│                                                                                                                     │ 
│*/                                               THEME = 'Deep-Void'                                               /*│  
│*/                                                  MODE = 'dark'                                                  /*│ 
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                     TYPOGRAPHY                                                      │ 
│                                                                                                                     │ 
│ If you would like to use other values instead of the provide options that are available through the ngin, you may   │
│ configure the following objects and values.                                                                         │ 
│                                                                                                                     │ 
│*/ USE_CUSTOM_TYPOGRAPHY = false                                                                                   /*│
│*/ TYPOGRAPHY = {                                                                                                  /*│ 
│*/    h1: {                                                                                                        /*│ 
│*/      fontSize: "1.875rem",                                                                                      /*│ 
│*/      fontWeight: "700",                                                                                         /*│ 
│*/      lineHeight: "1.25",                                                                                        /*│ 
│*/      letterSpacing: "-0.025em",                                                                                 /*│ 
│*/      textAlign: "center",                                                                                       /*│ 
│*/      "@media (min-width: 1024px)": {                                                                            /*│ 
│*/        lineHeight: "1.1",                                                                                       /*│ 
│*/      },                                                                                                         /*│ 
│*/    },                                                                                                           /*│ 
│*/    h2: {                                                                                                        /*│ 
│*/      marginTop: "0.75rem",                                                                                      /*│ 
│*/      color: "hsl(var(--muted-foreground))",                                                                     /*│ 
│*/      fontWeight: "300",                                                                                         /*│ 
│*/      textAlign: "center",                                                                                       /*│ 
│*/    },                                                                                                           /*│ 
│*/    h3: {                                                                                                        /*│ 
│*/      fontWeight: "600",                                                                                         /*│ 
│*/      marginBottom: "1rem",                                                                                      /*│ 
│*/      marginTop: "1rem",                                                                                         /*│ 
│*/    },                                                                                                           /*│ 
│*/    h4: {                                                                                                        /*│ 
│*/      fontSize: "1.25rem",                                                                                       /*│ 
│*/      fontWeight: "600",                                                                                         /*│ 
│*/      marginBottom: "0.75rem",                                                                                   /*│ 
│*/      marginTop: "0.75rem",                                                                                      /*│ 
│*/    },                                                                                                           /*│ 
│*/    h5: {                                                                                                        /*│ 
│*/      fontSize: "1.125rem",                                                                                      /*│ 
│*/      fontWeight: "500",                                                                                         /*│ 
│*/      marginBottom: "0.5rem",                                                                                    /*│ 
│*/      marginTop: "0.5rem",                                                                                       /*│ 
│*/    },                                                                                                           /*│ 
│*/    p: {                                                                                                         /*│ 
│*/      textWrap: "balance",                                                                                       /*│ 
│*/      fontWeight: "300",                                                                                         /*│ 
│*/      color: "hsl(var(--foreground))",                                                                           /*│ 
│*/      fontSize: "0.875rem",                                                                                      /*│ 
│*/    },                                                                                                           /*│ 
│*/  }                                                                                                              /*│  
│                                                                                                                     │ 
│*/ USE_FONT_WEIGHTS = false                                                                                        /*│
│*/ FONT_WEIGHTS = {                                                                                                /*│
│*/    thin: "100",                                                                                                 /*│
│*/    light: "300",                                                                                                /*│
│*/    normal: "400",                                                                                               /*│
│*/    medium: "500",                                                                                               /*│
│*/    semibold: "600",                                                                                             /*│
│*/    bold: "700",                                                                                                 /*│
│*/    black: "900",                                                                                                /*│
│*/  }                                                                                                              /*│  
│                                                                                                                     │ 
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                     ENVIROMENT                                                      │ 
│                                                                                                                     │ 
│ Depending on what your building, the css will need to be built differently. For example if building a vscode        │
│ extension, it is a much wiser choice to use the already configured color theme that the user has chosen in place    │
│ of your own custom theme. Setting this value to VSCODE, will do just that.                                          │
│ "VSCODE" and "OTHER"                                                                                                │ 
│                                                                                                                     │ 
│*/ ENVIROMENT = "VSCODE"                                                                                           /*│ 
│                                                                                                                     │ 
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                    CUSTOM COLORS                                                    │ 
│                                                                                                                     │ 
│ If you would like to use your own theme in place of the available options, set colors to "CUSTOM" and you will      │
│ be free to set the values as you wish. The ngin expects the colors to be bare hsl strings without the use of 'hsl()'│ 
│ "CUSTOM" | "NGIN"                                                                                                   │ 
│                                                                                                                     │ 
│*/ COLORS = "NGIN"                                                                                                 /*│ 
│*/ CUSTOM_THEME = {                                                                                                /*│
│*/    "--background": '222.2 84% 4.9%',                                                                            /*│
│*/    "--foreground": '210 40% 98%',                                                                               /*│
│*/    "--card": '222.2 84% 4.9%',                                                                                  /*│
│*/    "--card-foreground": '210 40% 98%',                                                                          /*│
│*/    "--popover": '222.2 84% 4.9%',                                                                               /*│
│*/    "--popover-foreground": '210 40% 98%',                                                                       /*│
│*/    "--primary": '217.2 91.2% 59.8%',                                                                            /*│
│*/    "--primary-foreground": '222.2 47.4% 11.2%',                                                                 /*│
│*/    "--secondary": '217.2 32.6% 17.5%',                                                                          /*│
│*/    "--secondary-foreground": '210 40% 98%',                                                                     /*│
│*/    "--muted": '217.2 32.6% 17.5%',                                                                              /*│
│*/    "--muted-foreground": '215 20.2% 65.1%',                                                                     /*│
│*/    "--accent": '217.2 32.6% 17.5%',                                                                             /*│
│*/    "--accent-foreground": '210 40% 98%',                                                                        /*│
│*/    "--destructive": '0 62.8% 30.6%',                                                                            /*│
│*/    "--border": '217.2 32.6% 17.5%',                                                                             /*│
│*/    "--input": '217.2 32.6% 17.5%',                                                                              /*│
│*/    "--ring": '224.3 76.3% 48%',                                                                                 /*│
│*/    "--sidebar": "",                                                                                             /*│
│*/    "--sidebar-foreground": "",                                                                                  /*│
│*/    "--sidebar-primary": "",                                                                                     /*│
│*/    "--sidebar-primary-foreground": "",                                                                          /*│
│*/    "--sidebar-accent": "",                                                                                      /*│
│*/    "--sidebar-accent-foreground": "",                                                                           /*│
│*/    "--sidebar-border": "",                                                                                      /*│
│*/    "--sidebar-ring": "",                                                                                        /*│
│*/                                                                                                                 /*│
│*/    "--chart-1": '220 70% 50%',                                                                                  /*│
│*/    "--chart-2": '160 60% 45%',                                                                                  /*│
│*/    "--chart-3": '30 80% 55%',                                                                                   /*│
│*/    "--chart-4": '280 65% 60%',                                                                                  /*│
│*/    "--chart-5": '340 75% 55%',                                                                                  /*│
│*/                                                                                                                 /*│
│*/    "--font-sans": "",                                                                                           /*│
│*/    "--font-serif": "",                                                                                          /*│
│*/    "--font-mono": "",                                                                                           /*│
│*/                                                                                                                 /*│
│*/    "--radius": '0.5rem',                                                                                        /*│
│*/                                                                                                                 /*│
│*/    "--shadow-color": "",                                                                                        /*│
│*/    "--shadow-opacity": "",                                                                                      /*│
│*/    "--shadow-blur": "",                                                                                         /*│
│*/    "--shadow-spread": "",                                                                                       /*│
│*/    "--shadow-offset-x": "",                                                                                     /*│
│*/    "--shadow-offset-y": "",                                                                                     /*│
│*/  }                                                                                                              /*│ 
│                                                                                                                     │ 
│                                                                                                                     │ 
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│ The following configurable values are for the 1% use cases and are more here due to the preset ngin already coded   │
│ to have these included but instead of removing them I have decided to include them just incase they are needed in   │
│ the future. In other words, if you are not editing the code, do not change these values.                            │ 
│*/ THEME_SWITCHER = false                                                                                          /*│ 
│*/ VERSION = 'v3'                                                                                                  /*│ 
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
*/
```


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Tailwind CSS
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

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Tailwind Config
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

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Tailwind Config Preset Ngin
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
 

> [!IMPORTANT]
> VSCode, for some reason, will display the below warning.
>
> Ignore this warning, as it is a false positive. You can see for yourself, that whatever font you select will infact work. 
>
> Obviously, its properly coded or else it would simply not work. I have tried to code it in a way where this warning does not show up, but can't find another solution. 
>
> Till I find a solution that still works, without this warning, we will have to live with this displaying in our terminals.


![Z](https://raw.githubusercontent.com/8an3/midgardr-notes/main/vfs/tailwind-config-preset-warning.png)


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

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Tailwind V4 Plug-in
It's just plug and play, and drop a v4 configured component into your project.

> [!IMPORTANT]
> Some changes were made, simply I misread part of the docs and instead of adding to, I was replacing v3 features. That is now fixed, all v3 features have been preserved. In order to preseve those features, prefixes have been implemented for v4 features that would otherwise create a collision. Kinda sucks, but the main goal was to ADD v4 features and not replace v3. 
>
> **Prefixes used to avoid v3 conflicts:**
> 
> 1. **`bg-v4-`** - color-mix backgrounds (e.g., `bg-v4-red-500`)
> 2. **`text-v4-`** - color-mix text colors (e.g., `text-v4-blue-600`)
> 3. **`border-v4-`** - color-mix border colors (e.g., `border-v4-gray-300`)
> 4. **`outline-v4-`** - color-mix outline colors (e.g., `outline-v4-purple-500`)
> 5. **`.container-v4`** - v4 container with container-type (v3 `.container` stays unchanged)
> 6. **`mb-v4-`** - margin-block logical property (v3 `mb-` is margin-bottom)
> 7. **`pb-v4-`** - padding-block logical property (v3 `pb-` is padding-bottom)
> 8. **`inset-b-v4-`** - inset-block logical property (v3 `inset-b-` conflicts)
>
> Also a hard learned lesson, no matter what amount of plugins or lack there of, that you have currently in your config... the v4 plugin must be declared FIRST amongst the plugins.


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

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Tailwind Plugin Library (Ngin) - Documentation

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



## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> CSS

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


