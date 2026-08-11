## VS Code

## Table of Contents

- [Configuration Testing Suite](#vscode-extension-configuration-testing-suite)
- [Performance Switch](#performance-switch)
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
- [Auto Fold Regions At File Open](#auto-fold-regions-at-file-open)

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Configuration Testing Suite

Are you creating an extension for vscode?
Are you sick and tired of microsofts shit documentation, or lack of rather.
Are you sick and tired of not know what does what exactly while creating your extension and blindly firing off configuration values, then only relying on warning or error logs?

Well fear no more

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Performance Switch

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

![Performance Switch](https://raw.githubusercontent.com/8an3/midgardr-notes/main/vfs/performance.jpg)
![Performance Options](https://raw.githubusercontent.com/8an3/midgardr-notes/main/vfs/performance2.jpg)


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Region Folding

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
- `ocrmnavigator.vscode.region.1.toggle` - Toggle Region Level 1
- `ocrmnavigator.vscode.region.2.toggle` - Toggle Region Level 2
- `ocrmnavigator.vscode.region.3.toggle` - Toggle Region Level 3
- `ocrmnavigator.vscode.region.4.toggle` - Toggle Region Level 4
- `ocrmnavigator.vscode.region.5.toggle` - Toggle Region Level 5
- `ocrmnavigator.vscode.region.6.toggle` - Toggle Region Level 6
- `ocrmnavigator.vscode.region.7.toggle` - Toggle Region Level 7

**Usage:** Create DevStack item with type `command` using these command IDs, or access via DevStack Quick Pick


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Encoder/Decoder

Convert between multiple file formats with support for 13+ format types.

**Access:** Web GUI

**Features:**
- Base64 encoding/decoding
- SVG conversion
- MP4 to MP3 conversion
- Batch processing support
- Quality settings configuration
- Multiple format support






## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Zombie Process Killer (portReaper)

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

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Auto Zombie Process Killer

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

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  The ".env" Context Swapper (envProfile)

A zero-error environment configuration system that eliminates manual .env editing and ensures your app never breaks from typos or misconfigurations.

**The Problem:**
Manual .env editing is error-prone and tedious. Switching between development and production requires commenting/uncommenting multiple variable sets across microservices—one typo breaks everything.

**The Solution:**
Automated environment switching with a single click. No manual editing, no commenting, no errors.

**How It Works:**

**File Structure:**
- `.env` - Active configuration file (auto-generated, never edit manually)
- `.hermes` - Source file containing all environment variable pairs

**Variable Format:**
Each environment variable has two versions prefixed with `LOCAL_` or `REMOTE_`:

```env
LOCAL_environment='development'
REMOTE_environment='production'

LOCAL_DATABASE_URL="postgres://postgres:Ch3w8acca66@localhost:5432/catalyst"
REMOTE_DATABASE_URL="postgresql://neondb_owner:npg_mfHjL51BCRlg@ep-solitary-glade-adoppzpt-pooler.c-2.us-east-1.aws.neon.tech/neondb?sslmode=require"

LOCAL_SESSION_SECRET='9k7mN2pQ8xR4vL6wE3tY1zH5jC0bF8dG7aS4nM9qK2uI6oP3vX8wR1eT5yH7jN0m'
REMOTE_SESSION_SECRET='9k7mN2pQ8xR4vL6wE3tY1zH5jC0bF8dG7aS4nM9qK2uI6oP3vX8wR1eT5yH7jN0m'

LOCAL_UI_CHECKOUT='/asgard/midgardr/code/list/all'
REMOTE_UI_CHECKOUT='/asgard/midgardr/code/list/all'

LOCAL_PADDLE_CLIENT_TOKEN="live_79e842b9aee2a289dc3431d8967"
REMOTE_PADDLE_CLIENT_TOKEN="live_79e842b9aee2a289dc3431d8967"

LOCAL_PADDLE_SERVER_TOKEN="pdl_live_apikey_01k4v3y240x0t4v8t39ytj7swr_yAAtEFKtVdpaYCqYHVBvyt_Aln"
REMOTE_PADDLE_SERVER_TOKEN="pdl_live_apikey_01k4v3y240x0t4v8t39ytj7swr_yAAtEFKtVdpaYCqYHVBvyt_Aln"
```

**Missing Values:**
If either `LOCAL_` or `REMOTE_` value is missing in `.hermes`, the variable is still included in `.env` but set to empty:

```env
DATABASE_URL=""
```

**Quick Switch Interface:**
Built-in quickpick with two options:
- `Set Local .env Var's` - Switches to development configuration
- `Set Remote .env Var's` - Switches to production configuration

**Safety Guarantee:**
The system always reads from `.hermes` and writes a complete `.env` file, regardless of current state. This idempotent approach ensures the configuration never enters an invalid state.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Intelligent JSON Schema Support
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

- ocrmnavigator.intellisense.schema.cache.clear
  - Clears the internal schema cache. Useful if you have updated your schema file and want to see the changes immediately.


<!-- #endregion -->

<!-- #region Shortcuts REFERENCE -->

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  VSCode Commands reference
- available via devstack quickpick and click on vscode cmds
- features 1800+ vscode settings to be used within settings.json files
- when a settings.json key has been clicked, copies that key into your clipboard

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  VSCode Commands reference V2 Dynamic
- available via devstack quickpick and click on vscode cmds dynamic
- the biggest difference between this and v1 is that this list is dynamically fetched, and when clicking on a key instead of just copying that key to your clipboard to be pasted into your settings.json file, it will open another menu with all of the values relative to that key, then once one of these key : value pairs bas been clicked it will copy the pair into your clipboard to be pasted into your settings.json file
- due to it being dynamic, till its tested thoroughly I do not know how reliable or stable it will be which is why v1 will remain an option in the menu as those options are hardcoded, and has been extremely reliable obviously

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Auto Fold Regions At File Open
- several options avialable for you to choose from, to configure the following options need to be within your workspace or user settings.json file
  - all files:
    - auto fold level one - `"ocrmnavigator.vfs.AUTO_FOLD_1": false,`
    - auto fold levels one and two - `"ocrmnavigator.vfs.AUTO_FOLD_1_2": true,`
  - package.json
    - auto fold level two - `"ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2": false,`
    - auto fold levels two and three - `"ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2_3": true,`


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Open file in specific editor group

Can set via the extensions settings which editor group to force open files whenever you use a set up that is beyond a single editor group config. Works amazingly well with the layout ngin whenever you configure 2 or more cols as editor groups

---

[🡄 Return](https://github.com/8an3/DevStack)


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Left Off Note

Project-specific note system to track where you left off in your work.

**Access:** Context menu → Open Leftoff Note

**Features:**
- Leave detailed notes for each project
- Persistent storage per workspace
- Full markdown support
- Quick access from context menu
- Never lose track of your progress
- Automatic workspace association

![Left Off Note](https://raw.githubusercontent.com/8an3/midgardr-notes/main/config/left-off.jpg)

---


