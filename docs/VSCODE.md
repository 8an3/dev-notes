## VS Code

## Table of Contents

- [VSCode Extension Configuration Testing Suite](#vscode-extension-configuration-testing-suite)
- [Performance Switch](#performance-switch)
- [Custom VSIX Packager](#custom-vsix-packager)
- [Region Folding](#region-folding)
- [JSON File Formatting and Validation](#json-file-formatting-and-validation)
- [Encoder/Decoder](#encoderdecoder)
- [File Formatting Configurator](#file-formatting-configurator)
- [Formatter](#formatter)
- [Inline Imports](#inline-imports)
- [Batch Rename](#batch-rename)
- [Dependency "Deep Link" (packageSearch)](#dependency-deep-link-packagesearch)
- [File Line Jumper](#file-line-jumper)
- [File Search Jumper](#file-search-jumper)
- [File Nesting](#file-nesting)
- [Remove Trailing Commas](#remove-trailing-commas)
- [Remove All Comments](#remove-all-comments)
- [Remove console.log](#remove-consolelog)
- [Remove Unused Imports](#remove-unused-imports)
- [Zombie Process Killer (portReaper)](#zombie-process-killer-portreaper)
- [Auto Zombie Process Killer](#auto-zombie-process-killer)
- [Snapshot Engine](#snapshot-engine)
- [The ".env" Context Swapper (envProfile)](#the-env-context-swapper-envprofile)
- [Intelligent JSON Schema Support](#intelligent-json-schema-support)
- [VSCode Commands reference](#vscode-commands-reference)
- [VSCode Commands reference V2 Dynamic](#vscode-commands-reference-v2-dynamic)

### VSCode Extension Configuration Testing Suite

Are you creating an extension for vscode?
Are you sick and tired of microsofts shit documentation, or lack of rather.
Are you sick and tired of not know what does what exactly while creating your extension and blindly firing off configuration values, then only relying on warning or error logs?

Well fear no more

### Performance Switch

Toggle performance modes for working with large files or resource-intensive operations.

**Access:** DevStack Quick Pick or editor context menu

**Available Options:**

**Disable For Current File**
- Disables DevStack features for the currently active file
- Improves performance when working with large files

**Enable For Current File**
- Re-enables DevStack features for the currently active file
- Restores full functionality

**Disable Everything**
- Globally disables all DevStack features across the workspace
- Maximum performance mode

**Enable Everything**
- Re-enables all DevStack features across the workspace
- Full feature restoration

**Toggle Global Disable**
- Quick toggle between enabled and disabled states
- Fastest way to switch performance modes

![Performance Switch](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/performance.jpg)
![Performance Options](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/performance2.jpg)

### Custom VSIX Packager

Alternative VSIX packaging solution as an alternative to vsce.

**Access:** DevStack Quick Pick → Custom VSIX Packager

**Features:**
- Smaller file sizes compared to vsce
- Custom ignore patterns
- Structure visualization
- More resilient build process

![VSIX Packager](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/performance2.jpg)

### Region Folding

Fold by region level (1-7) instead of actual nesting level.

**Available Commands:**

**Fold Commands:**
- `ocrmnavigator.foldRegionLevel1` - Fold Region Level 1
- `ocrmnavigator.foldRegionLevel2` - Fold Region Level 2
- `ocrmnavigator.foldRegionLevel3` - Fold Region Level 3
- `ocrmnavigator.foldRegionLevel4` - Fold Region Level 4
- `ocrmnavigator.foldRegionLevel5` - Fold Region Level 5
- `ocrmnavigator.foldRegionLevel6` - Fold Region Level 6
- `ocrmnavigator.foldRegionLevel7` - Fold Region Level 7

**Toggle Commands:**
- `ocrmnavigator.toggleFoldRegionLevel1` - Toggle Region Level 1
- `ocrmnavigator.toggleFoldRegionLevel2` - Toggle Region Level 2
- `ocrmnavigator.toggleFoldRegionLevel3` - Toggle Region Level 3
- `ocrmnavigator.toggleFoldRegionLevel4` - Toggle Region Level 4
- `ocrmnavigator.toggleFoldRegionLevel5` - Toggle Region Level 5
- `ocrmnavigator.toggleFoldRegionLevel6` - Toggle Region Level 6
- `ocrmnavigator.toggleFoldRegionLevel7` - Toggle Region Level 7

**Usage:** Create DevStack item with type `command` using these command IDs, or access via DevStack Quick Pick

### JSON File Formatting and Validation

Format JSON/JSONC files and toggle error checking.

**Available Commands:**

**Formatting:**
- `ocrmnavigator.formatCurrentJsonFile` - Format Current JSON File (converts multiline to inline)
- `ocrmnavigator.formatPackgeDevJson` - Format package.dev.json
- `ocrmnavigator.formatGlobalNavigatorConfigJson` - Format Global Navigator Config JSON

**Validation Toggle:**
- `ocrmnavigator.toggleJsonValidation` - Toggle JSON error checking
- `ocrmnavigator.toggleJsoncValidation` - Toggle JSONC error checking

**Usage:** Create DevStack item with type `command` using these command IDs, or access via DevStack Quick Pick

### Encoder/Decoder

Convert between multiple file formats with support for 13+ format types.

**Access:** Web GUI

**Features:**
- Base64 encoding/decoding
- SVG conversion
- MP4 to MP3 conversion
- Batch processing support
- Quality settings configuration
- Multiple format support

### File Formatting Configurator

Configure custom formatters per file type with live preview.

**Access:** Web GUI

**Features:**
- Per-file-type formatter configuration
- Live preview of formatting changes
- Custom formatting rules
- Save and apply configurations

### Formatter

Multi-format file formatter supporting 33+ file types.

**Access:** Right-click → Formatters → Select option

**Features:**
- Format 33+ file types
- Set as default formatter per file type
- Configure via "Format Document with..." → Configure → Select desired formatter

![Formatters](https://raw.githubusercontent.com/8an3/dev-notes/main/config/formatters.jpg)

### Inline Imports

Convert multi-line imports to single-line format.

**Access:** Right-click → Format document with → Select option

**Features:**
- Transforms multi-line imports into single-line format
- Automatically converts `@` to `~` in import paths
- Clean, consistent import statements

[Video Demo](https://youtu.be/YV9dIXP1ob4)

### Batch Rename

Mass file renaming tool with advanced pattern matching.

**Access:** Highlight files → Right-click → Batch Rename

**Features:**
- Edit multiple filenames via generated .txt file
- Pattern matching support
- Regex support
- Undo functionality
- Bulk operations

### Dependency "Deep Link" (packageSearch)

Quick access to library documentation and entry points directly from imports.

**Access:** Hover over imports in your code

**Features:**
- Clickable links for package.json
- Clickable links for README.md
- Direct access to package entry point
- No more scrolling through node_modules in sidebar
- Instant documentation access

**Usage:** Hover over any import statement to reveal clickable links to package documentation and code.

### File Line Jumper

Create clickable file links with specific line numbers.

**Access:** Use `// @dev path:line` syntax in comments

**Syntax:** `// @dev path/to/file.tsx:lineNumber`

**Example:** `// @dev app/components/catalyst-ui/primitives/table.tsx:6`

**Features:**
- Creates clickable links in any file
- Opens files at specific line numbers
- Works before and after return statements
- Quick navigation to exact code locations

[Video Demo](https://youtu.be/xR1osGkuNCA)
![File Line Jumper](https://raw.githubusercontent.com/8an3/dev-notes/main/ui/vfs/file-linking.jpg?raw=true)

### File Search Jumper

Create search-based file links that navigate to the first instance of a search term.

**Access:** Use `// @devsearch path:term` syntax in comments

**Syntax:** `// @devsearch path/to/file.tsx:SearchTerm`

**Example:** `// @devsearch app/components/catalyst-ui/data/table-data.tsx:Table`

**Features:**
- Creates links that search for specific terms
- Navigates to first instance of search term
- Useful for finding component definitions
- Quick code exploration

[Video Demo](https://youtu.be/Otd3jWfSf4M)
![File Search Jumper](https://raw.githubusercontent.com/8an3/dev-notes/main/ui/vfs/file-searching.jpg?raw=true)

### File Nesting

**🚧 COMING SOON**

Configure file nesting rules to organize related files in explorer view.

**Access:** Configure via settings

**Planned Features:**
- Custom nesting patterns
- Group related files automatically
- Clean explorer view
- Configurable rules

### Remove Trailing Commas

Remove trailing commas from JSON and JavaScript objects.

**Access:** Right-click → Formatters → Select option

**Features:**
- Cleans JSON files
- Cleans JavaScript objects
- Ensures code compatibility
- One-click cleanup

![Formatters](https://raw.githubusercontent.com/8an3/dev-notes/main/config/formatters.jpg)

### Remove All Comments

Strip all comments from the current file.

**Access:** Right-click → Formatters → Select option or Command Palette

**Features:**
- Removes all comment types
- Works with multiple languages
- Clean code output
- Preserves code functionality

![Formatters](https://raw.githubusercontent.com/8an3/dev-notes/main/config/formatters.jpg)

### Remove console.log

Remove console.log statements from files, folders, or entire workspace.

**From File:**
- **Access:** Right-click → Formatters → Select option or Command Palette
- Removes all console.log statements from current file

**From Folder:**
- **Access:** Right-click folder → Formatters → Select option
- Removes all console.log statements from all files in selected folder

**From Workspace:**
- **Access:** Command Palette → Select remove console.log from workspace
- Removes all console.log statements from entire workspace

![Formatters](https://raw.githubusercontent.com/8an3/dev-notes/main/config/formatters.jpg)

### Remove Unused Imports

Detect and remove import statements that are not used in the file.

**Access:** Right-click → Formatters → Select option or Command Palette

**Features:**
- Automatic detection of unused imports
- Clean up import statements
- Improved code readability
- Reduces bundle size

![Formatters](https://raw.githubusercontent.com/8an3/dev-notes/main/config/formatters.jpg)

### Zombie Process Killer (portReaper)

Kill processes running on specific ports to free them for your dev server.

**Access:** DevStack Quick Pick → VS Code → Zombie Process Killer

**The Problem:**
```
Error: EADDRINUSE: address already in use :::3000
```

**Old Solution:**
```bash
lsof -i :3000
kill -9 <PID>
```

**Features:**
- Quick access to top 5 most common dev server ports (3000, 3001, 5173, 8080, 4200)
- Custom port number input option
- One-click port clearing
- Cross-platform support

### Auto Zombie Process Killer

Automatically detect and kill processes blocking your dev server port.

**Access:** DevStack Quick Pick → VS Code → Auto Zombie Process Killer

**How It Works:**
1. Scans package.json for your dev script
2. Extracts port number from dev script
3. Runs shell script: `fuser -k 3000/tcp` (or cross-platform equivalent)
4. Automatically clears the port

**Features:**
- Automatic port detection from package.json
- No manual port entry needed
- Cross-platform compatibility
- Instant port clearing

### Snapshot Engine

Save and restore your VS Code workspace layout states.

**Access:** Dedicated quick pick menu in status bar

**Features:**
- Capture current workspace state
- Save granular layout configurations
- Restore to previous workspace states
- Create named snapshots
- Quick switching between layouts
- Same configuration type as `layout` item type

**Use Cases:**
- Save ideal working layouts
- Switch between different project configurations
- Restore after workspace disruption
- Share layouts with team members

### The ".env" Context Swapper (envProfile)

A zero-error environment configuration system that eliminates manual .env editing and ensures your app never breaks from typos or misconfigurations.

**The Problem:**
Manual .env editing is error-prone and tedious. Switching between development and production requires commenting/uncommenting multiple variable sets across microservices—one typo breaks everything.

**The Solution:**
Automated environment switching with a single click. No manual editing, no commenting, no errors.

**How It Works:**

**File Structure:**
- `.env` - Active configuration file (auto-generated, never edit manually)
- `.dev.env` - Source file containing all environment variable pairs

**Variable Format:**
Each environment variable has two versions prefixed with `LOCAL_` or `REMOTE_`:

```env
LOCAL_environment='development'
REMOTE_environment='production'

LOCAL_DATABASE_URL="postgres://postgres:Ch3w8acca66@localhost:5432/catalyst"
REMOTE_DATABASE_URL="postgresql://neondb_owner:npg_mfHjL51BCRlg@ep-solitary-glade-adoppzpt-pooler.c-2.us-east-1.aws.neon.tech/neondb?sslmode=require"

LOCAL_SESSION_SECRET='9k7mN2pQ8xR4vL6wE3tY1zH5jC0bF8dG7aS4nM9qK2uI6oP3vX8wR1eT5yH7jN0m'
REMOTE_SESSION_SECRET='9k7mN2pQ8xR4vL6wE3tY1zH5jC0bF8dG7aS4nM9qK2uI6oP3vX8wR1eT5yH7jN0m'

LOCAL_UI_CHECKOUT='/Catalyst/UI/code/list/all'
REMOTE_UI_CHECKOUT='/Catalyst/UI/code/list/all'

LOCAL_PADDLE_CLIENT_TOKEN="live_79e842b9aee2a289dc3431d8967"
REMOTE_PADDLE_CLIENT_TOKEN="live_79e842b9aee2a289dc3431d8967"

LOCAL_PADDLE_SERVER_TOKEN="pdl_live_apikey_01k4v3y240x0t4v8t39ytj7swr_yAAtEFKtVdpaYCqYHVBvyt_Aln"
REMOTE_PADDLE_SERVER_TOKEN="pdl_live_apikey_01k4v3y240x0t4v8t39ytj7swr_yAAtEFKtVdpaYCqYHVBvyt_Aln"
```

**Missing Values:**
If either `LOCAL_` or `REMOTE_` value is missing in `.dev.env`, the variable is still included in `.env` but set to empty:

```env
DATABASE_URL=""
```

**Quick Switch Interface:**
Built-in quickpick with two options:
- `Set Local .env Var's` - Switches to development configuration
- `Set Remote .env Var's` - Switches to production configuration

**Safety Guarantee:**
The system always reads from `.dev.env` and writes a complete `.env` file, regardless of current state. This idempotent approach ensures the configuration never enters an invalid state.


### Intelligent JSON Schema Support
The extension includes a powerful schema-driven engine that provides deep IntelliSense and automated workflows for JSON and JSONC files. By detecting the $schema property in your files, it provides context-aware assistance tailored to your specific data structure.

#### ✨ Key Features
Smart Autocomplete:

Booleans: Instant suggestions for true/false.

Enums: Automatically lists all allowed values defined in the schema with their descriptions.

Numbers: Suggests default values and displays minimum or maximum constraints directly in the completion list.

Context-Aware Path Detection: High-accuracy logic to determine your exact position within nested JSON objects, ensuring suggestions are always relevant to the current key.

Quick Fix Code Actions: Use Cmd+. (Mac) or Ctrl+. (Windows) on a value to quickly swap between enum members or toggle booleans without typing.

Schema Caching: Optimized performance through a local cache, ensuring the UI remains snappy even when working with large or complex schemas.

Deep Schema Support: Correctly resolves complex schema structures including definitions, items, and anyOf blocks.

#### 🛠 How it Works
Detection: The engine looks for a "$schema": "./path/to/schema.json" entry in your JSON file.

Parsing: The SchemaParser extracts all possible fields, types, and constraints.

Mapping: As you move your cursor, the extension calculates your "JSON Path" and matches it against the parsed schema to provide the right suggestions at the right time.

#### Commands

- ocrmnavigator.clearSchemaCache
  - Clears the internal schema cache. Useful if you have updated your schema file and want to see the changes immediately.


<!-- #endregion -->

<!-- #region Shortcuts REFERENCE -->

### VSCode Commands reference
- available via devstack quickpick and click on vscode cmds
- features 1800+ vscode settings to be used within settings.json files
- when a settings.json key has been clicked, copies that key into your clipboard

### VSCode Commands reference V2 Dynamic
- available via devstack quickpick and click on vscode cmds dynamic
- the biggest difference between this and v1 is that this list is dynamically fetched, and when clicking on a key instead of just copying that key to your clipboard to be pasted into your settings.json file, it will open another menu with all of the values relative to that key, then once one of these key : value pairs bas been clicked it will copy the pair into your clipboard to be pasted into your settings.json file
- due to it being dynamic, till its tested thoroughly I do not know how reliable or stable it will be which is why v1 will remain an option in the menu as those options are hardcoded, and has been extremely reliable obviously


---

[🡄 Return](https://github.com/8an3/DevStack)
