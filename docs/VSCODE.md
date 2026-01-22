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
- [Auto Fold Regions At File Open](#auto-fold-regions-at-file-open)

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
- `ocrmnavigator.vscode.region.1.toggle` - Toggle Region Level 1
- `ocrmnavigator.vscode.region.2.toggle` - Toggle Region Level 2
- `ocrmnavigator.vscode.region.3.toggle` - Toggle Region Level 3
- `ocrmnavigator.vscode.region.4.toggle` - Toggle Region Level 4
- `ocrmnavigator.vscode.region.5.toggle` - Toggle Region Level 5
- `ocrmnavigator.vscode.region.6.toggle` - Toggle Region Level 6
- `ocrmnavigator.vscode.region.7.toggle` - Toggle Region Level 7

**Usage:** Create DevStack item with type `command` using these command IDs, or access via DevStack Quick Pick

### JSON File Formatting and Validation

I haven't had much luck with formatters in the past tbh, but I have been using this foramtter for a while now without issue. I will revisit the formatter configurator at some point to re create the underlying functionality of it as it is not in the best condition currently. At that time, I will make the json/jsonc formatter configurable as it is not in its current state. As I'm assuming not many people will enjoy the current settings that it was coded with as it turns multi line objects into single line. For some reason I seem to be one of a few who opt for this configuration. IF you are one of those few, enjoy! 

This is now available to be configured as a default formatter for the json and jsonc file type with vscode.

Format JSON/JSONC files and toggle error checking.

**Available Commands:**

**Formatting:**
- `ocrmnavigator.formatCurrentJsonFile` - Format Current JSON File (converts multiline to inline)
- `ocrmnavigator.formatPackgeDevJson` - Format package.dev.json
- `ocrmnavigator.formatGlobalNavigatorConfigJson` - Format Global Navigator Config JSON

**Validation Toggle:**
- `ocrmnavigator.performanceSwitch.json.validate.toggle` - Toggle JSON error checking
- `ocrmnavigator.performanceSwitch.jsonc.validate.toggle` - Toggle JSONC error checking

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

Usage:
- in your file tree highlight all the files you want to rename
- right click on any file that is currently highlight and select `Rename Batch`
- this opens a text file with all the names of the selected files
- each line is associated with that file it is referencing and whatever value is on that line when saved, overwrites the file name 


> [!IMPORTANT]
> Due to the size of this extension, this is a feature that fell through the cracks. 
> I remember when first creating this feature, I had issues creating it in terms of making it function exactly the way I wanted it to. As I was converting each function to the new naming convention, and when I got to renaming this one, I noticed that it was completely empty. 
> My bad, ever since I decided to create the functionality I needed rather then trying to hunt down a new extension for it, I haven't opened that tab in a very long time or else I would have noticed that the extension I thought I used to use for it is infact still active. 
>
> With saying, this time around it has been created and functions exactly the way I want it to. Again I apologize but I hope you can understand where I'm coming from with making that mistake. 
> 
> Since this extension is well over the 100 mark in terms of extensions worth of functionality, even though the readme only states 100+. If I had to guess... I know its currently sitting at atleast 125 as that was the number I counted the last time but that was a while ago, 135+ maybe even 145+, I know that number is just rediculous, but I know for a fact that even at 145 its a conservatinumber and lower then the actual number. Due to a lot of features I have coded in, typically get features found from 2, 3 sometimes even 4 extensions and consolidating it down into one feature. 
> Because of that I will never know the true number of where it's currently at. 
> This is due to, whenever I feel that a feature is lacking in something or just needs something I wish it had but can't put my finger on it. I will go through the marketplace, search for extensions relevant to what I want, and research each one, and making notes of anything I want to include into this extension. 
> That alone contributes the most when it comes to feature parity when comparing a feature found here to another extension in its entirety. Snippets being an area for a good example, while there are 15+ extensions devoted to snippets, with the majority of them being terrible, all of them atleast have one good idea that they implemented.




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

- ocrmnavigator.intellisense.schema.cache.clear
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

### Auto Fold Regions At File Open
- several options avialable for you to choose from, to configure the following options need to be within your workspace or user settings.json file
  - all files:
    - auto fold level one - `"ocrmnavigator.vfs.AUTO_FOLD_1": false,`
    - auto fold levels one and two - `"ocrmnavigator.vfs.AUTO_FOLD_1_2": true,`
  - package.json
    - auto fold level two - `"ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2": false,`
    - auto fold levels two and three - `"ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2_3": true,`


### Open file in specific editor group

Fucking microsoft... Why do you reveal so many apis but lock others when they should be open? Some that don't even make sense...

With the new layout engine, more ideas have surfaced, for exmaple with how I configured my layout by column:
- 1. 1/3 the size of the other two columns, hosts my to do list and notes, the extensions interface allows each item to be clickable, but for some projects i would just like to have the doc open so i can very quickly add / edit items mean while still using the interface to check them off or delete whole docs
- 2. this being the editor group I want to be actively coding in, which is the editor group I would like to have files open in, no matter where your currently focused, both in this extensions workspace and a couple of other larger projects where the explorer view... is rediclously long, I'm always opening files in the wrong group. Coupled with the ability to now open pinned and non pinned files on a per group basis at initial load, having this ability to force open into a specfic group would be phenominal, considering I also have one workspace that opens 4 columns wide
- 3. this colummn I devote to files like, configs, pkg.json, readme.md, or files where I need to reference a lot of things but not actually code in them 

so currently, there is no way to intercept the file opening process, theres no way to hover over a file line item in the explorer view and say use a short cut to open the file instead, that way you can map it to a mouse button or even just use your keyboard, theres no way to program any mouse button in vscode... at all, why though with the million other fucking things can be done... that just seems like such a glaringly missed oppurtunity. Especially when you compare it to the gaming industry, where as, if it has a button... no matter where it is in terms of a device, or what type of button it may or may not be... they're ALL configurable and depending on the provider you can program some rediculous things.

SO verrrry annoyingly, I'm going to test the only way that is available, that does not ADD to the end-users process which means it is still just a left click in order to obtain the end result... it is just not the way I want the actual function, to perform unfortuantly. Despite that, you may love or may hate it like I currently do, but who knows maybe after testing I'll put up with the cost of doing business as they say. The cost of doing it this way, once the file opens in whatever group your currently focused in, once that event happens it checks to see which group the file opened in and if it opened in the wrong group it closes the file and re opens in the correct group. I know it seems like a small thing to pay, but I'm just annoyed because having the ability to program mouse buttons and intercept that process would open up so many more configurable options for the layout engine. Because of this I will be looking at, hopefully, adding a new group to configure with the layout engine which would be a keyboard shortcut map, allowing you to change maps on a workspace basis, if you wanted. I think that's possible, but who knows with microsoft even though you can manually program shortcuts through the interface, maybe that api is locked too. I think that would be a nice feature because you could base your map, maybe not on a workspace basis per say, but on a per language basis having one map for typescript and another for c++, it would still have to configured as a workspace, but theres only a single main language per workspace anyways. 

BTW, if you haven't tried the layout engine, just go try it because my inital thoughts were, maybe I'll use it, lets try it and see... to, jesus this has honestly changed my entire coding experience within vscode.
Open icon library, with all the main files I NEED open in order to do what needs to be done, FAST and gtfo
Components library, its so fucking massive its stupid, but now I don't just open critical files, but also use the default files kind of like a cheat in order to get to nested folders more quickly that are an absolute pain to navigate to 
this extensions workspace, open all critical files, as there are several and on top of that, because I'm constantly testing things, depending on what feature is being added, while coding I need certain files open that aren't even in the workspace, that's been a very welcoming change since I no longer have to open a file explorer, navigate to the folder I need to get to ( even though I do have those folders listed as a shortcut in file explorer ), just to vscode DEFAULT to have everything I need open

and due to just how much more devstack gets used than the vscodes file explorer, ive swapped their locations including the activity bar 

All the while, each workspace has dedicated notes, to do lists, reminders and so on... each opening the correct relevant docs everything single time, with 0 user interaction. The theme part of the engine is cute and all but being able to control, with a click or at workspace load, your entire vscode instance changes based on what your doing or what you need to focus on since you can have 30 layouts for a workspace 

yes it is configurable on a workspace by workspace case: `"ocrmnavigator.vfs.targetEditorGroup": 1-9` 

---

[🡄 Return](https://github.com/8an3/DevStack)

