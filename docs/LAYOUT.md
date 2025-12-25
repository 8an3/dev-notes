# Layout Configuration Guide

The Workspace Layout Engine is designed for developers who switch contexts frequently—moving from heavy feature development to a focused debugging session or a minimal writing environment. It automates the tedious process of rearranging your editor every time you start a task.

This guide explains how to configure custom workspace layouts using the DevStack layout system. Each layout defines how VS Code appears when activated, including UI elements, editor tabs, terminals, and color themes.

> [!NOTE]
> The Workspace Layout Engine, a sophisticated orchestrator that allows you to define and switch between entire development environments with a single click. It doesn't just change a theme; it reconfigures the entire VS Code UI, opens your project files in specific grid positions, and prepares your terminal environment.
>
> At this time the issues have been resolved but the new item type still needs to tested thoroughly, but initial tests are perfect so far as I don't see a single item wrong even with the ridiculously long config I'm testing with. As my UI just loaded perfectly, with a config item of 516 lines long.
>
> During testing there is one crucial... fuck up on vscodes part. There is no way to view vscodes context progmatically. Which is a pain because items like, zen mode, full screen mode / toggle and other toggles like those, all are either true... or false. For example, if you are already currently in zen mode, and you select a new layout that also has zenmode set to true, the end result will be that you will be taken out of zenmode when selecting the new layout config. I have seen a lot of strategies to create a workaround with this, but none of them are reliable enough to even bother coding them. Currently, the best way I have been able to work around this is by creating my configs around the default start of vscodes ui. For example, in my configs I have panel set to hidden when vscode opens, it always has it open for me anyways. So before I click on a new layout, I just make sure its open. Annoying... yes, but theres no current workaround for this. I have even looked into... progmatically triggering `workbench.action.inspectContextKeys`, then progmatically triggering a mouse click inside vscodes instance because there is an api for that, then grabbing the output. The issue here is, everything is sandboxed so there is no way for the extension to acquire that output. Shame because it has everything that you would need in order to properly create a truly independant layout engine where the user, literlly did nothing to help it. So... unless I find something that allows me to get those values this is probably the best iteration that I will be able to make. I've even coded it so, when you have a config with zen mode, I make sure that after it has been toggled, that your sidebars ALSO get `re-toggled` so that they display since zen mode toggles their display values to false. I am going to download a bunch of other extensions that do any type of ui work, only issue here is as far as I have read anyways, none of them go as deep as far as configurating the ui as I have gone.

Before moving on, your more then welcome to check the demo to view exactly what it can do. In the demo it starts by closing all terminals, editors and editor groups. Then proceeds to handle a number of files to open, pin and layout with a set configuration. Having my todo doc set at a specfic smaller value then the other two editor groups, which split the remainder in half. Visually anyways, you will see that it activates zen mode, and because of the mode toggles the sidebars and activity bar to false. Due to my config, they get re-activated to ensure they display in zen mode. Finishing off by creating a editor terminal and panel terminal to execute 2 commands. Meanwhile it sets a ton of behind the scenes settings that do not have any visual representation, [Workspace Layout Engine Demo](https://youtu.be/m6-h4imuCeA)

Despite being the most configurable workspace context layout engines, it was made with new and experienced devs in mind. If your new to dev and still want to use it, don't be intimated by it as it is extremely easy to set up a `simple` but still power layout. As for the more experienced devs, obviously if my config is 516 lines long without even trying, it can get a lot longer which grants you access to a lot more granular level of control of your vscode instance.
## Configuration Approachs

#### The quick and dirty method
Technically speaking... you can literally dump all the values you want / need to control within the `settings.workspace` object. As this object was created as a `dumping` ground for any and all vscode settings values. If all you want to use this for is a theme and very basic layout control, the only item you will need to configure is settings, by placing your values in either theme and workspace or both.

#### For ALOT more granular control

Smart Layout Capabilities
- Automated Workspace Reset: Optionally clears the deck by closing all open editors and killing active terminals to ensure a clean slate.
- Deep UI Configuration: Controls the visibility and position of the Activity Bar, Sidebars, Panel, and Status Bar via workspace-level settings.json automation.
- Performance Profiles: Automatically toggles high-overhead features like Inlay Hints, CodeLens, and Git Decorations to optimize performance based on your current task.
- Dynamic Editor Grids:
  - Define custom grid orientations (Horizontal/Vertical).
  - Specify group sizes (e.g., 20% sidebar group, 80% main group).
  - Auto-Open & Pin: Define sets of files to open in specific grid columns, with optional pinning for essential documentation or TODO lists.
- Terminal Automation: Spawns multiple terminals (in the Panel or Editor area) and automatically executes startup commands like npm run dev or log tailing.

Built-in Layout Presets

- Minimal -	Distraction-free writing -Hides Status Bar, Activity Bar, and Tabs. Disables Minimap.
- Focus -	Deep work / Logic -	Hidden Activity Bar, single-tab mode, centered editor layout.
- Full - Standard Development -	Enables Breadcrumbs, Sticky Scroll, and all UI navigation elements.
- Debug -	Troubleshooting -	Optimized for the debug console and secondary sidebars.

To control everything a 4 tier system has been implemented
1. Context/State commands - Runtime UI state (focus, visibility)
2. `customizeLayout` commands - Layout-specific UI state
3. `.vscode/settings.json` file - Workspace-specific overrides
4. VS Code Configuration API (`config.update()`) - Base settings

Not only allowing for a much cleaner looking config but also an easier time in the overall configuration process. You can think of each value within the appearance object as an organized version of its vscodes settings.jsons items, ie `editor.minimap.autohide` is simply `autoHide` within the minimap object

## Root object
- **label**
  - to be displayed as its label within the vfs
- **path** 
  - if you are only looking to create a single terminal instance and auto run that command, you may place the command within the path key
- **type**
  - `layout`
- **icon**
  - you may place any vscode icon value here to be shown in the vfs
  
## args

The `args` array contains the main configuration object(s) for your layout. Each object in this array can include:

- **`default`** - Boolean - marks this as the default layout configuration
- **`appearance`** - Object - controls all UI element visibility, positioning, and styling
- **`editorGrid`** - Object - defines editor group layout and which files to open
- **`performance`** - Object - toggles for resource-intensive features
- **`terminals`** - Array - terminal instances and commands to run
- **`settings`** - Object - workspace settings, extension settings, and theme customizations

## Appearance Settings

### Quick Input
- **`quickInputPosition`**
  - Controls the position of quick input dialogs (command palette, etc.)
  - **Values**: `"centered"` | `"top"`

### Window
- **`window`** - Object containing window-level settings:
  - **`menuBarVisibility`** - Menu bar display style
    - **Values**: `"classic"` (always visible) | `"toggle"` (hide, show on Alt) | `"hidden"` (always hidden) | `"compact"` (compact form)
  - **`commandCenter`** - Shows/hides the command center
    - **Values**: `true` | `false`
  - **`zoomLevel`** - Window zoom level
    - **Values**: Number (e.g., `-1` = zoom out, `0` = normal, `1` = zoom in)
  - **`titleBarStyle`** - Title bar style
    - **Values**: `"custom"` | `"native"`

### Workbench
- **`workbench`** - Object containing workbench-level settings:
  - **`settings`** - General settings configuration
    - **`editor`** - Editor settings mode
      - **Values**: `"ui"` | `"json"`
  
  - **`activityBar`** - Object controlling activity bar
    - **`location`** - Position of activity bar
      - **Values**: `"default"` (left side) | `"right"` | `"hidden"`
    - **`visible`** - Shows/hides the activity bar
      - **Values**: `true` | `false`
  
  - **`editor`** - Object controlling workbench editor behavior
    - **`showTabs`** - Tab display mode
      - **Values**: `"multiple"` | `"single"` | `"none"`
    - **`wrapTabs`** - Wrap tabs when they overflow
      - **Values**: `true` | `false`
    - **`pinnedTabsOnSeparateRow`** - Display pinned tabs on separate row
      - **Values**: `true` | `false`
    - **`enablePreviewFromQuickOpen`** - Enable preview mode from quick open
      - **Values**: `true` | `false`
    - **`focusRecentEditorAfterClose`** - Focus most recent editor after closing current
      - **Values**: `true` | `false`
    - **`restoreViewState`** - Restore editor scroll/cursor position on reopen
      - **Values**: `true` | `false`
    - **`limit`** - Object controlling editor width limits
      - **`enabled`** - Enable editor width limit
        - **Values**: `true` | `false`
  
  - **`layoutControl`** - Object controlling layout controls
    - **`enabled`** - Enable layout control buttons in UI
      - **Values**: `true` | `false`

### Editor
- **`editor`** - Object containing editor-specific settings:
  - **`fontSize`** - Editor font size in pixels
    - **Values**: Number (e.g., `11`, `14`, `16`)
  - **`fontFamily`** - Editor font family
    - **Values**: Font name string (e.g., `"JetBrains Mono"`, `"Fira Code"`, `"Consolas"`)
  - **`fontLigatures`** - Enable font ligatures
    - **Values**: `true` | `false`
  - **`lineNumbers`** - Line number display style
    - **Values**: `"on"` | `"off"` | `"relative"` | `"interval"`
  - **`wordWrap`** - Word wrapping behavior
    - **Values**: `"on"` | `"off"` | `"wordWrapColumn"` | `"bounded"`
  - **`glyphMargin`** - Show glyph margin (for breakpoints, debugging icons, etc.)
    - **Values**: `true` | `false`
  - **`folding`** - Enable code folding
    - **Values**: `true` | `false`
  - **`foldingImportsByDefault`** - Automatically fold import statements on file open
    - **Values**: `true` | `false`
  - **`showFoldingControls`** - When to show folding controls
    - **Values**: `"always"` | `"mouseover"`
  - **`renderWhitespace`** - How to render whitespace characters
    - **Values**: `"none"` | `"boundary"` | `"selection"` | `"all"`
  - **`renderControlCharacters`** - Render control characters (null, bell, etc.)
    - **Values**: `true` | `false`
  - **`scrollBeyondLastLine`** - Allow scrolling past the last line
    - **Values**: `true` | `false`
  - **`accessibilitySupport`** - Accessibility support level
    - **Values**: `"off"` | `"on"` | `"auto"`
  
  - **`scrollbar`** - Object controlling scrollbar behavior
    - **`vertical`** - Vertical scrollbar visibility
      - **Values**: `"auto"` | `"visible"` | `"hidden"`
  
  - **`stickyScroll`** - Object controlling sticky scroll feature
    - **`enabled`** - Enable sticky scroll (keeps current scope visible at top)
      - **Values**: `true` | `false`
    - **`maxLineCount`** - Maximum lines to show in sticky scroll area
      - **Values**: Number (e.g., `3`, `5`, `10`)
  
  - **`minimap`** - Object controlling minimap
    - **`enabled`** - Enable/disable minimap
      - **Values**: `true` | `false`
    - **`autohide`** - Auto-hide minimap when not in use
      - **Values**: `true` | `false`
    - **`showMarkSectionHeaders`** - Show mark section headers in minimap
      - **Values**: `true` | `false`
    - **`showRegionSectionHeaders`** - Show region section headers in minimap
      - **Values**: `true` | `false`
    - **`showSlider`** - Minimap slider visibility
      - **Values**: `"always"` | `"mouseover"` | `"never"`
    - **`side`** - Minimap position
      - **Values**: `"left"` | `"right"`
    - **`size`** - Minimap sizing mode
      - **Values**: `"fill"` | `"fit"` | `"proportional"`
    - **`renderCharacters`** - Render actual characters vs colored blocks
      - **Values**: `true` | `false`
    - **`maxColumn`** - Maximum column width for minimap rendering
      - **Values**: Number (e.g., `50`, `80`, `120`)

### Breadcrumbs
- **`breadcrumbs`** - Object controlling breadcrumb navigation
  - **`enabled`** - Show/hide breadcrumb navigation at top of editor
    - **Values**: `true` | `false`

### Terminal
- **`terminal`** - Object containing terminal settings:
  - **`integrated`** - Object for integrated terminal settings
    - **`fontSize`** - Terminal font size in pixels
      - **Values**: Number (e.g., `10`, `12`, `14`)
    - **`defaultLocation`** - Default location where new terminals spawn
      - **Values**: `"editor"` (opens in editor area) | `"panel"` (opens in panel)

### Menu Bar
- **`menuBar`** - Object controlling menu bar and its buttons:
  - **`view`** - Menu bar visibility style
    - **Values**: `"classic"` (always visible) | `"toggle"` (hide, show on Alt) | `"hidden"` (always hidden) | `"compact"` (compact form)
  - **`commandCenter`** - Show/hide command center
    - **Values**: `true` | `false`
  - **`navigationControls`** - Show/hide navigation buttons (back/forward)
    - **Values**: `true` | `false`
  - **`share`** - Show/hide share button
    - **Values**: `true` | `false`
  - **`layoutControls`** - Show/hide layout control buttons
    - **Values**: `true` | `false`
  - **`customizeLayout`** - Show/hide customize layout button
    - **Values**: `true` | `false`
  - **`togglePrimarySidebar`** - Show/hide primary sidebar toggle button
    - **Values**: `true` | `false`
  - **`toggleSecondarySidebar`** - Show/hide secondary sidebar toggle button
    - **Values**: `true` | `false`
  - **`togglePanel`** - Show/hide panel toggle button
    - **Values**: `true` | `false`

### Primary Sidebar
- **`primarySidebar`** - Object controlling the primary sidebar:
  - **`display`** - Show/hide primary sidebar
    - **Values**: `true` | `false`
  - **`position`** - Sidebar position
    - **Values**: `"left"` | `"right"`
  - **`view`** - Default view to show in primary sidebar
    - **Values**: `"workbench.view.explorer"` (File Explorer) | `"workbench.view.search"` (Search) | `"workbench.view.scm"` (Source Control) | `"workbench.view.debug"` (Run and Debug) | `"workbench.view.extensions"` (Extensions)

### Secondary Sidebar
- **`secondarySidebar`** - Object controlling the secondary sidebar:
  - **`display`** - Show/hide secondary sidebar
    - **Values**: `true` | `false`
  - **`view`** - View to display (typically an extension view ID)
    - **Values**: Extension view ID string (e.g., `"skyler.ocrmnav"` for custom navigator)

### Panel
- **`panel`** - Object controlling the bottom/side panel:
  - **`display`** - Show/hide panel
    - **Values**: `true` | `false`
  - **`position`** - Panel position
    - **Values**: `"bottom"` | `"right"` | `"left"`
  - **`alignment`** - Panel alignment when docked
    - **Values**: `"center"` | `"left"` | `"right"` | `"justify"`
  - **`view`** - Default view to show in panel
    - **Values**: `"workbench.panel.output"` (Output) | `"workbench.panel.terminal"` (Terminal) | `"workbench.panel.problems"` (Problems) | `"workbench.panel.debug"` (Debug Console)
  - **`maximized`** - Open panel in maximized state
    - **Values**: `true` | `false`

### Status Bar
- **`statusBar`** - Object controlling status bar:
  - **`visible`** - Show/hide status bar at bottom
    - **Values**: `true` | `false`

### Modes
- **`modes`** - Object controlling special display modes:
  - **`fullScreen`** - Enable full screen mode
    - **Values**: `true` | `false`
  - **`zenMode`** - Enable Zen mode (distraction-free editing)
    - **Values**: `true` | `false`
  - **`centered`** - Enable centered layout mode
    - **Values**: `true` | `false`

## Editor Grid Settings

- **`editorGrid`** - Object defining the editor group layout:
  - **`orientation`** - Grid split direction
    - **Values**: `0` (horizontal split - groups side by side) | `1` (vertical split - groups stacked)
  
  - **`groups`** - Array of editor group definitions
    - Each group is an object with:
      - **`size`** - Relative size as decimal between 0 and 1
      - **Example**: `[{"size": 0.2}, {"size": 0.45}, {"size": 0.45}]` creates three groups at 20%, 45%, and 45% of available space
  
  - **`files`** - Array of file objects to open in specific groups
    - Each file object contains:
      - **`path`** - File path(s) to open
        - **Values**: String (single file) or Array of strings (multiple files)
      - **`group`** - Which editor group to open files in
        - **Values**: Number, 1-indexed (1 = first group, 2 = second group, etc.)
      - **`pinned`** - Whether to pin the tab(s)
        - **Values**: `true` | `false`

## Performance Settings

The `performance` object controls resource-intensive features for optimization:

### Editor Features
- **`editor`** - Object containing editor performance settings:
  - **`suggestOnTriggerCharacters`** - Auto-suggest when typing trigger characters (`.`, `::`, etc.)
    - **Values**: `true` | `false`
  - **`acceptSuggestionOnEnter`** - Accept suggestions with Enter key
    - **Values**: `"on"` | `"off"` | `"smart"`
  - **`acceptSuggestionOnCommitCharacter`** - Accept suggestions when typing commit characters
    - **Values**: `true` | `false`
  - **`wordBasedSuggestions`** - Enable word-based code suggestions
    - **Values**: `"off"` | `"matchingDocuments"` | `"currentDocument"` | `"allDocuments"`
  - **`formatOnType`** - Automatically format code as you type
    - **Values**: `true` | `false`
  - **`formatOnPaste`** - Automatically format pasted code
    - **Values**: `true` | `false`
  - **`formatOnSave`** - Automatically format files when saved
    - **Values**: `true` | `false`
  - **`occurrencesHighlight`** - Highlight other occurrences of selected symbol
    - **Values**: `"off"` | `"singleFile"` | `"multiFile"`
  - **`selectionHighlight`** - Highlight other matches of current selection
    - **Values**: `true` | `false`
  - **`codeLens`** - Show CodeLens (reference counts, implementations above code)
    - **Values**: `true` | `false`
  
  - **`inlineSuggest`** - Object for inline suggestions (Copilot, etc.)
    - **`enabled`** - Enable inline suggestions
      - **Values**: `true` | `false`
  
  - **`inlayHints`** - Object for inlay hints (type hints, parameter names)
    - **`enabled`** - Enable inlay hints
      - **Values**: `"on"` | `"off"` | `"onUnlessPressed"` | `"offUnlessPressed"`
  
  - **`parameterHints`** - Object for parameter hints
    - **`enabled`** - Show parameter hints when typing function calls
      - **Values**: `true` | `false`
  
  - **`semanticHighlighting`** - Object for semantic syntax highlighting
    - **`enabled`** - Enable semantic colorization (more accurate than syntax highlighting)
      - **Values**: `true` | `false` | `"configuredByTheme"`

### Git Integration
- **`git`** - Object containing Git performance settings:
  - **`decorations.enabled`** - Enable Git decorations in editor and explorer
    - **Values**: `true` | `false`
  - **`diffDecorations`** - Show Git diff decorations in editor
    - **Values**: `"all"` | `"gutter"` | `"overview"` | `"none"`
  - **`diffDecorationsGutterAction`** - Action when clicking diff decorations in gutter
    - **Values**: `"diff"` | `"peek"` | `"none"`
  
  - **`diffEditor`** - Object for diff editor settings
    - **`renderGutterMenu`** - Show menu in diff editor gutter
      - **Values**: `true` | `false`
  
  - **`mergeEditor`** - Object for merge editor settings
    - **`codeLens`** - Object for CodeLens in merge editor
      - **`enabled`** - Show CodeLens in merge editor
        - **Values**: `true` | `false`

### Search
- **`search`** - Object containing search performance settings:
  - **`smartCase`** - Case-insensitive search unless uppercase letters are used
    - **Values**: `true` | `false`
  - **`useIgnoreFiles`** - Respect `.gitignore` and other ignore files in search
    - **Values**: `true` | `false`
  - **`exclude`** - Glob patterns to exclude from search results
    - **Values**: Object with pattern keys (e.g., `{"**/node_modules": true, "**/.git": true}`)

### File Management
- **`files`** - Object containing file system performance settings:
  - **`watcherExclude`** - Files/folders to exclude from file watching
    - **Values**: Object with glob patterns (e.g., `{"**/node_modules/**": true}`)
  - **`exclude`** - Files/folders to hide from file explorer
    - **Values**: Object with glob patterns
  - **`maxMemoryForLargeFilesMB`** - Maximum memory allocated for large files
    - **Values**: Number in MB (e.g., `4096` = 4GB)

### Extensions
- **`extensions`** - Object containing extension performance settings:
  - **`ignoreRecommendations`** - Ignore extension recommendations
    - **Values**: `true` | `false`
  - **`showRecommendationsOnlyOnDemand`** - Only show extension recommendations when requested
    - **Values**: `true` | `false`

### Workbench
- **`workbench`** - Object containing workbench performance settings:
  - **`editor`** - Object for editor behavior
    - **`enablePreview`** - Open files in preview mode (single-click replaces tab, double-click pins)
      - **Values**: `true` | `false`

### CSS
- **`css`** - Object containing CSS performance settings:
  - **`validate`** - Enable CSS syntax validation and error reporting
    - **Values**: `true` | `false`

## Terminals Configuration

- **`terminals`** - Array of terminal configuration objects:
  - Each terminal object contains:
    - **`name`** - Display name for the terminal tab
      - **Values**: String
    - **`cmd`** - Command to execute in the terminal
      - **Values**: Shell command string (e.g., `"npm run dev"`, `"tail -f dev.log"`)
    - **`location`** - Where the terminal should spawn
      - **Values**: `"editor"` (opens in editor area) | `"panel"` (opens in panel)
    - **`cwd`** - Working directory for the command
      - **Values**: Path string or empty string `""` (empty = current workspace root)

## Settings & Workspace Configuration

The `settings` object contains three main sections for comprehensive workspace configuration:

### Extension Settings
Configure extension-specific settings using the extension ID as the key:

```json
"settings": {
  "ocrmnavigator": {
    "todo": {
      "repo": "mynotesrepo",
      "branch": "main"
    }
  }
}
```

Each extension's settings are nested under its ID and can include any settings that extension exposes.

### Editor Settings
Direct VS Code editor settings using full setting paths:

```json
"editor": {
  "minimap.renderCharacters": false,
  "minimap.maxColumn": "50"
}
```

### Window Settings
- **`window`** - Object containing window-level settings:
  - **`restoreWindows`** - Window restoration behavior on startup
    - **Values**: `"all"` (restore all windows) | `"folders"` (restore folder windows) | `"one"` (restore one window) | `"none"` (don't restore)
  - **`openFilesInNewWindow`** - How files open when VS Code is already running
    - **Values**: `"on"` (always new window) | `"off"` (reuse window) | `"default"` (system default)

### Workspace Settings

> [!TIP]
> Workspace
> This is your vscode settings.json dumping ground that will change the settings found within the workspace settings.json file. Allowing you to create a profile system and change its settings based on the layout config of your choosing. I have never even heard of another extension implementing such a system, but I have to say this has been a nice touch to the layout engine. 

- **`workspace`** - Object containing any VS Code workspace settings:
  - Can include any valid VS Code setting
  - Supports language-specific settings using `[language]` syntax:
    ```json
    "[markdown]": {
      "editor.wordWrap": "on",
      "editor.quickSuggestions": false
    }
    ```
  - Common settings:
    - **`workbench.editorAssociations`** - File type associations
      - **Values**: Object mapping file patterns to editor IDs (e.g., `{"*.html": "default"}`)
    - **`files.defaultLanguage`** - Default language for new files
      - **Values**: Language ID string (e.g., `"TypeScript"`, `"JavaScript"`, `"markdown"`)
    - **`files.associations`** - Custom file associations
      - **Values**: Object mapping patterns to languages (e.g., `{".env*": "dotenv"}`)
    - **`files.exclude`** - Files to hide from explorer
      - **Values**: Object with glob patterns
    - **`editor.defaultFormatter`** - Default formatter for all files
      - **Values**: Extension ID (e.g., `"vscode.typescript-language-features"`)

### Theme Customizations (`workbench.colorCustomizations`)
- **`workbench.colorCustomizations`** - Object overriding theme colors with custom values
  - **Common color keys**:
    - **Background colors**: `"editor.background"`, `"sideBar.background"`, `"panel.background"`, `"terminal.background"`, `"activityBar.background"`, `"statusBar.background"`, `"titleBar.activeBackground"`
    - **Foreground colors**: `"editor.foreground"`, `"sideBar.foreground"`, `"statusBar.foreground"`, `"activityBar.foreground"`
    - **Border colors**: `"sideBar.border"`, `"panel.border"`, `"statusBar.border"`, `"tab.border"`
    - **UI element colors**: `"menu.background"`, `"menu.foreground"`, `"input.background"`, `"dropdown.background"`, `"button.background"`
    - **Selection colors**: `"list.activeSelectionBackground"`, `"list.hoverBackground"`, `"editor.selectionBackground"`
    - **Terminal colors**: `"terminal.ansiBlack"`, `"terminal.ansiRed"`, `"terminal.ansiGreen"`, `"terminal.ansiYellow"`, `"terminal.ansiBlue"`, `"terminal.ansiMagenta"`, `"terminal.ansiCyan"`, `"terminal.ansiWhite"`
    - **Git colors**: `"gitDecoration.deletedResourceForeground"`, `"gitDecoration.modifiedResourceForeground"`, `"gitDecoration.conflictingResourceForeground"`
  - **Values**: Hex color codes (e.g., `"#020817"`, `"#F8FAFC"`) or CSS color names

> [!TIP]
> Theme
> To quickly create this section you can use the theme builder that can be found on the web ui.
> Once your theme has been built just copy over the settings into the config


## Example Config

```json
   {
          "$schema": "./schemas/layout-config-schema.json",
          "label": "DevStack Default",
          "path": "",
          "type": "layout",
          "icon": "editor-layout",
          "args": [
            {
              "default": true,
              "appearance": {
                "quickInputPosition": true,
                "menuBar": {
                  "view": "classic",
                  "commandCenter": true,
                  "navigationControls": true,
                  "share": true,
                  "layoutControls": true,
                  "customizeLayout": true,
                  "togglePrimarySidebar": true,
                  "toggleSecondarySidebar": true,
                  "togglePanel": true
                },
                "activityBar": {
                  "display": true,
                  "position": "default"
                },
                "primarySidebar": {
                  "display": true,
                  "position": "left",
                  "view": "Explorer",
                  "showLabels": true
                },
                "secondarySidebar": {
                  "display": true,
                  "view": "skyler.ocrmnav",
                  "showLabels": false
                },
                "panel": {
                  "display": false,
                  "position": "bottom",
                  "alignment": "center",
                  "view": "output",
                  "maximized": true
                },
                "modes": {
                  "fullScreen": false,
                  "zenMode": false,
                  "centered": true
                },
                "statusBar": {
                  "visible": true,
                  "hoverDebug": true
                },
                "minimap": {
                  "minimap": true,
                  "autohide": "mouseover",
                  "showMarkSectionHeaders": false,
                  "showRegionSectionHeaders": true,
                  "showSlider": "mouseover",
                  "side": "left",
                  "NEWBELOW": false,
                  "size": "fill",
                  "renderCharacters": false,
                  "maxColumn": "50"
                },
                "terminal": {
                  "location": "editor",
                  "fontSize": 12
                },
                "editor": {
                  "zoomLevel": -1,
                  "fontSize": 11,
                  "breadcrumbs": false,
                  "tabBar": "multiple",
                  "editorsActionPosition": "tab",
                  "wordWrap": true,
                  "fontFamily": "JetBrains Mono",
                  "fontLigatures": true,
                  "foldingImportsByDefault": false,
                  "accessibilitySupport": "off",
                  "showFoldingControls": "always",
                  "showTabs": "multiple",
                  "alwaysShowEditorActions": true,
                  "enablePreviewFromQuickOpen": false,
                  "focusRecentEditorAfterClose": false,
                  "pinnedTabsOnSeparateRow": true,
                  "wrapTabs": true,
                  "limit.enabled": true,
                  "lineNumbers": "relative",
                  "scrollBeyondLastLine": false,
                  "updateImportsOnPaste.enabled": false,
                  "restoreViewState": true,
                  "renderWhitespace": "none",
                  "renderControlCharacters": true,
                  "folding": true,
                  "glyphMargin": true,
                  "stickyScroll": {
                    "enabled": true,
                    "maxLineCount": 5
                  }
                }
              },
              "editorGrid": {
                "orientation": 0,
                "groups": [
                  {
                    "size": 0.2
                  },
                  {
                    "size": 0.45
                  },
                  {
                    "size": 0.45
                  }
                ],
                "files": [
                  {
                    "path": ".vscode/ntrsync/10516_DevStack_todo.md",
                    "group": 1,
                    "pinned": true
                  },
                  {
                    "path": [
                      "src/extension.ts",
                      "src/helpers/master.ts",
                      "src/helpers/menus.ts",
                      "src/helpers/workspace.ts",
                      "src/extension/navigatorView.ts",
                      "src/helpers/itemsActionsMenu.ts",
                      "src/helpers/modular-commands.ts"
                    ],
                    "group": 2
                  },
                  {
                    "group": 3,
                    "pinned": true,
                    "path": [
                      "README.dev.md",
                      "package.dev.jsonc",
                    ]
                  }
                ]
              },
              "performance": {
                "editor.inlineSuggest.enabled": false,
                "editor.inlayHints.enabled": "off",
                "editor.parameterHints.enabled": false,
                "editor.suggestOnTriggerCharacters": false,
                "editor.acceptSuggestionOnEnter": "off",
                "editor.acceptSuggestionOnCommitCharacter": false,
                "editor.wordBasedSuggestions": "off",
                "editor.formatOnType": false,
                "editor.formatOnPaste": false,
                "editor.formatOnSave": false,
                "editor.semanticHighlighting.enabled": true,
                "editor.occurrencesHighlight": "off",
                "editor.selectionHighlight": true,
                "editor.codeLens": false,
                "git.decorations.enabled": false,
                "git.diffDecorations": "none",
                "git.diffDecorationsGutterAction": "none",
                "git.diffEditor.renderGutterMenu": false,
                "search.smartCase": true,
                "search.useIgnoreFiles": false,
                "search.exclude": {},
                "files.watcherExclude": {},
                "files.exclude": {},
                "files.maxMemoryForLargeFilesMB": 4096,
                "extensions.ignoreRecommendations": true,
                "extensions.showRecommendationsOnlyOnDemand": true,
                "git.mergeEditor.codeLens.enabled": false,
                "workbench.editor.enablePreview": false,
                "css.validate": true
              },
              "terminals": [
                {
                  "name": "Server",
                  "cmd": "npm run dev",
                  "location": "editor",
                  "cwd": ""
                },
                {
                  "name": "Logs",
                  "cmd": "tail -f dev.log",
                  "location": "panel",
                  "cwd": ""
                }
              ],
              "settings": {
                "workspace": {
                  "editor.minimap.renderCharacters": false,
                  "editor.minimap.maxColumn": "50",
                  "editor.minimap.size": "fill",
                  "ocrmnavigator.AUTO_FOLD_PKG": true,
                  "ocrmnavigator.BE_QP": true,
                  "ocrmnavigator.vscodeVersion": "Code - Insiders",
                  "ocrmnavigator.AUTORUN_DIR": "src",
                  "ocrmnavigator.UPDATE_PROMPT_OBJECTS": false,
                  "ocrmnavigator.AUTORUN_SCRIPTS": true,
                  "ocrmnavigator.CONVERT_README_DEV_MD": false,
                  "ocrmnavigator.PRO7": false,
                  "ocrmnavigator.CONCURRENT": "bleeding-edge",
                  "ocrmnavigator.ARCHIVER": "custom",
                  "ocrmnavigator.DELETE_OLD_VSIX": true,
                  "ocrmnavigator.AUTO_INSTALL_VSIX": true,
                  "ocrmnavigator.OPEN_PUB_DASH": true,
                  "ocrmnavigator.RELOAD_INSTANCE": true,
                  "ocrmnavigator.codesnap.windowControlStyle": "Windows",
                  "ocrmnavigator.codesnap.showWindowTitle": true,
                  "ocrmnavigator.codesnap.windowBorderRadius": "8px",
                  "ocrmnavigator.codesnap.windowTitleStyle": "Filename",
                  "ocrmnavigator.codesnap.showLineNumbers": true,
                  "ocrmnavigator.codesnap.realLineNumbers": false,
                  "ocrmnavigator.codesnap.transparentBackground": false,
                  "ocrmnavigator.codesnap.trimEmptyLines": false,
                  "ocrmnavigator.todo.branch": "main",
                  "ocrmnavigator.todo.checkRemindersInterval": "10",
                  "ocrmnavigator.todo.syncInterval": "20",
                  "ocrmnavigator.todo.syncOnSave": true,
                  "ocrmnavigator.todo.owner": "8an3",
                  "ocrmnavigator.todo.repository": "8an3/mynotesrepo",
                  "ocrmnavigator.todo.isPriv": false,
                  "ocrmnavigator.toggleHiddenItems": true,
                  "ocrmnavigator.strPrismaUpdater": true,
                  "ocrmnavigator.commands": true,
                  "ocrmnavigator.vscodecmdref": true,
                  "ocrmnavigator.markdownViewer": true,
                  "ocrmnavigator.snippets": true,
                  "ocrmnavigator.snippetsInEditor": true,
                  "ocrmnavigator.editorContextSnippets": true,
                  "ocrmnavigator.formatters": true,
                  "ocrmnavigator.trailingCommas": true,
                  "ocrmnavigator.batchRename": true,
                  "ocrmnavigator.eslintPrettier": true,
                  "ocrmnavigator.remixUtils": true,
                  "ocrmnavigator.theme": true,
                  "ocrmnavigator.blackedOut": true,
                  "ocrmnavigator.windowDifferentiator": true,
                  "ocrmnavigator.shadCNComponents": true,
                  "ocrmnavigator.repoMgr": true,
                  "ocrmnavigator.openGithub": true,
                  "ocrmnavigator.githubFunctions": true,
                  "ocrmnavigator.prismaFunctions": true,
                  "ocrmnavigator.remixComponents": true,
                  "ocrmnavigator.clickToSchema": true,
                  "ocrmnavigator.crudResolvers": true,
                  "ocrmnavigator.fileNesting": true,
                  "ocrmnavigator.revealExplorer": true,
                  "ocrmnavigator.copyPath": true,
                  "ocrmnavigator.bookmarks": true,
                  "ocrmnavigator.searchBar": true,
                  "ocrmnavigator.clipBoardHistory": true,
                  "ocrmnavigator.colorWheel": true,
                  "ocrmnavigator.lucideIcons": true,
                  "ocrmnavigator.share": true,
                  "ocrmnavigator.url": true,
                  "ocrmnavigator.jsonComments": true,
                  "ocrmnavigator.con": true,
                  "ocrmnavigator.removeAllComments": true,
                  "ocrmnavigator.unusedFunctions": true,
                  "ocrmnavigator.viewers": true,
                  "ocrmnavigator.uiDashboard": true,
                  "ocrmnavigator.devStackFunctions": true,
                  "ocrmnavigator.openLeftOffNote": true,
                  "ocrmnavigator.renderMd": true,
                  "ocrmnavigator.createFolderSmartIndex": true,
                  "ocrmnavigator.tailwindConverter": true,
                  "ocrmnavigator.convertToAgnostic": true,
                  "ocrmnavigator.concurrent": true,
                  "ocrmnavigator.autoSequencer": true,
                  "window.restoreWindows": "one",
                  "window.openFilesInNewWindow": "default",
                  "workbench.editorAssociations": {
                    "*.html": "default",
                    "*.svg": "default"
                  },
                  "workbench.editor.autoLockGroups": {
                    "default": false,
                    "mainThreadWebview-simpleBrowser.view": false,
                    "mainThreadWebview-browserPreview": false
                  },
                  "files.defaultLanguage": "TypeScript",
                  "terminal.integrated.profiles.windows": {
                    "PowerShell": {
                      "source": "PowerShell",
                      "icon": "terminal-powershell"
                    },
                    "Command Prompt": {
                      "path": [
                        "${env:windir}\\Sysnative\\cmd.exe",
                        "${env:windir}\\System32\\cmd.exe"
                      ],
                      "args": [],
                      "icon": "terminal-cmd"
                    },
                    "Git Bash": {
                      "source": "Git Bash"
                    },
                    "Debian (WSL)": {
                      "path": "C:\\Windows\\System32\\wsl.exe",
                      "args": [
                        "-d",
                        "Debian"
                      ],
                      "icon": "terminal-debian"
                    }
                  },
                  "[markdown]": {
                    "editor.quickSuggestions": {
                      "comments": false,
                      "strings": false,
                      "other": false
                    },
                    "workbench.quickOpen.preserveInput": true,
                    "workbench.editor.languageDetection": false,
                    "editor.defaultFormatter": "yzhang.markdown-all-in-one",
                    "editor.suggest.snippetsPreventQuickSuggestions": true,
                    "editor.acceptSuggestionOnEnter": "off",
                    "editor.suggest.showStatusBar": true,
                    "editor.hover.enabled": "on",
                    "editor.renderWhitespace": "none",
                    "editor.renderControlCharacters": false,
                    "editor.renderLineHighlight": "line",
                    "editor.matchBrackets": "always",
                    "editor.glyphMargin": true,
                    "editor.folding": true,
                    "editor.gotoLocation.multipleDefinitions": "gotoAndPeek",
                    "editor.gotoLocation.multipleTypeDefinitions": "gotoAndPeek",
                    "editor.gotoLocation.multipleDeclarations": "gotoAndPeek",
                    "editor.gotoLocation.multipleImplementations": "gotoAndPeek",
                    "editor.gotoLocation.multipleReferences": "gotoAndPeek",
                    "editor.links": true,
                    "editor.occurrencesHighlight": "off",
                    "editor.selectionHighlight": true,
                    "editor.semanticHighlighting.enabled": true,
                    "editor.showFoldingControls": "always",
                    "editor.suggest.insertMode": "replace",
                    "editor.suggest.filterGraceful": false,
                    "editor.suggest.shareSuggestSelections": false,
                    "editor.suggest.showClasses": false,
                    "editor.suggest.showColors": false,
                    "editor.suggest.showConstants": false,
                    "editor.suggest.showConstructors": false,
                    "editor.suggest.showCustomcolors": false,
                    "editor.suggest.showDeprecated": false,
                    "editor.suggest.showEnumMembers": false,
                    "editor.suggest.showEnums": false,
                    "editor.suggest.showEvents": false,
                    "editor.suggest.showFields": false,
                    "editor.suggest.showFiles": false,
                    "editor.suggest.showFolders": false,
                    "editor.suggest.showFunctions": false,
                    "editor.suggest.showInterfaces": false,
                    "editor.suggest.showIssues": false,
                    "editor.suggest.showKeywords": false,
                    "editor.suggest.showMethods": false,
                    "editor.suggest.showModules": false,
                    "editor.suggest.showOperators": false,
                    "editor.suggest.showProperties": false,
                    "editor.suggest.showReferences": false,
                    "editor.suggest.showSnippets": false,
                    "editor.suggest.showStructs": false,
                    "editor.suggest.showTypeParameters": false,
                    "editor.suggest.showUnits": false,
                    "editor.suggest.showUsers": false,
                    "editor.suggest.showValues": false,
                    "editor.suggest.showVariables": false,
                    "editor.suggest.showWords": false,
                    "editor.wordBasedSuggestions": "off",
                    "editor.wordBasedSuggestionsMode": "allDocuments",
                    "editor.suggestSelection": "recentlyUsed",
                    "diffEditor.wordWrap": "inherit"
                  },
                  "files.associations": {
                    ".env*": "dotenv"
                  },
                  "files.exclude": {},
                  "editor.defaultFormatter": "vscode.typescript-language-features",
                  "[typescriptreact]": {
                    "editor.defaultFormatter": "vscode.typescript-language-features"
                  },
                  "[javascriptreact]": {
                    "editor.defaultFormatter": "vscode.typescript-language-features"
                  },
                  "[typescript]": {
                    "editor.defaultFormatter": "vscode.typescript-language-features"
                  },
                  "[javascript]": {
                    "editor.defaultFormatter": "vscode.typescript-language-features"
                  },
                  "[json]": {
                    "editor.defaultFormatter": "vscode.json-language-features"
                  },
                  "[jsonc]": {
                    "editor.validate": false
                  },
                  "[css]": {
                    "editor.defaultFormatter": "vscode.css-language-features"
                  },
                  "[html]": {
                    "editor.defaultFormatter": "vscode.html-language-features"
                  },
                  "[snippets]": {
                    "editor.defaultFormatter": "vscode.json-language-features"
                  }
                },
                "workbench.colorCustomizations": {
                  "background": "#020817",
                  "menubar.background": "#020817",
                  "menubar.menu": "#020817",
                  "activityBar.background": "#020817",
                  "terminal.background": "#020817",
                  "titleBar.inactiveBackground": "#020817",
                  "titleBar.activeBackground": "#020817",
                  "panel.background": "#020817",
                  "terminalCommandDecoration.defaultBackground": "#020817",
                  "sideBar.background": "#020817",
                  "sideBarSectionHeader.background": "#1E293B",
                  "editor.background": "#020817",
                  "editorGroup.emptyBackground": "#020817",
                  "statusBar.background": "#020817",
                  "editorGroupHeader.tabsBackground": "#020817",
                  "activityBar.border": "#020817",
                  "menu.border": "#1E293B",
                  "menu.separatorBackground": "#1E293B",
                  "sideBar.border": "#1E293B",
                  "tree.tableColumnsBorder": "#1E293B",
                  "tab.border": "#1E293B",
                  "statusBar.border": "#1E293B",
                  "panel.border": "#1E293B",
                  "menu.foreground": "#94A3B8",
                  "foreground": "#94A3B8",
                  "menubar.foreground": "#94A3B8",
                  "activityBar.foreground": "#F8FAFC",
                  "sideBarSectionHeader.foreground": "#F8FAFC",
                  "explorer.folderItem.foreground": "#1E293B",
                  "panelTitle.activeForeground": "#F8FAFC",
                  "list.focusForeground": "#F8FAFC",
                  "sideBar.foreground": "#94A3B8",
                  "statusBar.foreground": "#94A3B8",
                  "editor.foreground": "#F8FAFC",
                  "activityBar.inactiveForeground": "#94A3B8",
                  "explorer.fileItem.foreground": "#94A3B8",
                  "input.background": "#1E293B",
                  "dropdown.background": "#1E293B",
                  "button.background": "#3B82F6",
                  "button.hoverBackground": "#3B82F6",
                  "input.foreground": "#F8FAFC",
                  "button.foreground": "#0F172A",
                  "menubar.selectionBackground": "#1E293B",
                  "menu.selectionBackground": "#1E293B",
                  "menubar.selectionForeground": "#F8FAFC",
                  "menu.selectionForeground": "#F8FAFC",
                  "list.activeSelectionBackground": "#1E293B",
                  "list.activeSelectionForeground": "#F8FAFC",
                  "input.border": "#1E293B",
                  "inputOption.activeBorder": "#1D4ED8",
                  "focusBorder": "#1D4ED8",
                  "errorForeground": "#7F1D1D",
                  "editor.lineHighlightBackground": "#1E293B",
                  "editor.selectionBackground": "#1E293B",
                  "editorCursor.foreground": "#F8FAFC",
                  "editorIndentGuide.background1": "#1E293B",
                  "editorWhitespace.foreground": "#1E293B",
                  "list.focusBackground": "#1E293B",
                  "list.hoverBackground": "#1E293B",
                  "list.highlightForeground": "#3B82F6",
                  "explorer.fileItem.hoverForeground": "#F8FAFC",
                  "explorer.folderItem.hoverForeground": "#F8FAFC",
                  "tree.indentGuidesStroke": "#1E293B",
                  "tab.activeBackground": "#020817",
                  "tab.activeForeground": "#F8FAFC",
                  "tab.inactiveBackground": "#020817",
                  "tab.inactiveForeground": "#94A3B8",
                  "tab.activeBorder": "#020817",
                  "gitDecoration.deletedResourceForeground": "#7F1D1D",
                  "gitDecoration.conflictingResourceForeground": "#3B82F6",
                  "terminal.ansiBlack": "#020817",
                  "terminal.ansiBlue": "#3B82F6",
                  "terminal.ansiCyan": "#29c3a0",
                  "terminal.ansiGreen": "#29c3a0",
                  "terminal.ansiMagenta": "#3B82F6",
                  "terminal.ansiRed": "#7F1D1D",
                  "terminal.ansiWhite": "#F8FAFC",
                  "terminal.ansiYellow": "#d29922",
                  "scrollbarSlider.hoverBackground": "#3B82F6",
                  "scrollbarSlider.activeBackground": "#3B82F6",
                  "scrollbarSlider.background": "#3B82F620",
                  "activityBarBadge.background": "#3B82F6",
                  "activityBarBadge.foreground": "#F8FAFC",
                  "explorer.folderItem.selectedIconForeground": "#3B82F6",
                  "explorer.fileItem.conflictForeground": "#7F1D1D",
                  "explorer.fileItem.errorForeground": "#7F1D1D",
                  "explorer.fileItem.warningForeground": "#d29922",
                  "explorer.folderItem.iconForeground": "#F8FAFC",
                  "explorer.fileItem.selectedIconForeground": "#F8FAFC",
                  "explorer.fileItem.modifiedForeground": "#29c3a0",
                  "list.dropBackground": "#02081740",
                  "list.filterMatchBackground": "#02081720",
                  "list.inactiveSelectionBackground": "#1E293B40",
                  "list.hoverForeground": "#F8FAFC",
                  "statusBarItem.hoverBackground": "#1E293B",
                  "gitDecoration.submoduleResourceForeground": "#F8FAFC"
                }
              }
            }
          ]
        }
```

> [!TIP]
> Troubleshooting
> If there is a setting that you want to use but do not see it among the options under appearance, I still got you covered. You can place anything you need in the settings.workspace object and will be included when updating the configuration.
> If a setting isn't applying:
> 1. Check the setting name matches VS Code's exact setting key
> 2. Try placing it in `settings.workspace` instead
> 3. Restart VS Code after applying the layout
> 4. Check the VS Code output panel for errors
> 5. Verify the setting type (boolean, string, number, object)

> [!TIP]
> Additional Resources
> - [VS Code Settings Reference](https://code.visualstudio.com/docs/getstarted/settings)
> - [VS Code API Documentation](https://code.visualstudio.com/api)
> - [Workspace Configuration](https://code.visualstudio.com/docs/editor/workspaces)

> [!TIP]
> Theme
> To quickly create this section you can use the theme builder that can be found on the web ui.
> Once your theme has been built just copy over the settings into the config


