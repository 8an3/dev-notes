
<!-- #region GETTING STARTED -->


***Requirements***

***Your VSCode instance must be within a workspace for the extension to become and remain active.*** For example, if you open a single file while that instance is not within a workspace or in a new window / instance, the extension will not be available for use and will be hidden from view.

<!-- #endregion -->

<!-- #region usage -->


## Usage Guide


#### VS Code GUI

##### Adding Items

**Access:** Click the plus icon in the extensions title pane

**Steps:**
1. Choose between VS Code interface or web interface (VS Code interface recommended for first-time use)
2. Select item type from quick pick menu
3. Enter item label
4. Enter item value (e.g., `editor.foldLevel2`)
   - **Auto-paste:** If you have a value in your clipboard, it automatically pastes here
   - **Tip:** Copy command values while browsing - they'll be inserted automatically at this step
5. Select which folder to place the item in

[Step-by-step Visual Breakdown](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/add-item.md?raw=true)

##### Adding Files As Items

**Access:** Explorer view → Right-click any file → Add to DevStack

**Process:**
- Same as adding regular items
- No value entry needed (file location becomes the value automatically)

[Step-by-step Visual Breakdown](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/add-file.md?raw=true)

##### Editing/Deleting Items

**Access:** Right-click any item in the extensions file tree

**Available Actions:**
- **Edit Item** - Step-by-step editing of label, value, and location
- **Edit Label** - Change item name
- **Edit Value** - Modify item value
- **Move Item** - Relocate to different folder
- **Delete** - Remove item
- **Toggle Hidden** - Switch visibility (false ↔ true)

[Context Menu Screenshot](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/edit-file.jpg?raw=true)

##### Editing/Deleting Folders

**Access:** Right-click any folder in the extensions file tree

**Available Actions:**
- **Edit Folder Label** - Rename folder
- **Move Folder** - Relocate folder
- **Delete** - Remove folder and contents
- **Expand Folder by Default** - Set default expanded state
- **Collapse Folder by Default** - Set default collapsed state
- **Toggle Hidden** - Switch visibility (false ↔ true)

[Context Menu Screenshot](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/folder-context.jpg?raw=true)

##### Executing/Triggering Items

**Usage:** Simply click any item to trigger its configured action

[Quick Demo Video](https://youtu.be/1zkGK3kxE_8)

---

#### JSON Config Settings

##### Overview

> **Note:** You never need to manually edit the config file. This documentation is for users who prefer configuring through JSON instead of the VS Code or Web GUI.
>
> **Code vs Code-Insiders:** If using standard VS Code (not Insiders), replace `code-insiders` with `code` in all examples.

##### Global and Workspace Folders

**Folder Structure:**

Folders require these values:
- `label` (string) - Folder name
- `type` - Must be `"folder"`
- `expanded` (boolean) - Whether folder expands on startup
- `global` (boolean) - Global or workspace-specific
- `items` (array) - Contains folder items
- `hidden` (boolean, optional) - Hide from view

**Global vs Workspace:**
- **Global folders:** Available in all workspaces
- **Workspace folders:** Only available in current workspace

**Example Configuration:**

```json
{
  "categories": [
    {
      "label": "MAIN",
      "expanded": false,
      "type": "folder",
      "global": true,
      "items": [
        {
          "label": "CRM",
          "path": "code-insiders -n f:/DevStack",
          "type": "powershellCommand"
        }
      ]
    },
    {
      "label": "UTILS",
      "expanded": false,
      "type": "folder",
      "global": false,
      "items": [
        {
          "label": "prisma.schema",
          "path": "prisma/prisma.schema",
          "type": "file"
        }
      ]
    },
    {
      "label": "HIDDEN",
      "expanded": false,
      "type": "folder",
      "global": false,
      "hidden": true,
      "items": [
        {
          "label": "generateAndBuild",
          "path": "pnpm run generate && pnpm run build",
          "hidden": true,
          "type": "powershellCommand"
        }
      ]
    }
  ]
}
```

##### Item Types

**Available Types:**
- `url` - Opens default browser at specified URL
- `command` - Triggers VS Code command
- `file` - Opens file in VS Code
- `fileAtLine` - Opens file at specific line number
- `snippet` - Copies snippet body to clipboard
- `powershellCommand` - Executes command in PowerShell
- `debianCMD` - Executes command in Windows Debian WSL
- `chain` - Executes commands sequentially
- `concurrent` - Executes commands simultaneously
- `copyValue` - Copies value to clipboard

**Item Structure:**

Each item requires:
- `label` (string) - Item name
- `path` (string) - Item value/command
- `type` (string) - One of the types listed above
- `hidden` (boolean, optional) - Hide from view

**Example Configuration:**

```json
{
  "categories": [
    {
      "label": "MAIN",
      "expanded": false,
      "type": "folder",
      "global": true,
      "items": [
        {
          "label": "seed.ts",
          "path": "prisma/seed.ts",
          "type": "file"
        },
        {
          "label": "seed.ts at line 425",
          "path": "prisma/seed.ts:425",
          "type": "fileAtLine"
        },
        {
          "label": "Google",
          "path": "https://www.google.com",
          "type": "url"
        },
        {
          "label": "CRM",
          "path": "code-insiders -n f:/DevStack",
          "type": "powershellCommand"
        },
        {
          "label": "SAVE ALL",
          "path": "workbench.action.files.saveAll",
          "type": "command"
        },
        {
          "label": "Copy to clipboard",
          "path": "Value to be copied into the clipboard",
          "type": "copyValue"
        },
        {
          "label": "Snippet Name",
          "path": "ocrmnavigator.code-snippets",
          "type": "snippet"
        }
      ]
    }
  ]
}
```

##### Chain Type (Sequential Execution)

Executes items one at a time, waiting for each to complete before moving to the next.

**How It Works:**
- Determines each item's type (file, command, URL, PowerShell, etc.)
- Executes in respective environment
- Proceeds to next item only after current completes

**Supported Item Types:**
- file
- markdown files
- command
- url
- powershellCommand
- debianCMD
- copyValue
- chain (nested chains supported)
- concurrent

**Example:**

```json
{
  "label": "Kill Terminals && Start DEV Server",
  "path": "saveall, killterms, devApp",
  "type": "chain"
}
```

##### Concurrent Type (Parallel Execution)

Executes all commands simultaneously in their respective environments.

**PowerShell Output:**
- All PowerShell commands pipe through a single terminal
- Similar to Turborepo's terminal output
- Each command has a unique color for easy identification
- Example: Running 3 dev servers shows all output in one window with color-coded streams

**Terminal Features:**
- Accepts input piped to all active shells
- Close dev servers anytime with single command
- Terminal remains open after completion
- Functions as normal PowerShell window

**Advanced Usage:**
- Can include `chain` items within concurrent sets
- Allows mixing sequential and parallel execution

**Future Plans:** Windows Debian WSL shell will pipe through same instance (currently opens separate shells)

**Example:**

```json
{
  "label": "dev:all",
  "path": "devApp, devCalc",
  "type": "concurrent"
}
```

**With Hidden Items:**

```json
{
  "label": "HIDDEN",
  "expanded": false,
  "type": "folder",
  "global": true,
  "hidden": true,
  "items": [
    {
      "label": "saveall",
      "path": "workbench.action.files.saveAll",
      "type": "command",
      "hidden": true
    }
  ]
}
```

##### Debian CMD Type

Opens Debian (WSL) terminal within VS Code, providing full shell capabilities.

**Example Use Case:**

```json
{
  "label": "VLC w/ playlist",
  "path": "cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' playlist.xspf",
  "type": "debianCMD"
}
```

**How It Works:**
1. Opens Debian WSL terminal
2. Changes to specified directory
3. Executes command (e.g., opens VLC with playlist from Windows file system)
4. Terminal remains open for additional commands
5. Closing terminal doesn't affect running programs

**Benefits:**
- Access to programs requiring specific shell flags
- Full Linux command access from Windows
- Persistent terminal session
- Same behavior as manual command execution

##### Snippet Type

Manages globally available code snippets.

**Snippet File:**
- Extension uses `ocrmnavigator.code-snippets`
- Global file copied to workspace `.vscode` folder on startup
- Maintains VS Code's inline snippet insertion 

**⚠️ Important:** Don't edit the workspace copy - it's overwritten on startup. Edit the global file instead.

**Example:**

```json
{
  "label": "Snippet Name",
  "path": "ocrmnavigator.code-snippets",
  "type": "snippet"
}
```




<!-- #endregion -->
