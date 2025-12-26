## CONFIG

> [!TIP]
> Configuration files are automatically formatted at load time, removing trailing commas and comments. While comments are stripped during loading, it's recommended not to store comments in config files since formatted versions are used when the save function triggers.

## Table of Contents

- [Share Config With Friends / Export All Configs](#share-config-with-friends--export-all-configs)
- [View Config Example](#view-config-example)
- [Add Missing Imports w/ Global Config](#add-missing-imports-w-global-config)
- [Default Apps Configuration](#default-apps-configuration)
- [Create Export Index && Create Named Export Index](#create-export-index--create-named-export-index)
- [Edit .json Config](#edit-json-config)
- [Export Config](#export-config)
- [Import Config](#import-config)
- [Add ESLint & Prettier Configs](#add-eslint--prettier-configs)
- [To Do Notes Reminders and Post Its](#to-do-notes-reminders-and-post-its)
- [Markdown Pre-Processor](#markdown-pre-processor)

### Share Config With Friends / Export All Configs

Export your complete DevStack configuration to share with team members or backup your setup.

**Access:** Settings dropdown → Share Config

**What Gets Exported:**
- All configuration files
- README with setup instructions
- Saves to `shareWithFriends` folder in workspace

**Features:**
- Complete setup export
- Easy sharing with others
- Includes documentation
- Ready-to-import format

**⚠️ Important:** Review exported files for sensitive data (API keys, tokens, paths) before sharing.

![Share Config](https://raw.githubusercontent.com/8an3/dev-notes/main/config/share-config.jpg)
![Settings](https://raw.githubusercontent.com/8an3/dev-notes/main/config/settings.jpg)

---

### View Config Example

Browse example configuration files to understand DevStack's setup and structure.

**Access:** Settings dropdown → View Config Example, or Web GUI Sidebar

**What's Included:**
- Example configuration files
- Commented explanations
- Best practices
- Common patterns
- Setup templates

![View Config](https://raw.githubusercontent.com/8an3/dev-notes/main/config/view-config.jpg)
![Settings](https://raw.githubusercontent.com/8an3/dev-notes/main/config/settings.jpg)

---

### Add Missing Imports w/ Global Config

Automatically detect and add missing import statements based on your global configuration.

**Access:** Right-click in editor → Formatters → Add Missing Imports

**Features:**
- Scans for undefined references
- Adds appropriate import statements
- Uses global config for import paths
- Works with custom module mappings
- Supports multiple import styles

![Add Missing Imports](https://raw.githubusercontent.com/8an3/dev-notes/main/config/add-missing.jpg)

---

### Default Apps Configuration

Control which DevStack features load on startup for optimal performance and workflow.

**Access:** Extension settings, workspace settings, user settings, or Web GUI

**Available Settings:**
```json
{
  "ocrmnavigator.vscodeVersion": "Code - Insiders",
  "ocrmnavigator.configPath": ".vscode/ocrmnavigator/search-config.json",
  "ocrmnavigator.toggleHiddenItems": true,
  "ocrmnavigator.superuserTaskRunner": true,
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
  "ocrmnavigator.addMissingImports": true,
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
  "ocrmnavigator.extMgrForDevs": true,
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
  "ocrmnavigator.notesTodoAndThings": true,
  "ocrmnavigator.renderMd": true,
  "ocrmnavigator.visualizeSchemaRelations": true,
  "ocrmnavigator.createFolderSmartIndex": true,
  "ocrmnavigator.tailwindConverter": true,
  "ocrmnavigator.convertToAgnostic": true,
  "ocrmnavigator.concurrent": true,
  "ocrmnavigator.autoSequencer": true
}
```

---

### Create Export Index && Create Named Export Index

Generate index files that act as registries for easier imports across your project.

**Access:** Right-click any folder → Create Export Index

**Use Case Example:**

Instead of importing each component individually:
```javascript
import DemoOne from './blocks/DemoOne';
import DemoTwo from './blocks/DemoTwo';
import LoanApp from './blocks/LoanApp';
// ... 1550+ more imports
```

Create a registry and import once:
```javascript
import * as Components from './index';

// Then use:
<Components.LoanApp />
<Components.ServiceRepairForm />
<Components.DemoOne />
```

**Features:**
- Recursive export generation
- Works with any folder structure
- Saves massive time on large component libraries
- Enables find-and-replace workflows
- Creates index.tsx automatically

**Real-World Impact:** Converted 1550+ individual imports to single registry import using find-and-replace in seconds.

![Registry](https://raw.githubusercontent.com/8an3/dev-notes/main/config/registry.jpg)

---

### Edit .json Config

Quick access to edit your DevStack configuration file directly in the editor.

**Access:** Settings dropdown → Edit Config

**Features:**
- Opens config in editor
- No need to navigate file system
- Syntax highlighting
- Auto-completion support
- Instant access

![Edit Config](https://raw.githubusercontent.com/8an3/dev-notes/main/config/edit-config.jpg)

---

### Export Config

Export your current configuration to a file in your workspace root directory.

**Access:** Settings dropdown → Export Config

**Features:**
- Creates backup in workspace root
- Timestamped exports
- Complete configuration snapshot
- Easy to version control
- Shareable format

![Export Config](https://raw.githubusercontent.com/8an3/dev-notes/main/config/export-config.jpg)

---

### Import Config

Import a previously exported configuration or load a modified config file.

**Access:** Settings dropdown → Import Config

**Features:**
- Restore from backups
- Load shared configurations
- Apply custom modifications
- Validate on import
- Safe replacement

![Import Config](https://raw.githubusercontent.com/8an3/dev-notes/main/config/import-config.jpg)

---

### Add ESLint & Prettier Configs

Install standard ESLint and Prettier configuration files to your project.

**Access:** Viewers dropdown → Project → Add ESLint & Prettier Configs

**What Gets Added:**
- `.eslintrc.json` configuration
- `.prettierrc` configuration
- `.prettierignore` file
- Standard rule sets
- Ready to customize

![ESLint](https://raw.githubusercontent.com/8an3/dev-notes/main/config/eslint.jpg)

---

### To Do Notes Reminders and Post Its

Comprehensive task and note management system with GitHub repo sync and mobile-friendly web app.

**Access:** Explorer pane sections

**Key Features:**

**Single Source of Truth:**
- Uses GitHub repo for storage
- Access from any workspace
- Mobile-friendly web app available
- Always in sync

**Smart List View:**
- Toggle in bottom-right merges all lists
- Review all items at once
- Click any item to toggle complete/incomplete
- No more opening/closing individual lists
- Separated by list titles for clarity

**Explorer Pane Structure:**

**4 Main Sections:**
1. **To Do Lists**
   - Clickable checklist items in file tree
   - Click list title to edit in markdown
   - Auto-saves and syncs to repo
   - Nested items with folding support
   - Full GitHub integration (create, share, switch repos)

2. **Notes**
   - Simple note format
   - First line: `# NOTE` (title)
   - Line 3+: Your content
   - Unlimited notes
   - Markdown support

3. **Reminders**
   - Same as notes with date/time
   - First line: `# REMINDER` (title)
   - Third line: `DUE: 2025-05-22 09:00`
   - Line 5+: Your content

4. **Post Its**
   - Quick temporary notes during coding
   - Tab-based organization (5 color-coded tabs)
   - Click tab trigger to copy contents
   - No need for separate files or external apps

**Post It Tab System Example:**
```javascript
<Tabs>
  <TabsList>
    <TabsTrigger value="white">White</TabsTrigger>
    <TabsTrigger value="green">Green</TabsTrigger>
    <TabsTrigger value="blue">Blue</TabsTrigger>
    <TabsTrigger value="yellow">Yellow</TabsTrigger>
    <TabsTrigger value="purple">Purple</TabsTrigger>
  </TabsList>
  <TabsContent value="white">notes data</TabsContent>
  <TabsContent value="green">notes data</TabsContent>
  <TabsContent value="blue">notes data</TabsContent>
  <TabsContent value="yellow">notes data</TabsContent>
  <TabsContent value="purple">notes data</TabsContent>
</Tabs>
```

**Context Menu Actions:**
- Label items: Priority, Trash, Completed
- Delete items
- Copy contents (Post Its)
- Clear contents (Post Its)
- Delete all (Post Its)

**Title Bar Actions:**
- Quick create buttons for each section
- Expand/collapse sections
- Category management

> [!TIP]
> **Migrating from old extension?** Easy! In your global settings, change all `ntrsync` values to `ocrmnavigator` (e.g., `"ocrmnavigator.todo.branch": "main"`). On next startup, everything loads exactly as before.

---

### Markdown Pre-Processor

Advanced markdown document processor with variables, table of contents, sourcemap generation, and content conversion.

**Access:** DevStack Quick Pick → Markdown Pre-Processor, or run JavaScript file from terminal

**Available Features:**

**1. Variable System**
- Define variables: `<!-- const varName: value -->`
- Use variables: `${varName}`
- Automatic substitution
- Recursive processing

**2. List Conversion**
- Converts markdown lists to inline HTML
- Perfect for tables requiring HTML lists
- Human-readable source, render-ready output
- Example: `- list item` → `<ul><li>list item</li></ul>`

**3. Table of Contents Generator**
- Auto-generates from headers
- Multiple styles: unordered, ordered, roman, accordion
- Auto-updates on each run
- Configurable placement

**4. Sourcemap Creator/Updater**
- Generates document structure map
- Section and subsection tracking
- Auto-placement before License section
- Always current with content

**5. Code Section Conversion**
- Processes code blocks in tables
- Syntax highlighting preservation
- Proper escaping for HTML

**Configuration:**
```javascript
const srcFile = 'README.dev.md'      // Source file
const tgtFile = 'README.md'          // Target file
const variableSystem = true          // Enable variables
const sourcemapUpdater = true        // Enable sourcemap
const tocUpdater = true              // Enable TOC
const tocType = 'roman'              // 'unordered', 'ordered', 'roman', 'accordion'
const tableConversion = true         // Enable table conversion
```

**Usage Options:**
- Run from DevStack Quick Pick menu
- Place in autorun folder for automatic processing
- Execute from terminal: `node markdown-pre-processor.js`
- Integrate into build workflows

**Full processor code available in config documentation.**

---