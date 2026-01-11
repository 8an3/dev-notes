## CATALYST UI LIBRARY

## Table of Contents

- [Catalyst UI](#catalyst-ui)
- [Insert Component via Editor Context Menu](#insert-component-via-editor-context-menu)
- [Insert Component via Quick Pick](#insert-component-via-quick-pick)
- [Install Library Through Extension](#install-library-through-extension)


### Catalyst UI

Overview


A comprehensive UI component library with 1808+ components spanning free and premium tiers. Currently features 193 free components alongside extensive development tools.

**Access:** Shortcut available through title pane

**Website:** [Catalyst Software](https://catalyst-software.vercel.app/Catalyst/UI)

##### Features

**Component Library:**
- Search and filter capabilities
- Component viewer with live preview
- React sandbox environment
- One-click library installation with Tailwind configuration
- Option to install components only (without full setup)

##### Built-in Tools

**Development Environment:**
- **Sandbox** - Live React/Tailwind development environment with accessible libraries inventory
  - ![Live Playground 1](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/tools/live-playground1.png?raw=true)
  - ![Live Playground 2](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/tools/live-playground.png?raw=true)

**Utility Tools:**
- Color Wheel
- MD Reference Sheet
- Icons Library
- VS Code Commands Reference
- Tailwind CSS v3 ↔ v4 Converter
- Tailwind and VS Code Theme Builder
- Code Formatters
- Catalyst Editor
- Encoder/Decoder

**Reusable Project Tools:**
All tools are designed to be integrated into your own projects for extended functionality.


### Insert Component via Editor Context Menu

Access the entire 1808+ component library directly from the editor context menu, inserting components at your cursor position.


**Access:** Right-click → Catalyst UI → Select component

![Context Menu](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/ui/context-menu.png?raw=true)


### Insert Component via Quick Pick

Quick pick menu with search capabilities featuring a nested list of all available components for fast insertion at cursor


**Access:** Click UI button on status bar → Select component

![Quick Pick](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/ui/quickpick.jpg)


### Installing Catalyst-UI Components

A comprehensive React component library with 100+ production-ready components for building modern web applications.

## Installation

### Quick Start

Install a single component:

```bash
bunx @catalystsoftware/ui button
```

### Menu

```bash
bunx @catalystsoftware/ui
```

Then select from the interactive menu:
- **Full Install** - Components + Libraries + Tailwind + PostCSS
- **Full Install with Ngin** - Includes 18,000 Tailwind config presets
- **Components + Libraries** - Install without config files
- **Configure Tailwind + PostCSS** - Setup only
- **Configure Tailwind + PostCSS w/ ngin** - Setup with preset that contains 18,000 configurations set with only 3 variables
- **Select Components** - Choose specific components
- **Create Config** - Creates config file that can be used in conjuction with the bunx command

## Premium Access

Unlock the full component library with a premium access key:


Premium features include:
- Access to all 2000+ components
- Advanced interactive components
- Specialized tools and utilities
- Priority updates

## Component Categories

### Primitives
Core UI components following modern design patterns:
- Button, Input, Select, Checkbox, Radio, Switch
- Dialog, Sheet, Popover, Tooltip
- Card, Badge, Avatar, Separator
- Accordion, Tabs, Collapsible
- And more...

### Forms
Advanced form components with validation:
- Input variants (masked, OTP, password)
- Date pickers and calendars
- File uploads and dropzone
- Toggle groups and button groups

### Data Display
Components for presenting data:
- Tables with sorting and filtering
- Charts and data visualizations
- Timeline and progress indicators
- Empty states and skeletons

### Navigation
Navigation and layout components:
- Menus and navigation bars
- Breadcrumbs and pagination
- Sidebars and dual sidebars
- Command palette

### Feedback
User feedback components:
- Alerts and notifications
- Toast messages
- Loading spinners
- Progress indicators

### Interactive
Advanced interactive elements:
- Drag and drop
- Resizable panels
- Image zoom and crop
- Code editors with syntax highlighting

### Utilities
Helper components and hooks:
- Custom hooks (useTimer, useCopyToClipboard, etc.)
- Auth utilities
- Server middleware
- Context management

## Package Managers

Catalyst UI automatically detects and uses your package manager:
- npm
- pnpm
- yarn

## Configuration

### Config File (Optional)

Create a `catalyst.config.jsonc` file in your project root to customize installation behavior:

```bash
bunx @catalystsoftware/ui
# Select: Create Config File
```

Or create it manually:

```jsonc
// catalyst.config.jsonc
{
    "theme": "blue",                      // presetting the theme
    "preset": "MODERN",                   // presetting the preset
    "font": "Geist",                      // presetting the font
    "all-components": false,              // auto-install all on `bunx @catalystsoftware/ui`
    "install-tailwind": true,             // install Tailwind dependencies
    "configure-tailwind": true,           // create and paste .css file
    "configure-tailwind.config": true,    // true, "ngin", or false
    "install-postcss": true,              // install PostCSS dependencies
    "configure-postcss": true,            // create postcss.config.js
    "css": "app/routes/styles/tailwind.css",  // CSS file location
    "components": "app/"                  // components folder location
}
```

### Config Options Explained

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `theme` | string | `"blue"` | Default theme color |
| `preset` | string | `"MODERN"` | Default preset style |
| `font` | string | `"Geist"` | Default font family |
| `all-components` | boolean | `false` | Auto-install all components when running `bunx @catalystsoftware/ui` |
| `install-tailwind` | boolean | `true` | Install Tailwind CSS and related dependencies |
| `configure-tailwind` | boolean | `true` | Create the tailwind.css file at specified location |
| `configure-tailwind.config` | boolean\|"ngin" | `true` | `true` for basic config, `"ngin"` for 18k presets, `false` for none |
| `install-postcss` | boolean | `true` | Install PostCSS dependencies |
| `configure-postcss` | boolean | `true` | Create postcss.config.js file |
| `css` | string | `"app/routes/styles/tailwind.css"` | Path and filename for tailwind.css |
| `components` | string | `"app/"` | Base directory for components folder |

### Auto-Install with Config

Once you have a config file with `"all-components": true`, simply run:

```bash
bunx @catalystsoftware/ui
```

This will automatically:
1. Install all components to your specified components directory
2. Install required dependencies (if enabled)
3. Configure Tailwind CSS (if enabled)
4. Configure PostCSS (if enabled)
5. Create utils file

No menu selection needed!

### Tailwind Setup

Catalyst UI includes pre-configured Tailwind setups:

**Standard Configuration:**
```bash
bunx @catalystsoftware/ui
# Select: Configure Tailwind + PostCSS
```

**Ngin Configuration** (18,000 presets):
```bash
bunx @catalystsoftware/ui
# Select: Configure with Ngin
```

Or set in config:
```jsonc
{
    "configure-tailwind.config": "ngin"
}
```

### Utils File

All installations automatically create a `components/catalyst-ui/utils/utils.ts` file with helper functions:
- `cn()` - Class name merger
- `focusInput` - Focus styles
- `focusRing` - Focus ring utilities
- `formatDate()` - Date formatting


## Requirements

- React 18+
- Tailwind CSS 3+
- Node.js 16+

### Utils File

All installations automatically create a `utils/utils.ts` file with helper functions:
- `cn()` - Class name merger
- `focusInput` - Focus styles
- `focusRing` - Focus ring utilities
- `formatDate()` - Date formatting

## Examples

### Installing a Button Component

```bash
bunx @catalystsoftware/ui button
```

This will:
1. Create `/components/catalyst-ui/primitives/button.tsx`
2. Install required dependencies (extracted from component imports)
3. Create `utils/utils.ts` if it doesn't exist

### Using the Button Component

```tsx
import { Button } from '~/components/catalyst-ui';

export default function MyPage() {
  return (
    <Button 
      variant="default"
      size="lg"
      onClick={() => console.log('clicked')}
    >
      Click Me
    </Button>
  );
}
```

### Installing Multiple Components

```bash
bunx @catalystsoftware/ui
# Select: Select Components
# Choose from the list
```

## Component Import Paths

All components use the centralized import path:

```tsx
import { Button, Card, Dialog } from '~/components/catalyst-ui';
```

Or import directly from category folders:

```tsx
import { Button } from '~/components/catalyst-ui/primitives';
import { useTimer } from '~/components/catalyst-ui/hooks';
```

## Features

- **TypeScript First** - Full TypeScript support with type definitions
- **Accessible** - Built with accessibility in mind following WAI-ARIA standards
- **Customizable** - Highly customizable with Tailwind CSS
- **Tree-shakeable** - Import only what you need
- **Dark Mode** - Built-in dark mode support
- **Responsive** - Mobile-first responsive design
- **Zero Config** - Works out of the box with sensible defaults

## Dependencies

Components automatically install their required dependencies. Common dependencies include:
- `@radix-ui/react-*` - Primitive components
- `class-variance-authority` - Variant management
- `clsx` & `tailwind-merge` - Class name utilities
- `lucide-react` - Icons
- `framer-motion` - Animations (where applicable)

## File Structure

After installation, your project will have:

```
your-project/
├── components/
│   └── catalyst-ui/
│       ├── primitives/
│       ├── forms/
│       ├── overlays/
│       ├── hooks/
│       ├── utils/
│       │   └── utils.ts
│       └── index.ts
└── (optional config files)
    ├── tailwind.config.js
    └── postcss.config.js
```

## Support

For issues, questions, or feature requests, please visit our documentation or contact support.

## License

MIT License - See LICENSE file for details


---
[🡄 Return](https://github.com/8an3/DevStack)