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


### Install Library Through Extension

One-click installation of the Catalyst UI library with complete setup and configuration


**Access:** Right-click → Install Catalyst UI

**Installation Options:**

**Full Installation:**
- Installs all required libraries
- Creates `tailwind.config.js`
- Creates `styles/tailwind.css`
- Creates `postcss.config.js`
- Creates all available components within the components folder

**Components Only:**
- Installs all required libraries
- Creates all available components within the components folder
- No configuration files (assumes existing Tailwind setup)

![Installation](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/ui/install.png?raw=true)
