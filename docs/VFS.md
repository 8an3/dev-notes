#### Item Types

#### Files & Navigation

##### `file`
Quick access to frequently-used files with customizable labels and icons.
- Copy file paths from context menu
- Reveal files in explorer
- Set items as hidden
- Custom icon support via [VS Code icon library](https://code.visualstudio.com/api/references/icons-in-labels)

```json
{ "label": "prisma.schema", "path": "prisma/prisma.schema", "type": "file" }
```

##### `fileAtLine`
Open files at specific line numbers for immediate context.

```json
{ "label": "seed.ts", "path": "prisma/seed.ts:425", "type": "fileAtLine" }
```

**Path Format**: `relative/file/path:lineNumber`

##### `folder`
Organize items into collapsible groups.
- Set as global or workspace-specific
- Configure expanded/collapsed state on startup
- Hide folders when needed
- Add unlimited folders for either global or workspace
- UPDATE: can now create unlimited nested folders, where folders 2 deep would display

```json
{
  "label": "MAIN",
  "expanded": false,
  "type": "folder",
  "global": true,
  "hidden": false,
  "items": []
}
```

##### `url`
Access websites directly from the extensions pane.

```json
{ "label": "Google", "path": "https://www.google.com", "type": "url" }
```

#### Commands & Automation

##### `command`
Execute any VS Code command with a single click. Access 550+ built-in VS Code commands plus 450+ DevStack functions.

```json
{ "label": "SAVE ALL", "path": "workbench.action.files.saveAll", "type": "command" }
```

**Creating Commands:**
- **Custom Input**: Enter any command manually
- **VS Code Commands List**: Browse 550+ built-in commands with descriptions and categories
- **DevStack Commands List**: Access 450+ extension functions (400+ currently have AI-generated descriptions as work in progress)
- Auto-updating command picker that refreshes with each extension build

**Advanced Usage**: 
- Chain commands
- Sequential execution
- Access cheat sheet with 1050+ commands
- Set arguments for commands

```json
{ 
  "label": "Open Settings", 
  "type": "command", 
  "path": "workbench.action.openSettings", 
  "args": ["editor.fontSize"] 
}
```

##### `chain` - Sequential Execution
Execute commands one after another in your specified order. When creating items through the interface, the concurrent/sequential creation process enters a for loop allowing you to add as many custom or listed commands as needed.

```json
{ 
  "label": "Kill Terminals && Start DEV Server", 
  "path": "saveall, killterms, devApp", 
  "type": "chain" 
}
```

**Advanced Usage**: Mixed sequential/concurrent flows, conditional execution

**Preview**: [Video](https://youtu.be/ySp83VqxQ8s) | [Image](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/vfs/SequentialExecution+.gif?raw=true)

##### `concurrent` - Parallel Execution
Run multiple commands simultaneously for maximum speed. Can run alongside sequential commands.

```json
{ 
  "label": "dev:all", 
  "path": "devApp, devCalc", 
  "type": "concurrent" 
}
```

**Concurrent Execution Features:**
- Two execution patterns:
  - **Sequential Execution**: Functions called with `await` for ordered execution
  - **Concurrent Execution**: `await` keyword omitted for parallel execution
- Commands pipe into a single terminal instance with:
  - Distinct color-coded output for each command
  - Interactive terminal for user input (e.g., canceling processes)
  - Terminal remains open as regular PowerShell after cancellation
- All other commands execute in separate environments with persistent terminal instances
- Failed command outputs remain available for review and debugging

**Advanced Usage**: Priority-based execution, resource management

**Enable**: Navigate to extension settings and toggle "Bleeding Edge" to `true`, or set `"ocrmnavigator.CONCURRENT": "bleeding-edge"` in settings

##### `cmdChain`
Chain multiple VS Code or DevStack commands without building several config objects. Takes the value and executes each sequentially.

```json
{ "label": "Quick Setup", "path": "cmd1, cmd2, cmd3", "type": "cmdChain" }
```

#### Terminal Commands

##### `powershellCommand`
Execute commands in Windows PowerShell as if typed directly.

```json
{ "label": "CRM", "path": "code-insiders -n f:/DevStack", "type": "powershellCommand" }
```

**Advanced Usage**: WSL integration, environment variables, complex workflows

##### `debianCMD`
Run commands in Windows Debian WSL terminal environment. Execute programs with pre-programmed flags.

```json
{ 
  "label": "VLC w/ playlist", 
  "path": "cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' playlist.xspf", 
  "type": "debianCMD" 
}
```

**Advanced Usage**: WSL integration, environment variables, complex workflows

**Note**: The ability to set arguments for powershell and bash commands is in development.


#### Utilities

##### `snippet`
Save snippets that copy to clipboard when clicked. Adds to the already included functionality of inline snippet insertion.

```json
{ "label": "Snippet Name", "path": "ocrmnavigator.code-snippets", "type": "snippet" }
```

##### `copyValue`
Place any predefined value into your clipboard.

```json
{ 
  "label": "Copy to clipboard", 
  "path": "Value to be copied into the clipboard", 
  "type": "copyValue" 
}
```

##### `settingsToggle`
Toggle VS Code settings between values. Defaults to toggle between true/false. If provided the args value, toggles through the array one by one.

```json
{ 
  "label": "ARCHIVER", 
  "path": "ocrmnavigator.ARCHIVER", 
  "type": "settingsToggle", 
  "args": ["custom", "vsce"],
  "icon": "settings" 
}
```

```json
{ 
  "label": "NPM Scripts", 
  "path": "ocrmnavigator.vfs.npmScripts", 
  "type": "settingsToggle", 
  "icon": "settings" 
}
```

##### `search`
Open search editors with predefined parameters. Opens in a new tab with context lines, case sensitive by default. Allows multiple search editors at once.

```json
{ 
  "label": "console.log(", 
  "path": "regex pattern to find console.log(", 
  "type": "search", 
  "icon": "search" 
}
```

##### `apiCall`
Execute HTTP API requests directly from the file tree.

**GET Request:**
```json
{
  "label": "Check API Status",
  "path": "https://api.example.com/status",
  "type": "apiCall",
  "icon": "cloud",
  "tooltipText": ""
}
```

**POST Request with Body:**
```json
{
  "label": "Deploy to Production",
  "path": "https://hooks.example.com/deploy",
  "type": "apiCall",
  "args": [
    { "method": "POST" },
    { "body": { "branch": "main", "environment": "production" } }
  ],
  "icon": "rocket"
}
```

 ##### `layout`

[Layout Configuration Guide](./LAYOUT.md)

##### `label`

#### Auto-Generated Items

##### `tasks`
Automatically generated from `tasks.json` when workspace initializes.

##### `npmScripts`
Automatically generated from `package.json` when workspace initializes.

##### `settingsToggle`

- scans workspace settings.json and auto generates items within `SETTINGS` folder placing them in `workspace` so as to not overwrite any items you currently have within the settings folder. The auto generated items will only work for settings that use the values `false` | `true`

##### `snippet`

- snippets are now auto generated items within the vfs explorer pane
- You may also edit the items within this folder, as these auto generated items will not actually take up any space within the config file itself, if any labels match any label from the auto generated list, those items will not be included
- allowing you to create you organization system for your snippet files
- snippet files adopted the global / workspace system, making them workspace context intelligent, enabling you to organize your snippets at a workspace level so you could have a different config for each project 

> [!TIP] Philosophy: Empowering Developers
> This extension takes an unconventional approach by exposing every internal function directly to you. While this is rare in VS Code extensions, the reasoning is simple: these functions were already built for personal use, and automating their availability helps colleagues and the broader community with minimal additional effort.
>
> Development work involves countless time-consuming repetitive tasks. Unlike some industries where these inefficiencies are unavoidable, software development offers a unique advantage—we can program solutions to our own problems. This extension aims to eliminate those time sinks and help you focus on what matters: building great software.
>
> Getting Started with Chains
> The `chain` type is the most powerful feature in DevStack. It allows you to combine multiple commands into a single workflow, dramatically reducing the steps required for common development tasks.
>
> Example 1: Git Workflow with Version Bump
> This chain automates the complete process of committing, pushing, and incrementing your package version:
> ```text
> type: chain
> path: gitAdd, gitCom, gitPush, bumpVers, gitPush, gitPushTags
> ```
> **Required Component Commands:**
> ```text
> type: powershellCommand
> hidden: true
> path: git add *
> 
> type: powershellCommand
> hidden: true
> path: git commit -m "pushing local data"
> 
> type: powershellCommand
> hidden: true
> path: git push
> 
> type: powershellCommand
> hidden: true
> path: pnpm version patch
> 
> type: powershellCommand
> hidden: true
> path: git push
> 
> type: powershellCommand
> hidden: true
> path: git push --tags
> ```
> Previously, this was run as a single inline command, which had edge cases that caused failures. Breaking it into modular components solved those reliability issues completely.
>
> Example 2: Using Extension Commands
> You can achieve the same result using the extension's built-in commands:
> ```text
> type: cmdChain
> path: ocrmnavigator.gitAdd, ocrmnavigator.gitCom, ocrmnavigator.gitPush, 
>       ocrmnavigator.bumpPatchVersion, ocrmnavigator.gitPush, 
>       ocrmnavigator.gitPushTags
> ```
> 
> The extension automatically detects your package manager (npm, pnpm, yarn) and adjusts commands accordingly.
> 
> ##### Example 3: VS Code Extension Development Workflow
> 
> This comprehensive chain handles the entire build-and-reload process for VS Code extension development:
> 
> ```text
> type: cmdChain
> path: ocrmnavigator.saveAll, ocrmnavigator.killAll, 
>       ocrmnavigator.formatPackageJson, ocrmnavigator.convertReadmeDevMd, 
>       ocrmnavigator.compileWithPackager, ocrmnavigator.installNow, 
>       ocrmnavigator.reloadWindow
> ```
> 
> **breakdoown:**
> 1. Saves all open editors
> 2. Terminates all terminal instances
> 3. Formats package.json files (supports dual package.json setup for automation)
> 4. Converts readme files for pre-processing
> 5. Compiles the extension using either:
>    - **vsce**: Creates local package and publishes to marketplace
>    - **Custom archiver**: Faster compilation with fewer restrictions (supports SVGs in readme, which vsce blocks)
> 6. Installs the extension locally
> 7. Reloads the current VS Code window
> 
> #### Real-World Impact
> 
> The automation possibilities are extensive. For example, my icon library workflow is fully automated—I simply drop an SVG file into a folder, click one button in the DevStack explorer, and walk away. The entire process runs automatically:
> 
> - Icon creation and optimization
> - README updates
> - Project compilation and building
> - Git commit and push to GitHub
> - Version bump
> - NPM publication
> 
> Since my projects are interconnected, I've even created a single button that executes this workflow across all three projects simultaneously.
> 
> Going forward, the extension will embrace a more modular architecture. Previously, functionality was built either entirely in config files or as monolithic standalone functions. The modular approach demonstrated above provides better reliability, maintainability, and reusability.



[🡄 Return](https://github.com/8an3/DevStack)




---

[🡄 Return](https://github.com/8an3/DevStack)










