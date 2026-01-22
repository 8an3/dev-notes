# HEPHAESTUS: Formerly known as CATALYST UI LIBRARY

# Editor Context Insert

# Quick Pick Insert

# Automated Installation


## UPDATE

Adding a new line option 'Configure Import Call'. Configures your package.json and tsconfig.json files to allow the use of '#icons' and '#catalyst' in-place of the traditional '~/components/catalyst-ui' and '@catalystsoftware/icons'

```javascript
import { Command, CommandGroup, CommandItem, CommandList, cn } from '#catalyst'
import { X } from '#icons'
```
Selecting the full installation will also configure your project for this use as well.

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

Create a `config.catalyst` file in your project root to customize installation behavior:

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


# Smart Prop Autocomplete

# Signature Help

# Hover Documentation

Whenever hovering over a components name a hovercard will appear with its relevant documentation, removing the need to ever visit the site again.

> [!NOTE] 
> There will be a few components that will have duplicate data within the hovercard. While it won't be an exact duplicate, they will however contain 2 sets of usage examples and props values. 
> This is due to the fact that prior to learning how to progmatically provide a solution through the vscode extension itself, which was accomplished very easily and with zero extra effort all the while it covers the entire inventory, I was manually coding it into the source code of each and every single component. 
> At this time I don't remember how I came across the vscode implementation because I wasn't able to test it for a while after coding it, but however it came to be... thank-you, lol. 
> As you have saved me from manually writing it for 2500+ components which... would have sucked to say the least.

# Auto Import

To auto import the component right click the components name where ever it may be used within the editor, select `Add Import` in the editor context menu. 

# Go To Definition

Using cmd & ctrl & clicking the components name will bring up the source codes file in a, sheet style dropdown? I don't what what you call this really, any how, it allows you to view the source code file without navigating to it, while at the same time double clicking anywhere inside the "dropdown sheet" will navigate you to the source code file itself.

# Missing Import Warnings

Using the UI libraries inventory data, vscode will warn when not importing the component within any given file and should properly import from the correct location despite any other library installed that uses the same naming convention.

# In Editor Comp Autocomplete

Whenever you start to code a component `<`, pressing ctrl & spacebar will bring up the intellisense dropdown containing every single component currently available in the library, all 2500+.

> [!IMPORTANT]
> As far as you or I using the components library, I beleive the above mentioned features finally completes all the goals I set out in regards to the UI library and delivering the absolute best DX... possible.
>
> 1. Accessibility to any component without visiting the site - Acheived through the editor and quick pick menus that inserts the relevant usage example right into the editor
> 2. Shorten the length to mastery - Achieved but still on going, as this is more done so on the side of the actual components them selves. There are many faucets to this goal some examples include, removing as many required props as possible, where ever possible in the case of tabs you do not have to supply a default tab value, or values for any of the tabs themselves, providing default values... literally anywhere, and every where that I could which also saves you from remembering from what is required whenever using a component.
> 3. Providing the easiest to use components - Achieved, to be honest I replicated and expanded upon the build processs of components that shadcn used. As they were the first library I had ever used that whenever you used a component, it not only made sense but each component was easy to use.
> 4. Remove as much friction as possible to install the components - This by far is better than any other single compnents library, anywhere. Using the npm library there are several options on what to install or if a components name is provided then installtion of that one component. To top it off, whenever you select options like full installation, it literally does EVERYTHING:
>   - installs all components
>   - installs all required libraries
>   - checks to see if tailwind is already installed, if not installs it
>   - configures tailwind and goes so far as configuring everything else needed to run tailwind
>   - creates tailwind.css
>   - depending on the selection you get a basic tailwind.config.ts or an extremely feature rich version of it, grating access to over 18,000 configrations that you can change your projects font, theme and preset ( padding, margins, etc )
>   - whenever a component is installed, whether it is the full installation or just a single component, it creates a new index file in the relevant locations so as you get to use `~/components/catalyst-ui` for literlly every single component no mattter the location
>   - just today I added, 'Configure Imports' which takes the previous item... a whole step further by configuring the tsconfig and package.json files so that all you have to do to import a component is `#catalyst` and if you use the icon library as well `#icons`. Now that I think of it, I've never ever... seen a dev or heard of one use this technique. I know as of late, a ton of devs are moving towards the @ in place of the tilde ( ~ ), to save typing the slash, but if your going to so far as to configuring your project so that you save typing a single character... why wouldn't you go the step further and do this? Since it saves you typing out a shit ton of characters... **shrugs**, anyways this feature is also trigger whenever you use full installation
>   - all in all, it provides a one clickesque solution for everything related to the library. I say one clickish, because it used to be such when it was implemented in the extension and only moved it to its own npm library to offer more variations for installation, but still it's just a single command. There isn't one other library that I know of that comes close to that... to my knowledge anyways. To this day, I beleive I have tried them all, that are react based anyways, as I will touch exactly why I tried them all in the next point.
> 5. Completely removing the need in having to 'need' more than one library - When trying to fulfill this goal, I was shocked at the current trend. The main larger libraries, it feels as if each one of them started with an idea that was either specialized or somewhat so and never really expanded upon once they reached that initial goal. Meanwhile, the lazy copy cats create an exact carbon copy of shadcn without adding anything of their own, or if they did or it was at first perceived that they did, it was one... maybe two items at most. Thus, each main library has massive holes in its offered inventory that leaves users... wanting / needing more. For example, the amount of hooks in this library, is unparallel to say the least, but there is only a single other library that can even be considered as coming close in terms of total hooks. While yes, the foundation of this libraries components used shadcn's but if you look at them today, you wouldn't be able to discern that fact. As each and every single one of them have been edited and expanded upon. Not to mention, a whole category, x, that no one else has, an entire animations category, a tool suite unlike any other I've ever seen, a ever growing blocks category in which I try to copy over any page that I code whenever I think of it, and to top it off unique reusable tools that if they aren't available yet they soon will be since they're on the to do list such as: 
>   - events calendar
>   - calendar
>   - automotive calculator
>   - messenger
>   - rich text editor - completely custom, unlike everyone else that wraps tiptap or some other library
>   - table - while the current iteration does wrap another library, it does however host features I have yet to see anywhere else in terms of ease of use and flexibility. Once I have the time... I do plan on creating my own table... but this I foresee taking... A LOT of time in doing it right
>   - and more... Currently, none of the others come to mind though
> There were several other goals but you get the point.
>
> Meanwhile, I was able to achieve something that I had NOT set out to do in regards to the X category. If you had asked me early on when I was first learning to code, do you think you would create a new method in creating react components? I would have not beleived you so much that, not only would I disregard it immediately but it would never cross my mind again to think about. Not only doing just that, but in a way that comes with all the benefits it does all the while at zero cost to the user when using it, didn't see that one coming. Today, I started to replace the main page of the theme builder and decided to use it as a... I wouldn't call it a proving grounds but a place to showcase the new category by giving each component a hover card with the code that was used to implement it. Besides saving a ton of space in terms of files ie, instead of having 100+ files devoted to different variants of inputs... it's just one. I noticed it also reduces a ton of code needed when actually implementing any one variation. So much so, that I will probably leave in the original section that I used, but edit so that each component comes with a hovercard with its implementation of code, so as you can see the difference.
>
> The other big plus I never saw coming, in terms of helping users ( despite still seeing devs still struggle with everything it solves ). Loki AI, as its now called, not only solves virtually every single issue you come across as a dev, and thats not an exageration, but have also cracked the limitation on being limited by an AI engines data training set. While The first point is already out and written about, the latter I'm still testing but the how to should be out soon. The weidest part about that is, getting these results uses methods that are already out there... just used differently.
>
> Knowing that all the goals have been completed... is satisfying. Especially given the fact that, this kinda sucked. Not so much from a coding perspective, but due to its size and with items to do such as providing hover card documentation for every single component... that sucks, but where ever I can and as much as I can I try to find ways to code it so that it takes care of itself. There have been so many days, where I thought I was going to be able to move on to something else only to find out after coming on... that no... there are things to be done with the ui library. Even now, there is still a massive update/change to severel large items that are held up in being pushed due to a couple of smaller other items, I just hope they don't need changes when I can finally test them in a prod enviroment.

# Tool Suite
The library hosts a number of tools for devs to use, the following list is up to date, at the time of writing and will feature more tools as time goes on.

- VSCode Cmd Reference ........ Built-in command library
- Markdown Cheat Sheet ........ Web-based reference
- IRIS: Color Converter ....... Multi-format conversion
- IRIS: Color Wheel ........... Visual color picker
- React/Tailwind Sandbox ...... Development playground
- Theme Builder ............... settings.json & tailwind.css generator
- Typography Tester ........... Font testing suite
- Layout Generator ............ UI layout tools
- X Tester .................... Cross-testing utilities
- Components Reel ............. Component showcase
- Tailwind Converter .......... v3 <-> v4, oklch, hsl, 
- Animation Builder ........... Visual editor
- Responsive Design Helper .... Breakpoint visualizer
- Code Carousel ............... Code display tool
- Sandbox ..................... Live react playground hosting libraries comps
- Icons ....................... Searchable, Rendered icons
- RÚNAR Editor ................ Formally catalyst-editor
- Regex Tester ................ Build and test regex string, cheatsheet included
- JSON Formatter & Validator .. Sanity check for json files
- API Response Mocker ......... Mock REST endpoints with custom JSON responses
- Lorem Ipsum Generator ....... Pick any length and copy to clipboard
- Cron Expression Builder ..... Visual builder for scheduling cron jobs
- UUID Hash Generator ......... Generate random hashes in a flash
- Code Diff Viewer ............ Differences become illuminated
- Flexbox Sandbox ............. Live preview sandbox featuring flexbox 
- Grid Sandbox ................ Live preview sandbox feature grid
- QR Code Generator ........... Images, text, urls 
- Responsive Preview .......... Test layouts across platforms and breakpoints
- Accessibility Checker ....... Scan for WCAG compliance and contrast issues
- Animation Builder ........... Live preview animation builder
- Chart Playground ............ Build charts, outputing react code to paste
- MD Badge Builder ............ Quickly build md badges, that render in real time
- Spinner Generator ........... Build as large of a spinner as you need
- Terminal Menu Generator ..... Best in class, no limitations terminal menu builder
- ENCODER_DECODER_LAB/
  - PNG to Base64
  - JPG to Base64
  - WEBP to Base64
  - PDF to Base64
  - Base64 to PNG
  - Base64 to JPG
  - Base64 to WEBP
  - Base64 to PDF
  - CSV to JSON
  - PNG to SVG
  - JPG to SVG
  - WEBP to SVG
  - MP4 to MP3

# SKALD
### Monaco Editor
If this were anyone elses extension, this would be it's own extension but in this extension it is classified under the tool suite. What first started out as a simple markdown editor, it has since evolved into a full blown monaco editor with 150+ custom features with each feature making it become more and more a full blown ide. 

I have used this so much more than I ever thought I would and because of this it continues to receive regular updates. The largest update to date, is just about to be pushed to the site and will host a list of features so large I cannot remember them all to list but here are some of the features that will be available.
- Feature Set .............. 150-200+ click-to-clipboard MD features
- Special Chars ............ HTML and MD style format character list
- PRE_MADE_ASSETS/
  - File Trees ........... Automated folder visualization
  - Progress Bars ........ Markdown progress indicators
  - ASCII Tables ......... Pre-formatted tables
  - Spinners ............. 17+ different loading spinners
  - Terminal Dashboards .. Terminal-style UI layouts
  - Code Block Previews .. Code styling previews
  - Terminal Menus ....... Visual terminal menu blocks
  - Terminal Logs ........ Logs with hierarchy visualization
  - Git Branch Viz ....... Branch style visualization
  - Status Indicators .... Terminal status boxes
  - Notification Boxes ... Terminal notification styling
  - Output Separators .... Command output dividers
  - Nested Data .......... Nested data structure visualization
  - Activity Timeline .... Sequential activity logs
  - Terminal Dashboards .. Pre-made dashboards
  - Box Drawing .......... Character-based box drawing
  - Various Spinners ..... 17 different spinners
  - Badges and Logos ..... Pre-made badges and icons
  - One night while creating a terminal menu... I kinda went overboard with this section, because of this, part of the sidebar... does need an overhaul, lol, just because the sheer amount of items there are now in this section I need to figure out the best way for users to interact with it, myself included. In the mean time, all of it is available and each "category" of items is nicely categorized the only issue being once clicking on a category it copies the entire category to the clipboard instead of a single item.
- Readme Generator ......... Feature-rich readme builder
- Readme Templates ......... Includes several pre-made templates to start from
- Remote Access ............ Connect remotely to workspace MD files
- Local Settings ........... Locally saved editor settings




# HEPHAESTUS UI

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
