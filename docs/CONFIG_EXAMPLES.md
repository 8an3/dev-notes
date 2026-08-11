# Config Item Examples

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Table of Contents





- [Config Item Examples](#config-item-examples)
  - [Example 1: Local Build & Install VSCode Extension](#example-1-local-build--install-vscode-extension)
  - [Example 2: Open Project in New Window](#example-2-open-project-in-new-window)
  - [Example 3: Open URL in Browser](#example-3-open-url-in-browser)
  - [Example 4: VLC with Playlist](#example-4-vlc-with-playlist)
  - [Example 5: Clean Project](#example-5-clean-project)
  - [Example 6: Complete Automation Workflow](#example-6-complete-automation-workflow)
  - [Scripts And Others](#scripts-and-others)
  - [Return to Main](#return-to-main)



**Example 1: Local Build & Install VSCode Extension**

Complete workflow for building, packaging, and installing your extension locally.

| Setting | Value |
|---------|-------|
| **Description** | Saves all editors, formats package.json (removes comments), compiles extension, packages .vsix archive, waits 2 seconds, installs .vsix, and reloads window |
| **Type** | `chain` |
| **Commands** | `saveall, buildpkg, npmRunCompile, customVsixPackager, await2Secs, installNow, RWINDOW` |

**Component Commands:**
- `RWINDOW` - type: `command`, path: `ocrmnavigator.RWINDOW`, hidden: `true`
- `saveall` - type: `command`, path: `workbench.action.files.saveAll`, hidden: `true`
- `buildpkg` - type: `powershellCommand`, path: `npm run clean-package`, hidden: `true`
- `customVsixPackager` - type: `command`, path: `ocrmnavigator.vsix.archive`, hidden: `true`
- `installNow` - type: `command`, path: `ocrmnavigator.installNow`, hidden: `true`
- `await2Secs` - type: `command`, path: `ocrmnavigator.await.2`, hidden: `true`
- `npmRunCompile` - type: `powershellCommand`, path: `npm run compile`, hidden: `true`

---

**Example 2: Open Project in New Window**

| Setting | Value |
|---------|-------|
| **Description** | Opens new VSCode instance at specified path |
| **Type** | `powershellCommand` |
| **Command** | `code-insiders -n f:/OpinionatedCRM` |
| **Label** | Catalyst Software |

---

**Example 3: Open URL in Browser**

| Setting | Value |
|---------|-------|
| **Description** | Opens browser window to specified URL |
| **Type** | `url` |
| **Path** | `https://marketplace.visualstudio.com/manage/publishers/skyler?auth_redirect=True` |
| **Label** | Manage VS Extensions |

---

**Example 4: VLC with Playlist**

| Setting | Value |
|---------|-------|
| **Description** | Opens VLC media player with specified playlist using Debian WSL bash command (works where PowerShell cannot) |
| **Type** | `debianCMD` |
| **Command** | `cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' 1Firreee.xspf` |
| **Label** | VLC w/ playlist |

**Why this approach:** Standard PowerShell couldn't open VLC with playlists. This extension executes bash commands in a real Debian WSL environment, enabling any bash command with any flags.

---

**Example 5: Clean Project**

| Setting | Value |
|---------|-------|
| **Description** | Removes common build artifacts and cache directories from workspace root |
| **Type** | `powershellCommand` |
| **Command** | `foreach ($path in @('.pnpm-cache', 'node_modules', 'pnpm-lock.yaml', '.cache', 'public\build', 'build')) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }` |
| **Label** | clean |
| **Removes** | `.pnpm-cache`, `node_modules`, `pnpm-lock.yaml`, `.cache`, `public/build`, `build` |

---

**Example 6: Complete Automation Workflow**

The ultimate automation example - handles icon library updates, UI component generation, package.json updates (35,000+ lines), quickpick menu generation, markdown conversion, and local build/install.

| Setting | Value |
|---------|-------|
| **Description** | Complete automation for development testing: updates 600+ icons, generates 2800+ component functions, updates package.json commands and submenus, updates quickpick menus, converts markdown pre-prompts to JSON, and triggers local build/install |
| **Type** | `chain` |
| **Commands** | `saveall, CreateandRename, runGen2, ImportallcompsDevStack, genIcons, genIcons, genUi, iconInv, updatePrompts, localBuildAndInstall` |
| **Label** | TRIGGER ALL FOR LOCAL TESTING |

**Component Commands:**
- `CreateandRename` - type: `powershellCommand`, path: `powershell.exe -File ./updaters/CopyAndRenameFiles.ps1`, hidden: `true`
- `runGen2` - type: `powershellCommand`, path: `bun ./updaters/gen2.ts`, hidden: `true`
- `ImportallcompsDevStack` - type: `powershellCommand`, path: `node ./updaters/build-catalyst-functions.js`, hidden: `true`
- `genIcons` - type: `powershellCommand`, path: `node ./updaters/generate-icon-inventory.js`, hidden: `true`
- `genUi` - type: `powershellCommand`, path: `node ./updaters/generate-ui-inventory.js`, hidden: `true`
- `iconInv` - type: `powershellCommand`, path: `node ./updaters/icon-library-inventory.js`, hidden: `true`
- `updatePrompts` - type: `powershellCommand`, path: `node ./updaters/update-prompt-from-md.js`, hidden: `true`
- `localBuildAndInstall` - type: `chain`, path: (references first example chain), hidden: `true`

**What This Demonstrates:**
- Full project automation from single button
- Icon library scanning and updating (600+ icons)
- Component library scanning (2800+ components)
- Automated package.json generation (35,000+ lines)
- Context menu and quickpick menu generation
- Markdown to JSON conversion for configs
- Complete build and install pipeline

**Real-World Impact:** One-click updates everything needed for development and testing, regardless of complexity.


### Scripts And Others

Additional scripts, utilities, and documentation resources.

**Description:** Formerly hosted documentation site now serves as repository for scripts and large content items that would significantly increase README length.

**Coming Soon:**
- Site URL
- Available scripts and utilities
- Additional documentation
- Integration examples
- Advanced configuration samples



## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Complete Example

<details>
<summary>Config</summary>

```json
{
  "categories": [
 {
      "label": "EXAMPLES",
      "expanded": false,
      "type": "folder",
      "global": true,
      "items": [
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "Build and Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "onSuccess", "executeChain": "deploy, notify" },
            { "type": "onFailure", "executeChain": "rollback, alert" }
          ]
        },
        {
          "label": "Conditional Build",
          "path": "lint, test, build",
          "type": "conditionalChain",
          "args": [
            { "type": "itemSuccess", "itemLabel": "test", "executeChain": "deploy" }
          ]
        },
        {
          "label": "Environment-Based Deploy",
          "path": "build",
          "type": "conditionalChain",
          "args": [
            { "type": "configValue", "configKey": "ocrmnavigator.environment", "operator": "equals", "value": "production", "executeChain": "deployProd" },
            { "type": "configValue", "configKey": "ocrmnavigator.environment", "operator": "equals", "value": "staging", "executeChain": "deployStaging" }
          ]
        },
        {
          "label": "Conditional Install",
          "path": "checkDeps",
          "type": "conditionalChain",
          "args": [
            { "type": "fileNotExists", "filePath": "node_modules", "executeChain": "npmInstall" }
          ]
        },
        {
          "label": "Build with Cleanup",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "always", "executeChain": "cleanup, logResults" }
          ]
        },
        {
          "label": "Advanced Conditional",
          "path": "task1, task2, task3",
          "type": "conditionalChain",
          "args": [
            { "type": "custom", "expression": "results.filter(r => r.success).length >= 2", "executeChain": "partialSuccessHandler" }
          ]
        },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "Build with CI",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        { "label": "ciDeploy", "path": "dockerBuild, pushToRegistry, deployToK8s", "type": "chain" },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" },
            { "type": "itemSuccess", "itemLabel": "ciDeploy", "executeChain": "deployStaging" }
          ]
        },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "ciDeploy",
          "path": "dockerBuild, pushToRegistry",
          "type": "conditionalChain",
          "args": [
            { "type": "onSuccess", "executeChain": "deployStaging" }
          ]
        },
        {
          "type": "combined",
          "logic": "AND",
          "conditions": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true" },
            { "type": "onSuccess" }
          ],
          "executeChain": "ciDeploy"
        },
        { "label": "README.dev.md", "path": "README.dev.md", "type": "file", "icon": "markdown" },
        { "label": "Manage VS Extensions", "path": "https://marketplace.visualstudio.com/manage/publishers/skyler?auth_redirect=True", "type": "url" },
        { "label": "Scan File Imports", "path": "ocrmnavigator.imports.file.scan", "type": "command", "icon": "terminal-cmd" },
        { "label": "CRM", "path": "code-insiders -n f:/OpinionatedCRM", "type": "powershellCommand", "icon": "project" },
        { "label": "VLC w/ playlist", "path": "cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' 1Firreee.xspf", "type": "debianCMD" },
        { "label": "Format", "path": "formatfile, saveall", "type": "chain" },
        { "label": "Format", "path": "formatfile, saveall", "type": "concurrent" },
        { "label": "★ ━━━━ ☆ ━━━━ AUTORUN SCRIPTS ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆", "type": "label", "icon": "chrome-minimize" },
        { "label": "Prompt - Reusable Comps", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Tasks", "path": "ocrmnavigator.vfs.tasks", "type": "settingsToggle", "icon": "settings" },
        {
          "label": "ARCHIVER",
          "path": "ocrmnavigator.ARCHIVER",
          "type": "settingsToggle",
          "args": [
            "custom",
            "vsce"
          ],
          "icon": "settings"
        },
        {
          "label": "Create User",
          "path": "https://api.example.com/users",
          "args": [
            { "method": "POST" },
            { "headers": { "Content-Type": "application/json", "Authorization": "Bearer YOUR_TOKEN" } },
            { "body": { "name": "John Doe", "email": "john@example.com" } }
          ],
          "type": "apiCall",
          "icon": "person-add",
          "tooltipText": ""
        },
        {
          "label": "Deploy to Production",
          "path": "https://hooks.example.com/deploy",
          "args": [
            { "method": "POST" },
            { "body": { "branch": "main", "environment": "production" } }
          ],
          "type": "apiCall",
          "icon": "rocket"
        },
        {
          "label": "List Repos",
          "path": "https://api.github.com/users/yourname/repos",
          "args": [
            { "headers": { "Accept": "application/vnd.github.v3+json", "Authorization": "token YOUR_GITHUB_TOKEN" } }
          ],
          "type": "apiCall",
          "icon": "github",
          "tooltipText": ""
        },
        {
          "label": "Restart Dev Server",
          "path": "http://localhost:3000/api/restart",
          "args": [
            { "method": "POST" }
          ],
          "type": "apiCall",
          "icon": "debug-restart",
          "tooltipText": ""
        }
      ]
    }
  ]
}
```

</details>

<details>
<summary>Personal config if your interested</summary>

```json
{
  "categories": [
    {
      "label": "MAIN",
      "expanded": false,
      "type": "folder",
      "global": true,
      "items": [
        { "label": "CRM", "path": "code-insiders -n f:/OpinionatedCRM", "type": "powershellCommand", "icon": "project" },
        { "label": "Catalyst Software", "path": "code-insiders -n f:/playground", "type": "powershellCommand", "icon": "symbol-event" },
        { "label": "CatalystPOS", "path": "code-insiders -n f:/CatalystPOS", "type": "powershellCommand", "icon": "jersey" },
        {
          "label": "Dev Projects",
          "type": "folder",
          "expanded": true,
          "global": true,
          "items": [
            { "label": "DevStack", "path": "code-insiders -n f:/DevStack", "type": "powershellCommand", "icon": "symbol-event" },
            { "label": "icons", "path": "code-insiders -n f:/icons", "type": "powershellCommand", "icon": "symbol-event" },
            { "label": "Catalyst Editor", "path": "code-insiders -n f:/code-editor", "type": "powershellCommand", "icon": "project" },
            { "label": "dev notes", "path": "code-insiders -n f:/midgardr-notes", "type": "powershellCommand", "icon": "project" },
            {
              "label": "TO DO, NOTES, AND THINGS",
              "expanded": false,
              "type": "folder",
              "global": true,
              "items": [
                { "label": "Notes, To-Do And Things", "path": "code-insiders -n f:/ntrsync", "type": "powershellCommand", "icon": "notebook" },
                { "label": "Notes, To-Do And Things", "path": "code-insiders -n f:/mobilenrcsync", "type": "powershellCommand", "icon": "device-mobile" },
                { "label": "Notes, To-Do And Things - Website", "path": "https://www.ntrsync.dedyn.io/login", "type": "url", "icon": "device-mobile" }
              ]
            },
            {
              "label": "STACKS & MONOREPO",
              "expanded": false,
              "type": "folder",
              "global": true,
              "items": [
                { "label": "bane stack", "type": "powershellCommand", "path": "code-insiders -n f:/bane", "icon": "project" },
                { "label": "create remixv2", "type": "powershellCommand", "path": "code-insiders -n f:/create-remixv2", "icon": "project" },
                { "label": "bane-stack-monorepo", "type": "powershellCommand", "path": "code-insiders -n f:/bane-stack-monorepo", "icon": "project" }
              ]
            }
          ]
        }
      ]
    },
    {
      "label": "CMDS",
      "expanded": true,
      "type": "folder",
      "global": true,
      "icon": "terminal",
      "items": [
        { "label": "Scan File Imports", "path": "ocrmnavigator.imports.file.scan", "type": "command", "icon": "terminal-cmd" },
        { "label": "Toggle Zen Mode", "path": "workbench.action.toggleZenMode", "type": "command", "icon": "game" },
        { "label": "SAVE ALL", "path": "workbench.action.files.saveAll", "type": "command", "icon": "save-all" },
        { "label": "Search Editor", "path": "ocrmnavigator.odin.open", "type": "command", "icon": "search" },
        { "label": "Search VSCode", "path": "", "type": "search", "icon": "search" },
        { "label": "Format", "path": "formatfile, saveall", "type": "chain" },
        { "label": "1 DEV", "path": "saveall, killterms, startDevServer", "type": "chain", "icon": "debug-start", "tooltipText": "SINGLE KILL Terminals && Start DEV Server" },
        { "label": "2 DEV", "path": "saveall, killterms, devApp", "type": "chain", "icon": "debug-start", "tooltipText": "MONO KILL Terminals && Start DEV Server" },
        {
          "label": "MORE",
          "type": "folder",
          "expanded": false,
          "icon": "ellipsis",
          "items": [
            { "label": "1", "path": "editor.foldLevel1", "type": "command", "icon": "fold-down" },
            { "label": "2", "path": "editor.foldLevel2", "type": "command", "icon": "fold-down" },
            { "label": "3", "path": "editor.foldLevel3", "type": "command", "icon": "fold-down" },
            {
              "label": "JSON",
              "type": "folder",
              "expanded": false,
              "icon": "json",
              "items": [
                { "label": "Format .json", "path": "ocrmnavigator.format.json.file", "type": "command", "icon": "json" },
                { "label": "TGL Json Errors", "path": "ocrmnavigator.performanceSwitch.json.validate.toggle", "type": "command", "icon": "json" },
                { "label": "TGL Jsonc Errors", "path": "ocrmnavigator.performanceSwitch.jsonc.validate.toggle", "type": "command", "icon": "json" }
              ]
            },
            {
              "label": "FOLD",
              "type": "folder",
              "expanded": true,
              "icon": "fold-down",
              "items": [
                { "label": "UNFOLD All", "path": "editor.unfoldAll", "type": "command", "icon": "unfold" },
                { "label": "4", "path": "editor.foldLevel4", "type": "command", "icon": "fold-down" },
                { "label": "5", "path": "editor.foldLevel5", "type": "command", "icon": "fold-down" },
                { "label": "6", "path": "editor.foldLevel6", "type": "command", "icon": "fold-down" },
                { "label": "7", "path": "editor.foldLevel7", "type": "command", "icon": "fold-down" }
              ]
            },
            {
              "label": "TOGGLE",
              "type": "folder",
              "expanded": true,
              "icon": "fold-down",
              "items": [
                { "label": "TGL #R 1", "path": "ocrmnavigator.vscode.region.1.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 2", "path": "ocrmnavigator.vscode.region.2.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 3", "path": "ocrmnavigator.vscode.region.3.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 4", "path": "ocrmnavigator.vscode.region.4.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 5", "path": "ocrmnavigator.vscode.region.5.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 6", "path": "ocrmnavigator.vscode.region.6.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 7", "path": "ocrmnavigator.vscode.region.7.toggle", "type": "command", "icon": "fold-down" }
              ]
            },
            {
              "label": " VSCODE CMDS",
              "type": "folder",
              "expanded": false,
              "icon": "json",
              "items": [
                { "label": "Window", "path": "formatfile, saveall, reloadWindow", "type": "chain", "icon": "debug-restart", "tooltipText": "Reload Window" },
                { "label": "Terminals", "path": "workbench.action.terminal.killAll", "type": "command", "icon": "debug-stop" },
                { "label": "editors", "path": "saveall, closeeditors", "type": "chain", "icon": "close" },
                { "label": "toggle 💻", "path": "workbench.action.terminal.toggleTerminal", "type": "command", "icon": "unfold" },
                { "label": "TS", "path": "formatfile, saveall, reloadWindow", "type": "chain", "icon": "refresh", "tooltipText": "Reload Window" },
                { "label": "DevTools", "path": "formatfile, saveall, reloadWindow", "type": "chain", "icon": "tools", "tooltipText": "Open DevTools" },
                { "label": "Kill PORT 3000", "path": "killPort3000", "type": "command", "icon": "x" }
              ]
            }
          ]
        },
        {
          "label": "MONOREPO",
          "type": "folder",
          "expanded": false,
          "items": [
            { "label": "dev:all", "path": "devApp, devCalc", "type": "concurrent" },
            { "label": "nuclear:all", "path": "nuclear:all", "type": "powershellCommand" },
            { "label": "dev:app", "path": "saveall, killterms, devApp", "type": "chain" },
            { "label": "patch:app", "path": "cd apps/app && git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags && cd ../..", "type": "powershellCommand" },
            { "label": "db:app", "path": "cd apps/app && pnpm run db:all && cd ../..", "type": "powershellCommand" },
            { "label": "clean:app", "path": "cd apps/app && foreach ($path in @('.cache', 'build', 'node_modules', 'pnpm-lock.yaml', 'public\\build' )) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } } && cd ../..", "type": "powershellCommand" },
            { "label": "clean:all", "path": "cleanApp, cleanProd, cleanCalc, cleanRoot", "type": "concurrent" },
            { "label": "i:all", "path": "iapp, iProd, iRoot, iCalc", "type": "concurrent" },
            { "label": "build:all", "path": "buildapp, buildProd, buildCalc", "type": "concurrent" },
            { "label": "patch:all", "path": "patchRoot, patchapp, patchProd, patchCalc", "type": "concurrent" },
            { "label": "push:all", "path": "pushCalc, pushProd, pushApp, pushRoot", "type": "concurrent" },
            { "label": "db:all local", "path": "saveall, dbAllLocal, dbCalc, dbApp", "type": "chain" },
            { "label": "db:all remote", "path": "saveall, dbAllRemote, dbCalc, dbApp", "type": "chain" },
            { "label": "db:prod", "path": "cd apps/prod && pnpm run db:all && cd ../..", "type": "powershellCommand" },
            { "label": "gen:all", "path": "genCalc, genApp", "type": "concurrent" },
            { "label": "gen:prod", "path": "cd apps/prod && pnpm run db:gen && cd ../..", "type": "powershellCommand" }
          ]
        },
        {
          "label": "SINGLE REPO",
          "type": "folder",
          "expanded": false,
          "items": [
            { "label": "dev", "path": "saveall, killterms, singlestrdev", "type": "chain" },
            { "label": "patch", "path": "saveall, singlestrpatch", "type": "chain" },
            { "label": "db:all local", "path": "saveall, killterms, dbAllLocal", "type": "chain" },
            { "label": "db:all remote", "path": "saveall, killterms, dbAllRemote", "type": "chain" },
            { "label": "i", "path": "saveall, killterms, terminalInstall", "type": "chain" },
            { "label": "fromScratch", "path": "saveall, killterms, singlestrfromScratch", "type": "chain" },
            { "label": "build", "path": "saveall, killterms, runBuild", "type": "chain" },
            { "label": "start", "path": "saveall, killterms, runStart", "type": "chain" },
            { "label": "clean", "path": "saveall, killterms, singlestrclean", "type": "chain" },
            { "label": "i:shadCN", "path": "saveall, killterms, singlestrshadCN", "type": "chain" },
            { "label": "i:component", "path": "saveall, killterms, singlestrcomponent", "type": "chain" },
            { "label": "db:gen", "path": "saveall, killterms, prismaGenerate", "type": "chain" },
            { "label": "db:seed", "path": "saveall, killterms, singlestrdbseed", "type": "chain" },
            { "label": "db:studio", "path": "singlestrdbstudio", "type": "chain" }
          ]
        },
        {
          "label": "DIVIDERS",
          "expanded": false,
          "type": "folder",
          "global": true,
          "items": [
            [
              { "label": "━━━━ ● ━━━━ ● ━━━━", "type": "label", "icon": "circle-dot" },
              { "label": "★ ━━━━ ☆ ━━━━ ━━━━ ☆ ━━━━", "type": "label", "icon": "star" },
              { "label": "━━━━ ◆ ━━━━ ◆ ━━━━ ◆ ━━━━ ◆ ━━━━", "type": "label", "icon": "diamond" },
              { "label": "━━━━ ☆ ━━━━━━━━━━━━━", "type": "label", "icon": "minus" },
              { "label": "═══════════════════", "type": "label", "icon": "grip-horizontal" },
              { "label": "▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬", "type": "label", "icon": "maximize-2" },
              { "label": "▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓", "type": "label", "icon": "grid-3x3" },
              { "label": "░░░░░░░░░░░░░░░░░░░░", "type": "label", "icon": "grid" },
              { "label": "┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄", "type": "label", "icon": "more-horizontal" },
              { "label": "┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈", "type": "label", "icon": "more-horizontal" },
              { "label": "┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉", "type": "label", "icon": "menu" },
              { "label": "━ ━ ━ ━ ━ ━ ━ ━ ━ ━", "type": "label", "icon": "minus" },
              { "label": "─ ─ ─ ─ ─ ─ ─ ─ ─ ─", "type": "label", "icon": "minus" },
              { "label": "● ● ● ● ● ● ● ● ● ●", "type": "label", "icon": "circle" },
              { "label": "○ ○ ○ ○ ○ ○ ○ ○ ○ ○", "type": "label", "icon": "circle" },
              { "label": "• • • • • • • • • •", "type": "label", "icon": "more-horizontal" },
              { "label": "★ ★ ★ ★ ★ ★ ★ ★ ★ ★", "type": "label", "icon": "star" },
              { "label": "☆ ☆ ☆ ☆ ☆ ☆ ☆ ☆ ☆ ☆", "type": "label", "icon": "star" },
              { "label": "◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆", "type": "label", "icon": "diamond" },
              { "label": "◇ ◇ ◇ ◇ ◇ ◇ ◇ ◇ ◇ ◇", "type": "label", "icon": "diamond" },
              { "label": "■ ■ ■ ■ ■ ■ ■ ■ ■ ■", "type": "label", "icon": "square" },
              { "label": "□ □ □ □ □ □ □ □ □ □", "type": "label", "icon": "square" },
              { "label": "▪ ▪ ▪ ▪ ▪ ▪ ▪ ▪ ▪ ▪", "type": "label", "icon": "square" },
              { "label": "▫ ▫ ▫ ▫ ▫ ▫ ▫ ▫ ▫ ▫", "type": "label", "icon": "square" },
              { "label": "→ → → → → → → → → →", "type": "label", "icon": "arrow-right" },
              { "label": "⇒ ⇒ ⇒ ⇒ ⇒ ⇒ ⇒ ⇒ ⇒ ⇒", "type": "label", "icon": "chevrons-right" },
              { "label": "➜ ➜ ➜ ➜ ➜ ➜ ➜ ➜ ➜ ➜", "type": "label", "icon": "arrow-right" },
              { "label": "← ← ← ← ← ← ← ← ← ←", "type": "label", "icon": "arrow-left" },
              { "label": "⬅ ⬅ ⬅ ⬅ ⬅ ⬅ ⬅ ⬅ ⬅ ⬅", "type": "label", "icon": "arrow-left" },
              { "label": "╭──────────────────╮", "type": "label", "icon": "corner-up-right" },
              { "label": "╰──────────────────╯", "type": "label", "icon": "corner-down-right" },
              { "label": "╒══════════════════╕", "type": "label", "icon": "frame" },
              { "label": "╘══════════════════╛", "type": "label", "icon": "frame" },
              { "label": "╓──────────────────╖", "type": "label", "icon": "frame" },
              { "label": "╙──────────────────╜", "type": "label", "icon": "frame" },
              { "label": "▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀", "type": "label", "icon": "align-justify" },
              { "label": "▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄", "type": "label", "icon": "align-justify" },
              { "label": "▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌", "type": "label", "icon": "align-left" },
              { "label": "▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐", "type": "label", "icon": "align-right" },
              { "label": "… … … … … … … …", "type": "label", "icon": "more-horizontal" },
              { "label": "· · · · · · · · · ·", "type": "label", "icon": "more-horizontal" },
              { "label": "━━━ ➔ ━━━", "type": "label", "icon": "arrow-right-circle" },
              { "label": "═══ ⇒ ═══", "type": "label", "icon": "fast-forward" },
              { "label": "● ━━━━ ☆ ━━━━━━━━━ ●", "type": "label", "icon": "circle-dot" },
              { "label": "★ ━━━━ ☆ ━━━━━━━━━ ★", "type": "label", "icon": "sparkles" },
              { "label": "┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊", "type": "label", "icon": "separator-vertical" },
              { "label": "┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋", "type": "label", "icon": "separator-vertical" },
              { "label": "‖ ‖ ‖ ‖ ‖ ‖ ‖ ‖ ‖ ‖", "type": "label", "icon": "pause" },
              { "label": " → ← ↑ ↓ ⇒ ⇐ ← → ➔ ➜ ➞ ➡ ⇒ ⟹ ⬅ ⇐ ⟸ ⬆ ⇑ ⬇ ⇓ ↓↑", "type": "label", "icon": "three-bars" },
              { "label": "╒ ╓ ╕ ╖ ╘ ╙ ╛ ╜ ╭ ╮ ╰ ╯ ", "type": "label", "icon": "three-bars" },
              { "label": " ┄ ┅ ┆ ┇ ┈ ┉ ┊ ┋ ", "type": "label", "icon": "three-bars" },
              { "label": " □ ▪ ▫ ● ○ ◆ ◇ ★ ☆", "type": "label", "icon": "three-bars" },
              { "label": "• · … ― ‖ • · … ― ‖ ", "type": "label", "icon": "three-bars" },
              { "label": " ▀ ▄ █ ░ ▒ ▓ ▌ ▐ ■", "type": "label", "icon": "three-bars" }
            ]
          ]
        },
        {
          "label": "HIDDEN",
          "expanded": false,
          "type": "folder",
          "global": true,
          "hidden": true,
          "items": [
            { "label": "gen2tsU", "path": "bun ./updaters/gen2.ts", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "BuildCatalystFunctionsU", "path": "bun ./updaters/build-catalyst-functions.ts", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "MDPreProcessor", "path": "ocrmnavigator.md.convertReadme", "type": "command", "icon": "markdown", "hidden": true },
            { "label": "pro7", "path": "ocrmnavigator.pro7.acrhive", "type": "command", "icon": "json", "hidden": true },
            { "label": "CopyAndRenameFilesps1U", "path": "powershell ./updaters/CopyAndRenameFiles.ps1", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "generateiconinventoryjsU", "path": "node ./updaters/generate-icon-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "generateuiinventoryjsU", "path": "node ./updaters/generate-ui-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "iconlibraryinventoryjsU", "path": "node ./updaters/icon-library-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "updatepromptfrommdU", "path": "node ./updaters/update-prompt-from-md.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "Buildpkgjson", "path": "ocrmnavigator.format.json.pkg", "type": "command", "icon": "json", "hidden": true },
            { "label": "CreatekgJsonCommandsQpMenu", "path": "ocrmnavigator.menu.items.pkg.scan.convert.items", "type": "command", "icon": "three-bars", "hidden": true },
            { "label": "↓↓ DOES NOT WORK ↓↓", "path": "saveall", "type": "command", "hidden": true },
            { "label": "pro7 - AR", "path": "node ./src/autorun/pro7.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "MD Pre-Processor - AR", "path": "node ./src/autorun/markdown-pre-processor.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "Build pkg.json - AR", "path": "node ./src/autorun/build-package-json.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "pnpmrunbuild", "path": "pnpm run build", "type": "powershellCommand", "icon": "versions", "hidden": true },
            { "label": "pnpmrungenerate", "path": "pnpm run generate", "type": "powershellCommand", "icon": "versions", "hidden": true },
            { "label": "Bump Patch", "path": "saveall, PatchVersion", "type": "chain", "icon": "versions", "hidden": true },
            { "label": "PatchVersion", "path": "ocrmnavigator.version.patch", "type": "command", "icon": "versions", "hidden": true },
            { "label": "compileWIthPackager", "path": "ocrmnavigator.project.compile", "type": "command", "icon": "archive", "hidden": true },
            { "label": "await5Secs", "path": "ocrmnavigator.await.5", "type": "command", "icon": "markdown", "hidden": true },
            { "label": "await4Secs", "path": "ocrmnavigator.await.4", "type": "command", "icon": "markdown", "hidden": true },
            { "label": "await3Secs", "path": "ocrmnavigator.await.3", "type": "command", "icon": "markdown", "hidden": true },
            { "label": "await1Secs", "path": "ocrmnavigator.await.1", "type": "command", "icon": "markdown", "hidden": true },
            { "label": "await2Secs", "path": "ocrmnavigator.await.2", "type": "command", "hidden": true },
            { "label": "reloadWindow", "path": "workbench.action.reloadWindow", "type": "command", "hidden": true },
            { "label": "generateAndBuild", "path": "ocrmnavigator.project.compile", "type": "command", "hidden": true },
            { "label": "genCalc", "path": "cd apps/calc && npx prisma generate && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "genApp", "path": "cd apps/app && npx prisma generate && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "dbCalc", "path": "cd apps/calc && npx tsx prisma/pre-seed.ts && npx prisma db push --force-reset && npx prisma db push && npx tsx prisma/seed.ts && npx prisma generate && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "dbApp", "path": "cd apps/app && npx tsx prisma/pre-seed.ts && npx prisma db push --force-reset && npx prisma db push && npx tsx prisma/seed.ts && npx prisma generate && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "devApp", "path": "cd apps/app && pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "devCalc", "path": "cd apps/calc && pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "pushRoot", "path": "git add * && git commit -m \"Cleaning w/ push\" && git push", "type": "powershellCommand", "hidden": true },
            { "label": "pushApp", "path": "cd apps/app && git add * && git commit -m \"Cleaning w/ push\" && git push && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "pushProd", "path": "cd apps/prod && git add * && git commit -m \"Cleaning w/ push\" && git push && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "pushCalc", "path": "cd apps/calc && git add * && git commit -m \"Cleaning w/ push\" && git push && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "patchRoot", "path": "git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags", "type": "powershellCommand", "hidden": true },
            { "label": "patchapp", "path": "cd apps/app && git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "patchProd", "path": "cd apps/prod && git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "patchCalc", "path": "cd apps/calc && git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "buildapp", "path": "cd apps/app && pnpm run build && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "buildProd", "path": "cd apps/prod && pnpm run build && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "buildCalc", "path": "cd apps/calc && pnpm run build && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "iRoot", "path": "pnpm i --prefer-offline --no-cache", "type": "powershellCommand", "hidden": true },
            { "label": "iapp", "path": "cd apps/app && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "iProd", "path": "cd apps/prod && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "iCalc", "path": "cd apps/calc && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "cleanRoot", "path": "foreach ($path in @('.cache', 'build', 'node_modules', 'pnpm-lock.yaml', 'public\\build' )) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }", "type": "powershellCommand", "hidden": true },
            { "label": "cleanApp", "path": "cd apps/app && foreach ($path in @('.cache', 'build', 'node_modules', 'pnpm-lock.yaml', 'public\\build' )) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }", "type": "powershellCommand", "hidden": true },
            { "label": "cleanProd", "path": "cd apps/prod && foreach ($path in @('.cache', 'build', 'node_modules', 'pnpm-lock.yaml', 'public\\build' )) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }", "type": "powershellCommand", "hidden": true },
            { "label": "cleanCalc", "path": "cd apps/calc && foreach ($path in @('.cache', 'build', 'node_modules', 'pnpm-lock.yaml', 'public\\build' )) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }", "type": "powershellCommand", "hidden": true },
            { "label": "iProd", "path": "cd apps/prod && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "iCalc", "path": "cd apps/calc && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "iApp", "path": "cd apps/app && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "devProd", "path": "cd apps/prod && pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "devCalc", "path": "cd apps/calc && pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "devApp", "path": "cd apps/app && pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "runBuild", "path": "ocrmnavigator.project.build", "type": "command", "hidden": true },
            { "label": "runStart", "path": "ocrmnavigator.project.start", "type": "command", "hidden": true },
            { "label": "singlestrclean", "path": "foreach ($path in @('.pnpm-cache','.pnpm-cache', 'node_modules', 'pnpm-lock.yaml', '.cache', 'public\\build', 'build')) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }", "type": "powershellCommand", "hidden": true },
            { "label": "singlestrshadCN", "path": "pnpm dlx shadcn@latest init", "type": "powershellCommand", "hidden": true },
            { "label": "singlestrcomponent", "path": "pnpm dlx shadcn@latest add", "type": "powershellCommand", "hidden": true },
            { "label": "prismaGenerate", "path": "ocrmnavigator.prisma.generate", "type": "command", "hidden": true },
            { "label": "prismaSeed", "path": "ocrmnavigator.prisma.seed", "type": "command", "hidden": true },
            { "label": "prismaStudio", "path": "ocrmnavigator.prisma.studio", "type": "command", "hidden": true },
            { "label": "singlestrfromScratch", "path": "str fromScratch", "type": "powershellCommand", "hidden": true },
            { "label": "terminalInstall", "path": "ocrmnavigator.project.install", "type": "command", "hidden": true },
            { "label": "dbAllLocal", "path": "ocrmnavigator.git.dbAllLocal", "type": "command", "hidden": true },
            { "label": "dbAllRemote", "path": "ocrmnavigator.git.dbAllRemote", "type": "command", "hidden": true },
            { "label": "prismaMigrateReset", "path": "ocrmnavigator.prisma.migrateReset", "type": "command", "hidden": true },
            { "label": "prismaReset", "path": "ocrmnavigator.prisma.reset", "type": "command", "hidden": true },
            { "label": "prismaPush", "path": "ocrmnavigator.prisma.push", "type": "command", "hidden": true },
            { "label": "singlestrdball", "path": "npx tsx prisma/pre-seed.ts && npx prisma db push --force-reset && npx prisma db push && npx tsx prisma/seed.ts && npx prisma generate", "type": "powershellCommand", "hidden": true },
            { "label": "singlestrpatch", "path": "git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags", "type": "powershellCommand", "hidden": true },
            { "label": "singlestrdev", "path": "pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "generateroutes", "path": "pnpm run generate:routes", "type": "powershellCommand", "hidden": true },
            { "label": "methdbapp", "path": "cd apps/app && npx tsx prisma/pre-seed.ts && npx prisma db push --force-reset && npx prisma db push && npx tsx prisma/seed.ts && npx prisma generate && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "killterms", "path": "workbench.action.terminal.killAll", "type": "command", "hidden": true },
            { "label": "startDevServer", "path": "ocrmnavigator.project.dev", "type": "command", "hidden": true },
            { "label": "saveall", "path": "workbench.action.files.saveAll", "type": "command", "hidden": true },
            { "label": "runbuildthendev", "path": "ocrmnavigator.project.build, ocrmnavigator.project.dev", "type": "cmdChain", "hidden": true },
            { "label": "plusversion", "path": "ocrmnavigator.git.add, ocrmnavigator.git.diffCached, ocrmnavigator.git.push, ocrmnavigator.version.patch, ocrmnavigator.git.push, ocrmnavigator.git.pushTags", "type": "cmdChain", "hidden": true },
            { "label": "commitpush", "path": "ocrmnavigator.git.add, ocrmnavigator.git.diffCached, ocrmnavigator.git.push", "type": "cmdChain", "hidden": true },
            { "label": "closeeditors", "path": "workbench.action.closeAllEditors", "type": "command", "hidden": true },
            { "label": "formatfile", "path": "editor.action.formatDocument", "type": "command", "hidden": true },
            { "label": "patchAndPublishToNPM", "type": "cmdChain", "path": "ocrmnavigator.git.add, ocrmnavigator.git.diffCached, ocrmnavigator.git.push, ocrmnavigator.version.patch, ocrmnavigator.git.push, ocrmnavigator.git.pushTags", "hidden": true },
            { "label": "npmPublishWithToken", "path": "npm publish --//registry.npmjs.org/:_authToken=${NPM_TOKEN}", "type": "powershellCommand", "hidden": true },
            { "label": "╒ ╓ ╕ ╖ ╘ ╙ ╛ ╜ ╭ ╮ ╰ ╯ ┄ ┅ ┆ ┇ ┈ ┉ ┊ ┋ ▀ ▄ █ ░ ▒ ▓ ▌ ▐ ■ □ ▪ ▫ ● ○ ◆ ◇ ★ ☆ → ← ↑ ↓ ⇒ ⇐ • · … ― ‖ ← → ➔ ➜ ➞ ➡ ⇒ ⟹ ⬅ ⇐ ⟸ ⬆ ⇑ ⬇ ⇓ ↓↑", "type": "label", "icon": "three-bars", "hidden": true }
          ]
        }
      ]
    },
    {
      "label": "UPDATERS",
      "type": "folder",
      "global": true,
      "expanded": false,
      "items": [
        { "label": "★ ━━━━ ☆ ━━━━ PROJECT ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "ICONS: Auto Build ", "path": "saveall, pnpmrungenerate, pnpmrunbuild, patchAndPublishToNPM", "type": "chain", "icon": "repo-push", "tooltipText": "One button does all to generate / build / update, compile, archive, push to github, push to npm " },
        { "label": "★ ━━━━ ☆ ━━━━ DEPENDENCIES ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "Update icons via pwrshell", "path": "pnpm update @catalystsoftware/icons", "type": "powershellCommand" },
        { "label": "★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆", "path": "ocrmnavigator.patchVersion", "type": "label", "icon": "chrome-minimize" },
        { "label": "Bump Patch", "path": "saveall, PatchVersion", "type": "chain", "icon": "versions" },
        { "label": "PkgJson+ → MDPP+ → CVSIX+ → INS", "path": "ocrmnavigator.order1", "type": "command", "icon": "versions", "tooltipText": "Build pkg.json → md pre-processer → build custom vsix → install" },
        { "label": "Commit And Push Current Dir", "path": "saveall, commitpush", "type": "chain", "icon": "repo-push" },
        { "label": "Patch and Publish to NPM", "path": "saveall, patchAndPublishToNPM", "type": "chain", "icon": "repo-push" },
        { "label": "★ ━━━━ ☆ ━━━━ EXECUTE ORDER ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "Order 1", "path": "ocrmnavigator.order1", "type": "command", "icon": "symbol-event", "tooltipText": "saveAll → pkg.dev.json → pkg.jsn → MD Pre-Proc → compile → +cvsix → install → R" },
        { "label": "Order 2", "path": "ocrmnavigator.order2", "type": "command", "icon": "symbol-event", "tooltipText": "order 1 → autorun" },
        { "label": "Order 3", "path": "ocrmnavigator.order3", "type": "command", "icon": "symbol-event", "tooltipText": "order 2 → updates all" },
        { "label": "Order 4", "path": "ocrmnavigator.order4", "type": "command", "icon": "symbol-event", "tooltipText": "order 2 → bump patch → build all projects → send vsix to marketplace" },
        { "label": "Order 5", "path": "ocrmnavigator.order5", "type": "command", "icon": "symbol-event", "tooltipText": "bum patch → md pre-processor → convert pkg.json → compile and archive → send vsix to marketplace" },
        { "label": "★ ━━━━ ☆ ━━━━ ARCHIVE ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "CVSIX", "path": "ocrmnavigator.project.compile", "type": "command", "icon": "archive" },
        { "label": "VSCE", "path": "vsce package", "type": "powershellCommand", "icon": "archive" },
        { "label": "pro7", "path": "ocrmnavigator.pro7.acrhive", "type": "command", "icon": "json" },
        { "label": "★ ━━━━ ☆ ━━━━ PROCESS FILE ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "PACKAGE.DEV.JSON: Build pkg.json", "path": "ocrmnavigator.format.json.pkg", "type": "command", "icon": "json" },
        { "label": "README.DEV.MD: MD Pre-Processor", "path": "ocrmnavigator.md.convertReadme", "type": "command", "icon": "markdown" },
        { "label": "MD: Update Prompt From md", "path": "node ./updaters/update-prompt-from-md.js", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "★ ━━━━ ☆ ━━━━ AUTORUN SCRIPTS ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "CATALYST-UI: Copy & Rename Files", "path": "powershell ./updaters/CopyAndRenameFiles.ps1", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "DEVSTACK: gen2 USE THIS TO BUILD DEVSTACKS FUNCTIONS", "path": "bun ./updaters/gen2.ts", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "DEVSTACK: Build Catalyst Functions", "path": "bun ./updaters/build-catalyst-functions.ts", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "DEVSTACK: Generate pkg.json cmds for quickpick menu items", "path": "ocrmnavigator.menu.items.pkg.scan.convert.items", "type": "command", "icon": "three-bars" },
        { "label": "DEVSTACK: Generate icons inventory", "path": "node ./updaters/generate-icon-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "DEVSTACK: Generate catalyst-ui inventory", "path": "node ./updaters/generate-ui-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "DEVSTACK: Generate icon library items for devstack functions", "path": "node ./updaters/icon-library-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "★ ━━━━ ☆ ━━━━ FULL AUTO ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "autorun.exe", "path": "ocrmnavigator.triggerAutorunFolder", "type": "command", "icon": "folder" },
        { "label": "updaters.exe", "path": "ocrmnavigator.autorun.updaters", "type": "command", "icon": "folder" },
        { "label": "Build All Extras", "path": "gen2tsU, BuildCatalystFunctionsU, MDPreProcessor, pro7, CopyAndRenameFilesps1U, generateiconinventoryjsU, generateuiinventoryjsU, iconlibraryinventoryjsU, updatepromptfrommdU, Buildpkgjson, CreatekgJsonCommandsQpMenu", "type": "chain", "icon": "folder", "tooltipText": "MD Pre-Processor → Build pkg json → update prompt from md → icon library inventory js → generate ui inventory js → Copy And Rename Files ps1 → pro7 → Build Catalyst Functions → gen2 → Create Pkg Json Commands QpMenu" }
      ]
    },
    {
      "label": "SETTINGS",
      "expanded": false,
      "type": "folder",
      "global": true,
      "icon": "settings",
      "items": [
        { "label": "Tasks", "path": "ocrmnavigator.vfs.tasks", "type": "settingsToggle", "icon": "settings" },
        { "label": "NPM Scripts", "path": "ocrmnavigator.vfs.npmScripts", "type": "settingsToggle", "icon": "settings" },
        {
          "label": "ARCHIVER",
          "path": "ocrmnavigator.ARCHIVER",
          "type": "settingsToggle",
          "args": [
            "custom",
            "vsce"
          ],
          "icon": "settings"
        },
        { "label": "UPDATE_PROMPT_OBJECTS", "path": "ocrmnavigator.UPDATE_PROMPT_OBJECTS", "type": "settingsToggle", "icon": "settings" },
        { "label": "AUTORUN_SCRIPTS", "path": "ocrmnavigator.AUTORUN_SCRIPTS", "type": "settingsToggle", "icon": "settings" },
        { "label": "CONVERT_README_DEV_MD", "path": "ocrmnavigator.CONVERT_README_DEV_MD", "type": "settingsToggle", "icon": "settings" },
        { "label": "PRO7", "path": "ocrmnavigator.PRO7", "type": "settingsToggle", "icon": "settings" },
        { "label": "DELETE_OLD_VSIX", "path": "ocrmnavigator.DELETE_OLD_VSIX", "type": "settingsToggle", "icon": "settings" },
        { "label": "AUTO_INSTALL_VSIX", "path": "ocrmnavigator.AUTO_INSTALL_VSIX", "type": "settingsToggle", "icon": "settings" },
        { "label": "OPEN_PUB_DASH", "path": "ocrmnavigator.OPEN_PUB_DASH", "type": "settingsToggle", "icon": "settings" },
        { "label": "RELOAD_INSTANCE", "path": "ocrmnavigator.RELOAD_INSTANCE", "type": "settingsToggle", "icon": "settings" },
        { "label": "AUTO_FOLD_PKG", "path": "ocrmnavigator.AUTO_FOLD_PKG", "type": "settingsToggle", "icon": "settings" },
        { "label": "BE_QP", "path": "ocrmnavigator.devstack.be", "type": "settingsToggle", "icon": "settings" }
      ]
    },
    {
      "label": "FILES",
      "type": "folder",
      "expanded": false,
      "global": true,
      "icon": "file",
      "items": [
        {
          "label": "CONFIGS",
          "expanded": false,
          "type": "folder",
          "global": true,
          "icon": "gear",
          "items": [
            { "label": "global-navigator-config backup", "path": "F:\\devstackBackUp\\global-navigator-config.json", "type": "file", "icon": "settings", "tooltipText": "" },
            { "label": "global-navigator-config USER", "path": "C:\\Users\\skyle\\AppData\\Roaming\\Code - Insiders\\User\\globalStorage\\skyler.ocrmnav\\global-navigator-config.json", "type": "file", "icon": "settings", "tooltipText": "" },
            { "label": "DevStack WS Config", "path": "C:\\Users\\skyle\\AppData\\Roaming\\Code - Insiders\\User\\globalStorage\\skyler.ocrmnav\\project-configs\\project-1744496862041-y866zpqtd9.json", "type": "file", "icon": "settings", "tooltipText": "" },
            { "label": "Catalyst-ui WS Config", "path": "C:\\Users\\skyle\\AppData\\Roaming\\Code - Insiders\\User\\globalStorage\\skyler.ocrmnav\\project-configs\\project-1757010936487-i30yr98a4p7.json", "type": "file", "icon": "settings", "tooltipText": "" }
          ]
        },
        { "label": "README.dev.md", "path": "README.dev.md", "type": "file", "icon": "markdown" },
        { "label": "README.md", "path": "README.md", "type": "file", "icon": "markdown" },
        { "label": "package.dev.jsonc", "path": "package.dev.jsonc", "type": "file", "icon": "json" },
        { "label": "package.json", "path": "package.json", "type": "file", "icon": "json" },
        { "label": "prisma.schema", "path": "prisma/prisma.schema", "type": "file" },
        { "label": "seed.ts", "path": "prisma/seed.ts", "type": "file" },
        { "label": "seed.ts", "path": "prisma/seed.ts:425", "type": "fileAtLine" }
      ]
    },
    {
      "label": "PROMPT",
      "expanded": false,
      "type": "folder",
      "global": true,
      "icon": "markdown",
      "items": [
        { "label": "Prompt - Reusable Comps", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - Templates", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - UI Lib Objs", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - Blocks", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - VSCode Extension", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - Remix-Run", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - Default", "path": "", "type": "copyValue", "icon": "markdown" }
      ]
    },
    {
      "label": "OTHER",
      "expanded": false,
      "type": "folder",
      "global": true,
      "items": [
        { "label": "Manage VS Extensions", "path": "https://marketplace.visualstudio.com/manage/publishers/skyler?auth_redirect=True", "type": "url" },
        { "label": "VLC w/ playlist", "path": "cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' 1Firreee.xspf", "type": "debianCMD" },
        { "label": "PGAdmin", "path": "& \"c:/Program Files/PostgreSQL/16/pgAdmin 4/runtime/pgAdmin4.exe\"", "type": "powershellCommand" },
        { "label": "PWSH - Admin", "path": "Start-Process powershell -Verb RunAs", "type": "powershellCommand" },
        { "label": "Libre - Draw", "path": "& \"c:/Program Files/LibreOffice/program/sdraw.exe\"", "type": "powershellCommand" },
        { "label": "🌐 Mixes", "path": "https://www.youtube.com/watch?v=KuvaMUDaS-4&list=PLYHhlbShmci2VzDsrtVwMIEx1vBYVk6bj&index=1", "type": "url" },
        { "label": "shad", "path": "https://ui.shadcn.com/docs/components/accordion", "type": "url" },
        { "label": "shad github examples", "path": "https://github.com/shadcn-ui/ui/tree/main/apps/www/app/(app)/examples", "type": "url" },
        { "label": "lucide", "path": "https://lucide.dev/icons/", "type": "url" },
        { "label": "vercel", "path": "https://vercel.com/eights-projects", "type": "url" },
        { "label": "radix", "path": "https://www.radix-ui.com/primitives/docs/components/dialog", "type": "url" },
        { "label": "gmail", "path": "https://mail.google.com/mail/u/0/#all", "type": "url", "filePath": "https://mail.google.com/mail/u/0/#all" }
      ]
    },
    {
      "label": "EXAMPLES",
      "expanded": false,
      "type": "folder",
      "global": true,
      "items": [
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "Build and Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "onSuccess", "executeChain": "deploy, notify" },
            { "type": "onFailure", "executeChain": "rollback, alert" }
          ]
        },
        {
          "label": "Conditional Build",
          "path": "lint, test, build",
          "type": "conditionalChain",
          "args": [
            { "type": "itemSuccess", "itemLabel": "test", "executeChain": "deploy" }
          ]
        },
        {
          "label": "Environment-Based Deploy",
          "path": "build",
          "type": "conditionalChain",
          "args": [
            { "type": "configValue", "configKey": "ocrmnavigator.environment", "operator": "equals", "value": "production", "executeChain": "deployProd" },
            { "type": "configValue", "configKey": "ocrmnavigator.environment", "operator": "equals", "value": "staging", "executeChain": "deployStaging" }
          ]
        },
        {
          "label": "Conditional Install",
          "path": "checkDeps",
          "type": "conditionalChain",
          "args": [
            { "type": "fileNotExists", "filePath": "node_modules", "executeChain": "npmInstall" }
          ]
        },
        {
          "label": "Build with Cleanup",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "always", "executeChain": "cleanup, logResults" }
          ]
        },
        {
          "label": "Advanced Conditional",
          "path": "task1, task2, task3",
          "type": "conditionalChain",
          "args": [
            { "type": "custom", "expression": "results.filter(r => r.success).length >= 2", "executeChain": "partialSuccessHandler" }
          ]
        },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "Build with CI",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        { "label": "ciDeploy", "path": "dockerBuild, pushToRegistry, deployToK8s", "type": "chain" },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" },
            { "type": "itemSuccess", "itemLabel": "ciDeploy", "executeChain": "deployStaging" }
          ]
        },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "ciDeploy",
          "path": "dockerBuild, pushToRegistry",
          "type": "conditionalChain",
          "args": [
            { "type": "onSuccess", "executeChain": "deployStaging" }
          ]
        },
        {
          "type": "combined",
          "logic": "AND",
          "conditions": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true" },
            { "type": "onSuccess" }
          ],
          "executeChain": "ciDeploy"
        },
        { "label": "README.dev.md", "path": "README.dev.md", "type": "file", "icon": "markdown" },
        { "label": "Manage VS Extensions", "path": "https://marketplace.visualstudio.com/manage/publishers/skyler?auth_redirect=True", "type": "url" },
        { "label": "Scan File Imports", "path": "ocrmnavigator.imports.file.scan", "type": "command", "icon": "terminal-cmd" },
        { "label": "CRM", "path": "code-insiders -n f:/OpinionatedCRM", "type": "powershellCommand", "icon": "project" },
        { "label": "VLC w/ playlist", "path": "cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' 1Firreee.xspf", "type": "debianCMD" },
        { "label": "Format", "path": "formatfile, saveall", "type": "chain" },
        { "label": "Format", "path": "formatfile, saveall", "type": "concurrent" },
        { "label": "★ ━━━━ ☆ ━━━━ AUTORUN SCRIPTS ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆", "type": "label", "icon": "chrome-minimize" },
        { "label": "Prompt - Reusable Comps", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Tasks", "path": "ocrmnavigator.vfs.tasks", "type": "settingsToggle", "icon": "settings" },
        {
          "label": "ARCHIVER",
          "path": "ocrmnavigator.ARCHIVER",
          "type": "settingsToggle",
          "args": [
            "custom",
            "vsce"
          ],
          "icon": "settings"
        },
        {
          "label": "Create User",
          "path": "https://api.example.com/users",
          "args": [
            { "method": "POST" },
            { "headers": { "Content-Type": "application/json", "Authorization": "Bearer YOUR_TOKEN" } },
            { "body": { "name": "John Doe", "email": "john@example.com" } }
          ],
          "type": "apiCall",
          "icon": "person-add",
          "tooltipText": ""
        },
        {
          "label": "Deploy to Production",
          "path": "https://hooks.example.com/deploy",
          "args": [
            { "method": "POST" },
            { "body": { "branch": "main", "environment": "production" } }
          ],
          "type": "apiCall",
          "icon": "rocket"
        },
        {
          "label": "List Repos",
          "path": "https://api.github.com/users/yourname/repos",
          "args": [
            { "headers": { "Accept": "application/vnd.github.v3+json", "Authorization": "token YOUR_GITHUB_TOKEN" } }
          ],
          "type": "apiCall",
          "icon": "github",
          "tooltipText": ""
        },
        {
          "label": "Restart Dev Server",
          "path": "http://localhost:3000/api/restart",
          "args": [
            { "method": "POST" }
          ],
          "type": "apiCall",
          "icon": "debug-restart",
          "tooltipText": ""
        }
      ]
    },
        {
      "label": "LAYOUTS",
      "expanded": false,
      "type": "folder",
      "global": false,
      "items": [
        {
          "label": "DevStack Default",
          "path": "",
          "type": "layout",
          "icon": "editor-layout",
          "args": [
            {
              "default": true,
              "editorGrid": {
                "orientation": 0,
                "version": "classic",
                "editorFocus": "last",
                "groups": [
                  { "size": 0.2 },                  
                  { "size": 0.45 },
                  { "size": 0.45 }
                ],
                "files": [
                  { "path": ".vscode/ntrsync/10516_DevStack_todo.md", "group": 1, "pinned": true },
                  {
                    "group": 2,
                    "pinned": true,
                    "foldLevel": [1,2],
                    "path": [
                      "src/extension.ts",
                      "src/helpers/master.ts",
                      "src/helpers/menus.ts",
                      "src/context.ts",
                      "src/helpers/search.ts",
                      "src/extension/navigatorView.ts",
                      "src/helpers/itemsActionsMenu.ts"
                    ]
                  },
                  {
                    "group": 3,
                    "pinned": true,
                       "foldLevel": [1,2],
                    "path": [
                      "README.dev.md",
                      "package.dev.jsonc",
                      "F:/DevStack/docs/LAYOUT.md",
                      "src/helpers/search.ts",
                      "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/project-configs/project-1744496862041-y866zpqtd9.json",
                      "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/global-navigator-config.json"
                    ]
                  }
                ]
              },
              "terminalGrid": {
                "orientation": 0,
                "version": "classic",
                "terminals": [
                  {
                    "name": "Top-Left (API)",
                    "group": 1,
                    "cmd": "echo 'right'",
                    "location": "editor",
                    "priority": 1
                  },
                  {
                    "name": "Top-Right (UI)",
                    "group": 2,
                    "cmd": "echo 'right'",
                    "location": "editor",
                    "priority": 1
                  }
                ]
              },
              "keybindings": {
                "ocrmnavigator.menu.devstack": "alt+d",
                "ocrmnavigator.odin.open": "alt+s",
                "ocrmnavigator.icons.menu": "alt+i",
                "ocrmnavigator.menu.catalystUi": "alt+u",
                "ocrmnavigator.menu.snippets": "alt+f",
                "ocrmnavigator.region.insert": "alt+r",
                "ocrmnavigator.endregion.insert": "alt+e",
                "ocrmnavigator.region.wrap": "alt+w",
                "ocrmnavigator.devstack.site.colorWheel": "alt+q",
                "ocrmnavigator.clipboardMgr.history.show": "alt+h",
                "ocrmnavigator.bookmarks.show": "alt+b",
                "ocrmnavigator.menu.github": "alt+g",
                "ocrmnavigator.project.pkg.open": "alt+p",
                "ocrmnavigator.project.readme.open": "alt+m"
              },
              "autorun": [
                {
                  "runPolicy": "once",
                  "label": "test",
                  "path": "echo 'autorun'",
                  "type": "powershellCommand"
                }
              ],
              "onClose": [
                {
                  "label": "npm run dev",
                  "path": "echo 'onClose'",
                  "type": "powershellCommand"
                }
              ],
              "git": {
                "branch": "dev",
                "onLoad": [
                  {
                    "label": "pnpm i & ini / push prisma & ini .env & run scaffolding",
                    "path": "echo 'git on load'",
                    "type": "powershellCommand"
                  }
                ],
                "onClose": [
                  {
                    "label": "pnpm i & ini / push prisma & ini .env & run scaffolding",
                    "path": "echo 'git on close'",
                    "type": "powershellCommand"
                  }
                ]
              },
              "performance": {
                "css.validate": false,
                "diffEditor.codeLens": false,
                "debug.openDebug": "neverOpen",
                "debug.toolBarLocation": "hidden",
                "debug.showInStatusBar": "never",
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
                "editor.lightbulb.enabled": "onCode",
                "eslint.enable": true,
                "extensions.showRecommendationsOnlyOnDemand": true,
                "extensions.autoUpdate": false,
                "extensions.ignoreRecommendations": true,
                "files.watcherExclude": {},
                "files.exclude": {},
                "files.maxMemoryForLargeFilesMB": 4096,
                "git.decorations.enabled": false,
                "git.diffEditor.renderGutterMenu": false,
                "git.mergeEditor.codeLens.enabled": false,
                "github.copilot.enable": {
                  "*": false,
                  "plaintext": true,
                  "markdown": false,
                  "scminput": false
                },
                "github.copilot.nextEditSuggestions.allowWhitespaceOnlyChanges": false,
                "github.copilot.chat.agent.thinkingTool": true,
                "Codegeex.Chat.LanguagePreference": "English",
                "Codegeex.GenerationPreference": "line by line",
                "Codegeex.Privacy": false,
                "Codegeex.License": "",
                "codegeex.codeLens.functionQuickOptions": {
                  "addComment": false,
                  "ghostComment": false,
                  "fixBug": false,
                  "generateUnitTest": false,
                  "reviewCode": false,
                  "codeOptimization": false,
                  "addDocString": false,
                  "addExceptionHandling": false,
                  "printLogForDebugging": false,
                  "improveRunningEfficiency": false,
                  "renameSymbols": false,
                  "newFileForDebugging": false,
                  "tryANewApproach": false,
                  "explainCode": false
                },
                "codegeex.codeLens.classQuickOptions": {
                  "explainCode": false,
                  "ghostComment": false,
                  "fixBug": false,
                  "generateUnitTest": false,
                  "reviewCode": false,
                  "addDocStringForClass": false,
                  "addDocStringForMethods": false,
                  "addComment": false
                },
                "geminicodeassist.chat.changeView": "Default diff view",
                "geminicodeassist.displayInlineContextHint": false,
                "geminicodeassist.enableTelemetry": false,
                "geminicodeassist.inlineSuggestions.enableAuto": false,
                "geminicodeassist.localCodebaseAwareness": false,
                "html.validate.scripts": false,
                "jsonc.validate.enable": true,
                "json.validate.enable": true,
                "merge-conflict.codeLens.enabled": false,
                "multiDiffEditor.experimental.enabled": false,
                "markdown.validate.enable": false,
                "markdown.preview.automaticPreview": "never",
                "markdown.preview.fontSize": 12,
                "markdown.validate.enabled": false,
                "markdown.updateLinksOnFileMove.enabled": "never",
                "markdown.editor.pasteUrlAsFormattedLink.enabled": "always",
                "markdown.extension.print.theme": "dark",
                "markdown.extension.tableFormatter.normalizeIndentation": true,
                "markdown.extension.theming.decoration.renderParagraph": true,
                "markdown.extension.toc.orderedList": true,
                "markdown.server.log": "off",
                "prisma.showPrismaDataPlatformNotification": false,
                "prettier.enable": true,
                "scm.diffDecorationsGutterAction": "none",
                "scm.diffDecorations": "none",
                "search.smartCase": true,
                "search.useIgnoreFiles": false,
                "search.exclude": {},
                "javascript.validate.enable": true,
                "javascript.updateImportsOnFileMove.enabled": "always",
                "typescript.updateImportsOnFileMove.enabled": "always",
                "typescript.preferences.importModuleSpecifier": "project-relative",
                "typescript.tsserver.web.projectWideIntellisense.enabled": false,
                "typescript.validate.enable": true
              },
              "customizeLayout": {
                "menubar.navigationControls": true,
                "menubar.share": true,
                "menubar.layoutControls": true,
                "menubar.customizeLayout": true,
                "primarySidebar.view": "Explorer",
                "secondarySidebar.view": "skyler.ocrmnav",
                "secondarySidebar.position": "left",
                "primarySidebar.display": true,
                "workbench.activityBar.visible": true,
                "secondarySidebar.display": true,
                "panel.display": false,
                "panel.alignment": "center",
                "panel.view": "output",
                "modes.centeredLayout": false,
                "modes.fullScreen": false,
                "modes.zenMode": true
              },
              "workspace": {
                "editor.minimap.showRegionSectionHeaders": true,
                "editor.minimap.showMarkSectionHeaders": false,
                "breadcrumbs.enabled": false,
                "editor.minimap.autohide": true,
                "editor.minimap.enabled": true,
                "editor.minimap.showSlider": "mouseover",
                "editor.minimap.side": "left",
                "editor.minimap.size": "fill",
                "editor.minimap.renderCharacters": false,
                "editor.minimap.maxColumn": "50",
                "editor.fontSize": 11,
                "editor.wordWrap": "on",
                "editor.foldingStrategy": "auto",
                "editor.fontFamily": "JetBrains Mono",
                "editor.fontLigatures": true,
                "editor.fontVariations": true,
                "editor.accessibilitySupport": "off",
                "editor.showFoldingControls": "always",
                "editor.lineNumbers": "relative",
                "editor.scrollBeyondLastLine": false,
                "editor.foldingImportsByDefault": false,
                "editor.renderWhitespace": "none",
                "editor.renderControlCharacters": true,
                "editor.folding": true,
                "editor.glyphMargin": true,
                "editor.stickyScroll.enabled": true,
                "editor.largeFileOptimizations": true,
                "editor.stickyScroll.maxLineCount": 5,
                "editor.unicodeHighlight.invisibleCharacters": false,
                "javascript.updateImportsOnFileMove.enabled": "never",
                "problems.visibility": false,
                "terminal.integrated.defaultLocation": "editor",
                "terminal.integrated.suggest.suggestOnTriggerCharacters": true,
                "terminal.integrated.fontFamily": "monospace",
                "terminal.integrated.stickyScroll.enabled": true,
                "terminal.integrated.fontSize": 12,
                "workbench.editor.alwaysShowEditorActions": true,
                "workbench.editor.enablePreviewFromQuickOpen": false,
                "workbench.editor.focusRecentEditorAfterClose": false,
                "workbench.editor.pinnedTabsOnSeparateRow": true,
                "workbench.editor.wrapTabs": true,
                "workbench.panel.opensMaximized": "never",
                "workbench.panel.defaultLocation": "bottom",
                "workbench.secondarySideBar.showLabels": false,
                "workbench.externalBrowser": "Opera",
                "workbench.activityBar.location": "right",
                "workbench.editor.showTabs": "multiple",
                "workbench.statusBar.visible": true,
                "workbench.sideBar.location": "right",
                "workbench.commandPalette.history": 30,
                "workbench.remoteIndicator.showExtensionRecommendations": false,
                "workbench.welcomePage.walkthroughs.openOnInstall": false,
                "workbench.editor.restoreViewState": true,
                "window.restoreWindows": "one",
                "window.openFilesInNewWindow": "default",
                "window.menuBarVisibility": "classic",
                "window.commandCenter": true,
                "window.zoomLevel": -1,
                "update.mode": "none",
                "update.showReleaseNotes": false,
                "vsicons.dontShowNewVersionMessage": true,
                "update.enableWindowsBackgroundUpdates": false,
                "telemetry.telemetryLevel": "off",
                "extensions.autoCheckUpdates": false,
                "security.workspace.trust.untrustedFiles": "newWindow",
                "ocrmnavigator.terminal.location": "editor",
                "ocrmnavigator.codesnap.windowControlStyle": "Windows",
                "ocrmnavigator.codesnap.showWindowTitle": true,
                "ocrmnavigator.codesnap.windowBorderRadius": "8px",
                "ocrmnavigator.codesnap.windowTitleStyle": "Filename",
                "ocrmnavigator.codesnap.showLineNumbers": true,
                "ocrmnavigator.codesnap.realLineNumbers": false,
                "ocrmnavigator.codesnap.transparentBackground": false,
                "ocrmnavigator.codesnap.trimEmptyLines": false,
                "ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2": false,
                "ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2_3": true,
                "ocrmnavigator.vfs.AUTO_FOLD_1": false,
                "ocrmnavigator.vfs.AUTO_FOLD_1_2": true,
                "ocrmnavigator.vfs.tasks": true,
                "ocrmnavigator.vfs.npmScripts": true,
                "ocrmnavigator.vfs.snippets": true,
                "ocrmnavigator.AUTO_FOLD_PKG": true,
                "ocrmnavigator.devstack.be": true,
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
                "ocrmnavigator.todo.branch": "main",
                "ocrmnavigator.todo.checkRemindersInterval": "10",
                "ocrmnavigator.todo.syncInterval": "20",
                "ocrmnavigator.todo.syncOnSave": true,
                "ocrmnavigator.todo.owner": "8an3",
                "ocrmnavigator.todo.repository": "8an3/mynotesrepo",
                "ocrmnavigator.todo.isPriv": false,
                "ocrmnavigator.vfs.item.hidden.toggle": true,
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
                "ocrmnavigator.vscode.theme.blacked": true,
                "ocrmnavigator.vscode.theme.window.differentiator": true,
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
                "ocrmnavigator.vfs.item.path.copy": true,
                "ocrmnavigator.bookmarks": true,
                "ocrmnavigator.searchBar": true,
                "ocrmnavigator.clipBoardHistory": true,
                "ocrmnavigator.colorWheel": true,
                "ocrmnavigator.lucideIcons": true,
                "ocrmnavigator.share": true,
                "ocrmnavigator.url": true,
                "ocrmnavigator.format.json.remove.comments.file": true,
                "ocrmnavigator.con": true,
                "ocrmnavigator.format.remove.comments.file": true,
                "ocrmnavigator.unusedFunctions": true,
                "ocrmnavigator.viewers": true,
                "ocrmnavigator.uiDashboard": true,
                "ocrmnavigator.devStackFunctions": true,
                "ocrmnavigator.openLeftOffNote": true,
                "ocrmnavigator.devstack.site.md.render": true,
                "ocrmnavigator.project.index.smart.create": true,
                "ocrmnavigator.devstack.site.tailwindConverter": true,
                "ocrmnavigator.remix.project2agnostic.convert": true,
                "ocrmnavigator.concurrent": true,
                "ocrmnavigator.autoSequencer": true
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
          ]
        },
        {
          "label": "Test Extensions",
          "path": "",
          "type": "layout",
          "icon": "editor-layout",
          "args": [
            {
              "extensions": {
                "enable": [
                  "tomoki1207.pdf"
                ],
                "disable": [
                  "github.copilot",
                  "AMiner.codegeex",
                  "jmanuels.do",
                  "NoThlnG.vscode-open-wsl",
                  "ban.spellright",
                  "tauri-apps.tauri-vscode",
                  "ms-vscode-remote.remote-wsl",
                  "google.geminicodeassist",
                  "JetBrains.jetbrains-ai-assistant"
                ],
                "install": []
              },
              "editorGrid": {
                "columns": 3,
                "rows": 2,
                "groups": [
                  {
                    "slot": [
                      0,
                      0
                    ],
                    "active": ".vscode/ntrsync/10516_DevStack_todo.md",
                    "pinned": true
                  },
                  {
                    "slot": [
                      0,
                      1
                    ],
                    "active": "src/helpers/context.ts",
                    "pinned": true
                  },
                  {
                    "slot": [
                      1,
                      0
                    ],
                    "active": "README.dev.md",
                    "pinned": true
                  },
                  {
                    "slot": [
                      1,
                      1
                    ],
                    "active": "README.md",
                    "pinned": true
                  },
                  {
                    "slot": [
                      2,
                      0
                    ],
                    "active": "package.dev.jsonc",
                    "pinned": true
                  }
                ],
                "files": [
                  {
                    "path": "src/helpers/master.ts",
                    "slot": [
                      1,
                      0
                    ],
                    "pinned": true,
                    "fold": [
                      1,
                      2,
                      3
                    ]
                  },
                  {
                    "path": "src/helpers/menus.ts",
                    "slot": [
                      1,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "src/extension/navigatorView.ts",
                    "slot": [
                      1,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "src/helpers/modular-commands.ts",
                    "slot": [
                      1,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "src/extension.ts",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "package.dev.jsonc",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "C:/User/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/global-navigator-config.json",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "F:/devstackBackUp/global-navigator-config.json",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "F:/devstackBackUp/project-configs/project-1744496862041-y866zpqtd9.json",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "F:/devstackBackUp/project-configs/project-1757010936487-i30yr98a4p7.json",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  }
                ]
              },
              "performance": {
                "css.validate": false,
                "diffEditor.codeLens": false,
                "debug.openDebug": "neverOpen",
                "debug.toolBarLocation": "hidden",
                "debug.showInStatusBar": "never",
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
                "editor.lightbulb.enabled": "onCode",
                "eslint.enable": true,
                "extensions.showRecommendationsOnlyOnDemand": true,
                "extensions.autoUpdate": false,
                "extensions.ignoreRecommendations": true,
                "files.watcherExclude": {},
                "files.exclude": {},
                "files.maxMemoryForLargeFilesMB": 4096,
                "git.decorations.enabled": false,
                "git.diffEditor.renderGutterMenu": false,
                "git.mergeEditor.codeLens.enabled": false,
                "github.copilot.enable": {
                  "*": false,
                  "plaintext": true,
                  "markdown": false,
                  "scminput": false
                },
                "github.copilot.nextEditSuggestions.allowWhitespaceOnlyChanges": false,
                "github.copilot.chat.agent.thinkingTool": true,
                "Codegeex.Chat.LanguagePreference": "English",
                "Codegeex.GenerationPreference": "line by line",
                "Codegeex.Privacy": false,
                "Codegeex.License": "",
                "codegeex.codeLens.functionQuickOptions": {
                  "addComment": false,
                  "ghostComment": false,
                  "fixBug": false,
                  "generateUnitTest": false,
                  "reviewCode": false,
                  "codeOptimization": false,
                  "addDocString": false,
                  "addExceptionHandling": false,
                  "printLogForDebugging": false,
                  "improveRunningEfficiency": false,
                  "renameSymbols": false,
                  "newFileForDebugging": false,
                  "tryANewApproach": false,
                  "explainCode": false
                },
                "codegeex.codeLens.classQuickOptions": {
                  "explainCode": false,
                  "ghostComment": false,
                  "fixBug": false,
                  "generateUnitTest": false,
                  "reviewCode": false,
                  "addDocStringForClass": false,
                  "addDocStringForMethods": false,
                  "addComment": false
                },
                "geminicodeassist.chat.changeView": "Default diff view",
                "geminicodeassist.displayInlineContextHint": false,
                "geminicodeassist.enableTelemetry": false,
                "geminicodeassist.inlineSuggestions.enableAuto": false,
                "geminicodeassist.localCodebaseAwareness": false,
                "html.validate.scripts": false,
                "jsonc.validate.enable": true,
                "json.validate.enable": true,
                "merge-conflict.codeLens.enabled": false,
                "multiDiffEditor.experimental.enabled": false,
                "markdown.validate.enable": false,
                "markdown.preview.automaticPreview": "never",
                "markdown.preview.fontSize": 12,
                "markdown.validate.enabled": false,
                "markdown.updateLinksOnFileMove.enabled": "never",
                "markdown.editor.pasteUrlAsFormattedLink.enabled": "always",
                "markdown.extension.print.theme": "dark",
                "markdown.extension.tableFormatter.normalizeIndentation": true,
                "markdown.extension.theming.decoration.renderParagraph": true,
                "markdown.extension.toc.orderedList": true,
                "markdown.server.log": "off",
                "prisma.showPrismaDataPlatformNotification": false,
                "prettier.enable": true,
                "scm.diffDecorationsGutterAction": "none",
                "scm.diffDecorations": "none",
                "search.smartCase": true,
                "search.useIgnoreFiles": false,
                "search.exclude": {},
                "javascript.validate.enable": true,
                "javascript.updateImportsOnFileMove.enabled": "always",
                "typescript.updateImportsOnFileMove.enabled": "always",
                "typescript.preferences.importModuleSpecifier": "project-relative",
                "typescript.tsserver.web.projectWideIntellisense.enabled": false,
                "typescript.validate.enable": true
              },
              "customizeLayout": {
                "menubar.navigationControls": true,
                "menubar.share": true,
                "menubar.layoutControls": true,
                "menubar.customizeLayout": true,
                "primarySidebar.view": "Explorer",
                "secondarySidebar.view": "skyler.ocrmnav",
                "secondarySidebar.position": "left",
                "primarySidebar.display": true,
                "workbench.activityBar.visible": true,
                "secondarySidebar.display": true,
                "panel.display": false,
                "panel.alignment": "center",
                "panel.view": "output",
                "modes.centeredLayout": false,
                "modes.fullScreen": false,
                "modes.zenMode": true
              },
              "workspace": {
                "editor.minimap.showRegionSectionHeaders": true,
                "editor.minimap.showMarkSectionHeaders": false,
                "breadcrumbs.enabled": false,
                "editor.minimap.autohide": true,
                "editor.minimap.enabled": true,
                "editor.minimap.showSlider": "mouseover",
                "editor.minimap.side": "left",
                "editor.minimap.size": "fill",
                "editor.minimap.renderCharacters": false,
                "editor.minimap.maxColumn": "50",
                "editor.fontSize": 11,
                "editor.wordWrap": "on",
                "editor.foldingStrategy": "auto",
                "editor.fontFamily": "JetBrains Mono",
                "editor.fontLigatures": true,
                "editor.fontVariations": true,
                "editor.accessibilitySupport": "off",
                "editor.showFoldingControls": "always",
                "editor.lineNumbers": "relative",
                "editor.scrollBeyondLastLine": false,
                "editor.foldingImportsByDefault": false,
                "editor.renderWhitespace": "none",
                "editor.renderControlCharacters": true,
                "editor.folding": true,
                "editor.glyphMargin": true,
                "editor.stickyScroll.enabled": true,
                "editor.largeFileOptimizations": true,
                "editor.stickyScroll.maxLineCount": 5,
                "editor.unicodeHighlight.invisibleCharacters": false,
                "javascript.updateImportsOnFileMove.enabled": "never",
                "problems.visibility": false,
                "terminal.integrated.defaultLocation": "editor",
                "terminal.integrated.suggest.suggestOnTriggerCharacters": true,
                "terminal.integrated.fontFamily": "monospace",
                "terminal.integrated.stickyScroll.enabled": true,
                "terminal.integrated.fontSize": 12,
                "workbench.editor.alwaysShowEditorActions": true,
                "workbench.editor.enablePreviewFromQuickOpen": false,
                "workbench.editor.focusRecentEditorAfterClose": false,
                "workbench.editor.pinnedTabsOnSeparateRow": true,
                "workbench.editor.wrapTabs": true,
                "workbench.panel.opensMaximized": "never",
                "workbench.panel.defaultLocation": "bottom",
                "workbench.secondarySideBar.showLabels": false,
                "workbench.externalBrowser": "Opera",
                "workbench.activityBar.location": "right",
                "workbench.editor.showTabs": "multiple",
                "workbench.statusBar.visible": true,
                "workbench.sideBar.location": "right",
                "workbench.commandPalette.history": 30,
                "workbench.remoteIndicator.showExtensionRecommendations": false,
                "workbench.welcomePage.walkthroughs.openOnInstall": false,
                "workbench.editor.restoreViewState": true,
                "window.restoreWindows": "one",
                "window.openFilesInNewWindow": "default",
                "window.menuBarVisibility": "classic",
                "window.commandCenter": true,
                "window.zoomLevel": -1,
                "update.mode": "none",
                "update.showReleaseNotes": false,
                "vsicons.dontShowNewVersionMessage": true,
                "update.enableWindowsBackgroundUpdates": false,
                "telemetry.telemetryLevel": "off",
                "extensions.autoCheckUpdates": false,
                "security.workspace.trust.untrustedFiles": "newWindow",
                "ocrmnavigator.terminal.location": "editor",
                "ocrmnavigator.codesnap.windowControlStyle": "Windows",
                "ocrmnavigator.codesnap.showWindowTitle": true,
                "ocrmnavigator.codesnap.windowBorderRadius": "8px",
                "ocrmnavigator.codesnap.windowTitleStyle": "Filename",
                "ocrmnavigator.codesnap.showLineNumbers": true,
                "ocrmnavigator.codesnap.realLineNumbers": false,
                "ocrmnavigator.codesnap.transparentBackground": false,
                "ocrmnavigator.codesnap.trimEmptyLines": false,
                "ocrmnavigator.markdownpreprocessor.variableSystem": true,
                "ocrmnavigator.markdownpreprocessor.sourcemapUpdater": true,
                "ocrmnavigator.markdownpreprocessor.tocUpdater": true,
                "ocrmnavigator.markdownpreprocessor.tocType": "roman",
                "ocrmnavigator.markdownpreprocessor.tableConversion": true,
                "ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2": false,
                "ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2_3": true,
                "ocrmnavigator.vfs.AUTO_FOLD_1": false,
                "ocrmnavigator.vfs.AUTO_FOLD_1_2": true,
                "ocrmnavigator.vfs.tasks": true,
                "ocrmnavigator.vfs.npmScripts": true,
                "ocrmnavigator.vfs.snippets": true,
                "ocrmnavigator.AUTO_FOLD_PKG": true,
                "ocrmnavigator.devstack.be": true,
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
                "ocrmnavigator.todo.branch": "main",
                "ocrmnavigator.todo.checkRemindersInterval": "10",
                "ocrmnavigator.todo.syncInterval": "20",
                "ocrmnavigator.todo.syncOnSave": true,
                "ocrmnavigator.todo.owner": "8an3",
                "ocrmnavigator.todo.repository": "8an3/mynotesrepo",
                "ocrmnavigator.todo.isPriv": false,
                "ocrmnavigator.vfs.item.hidden.toggle": true,
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
                "ocrmnavigator.vscode.theme.blacked": true,
                "ocrmnavigator.vscode.theme.window.differentiator": true,
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
                "ocrmnavigator.vfs.item.path.copy": true,
                "ocrmnavigator.bookmarks": true,
                "ocrmnavigator.searchBar": true,
                "ocrmnavigator.clipBoardHistory": true,
                "ocrmnavigator.colorWheel": true,
                "ocrmnavigator.lucideIcons": true,
                "ocrmnavigator.share": true,
                "ocrmnavigator.url": true,
                "ocrmnavigator.format.json.remove.comments.file": true,
                "ocrmnavigator.con": true,
                "ocrmnavigator.format.remove.comments.file": true,
                "ocrmnavigator.unusedFunctions": true,
                "ocrmnavigator.viewers": true,
                "ocrmnavigator.uiDashboard": true,
                "ocrmnavigator.devStackFunctions": true,
                "ocrmnavigator.openLeftOffNote": true,
                "ocrmnavigator.devstack.site.md.render": true,
                "ocrmnavigator.project.index.smart.create": true,
                "ocrmnavigator.devstack.site.tailwindConverter": true,
                "ocrmnavigator.remix.project2agnostic.convert": true,
                "ocrmnavigator.concurrent": true,
                "ocrmnavigator.autoSequencer": true
              }
            }
          ]
        }
      ]
    },
    {
      "label": "PRIMARY",
      "expanded": false,
      "global": false,
      "type": "folder",
      "items": [
        {
          "label": "master.ts",
          "path": "src/helpers/master.ts",
          "type": "file"
        },
        {
          "label": "menus.ts",
          "path": "src/helpers/menus.ts",
          "type": "file"
        },
        {
          "label": "extension.ts",
          "path": "src/extension.ts",
          "type": "file"
        },
        {
          "label": "navigatorView.ts",
          "path": "src/extension/navigatorView.ts",
          "type": "file"
        },
        {
          "label": "workspace.ts",
          "path": "src/helpers/workspace.ts",
          "type": "file"
        },
        {
          "label": "itemsActionsMenu.ts",
          "path": "f:\\DevStack\\src\\helpers\\itemsActionsMenu.ts",
          "type": "file",
          "icon": "file"
        },
        {
          "label": "yeet",
          "path": "f:\\DevStack\\src\\helpers\\yeet.ts",
          "type": "file",
          "icon": "arrow-circle-up"
        },
        {
          "label": "modular-commands.ts",
          "path": "f:\\DevStack\\src\\helpers\\modular-commands.ts",
          "type": "file",
          "icon": "symbol-function"
        }
      ]
    },
    {
      "label": "SECONDARY",
      "expanded": false,
      "type": "folder",
      "global": false,
      "items": []
    }
  ]
}
```

</details>







---
[🡄 Return](https://github.com/8an3/DevStack)





