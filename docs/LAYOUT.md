# Layout Configuration Guide

As it currently stands, the redesign is 100% in a useable state as I have the 2 workspaces that I'm currently in host configs and to make the testing process even harder for my instance, in terms to working on this extension, instead of using the dev server for testing, I have just been doing hard instance restarts or completely closing and reopening vscode with zero issues but there are 2 things needed to be fixed / completed. In the grand scheme of things aren't that big of a deal. 

The first being the extension object in which, it is currently and entirely inactive. I have yet to receive word from microsoft in regards to this issue, but I'm not surprised due to the holiday season. At this point I seriouisly have no hope for this feature due to what I believe is a serious enough security threat to warrant ms to have their security team look into and fix, BUT who knows due to the nature of the software they may not deem it a threat at all, although I give that a 1% chance in happening, lol 1% may still happen. As I have deleted the explanation of how it works so as to not teach anyone else how to emulate it, but quickly after many attempts at getting it to work I finally was able to get it to a point where vscode closes and then re-opens with disabling the extensions the user specifies. Microsoft... does not want extensions doing this, DESPITE the fact that they do currently have a command in which an extension can disable ALL extensions at once. With saying that, in terms of inidvidual control of disabling extensions, ms has blocked virtually all avenues to do so. The workaround I found, escapes vscodes instance / sandbox and executes the command to open a new vscode instance... on the host itself, with zero ties to the vscodes instance. That is where the 1% of hope comes from, as you shouldn't be able to escape the sandbox to run any command in any shape or form on the host, adding fuel to the fire also having zero ties to the vscode instance. Meaning that an attacker could place a script to automatically run at any time of their choosing, whether or not your vscode instance is open and can still run AFTER you close the instance. 

Ater some considerable thought on this, whether or not microsoft deems it a threat I will not be coding this into the extension. As I have put myself through several offsec courses, I don't think the positives out weigh the negatives in order to include this and expose that door. Trust me when I say this, it pains me to not include this in the feature set of the extension.

The second are the on close objects for `git` and `onClose`. Currently these items are just running on initial load but I will continue to work on these to get them working they are a pretty valuable feature to have. 

#### The Workspace Layout Engine, a sophisticated orchestrator that allows you to define and switch between entire development environments with a single click. It doesn't just change a theme; it reconfigures the entire VS Code UI, opens your project files in specific grid positions, and prepares your terminal environment.

Designed for developers who switch contexts frequently—moving from heavy feature development to a focused debugging session or a minimal writing environment. It automates the tedious process of rearranging your editor every time you start a task.

This guide explains how to configure custom workspace layouts using the DevStack layout system. Each layout defines how VS Code appears when activated, including UI elements, editor tabs, terminals, and color themes.

> [!IMPORTANT] 
> **Major Update: Complete Rewrite**
> 
> This feature has been completely rebuilt from the ground up—not because anything was broken, but to make it even more powerful and configurable.
>
> If you're already using this feature, you'll need to replace your current configuration. I know that sounds like a hassle, but the improvements make it worthwhile.
>
> **New Capabilities:**
> - **Cloud sync**: Access your configurations remotely from anywhere
> - **Profile management**: Save configuration profiles directly from VS Code and push them to the web UI
> - **Easy sharing**: Log in via GitHub (using the same email) to download your profiles on any machine
> - **Team deployment**: Perfect for managers who want to standardize workspace setups across their team
>
> These features make onboarding new developers incredibly efficient—you can have their entire workspace configured instantly. Whether you're setting up different configurations for new hires or helping your current team optimize their development environment, this system has you covered.


> [!NOTE] 
> **New Configuration Parameters:**
>
> - **default** → `true | false` (unchanged from previous version)
>
> - **keybindings** → Configure custom keyboard shortcuts per configuration. Use the same key combinations in different contexts, workspace-specific shortcuts, or any mapping you can imagine.
> 
>     <details closed><summary>Keybindings config</summary>
>
>     ```json
>     "keybindings": { 
>            "ocrmnavigator.menu.devstack": "alt+d",
>            "ocrmnavigator.menu.icons": "alt+i",
>            "ocrmnavigator.menu.catalystUi": "alt+u",
>            "ocrmnavigator.menu.snippets": "alt+s",
>            "ocrmnavigator.region.insert": "alt+r",
>            "ocrmnavigator.endregion.insert": "alt+e",
>            "ocrmnavigator.region.wrap": "alt+w",
>            "ocrmnavigator.devstack.site": "alt+q",
>            "ocrmnavigator.clipboardMgr.history.show": "alt+h",
>            "ocrmnavigator.bookmarks.show": "alt+b",
>            "ocrmnavigator.menu.github": "alt+g",
>            "ocrmnavigator.project.pkg.open": "alt+p",
>            "ocrmnavigator.project.readme.open": "alt+m"
>          },
>     ```
> 
>      </details>
> 
> - **autorun** → Executes VFS item configs when loading your workspace. Includes a new `runPolicy` parameter with three options:
>   - `"once"` - Runs only on first load
>   - `"onLoad"` - Runs every time the workspace loads
>   - `"onReload"` - Runs when the workspace reloads
>   
>   If you're already familiar with the extension, the learning curve will be minimal since these configurations follow the same patterns.
>  
>     <details closed><summary>Autorun config</summary>
>
>     ```json
>       "autorun": [ 
>         {
>           "runPolicy": "once", // "once" | "onLoad" | "onReload"
>           "label": "watch",
>           "path": "watch",
>           "type": "tasks"
>         },
>         {
>           "runPolicy": "onLoad", 
>           "label": "build",
>           "path": "build",
>           "type": "npmScripts"
>         },
>         {
>           "runPolicy": "onReload", 
>           "label": "Scan File Imports",
>           "path": "ocrmnavigator.imports.file.scan",
>           "type": "command",
>           "icon": "terminal-cmd"
>         },
>         {
>           "runPolicy": "once", 
>           "label": "pnpm i & ini / push prisma & ini .env & run scaffolding",
>           "path": "install, iniPrisma, iniEnv, scaffolding",
>           "type": "chain",
>           "icon": "debug-start",
>           "tooltipText": "Fresh workspace, only executes on first load by checking if the workspace has a .git folder"
>         },
>         {
>           "runPolicy": "onLoad",
>           "label": "1 DEV",
>           "path": "saveall, killterms, startDevServer",
>           "type": "chain",
>           "icon": "debug-start",
>           "tooltipText": "SINGLE KILL Terminals && Start DEV Server"
>         }
>       ],
>     ```
> 
>      </details>
> 
>
> - **onClose** → Similar to autorun, but executes when closing VS Code. No special parameters required.
>  
>     <details closed><summary>onClose config</summary>
>
>     ```json
>         "onClose": [ 
>         {
>           "label": "clean",
>           "path": "clean",
>           "type": "chain"
>         }
>       ],
>     ```
> 
>      </details>
> 
> - **editorGrid** → Completely redesigned for easier configuration with more layout options. Create complex arrangements like 2×2 grids within a single editor group or T-bone layouts. New per-file parameters include `lineNumber` and `fold`.
>
>     <details closed><summary>editorGrid config</summary>
>
>     ```json
>         "editorGrid": {
>           "columns": 2,
>           "rows": 2,
>           "version": "plex",
>           "groups": [
>             { "slot": [ 0, 0 ], "active": "src/main.ts" }, // Top Left
>             { "slot": [ 1, 0 ], "active": "src/types.ts" }, // Top Right
>             { "slot": [ 0, 1 ], "active": "src/utils.ts" }, // Bottom Left
>             { "slot": [ 1, 1 ], "active": "README.md" } // Bottom Right
>           ],
>           "files": [
>             { "path": "src/main.ts", "slot": [ 0, 0 ], "pinned": true , "lineNumber": 1452, "fold": [ 2, 3 ] },
>             { "path": "src/helper.ts", "slot": [ 0, 0 ], "lineNumber": 1452, "fold": 2 }, // Also in Top Left!
>             { "path": "src/types.ts", "slot": [ 1, 0 ], "pinned": true },
>             { "path": "src/api.ts", "slot": [ 1, 0 ] }, // Also in Top Right!
>             { "path": "src/utils.ts", "slot": [ 0, 1 ] },
>             { "path": "README.md", "slot": [ 1, 1 ] }
>           ]
>         },
>     ```
> 
>      </details>
>
> During long term testing of the above grid system, personally I did not use the `plex` aspect of the layout system. There is a caveat to using the plex system, in that the feature that controls which col your files open cannot be used due to how each `square`, `column`, or `row` is made but I know people will want to use this style. Instead of being totally greedy and selfish and just reverting back to the old system, allowing me to gain a feautre I wanted back. Most of all, since it is already coded and working I decided to go with both variants and adding the value `version` that takes either `plex` | `classic`.
>
> The same also effects terminal grid, in which there will be 2 versions avialable as each grid system is made virtually identical to one another.
>
>     <details closed><summary>Classic Editor Grid</summary>
>
>     ```json
>          "editorGrid": {
>                "orientation": 0,
>                "version": "classic",
>                "editorFocus": "last",
>                "groups": [
>                  { "size": 0.2 },                  
>                  { "size": 0.45 },
>                  { "size": 0.45 }
>                ],
>                "files": [
>                  { "path": ".vscode/ntrsync/10516_DevStack_todo.md", "group": 1, "pinned": true },
>                  {
>                    "group": 2,
>                    "pinned": true,
>                    "foldLevel": [1,2],
>                    "path": [
>                      "src/extension.ts",
>                      "src/helpers/master.ts",
>                      "src/helpers/menus.ts",
>                      "src/helpers/context.ts",
>                      "src/helpers/search.ts",
>                      "src/extension/navigatorView.ts",
>                      "src/helpers/itemsActionsMenu.ts",
>                      "src/helpers/modular-commands.ts"
>                    ]
>                  },
>                  {
>                    "group": 3,
>                    "pinned": true,
>                       "foldLevel": [1,2],
>                    "path": [
>                      "README.dev.md",
>                      "package.dev.jsonc",
>                      "F:/DevStack/docs/LAYOUT.md",
>                      "F:/DevStack/docs/VFS2.md",
>                      "F:/DevStack/docs/VFS.md",
>                      "src/helpers/search.ts",
>                      "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/project-configs/project-1744496862041-y866zpqtd9.json",
>                      "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/global-navigator-config.json"
>                    ]
>                  }
>                ]
>              },
>     ```
> 
>      </details>
> 
> - **terminalGrid** → Now the engine sports 3 different version for executing commands in terminals. The first two are listed below in the examples. The third and final version is is using the items path value, just like a powershell command, vscode command or debian command. Along with declaring `"version": "classic",` immediatly following the path value. This variant is for people who only want to run one single command and do not wish to create a speacialized terminal for it. This makes it so each variant has there own specfic flags for the function to scan and become aware of which you would like to use
> 
>    <details closed><summary>Terminal grid config plex 2x2 layout</summary>
>
>     ```json
>       "terminalGrid": {
>           "columns": 2,
>           "rows": 2,
>           "terminals": [
>             { "name": "API Server", "slot": [ 0, 0 ], "cmd": "npm run dev", "active": true, "color": "terminal.ansiCyan" },
>             { "name": "Build Watcher", "slot": [ 0, 0 ], "cmd": "npm run watch" }, // Same slot, becomes a tab
>             { "name": "Database", "slot": [ 1, 0 ], "cmd": "docker-compose up" },
>             { "name": "Unit Tests", "slot": [ 0, 1 ], "cmd": "npm run test:watch" },
>             { "name": "System Logs", "slot": [ 1, 1 ], "cmd": "tail -f storage/logs/laravel.log" }
>           ]
>         },
>     ```
> 
>      </details>
>
> 
>    <details closed><summary>Terminal grid config classic 2x1 layout</summary>
>
>     ```json
>            "terminalGrid": {
>                 "orientation": 0,
>                 "version": "classic",
>                 "terminals": [
>                   {
>                     "name": "Top-Left (API)",
>                     "group": 1,
>                     "cmd": "echo 'right'",
>                     "location": "editor",
>                     "priority": 1
>                   },
>                   {
>                     "name": "Top-Right (UI)",
>                     "group": 2,
>                     "cmd": "echo 'right'",
>                     "location": "editor",
>                     "priority": 1
>                   }
>                 ]
>               },
>     ```
> 
>      </details>
> 
> - **git** → Parameters: `branch`, `onload`, `onclose`
>
>
>    <details closed><summary>terminalGrid config</summary>
>
>     ```json
>       "git": {
>                     "branch": "dev",
>                     "onLoad": [
>                       {
>                         "label": "pnpm i & ini / push prisma & ini .env & run scaffolding",
>                         "path": "echo 'git on load'",
>                         "type": "powershellCommand"
>                       }
>                     ],
>                     "onClose": [
>                       {
>                         "label": "pnpm i & ini / push prisma & ini .env & run scaffolding",
>                         "path": "echo 'git on close'",
>                         "type": "powershellCommand"
>                       }
>                     ]
>                   },
>
>         ```
>      </details>
> 
> - **extensions** → Control which extensions are active based on workspace context or configuration. Instead of being limited to 10-20 active extensions, you can now install 50+ extensions and swap between different sets with a single click. Switch from coding to debugging mode with completely different active extensions, dramatically expanding your available toolset.
>
> NOTE! Unfortuantly, for the time being anyways, this feature is not active and need to wait on a email reply from microsoft. While I have found a solution to the problems faced during coding this feature. I won't post or activate till I see what takes place with that email chain. As the solution involved escaping vscodes sandbox / instance and gains command execution on the host itself. If they deem this a security threat enough to warrant in sending their team a breakdown to fix, than this feature will not be moving forward sadly. BUT, who knows due to the nature of the software, they may not view this as a security issue enough for them to bother looking at it and move on, in which case I will finish off and activate this feature.
>
> It sucks because, not only did I spend a lot of time on something that at first glance looked really simple but also because this feature would be a great benefit, to literally every single vscode user since every user faces performance issues due to extensions.
> 
>    <details closed><summary>extensions config</summary>
>
>     ```json
>   "extensions": {
>         "enable": [
>           "esbenp.prettier-vscode",
>           "dbaeumer.vscode-eslint"
>         ],
>         "disable": [
>           "github.copilot",
>           "ms-vscode.vscode-typescript-next"
>         ],
>         "install": [
>           "skyler.ocrmnav@1.2.3"
>         ]
>       },
>     ```
> 
>      </details>
>
> - **workbench.colorCustomizations** → Unchanged from previous version
>
> 
>    <details closed><summary>workbench.colorCustomizations config</summary>
>
>     ```json
>      "workbench.colorCustomizations": {
>          "background": "#020817",
>          "menubar.background": "#020817",
>          "menubar.menu": "#020817",
>          "activityBar.background": "#020817",
>          "terminal.background": "#020817",
>          "titleBar.inactiveBackground": "#020817",
>          "titleBar.activeBackground": "#020817",
>          "panel.background": "#020817",
>          "terminalCommandDecoration.defaultBackground": "#020817",
>          "sideBar.background": "#020817",
>          "sideBarSectionHeader.background": "#1E293B",
>          "editor.background": "#020817",
>          "editorGroup.emptyBackground": "#020817",
>          "statusBar.background": "#020817",
>          "editorGroupHeader.tabsBackground": "#020817",
>          "activityBar.border": "#020817",
>          "menu.border": "#1E293B",
>          "menu.separatorBackground": "#1E293B",
>          "sideBar.border": "#1E293B",
>          "tree.tableColumnsBorder": "#1E293B",
>          "tab.border": "#1E293B",
>          "statusBar.border": "#1E293B",
>          "panel.border": "#1E293B",
>          "menu.foreground": "#94A3B8",
>          "foreground": "#94A3B8",
>          "menubar.foreground": "#94A3B8",
>          "activityBar.foreground": "#F8FAFC",
>          "sideBarSectionHeader.foreground": "#F8FAFC",
>          "explorer.folderItem.foreground": "#1E293B",
>          "panelTitle.activeForeground": "#F8FAFC",
>          "list.focusForeground": "#F8FAFC",
>          "sideBar.foreground": "#94A3B8",
>          "statusBar.foreground": "#94A3B8",
>          "editor.foreground": "#F8FAFC",
>          "activityBar.inactiveForeground": "#94A3B8",
>          "explorer.fileItem.foreground": "#94A3B8",
>          "input.background": "#1E293B",
>          "dropdown.background": "#1E293B",
>          "button.background": "#3B82F6",
>          "button.hoverBackground": "#3B82F6",
>          "input.foreground": "#F8FAFC",
>          "button.foreground": "#0F172A",
>          "menubar.selectionBackground": "#1E293B",
>          "menu.selectionBackground": "#1E293B",
>          "menubar.selectionForeground": "#F8FAFC",
>          "menu.selectionForeground": "#F8FAFC",
>          "list.activeSelectionBackground": "#1E293B",
>          "list.activeSelectionForeground": "#F8FAFC",
>          "input.border": "#1E293B",
>          "inputOption.activeBorder": "#1D4ED8",
>          "focusBorder": "#1D4ED8",
>          "errorForeground": "#7F1D1D",
>          "editor.lineHighlightBackground": "#1E293B",
>          "editor.selectionBackground": "#1E293B",
>          "editorCursor.foreground": "#F8FAFC",
>          "editorIndentGuide.background1": "#1E293B",
>          "editorWhitespace.foreground": "#1E293B",
>          "list.focusBackground": "#1E293B",
>          "list.hoverBackground": "#1E293B",
>          "list.highlightForeground": "#3B82F6",
>          "explorer.fileItem.hoverForeground": "#F8FAFC",
>          "explorer.folderItem.hoverForeground": "#F8FAFC",
>          "tree.indentGuidesStroke": "#1E293B",
>          "tab.activeBackground": "#020817",
>          "tab.activeForeground": "#F8FAFC",
>          "tab.inactiveBackground": "#020817",
>          "tab.inactiveForeground": "#94A3B8",
>          "tab.activeBorder": "#020817",
>          "gitDecoration.deletedResourceForeground": "#7F1D1D",
>          "gitDecoration.conflictingResourceForeground": "#3B82F6",
>          "terminal.ansiBlack": "#020817",
>          "terminal.ansiBlue": "#3B82F6",
>          "terminal.ansiCyan": "#29c3a0",
>          "terminal.ansiGreen": "#29c3a0",
>          "terminal.ansiMagenta": "#3B82F6",
>          "terminal.ansiRed": "#7F1D1D",
>          "terminal.ansiWhite": "#F8FAFC",
>          "terminal.ansiYellow": "#d29922",
>          "scrollbarSlider.hoverBackground": "#3B82F6",
>          "scrollbarSlider.activeBackground": "#3B82F6",
>          "scrollbarSlider.background": "#3B82F620",
>          "activityBarBadge.background": "#3B82F6",
>          "activityBarBadge.foreground": "#F8FAFC",
>          "explorer.folderItem.selectedIconForeground": "#3B82F6",
>          "explorer.fileItem.conflictForeground": "#7F1D1D",
>          "explorer.fileItem.errorForeground": "#7F1D1D",
>          "explorer.fileItem.warningForeground": "#d29922",
>          "explorer.folderItem.iconForeground": "#F8FAFC",
>          "explorer.fileItem.selectedIconForeground": "#F8FAFC",
>          "explorer.fileItem.modifiedForeground": "#29c3a0",
>          "list.dropBackground": "#02081740",
>          "list.filterMatchBackground": "#02081720",
>          "list.inactiveSelectionBackground": "#1E293B40",
>          "list.hoverForeground": "#F8FAFC",
>          "statusBarItem.hoverBackground": "#1E293B",
>          "gitDecoration.submoduleResourceForeground": "#F8FAFC"
>        }
>     ```
> 
>      </details>
> 
> - **performance** & **workspace** → Both now accept any `settings.json` key-value pairs for organizational purposes. Values here will override matching settings in your workspace's `settings.json` file, while leaving other settings untouched.
>
> - **customizeLayout** → Required configuration object. Copy this into your config and adjust values as needed.
> 
>    <details closed><summary>customizeLayout config</summary>
>
>     ```json
>    "menubar.navigationControls": true,
>          "menubar.share": true,
>          "menubar.layoutControls": true,
>          "menubar.customizeLayout": true,
>          "primarySidebar.view": "Explorer",
>          "secondarySidebar.view": "skyler.ocrmnav",
>          "secondarySidebar.position": "left",
>          "primarySidebar.display": true,
>          "workbench.activityBar.visible": true,
>          "secondarySidebar.display": true,
>          "panel.display": false,
>          "panel.alignment": "center",
>          "panel.view": "output",
>          "modes.centeredLayout": false,
>          "modes.fullScreen": false,
>          "modes.zenMode": true
>     ```
> 
>      </details>
>
> 
> The previous version worked, but VS Code's inability to expose certain UI context values created frustrating limitations. This overhaul addresses those issues while adding powerful new features.
>
> Moving forward, the layout engine will minimize reliance on `customizeLayout`, using it only for features unavailable through other means. Most UI customization now happens through `settings.json` key-value pairs.
>
> I'll provide a concise guide covering the essentials, followed by examples of my personal UI customizations. VS Code's settings can be challenging to work with—even documentation can be inconsistent—but the improved layout engine makes the effort worthwhile.



## Configuration Approachs

#### The quick and dirty method
For simple theming and basic layout control, you only need to configure the `workbench.colorCustomizations` and / or `workspace` object. This serves as a central location for any VS Code setting values. Place your customizations in either the `workbench.colorCustomizations` or `workspace` sections (or both), and you're done.


#### For ALOT more granular control
This guide takes a modular approach: a brief overview followed by detailed exploration of VS Code's key-value pairs.

Each collapsible section includes multiple examples demonstrating different approaches—T-bone layouts, 4×4 grids, 1×1 configurations, and more. These examples are followed by real-world implementations with inline comments explaining the purpose of each setting.

I've structured each section to mirror either VS Code's native configuration patterns or the conventions already established by this extension, minimizing the learning curve.

> [!TIP]
> **For Beginners & Those New to Configuration Files**
>
> If manual configuration feels overwhelming, that's completely normal. Start small: create a few items in your main config and get comfortable with the basics before diving into more complex setups. Remember, even the most intricate configurations are just individual config items added one at a time.
>
> **Safe Configuration Workflow:**
> 
> 1. **Always backup first** - Copy your config file (or the entire extension folder) to a safe location before making changes
> 2. **Edit your backup copy** - Use this as your testing playground
> 3. **Test your changes** - Close VS Code, copy your edited config to the extension folder, then reopen VS Code
> 4. **You're protected** - If anything goes wrong, you have a working backup to restore
>
> This backup-first approach eliminates 100% of the risk. If you make a mistake or miss a few lines during copying, you can simply restore from your backup.
>
> **A Note on Learning from Source Code:**
> 
> Early in my coding journey, I spent considerable time exploring node_modules. While most developers will tell you never to modify dependencies (and they're right for production code), there's immense learning value in experimenting with copied source code.
>
> By working with copies of libraries—modifying them, extracting specific functionality, or adapting features from older versions—I developed crucial skills that most developers lack: the ability to navigate and understand others' code quickly.
> 
> Reading other developers' code teaches you new patterns and techniques you'd never discover on your own. You'll frequently encounter clever solutions that make you think "that's brilliant" and expand your own toolkit. While many developers avoid reading others' code because it's challenging (especially across multiple files with complex execution flows), mastering this skill:
>
> - Frees you from being locked into specific libraries or versions
> - Gives you access to an unlimited learning resource
> - Develops a rare skill that makes you valuable to employers
> - Accelerates your learning exponentially
>
> Even experienced developers who don't currently do this should consider it. The ability to dive into any codebase and understand what's happening is what took my own development skills to the next level.

## Example Configs

> [!NOTE] 
> Due to time constraints, I'll admit that in order to provide the descriptions for every single settings key:value pair they were fed through an ai prompt.
>
> At some point I will come back to go over all of them, redoing any that warrant the need to. But I'm currently going into the 7th hour since I started working, and the only thing I have done so far is this doc and there are other things that I NEED to do. Everything has a description as promised, and what is my half ass attempt at providing a settings.json resource and cheating all the descriptions through ai. As an end result, is a resource that you cannot find anywhere else in terms of depth and just how broad of a spectrum in different areas that the settings control. Not to mention going over settings, that no one else even mentions. I just remembered I still have the theme section, and because of the processes I use with my theme builder, I cannot have the ai provide this section. So I will finish that before moving onto other matters. 

<details closed><summary  style="font-size: 1.2em;">editorGrid - plex - 3 cols</summary>

```json
{
          "editorGrid": {
            "version": "plex",
          "columns": 3,
          "rows": 1,
          "groups": [
             { "slot": [ 0, 0 ], "active": ".vscode/ntrsync/10516_DevStack_todo.md", "pinned": true },
             { "slot": [ 1, 0 ], "active": "README.dev.md", "pinned": true },
             { "slot": [ 2, 0 ], "active": "package.dev.jsonc", "pinned": true, "fold": [ 1, 2 ]  }
         ],
         "files": [
            { "path": "src/helpers/master.ts", "slot": [ 1, 0 ], "pinned": true, "fold": [ 1, 2, 3 ] },
            { "path": "src/helpers/menus.ts", "slot": [ 1, 0 ], "pinned": true, "fold": [ 1, 2 ]  },
            { "path": "src/extension/navigatorView.ts", "slot": [ 1, 0 ], "pinned": true , "fold": [ 1, 2 ] },
            { "path": "src/helpers/modular-commands.ts", "slot": [ 1, 0 ], "pinned": true, "fold": [ 1, 2 ]  },
            { "path": "src/context.ts", "slot": [ 1, 0 ], "pinned": true, "fold": [ 1, 2 ]  },
            { "path": "src/extension.ts", "slot": [ 2, 0 ], "pinned": true , "fold": [ 1, 2 ] },
            { "path": "package.dev.jsonc", "slot": [ 2, 0 ], "pinned": true, "fold": [ 1, 2 ]  },
            { "path": "F:/DevStack/docs/LAYOUT.md", "slot": 2, "pinned": true },
            { "path": "F:/DevStack/docs/VFS2.md", "slot": 2, "pinned": true },
            { "path": "F:/DevStack/docs/VFS2.md", "slot": 2, "pinned": true },
            { "path": "C:/User/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/global-navigator-config.json", "slot": 2, "pinned": true },
            { "path": "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/project-configs/project-1744496862041-y866zpqtd9.json", "slot": [ 2, 0 ], "pinned": true }
          ]
          },
          }
```

</details>


<details closed><summary  style="font-size: 1.2em;">terminalGrid - plex - 2x2 Layout</summary>

```json
{
    "terminalGrid": {
        "layout": "2x2",
        "terminals": [
            { "name": "Frontend Dev", "cmd": "npm run dev", "color": "terminal.ansiCyan", "position": "top-left" },
            { "name": "Backend Dev", "cmd": "npm run server", "color": "terminal.ansiMagenta", "position": "top-right" },
            { "name": "Database", "cmd": "docker-compose up db", "color": "terminal.ansiGreen", "position": "bottom-left" },
            { "name": "Tests", "cmd": "npm run test:watch", "color": "terminal.ansiYellow", "position": "bottom-right" }
        ]
    }
}

```
</details>

<details closed style="font-size: 1.2em;"><summary>terminalGrid - plex - The "T-Bone" Layout</summary>

```json
{
    "terminalGrid": {
        "layout": "tbone",
        "terminals": [
            { "name": "Frontend", "cmd": "npm run dev", "position": "left" },
            { "name": "Backend", "cmd": "npm run server", "position": "right" },
            { "name": "Database", "cmd": "docker-compose up", "position": "bottom" }
        ]
    }
}
```

</details>

<details closed><summary  style="font-size: 1.2em;">editorGrid - classic - 3 cols</summary>

```json
{
     "editorGrid": {
            "orientation": 0,
              "version": "classic",
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
                "path": [
                  "src/extension.ts",
                  "src/helpers/master.ts",
                  "src/helpers/menus.ts",
                  "src/helpers/context.ts",
                  "src/extension/navigatorView.ts",
                  "src/helpers/itemsActionsMenu.ts",
                  "src/helpers/modular-commands.ts"
                ]
              },
              {
                "group": 3,
                "pinned": true,
                "path": [
                  "README.dev.md",
                  "package.dev.jsonc",
                  "F:/DevStack/docs/LAYOUT.md",
                  "F:/DevStack/docs/VFS2.md",
                  "F:/DevStack/docs/VFS.md",
                  "src/helpers/search.ts",
                  "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/project-configs/project-1744496862041-y866zpqtd9.json",
                  "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/global-navigator-config.json"
                ]
              }
            ]
          }
}
```


</details>

<details closed><summary  style="font-size: 1.2em;">terminalGrid - classic - 2 cols 2 rows</summary>

```json
{
"terminalGrid": {
  "orientation": 0, // Vertical main splits (Columns)
   "version": "classic",
  "groups": [
    { "id": "col-1", "size": 0.5 },
    { "id": "col-2", "size": 0.5 }
  ],
  "terminals": [
    {
      "name": "Top-Left (API)",
      "group": 1, 
      "cmd": "npm run start:api",
      "location": "editor",
      "priority": 1 // Engine renders this first in group
    },
    {
      "name": "Bottom-Left (DB)",
      "group": 1,
      "cmd": "docker logs -f db",
      "location": "editor",
      "split": "horizontal" // Forces the 2x2 look in col-1
    },
    {
      "name": "Top-Right (UI)",
      "group": 2,
      "cmd": "npm run start:ui",
      "location": "editor",
      "priority": 1
    },
    {
      "name": "Bottom-Right (Tests)",
      "group": 2,
      "cmd": "npm run test:watch",
      "location": "editor",
      "split": "horizontal" // Forces the 2x2 look in col-2
    }
  ]
}
}
``` 

</details>

<details closed><summary style="font-size: 1.2em;">4x4 Terminal Grid Contained Within A Single Editor Group</summary>

```json
"terminalGrid": {
  "layout": "grid",
  "columns": 2,
  "rows": 2,
  "gap": 1, // Optional: UI spacing between terminals
  "terminals": [
    {
      "name": "API",
      "position": [0, 0], // Top Left
      "cmd": "npm run dev:api"
    },
    {
      "name": "WORKER",
      "position": [1, 0], // Top Right
      "cmd": "npm run dev:worker"
    },
    {
      "name": "LOGS",
      "position": [0, 1], // Bottom Left
      "cmd": "tail -f api.log"
    },
    {
      "name": "DB_UI",
      "position": [1, 1], // Bottom Right
      "cmd": "prisma studio"
    }
  ]
}

```

</details>

<details closed><summary style="font-size: 1.2em;">Full Config Example</summary>

```json
 {
  "$schema": "./schemas/layout-config-schema.json", //  this is not required, its not currently work correctly right now due to the frequent changes I have been making, but this will work in the future
  "label": "DevStack Default", // required
  "path": "", // if you do not need a terminal group with several terminals, but wish to execute one command when the layout loads, you may place your powershell command here ie, pnpm run dev
  "type": "layout", // required, do not change
  "icon": "editor-layout", // not required, and you can also change this to whatever vscode icon value you would like
  "args": [ // none of the items in args is required unless you want to configure your layout, if you are looking to configure your layout the only requirement being customizeLayout in which you just need to copy that object your config and set the values as you see fit
    {
      "default": true, // not required, if you would like this layout to load when you open your workspace set this to true. Depending on where you save your config, if it is in a workspace folder the layout config now because workspace context aware and only loads that config in that workspace, granting you the option to create a config on a per workspace basis. If you would rather use one config for ALL workspaces, just place this object in one of your global folders, and it will load this layout no matter which workspace you open
      "keybindings": { // in this example I have just placed this extensions shortcut map to provide you with a reference in how to create each a shortcut. This does not COMPLETELY overwrite your current shortcuts, but if you already have a short cut using alt+d for example if you create a new shortcut using the same mapping, it will overwrite that map with the new one mapping, as the function filters by both the key and the command to avoid conflicts
        "ocrmnavigator.menu.devstack": "alt+d",
        "ocrmnavigator.menu.icons": "alt+i",
        "ocrmnavigator.menu.catalystUi": "alt+u",
        "ocrmnavigator.menu.snippets": "alt+s",
        "ocrmnavigator.region.insert": "alt+r",
        "ocrmnavigator.endregion.insert": "alt+e",
        "ocrmnavigator.region.wrap": "alt+w",
        "ocrmnavigator.devstack.site": "alt+q",
        "ocrmnavigator.clipboardMgr.history.show": "alt+h",
        "ocrmnavigator.bookmarks.show": "alt+b",
        "ocrmnavigator.menu.github": "alt+g",
        "ocrmnavigator.project.pkg.open": "alt+p",
        "ocrmnavigator.project.readme.open": "alt+m"
      },
      "autorun": [ // adopting how this extension is already configured with executing items, you can literally just copy over and config item you want into this section and add the new value runPolicy
        {
          "runPolicy": "once", 
          "label": "test",
          "path": "pnpm run test once",
          "type": "powershellCommand"
        },
        {
          "runPolicy": "onLoad", 
          "label": "test",
          "path": "pnpm run test onLoad",
          "type": "powershellCommand"
        },
        {
          "runPolicy": "onReload",
          "label": "test",
          "path": "pnpm run test onReload",
          "type": "powershellCommand"
        }
      ],
      "onClose": [ // same as above, minus the new value
        {
          "label": "clean",
          "path": "clean",
          "type": "chain"
        }
      ],
      "terminalGrid": { // the old terminal grid, didn't offer any options other than opening a bunch of terminals. Now it offers the same ability that you can find in terminal plex applications you use in linux and configure your terminal layout in any fashion that tickles your fancy. Whether it be 2x2, a single terminal in an editor group, tbone layout, 2 terminals stacked ontop of one another... literally whatever you want. This example, configures the terminals in 2x2 grid, within an editor group
        "columns": 2,
        "rows": 2,
        "location": "editor",
        "terminals": [
          {
            "name": "API Server",
            "slot": [
              0,
              0
            ],
            "cmd": "npm run dev",
            "active": true,
            "color": "terminal.ansiCyan"
          },
          {
            "name": "Build Watcher",
            "slot": [
              0,
              0
            ],
            "cmd": "npm run watch"
          }, 
          {
            "name": "Database",
            "slot": [
              1,
              0
            ],
            "cmd": "docker-compose up"
          },
          {
            "name": "Unit Tests",
            "slot": [
              0,
              1
            ],
            "cmd": "npm run test:watch"
          },
          {
            "name": "System Logs",
            "slot": [
              1,
              1
            ],
            "cmd": "tail -f storage/logs/laravel.log"
          }
        ]
      },
      "git": { // when the layout loads, you can configure it to start off in a given branch, and have it execute git commands on load, and on close. This example, ensures that it opens on the main branch, pulls so that before I even start working I have the most up to date version of the repo, and then on close it adds all changes, commmits them and pushing them so as to never forget another push ever again, ensuring that in the case if my computer every fails, I know at the very least this repo will be up to date no matter what
        "branch": "main",
        "onLoad": [
          {
            "label": "pull on workspace load",
            "path": "git pull",
            "type": "powershellCommand"
          }
        ],
        "onClose": [
          {
            "label": "push changes on close",
            "path": "git add * && git commit && git push",
            "type": "powershellCommand"
          }
        ]
      },
      "editorGrid": { // while the previous version did offer a lot in terms of configuring the editor ui. It is now a lot more simple due to removing the math portion of the setup, in its place we are now just declaring the amount of columns and rows you would like to have displayed in your ui with your editors. The following example creates 3 groups with the first being the smallest, and pins a number of files and ensures a specific file is open when it finishes. This new set up not only allows you to control how the ui is set up on a column and row aspect but also the groups sizing in relation to one another
    "columns": 3,
    "rows": 1,
    "groups": [
        { "slot": [0, 0], "size": 0.2, "active": ".vscode/ntrsync/10516_DevStack_todo.md" },
        { "slot": [1, 0], "size": 0.45, "active": "src/extension.ts" },
        { "slot": [2, 0], "size": 0.45, "active": "README.dev.md" }
    ],
    "files": [
        {
            "path": ".vscode/ntrsync/10516_DevStack_todo.md",
            "slot": [0, 0],
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
            "slot": [1, 0],
            "pinned": true
        },
        {
            "path": [
                "README.dev.md",
                "package.dev.jsonc",
                "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/global-navigator-config.json",
                "F:/devstackBackUp/global-navigator-config.json",
                "src/helpers/workspace.ts",
                "F:/devstackBackUp/project-configs/project-1744496862041-y866zpqtd9.json",
                "F:/devstackBackUp/project-configs/project-1757010936487-i30yr98a4p7.json"
            ],
            "slot": [2, 0],
            "pinned": true
        }
      ]
    },
       "extensions": {
        "enable": [
          "esbenp.prettier-vscode",
          "dbaeumer.vscode-eslint"
        ],
        "disable": [
          "github.copilot",
          "ms-vscode.vscode-typescript-next"
        ],
        "install": [
          "skyler.ocrmnav@1.2.3"
        ]
      },
      "performance": { // this object you may paste any settings you wish, or if you would rather host ALL of your settings in one place, you may omit this object and just use workspace but if you would like to have atleast some organization to your settings, placing all performance related key:value pairs here
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
        "typescript.validate.enable": true,
        "workbench.editor.enablePreview": false
      },
      "customizeLayout": { // as previously stated, this being a requirement. This is due to the fact that the items that you see in this object do not have a settings.json key:value pair counterpart and can only be triggered via the customizeLayout command function. You are free to use any available value with each key 
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
      "workspace": { // key:value settings.json, you may place any key in you as you wish as the function walks over each, writing them to yoor .vscode/settings.json file. I truly wish vscode was developed differently because I have made the layout engine a dozen times over with trying to manipulate the ui in all manner of ways. 
      // I knew when I started, that this was an option, but everywhere you read up on configuring the ui they always state to use other methods that are just unreliable with ui manipulation due to not having access to its current state. As most of the functions that manipulate the ui... are toggles. There are a couple of areas, in which I can garauntee the value, unfortuantly the other 90% of values you simply cannot. 
      // For example, there are a couple of toggles that force the ui no matter what because that toggle, uses vscodes context in order to see what its current state is ie, if you wish to use zen mode like I do, zen mode virtually toggles off every ui component aside from your editors. Because of that, from a progmatic aspect, I now know with 100% certainty what the values are for the sidebar, secondary sidebar, statusbar, panel and so on. 
      // With that knowledge and how you would like your layout to look, I can now safely toggle those values. When my layout loads, once it enters zen mode, it then toggles back the sidebar, secondary sidebar, activity bar and status bar so that they are all displaying in zen mode. 
      // With saying that, the layout engine assumes you are in default configuration at load time: 
      // - primary sidebar open
      // - activity bar open
      // - status bar open
      // - panel open 
      // - and due to copilot the secondary sidebar open
      // - the editor group doesn't effect the layout engine because it's first function that runs is to close all terminals and editor groups, allowing it to start with a clean state
      // For 99% of you this will be the default state in which vscode opens, with the odd power user being left out. Even for the odd user that is left out, it is a very easy fix. Which means, when you load vscode you are 100% good to go. If you plan on activating a new layout mid session, just ensure that the ui is in that default state before clicking on that layout item. 
      // Personally, I hate how this relies on the user to ensure the current state of the ui because whenever I code any function I try to remove as much as I can from the user having to do any one thing, BUT the cost is outweighed by a large margin in respect to what you gain out of its functionality. Yes, you have to ensure your panel is open before and if it isn't it can either be 2 clicks or a shortcut and a click to open, so 2 user actions. Whereas, when the engine is activated it controls a series of events that would take you an hour or more if done manually. 
      // Pretty huge benefit over the cost of doing business, and this is the only time I have ever been ok with adding a step for the user to do something in order for a function to work. 
      // In terms of THIS config, if I were to manually do this every time... it would be hours each time as my config has been continously modified over the span of years. Previously I made the ui to serve all purposes and sitations, but now I can have a different ui set up for each and taylor the ui to fit my current coding needs which that was something I refused to do due to the cost of time in setup. All in all, before this engine was created I was happy enough to no longer look for an alternative to vscode. The layout engine, was definitely the missing puzzle piece I did not know was missing to really get the most out of it and be happy with my working enviroment, as imo this feature should be included in vscode as a default, because I know there are power users that work at microsoft who would love this level of control and not just power users but any user that has created a theme for vscode, so why is it not provided as a default?
      // If your someone who would like to learn more about key:value pairs in one place instead of scouring page after page of blogs and docs, I will go over that in the next section as promised.
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
        "workbench.editor.limit.enabled": true,
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
        "ocrmnavigator.devstack.site.snippets": true,
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
        "ocrmnavigator.devstack.site.colorWheel": true,
        "ocrmnavigator.lucideIcons": true,
        "ocrmnavigator.share": true,
        "ocrmnavigator.url": true,
        "ocrmnavigator.project.json.comments.remove": true,
        "ocrmnavigator.con": true,
        "ocrmnavigator.project.file.comments.remove": true,
        "ocrmnavigator.unusedFunctions": true,
        "ocrmnavigator.viewers": true,
        "ocrmnavigator.uiDashboard": true,
        "ocrmnavigator.devStackFunctions": true,
        "ocrmnavigator.leftOffNote.open": true,
        "ocrmnavigator.devstack.site.md.render": true,
        "ocrmnavigator.project.index.smart.create": true,
        "ocrmnavigator.devstack.site.tailwindConverter": true,
        "ocrmnavigator.remix.project2agnostic.convert": true,
        "ocrmnavigator.vfs.concurrent.execute": true,
        "ocrmnavigator.vfs.chain.execute": true
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
}
```


</details>

<details closed><summary style="font-size: 1.2em;">Full Config Example End Result</summary>

![Search Feature](https://raw.githubusercontent.com/8an3/dev-notes/main/layout/endResult.png)

</details>

### Showcasing different layouts
- 2x2 plex terminal group, 3x2 plex editor group, zen mode + all bars re-activated - [video](https://youtu.be/QGgaICeirqU)
- 3x1 classic editor group, zen mode + all bars re-activated - [video](https://youtu.be/QGgaICeirqU)


## settings.json key:value pairs

**Configuration Guide Structure**

This guide is divided into two main sections:

1. **Settings Overview** - Comprehensive walkthrough of available configuration options
2. **Theme Builder** - A streamlined approach to creating consistent, professional themes in minutes instead of hours

I've also developed a theme builder tool that dramatically simplifies what has traditionally been an unnecessarily complicated process.

**About This Resource**

While I don't claim to cover every available setting (VS Code has an extensive configuration surface), I'll walk through the majority of commonly used options that I've thoroughly tested and understand.

**Why This Guide Exists**

When I first explored VS Code customization, I struggled to find comprehensive resources. Most guides cover a handful of settings, leaving you to piece together information from scattered blog posts, incomplete documentation, and trial-and-error experimentation.

My own research process included manually walking through the `settings.json` file—triggering IntelliSense on new lines and activating each setting individually to see what it controlled. This took hours, but uncovered valuable customization options that aren't well-documented elsewhere.

**A Real Example:**

The default syntax highlighting in editors and gutters can be visually overwhelming. I couldn't find any resources explaining how to customize this. Eventually, I found a single mention of the parent setting category, which led me to manually test each related key until I achieved the clean interface I wanted.

This guide aims to save you from that same tedious process by consolidating what I've learned into a single, practical resource.

<details closed><summary  style="font-size: 1.4em;  color: #1447e6;">settings.json</summary>

This section covers settings from both the configuration file and my global settings, organized by parent key for easy reference.

Due to the extensive amount of content to document, this is a work in progress. Any missing descriptions will be added in future updates.


<details closed><summary  style="font-size: 1.2em;">performance</summary>

This object within the config, is either going to be LARGE or small for you, depending on a couple of factors. 

The first being extensions, they play a role whenever I look at changing the performance when I notice a considerable dip in how my instance performs. AI engines have a huge crux attached to them whenever you install one, in terms of background processes. In which I always tend to turn them off to the point now that if I were to download a new extension that features ai I immediatly open the settings to disable almost everything to the point that the only way that the ai can function is through a manually triggered event.

Almost forgot about this because my vscode expereience is vastly different from the average user. At some point the average user will experience a dip in performance due to extensions. I know everyone will, purely based off of the fact on just how many blog posts there are in troubleshooting this area. 

Unfortuantly, I have not read a single blog post that was correct in the information that they were providing in this dept. When I first started to try to solve these issues, I took their information as gospel and did exactly as what they outlined. Over time and learning more about vscode itself when I started to create extensions, that was when I learned exactly what the issues were due to. The dip in performance you are experiencing is NOT because of just how many extensions you are installng, it is due to how the extensions were coded couple with how vscode itself was coded. 

VSCode underlying code is built on electron and if you have ever looked at the current options to build an app in windows you will VERY quickly get told, repeatedly, that electron uses the most and in huge amounts of resources in windows in comparison to literally every other offering. 

So... we aren't starting off on the best foot, it's like starting a marathon when you weigh 350 lbs vs 125 lbs. 

NOW, this issue compounds when you have devs, who are trying to be smart and look cool, by offering features in extensions that have a ton of background processes running and doing god knows what. Multiplied by the 10-15 extensions you have running at any given time the second you start vscode. Meanwhile, all those extensions, I garauntee it, not only have the same base functions running as background process which all produce a base line result in needed to function the way they do, which from an effeciency aspect is horrible considering if those same amount of extensions were built as one, instead of the same 15 background processes, it could one but I digress. To make matters worse, the rest of their code probably isn't executing in the best ways possible, because they created it they looked at it as I have one feature so performance probably didn't even enter their thought process before publishing that extension. 

Up to this point in summary, we have a application that was built on the wrong platform, then we have extensions that run a bunch of shit in the background, to be completely honest probably don't even need to be running if they were built right, those same extensions were built without the thought process of performance in mind before they were done. And it doesn't end here... 

VSCode as a default gets shipped with some features, obviously. 

Github being one of the features, if you work in larger workspaces turning this off will net a huge return in performance. As you do not need to constantly be checking to see exactly what folder, file, files line number and so on is different locally compared to your repo. 

Next there are the language engines that are CONSTANTLY running, and get triggered with every key stroke and file opening event. For example, my package.json and readme.md files within this project suffered MASSIVELY from these background processes. Before I found the settings needed to optimize vscode in this regard, modfying these two files became impossible. In my package.json, I couldn't fold any region or object having to wait 1-3 mins, actually, before I could fold anything anytime I made a single change. Scrolling through my package.json was a pain due to stuttering. Now I imagine, the issues I experienced with my package.json will be very few and far between in terms of your experience because of the file size. Currently sitting at 37,000+ lines, I wouldn't be surprised if there is less than 1% that will get to that size.

My readme.md file was suffering so horribly from performance issues, I could no longer use vscode to edit that file. Pressing delete, and actually having the event register in the editor, was more than 60 seconds. Any other keystroke, was between 15-30 secs depending on what was going on at that time. Which you can imagine was such a fucking pain. Thankfully, my current config has fixed all issues that I have experienced up to date albeit it was a very painstaking process in order to figure out and in the end it was a stroke of luck to finally be able to edit markdown docs in the editor again. 

And it was such a pain because, no one... and I mean no one, goes over this topic in any form... that is correct with the information they provide... microsoft doesn't even go over this topic and how to optimize vscode from a performance aspect. To get to the solution, it was literlly walking through every single setting, activating it by setting a value, then testing it to see if it made a difference, then going back and moving on to the next one. I wish you could just turn the engines off, but unfortuantly you can't disable all of them.

The second you may never even experience, because it comes down to workspace sizing we touched on it earlier but I'll go into it in more depth. If you never code a larger project, you will never experience huge stutters where vscode is rendered unsuable to the point where you cannot even click on anything while the background processes play catch up when opening certain files. This extension alone was what prompted the feature `performance switch`. Thankfully to date I have tuned my settings enough where I don't currently have a reason to use it as much as I have, but as this continues to grow I will probably have to resort to it again because the settings will only go so far.

If you do code in larger projects, I don't know the exact file count but lets say more than 2500+. This count does NOT include any files found within node_modules, build output folders and such. Stating that number, I'm counting the files that you would actually would have touched in some form or fashion rather it be manually or automated through your own custom scripts. I know it is less dependant on line and word count because:
- while this extension hosts all the same code, practically, that my components ui library hosts x2 ( because there more than one function that deals with that library and unfortuantly do not use the same obj ) 
- ONTOP of that, all the other files that are used for the rest of the extension 
- PLUS also hosting all the functions code to insert shadcn components
- I have 2 icon libraries worth of data, because I haven't cleaned out the first that I removed functionlity for when I got sick and tired of that library and created my own
- there are 2 different version of referencing vscode commands, but one of the lists is generated by scanning your vscode instance and presenting that list ensuring, without my help, you always get an up to date list no matter how many version updates vscode gets, the other list was manually created and will consist of 3500+ line items
- you already know the last one, hosting all the code for 125+ extensions including documentation

To say that vsce prompts me with warning after warning due to extension size would be an understatement because, I remebmer VERY early in this extensions developemnt see that prompt. It runs better then so many other extensions that just host one feature, so I don't know what it's problem is.
Anyways, this workspace doesn't suffer from this issue while my components library does. It has a TON more individual files, but this extensions code has more lines of code. Which indidcates vscode doesn't have an issue with total lines per file, unless its a json file with 35,000+ lines, but it starts to have an issue based on total file count due to opening every single file and scanning it for god knows what bullshit its trying to figure out.

Now we can negate these performance losses in several ways, because if it weren't for these optimizations, YOU WILL SEE THAT PERFORMANCE TANK way before 2500+ files. 

BUT obviously there is a trade off, and it comes down to what can you live without in terms of features. Personally, I value performance at the number 1 or 2 spot. I'll go over every single value once we get to the list but as for a quick breakdown based off of memory:
- you can live without your github repo, constantly updating on whether your local repo is dirty or not and by how many files and lines of code its dirty by, IF this is a concern of yours... just use the layout engine to push data at workspace close. At which point, if you also configure it to pull at workspace initialization... you will never have to worry or do anything in the git explorer pane ever again, essentialy I will be 'hiding' that tab in the activity bar moving forward to have it completely removed from my thought process. Hopefully, the next conversation with a dev in regards to git, I'll just respond, 'huh, wtf are you doing in git? I haven't touched that in years. Oh, your just a muggle who has to manually go and work that...' 
- disabling codelens
- disabling intellisense
- disabling lightbulb
- disabling auto import helpers ( I haven't had the best luck in creating a replacement for vscodes implementation purely because of performance reasons. With the layout engine out of the way, this will get back on the list of things to do. When its available, you hammer out your code and forget about importing anything, once that file is done trigger the function ( that way there isn't some stupid background process running and eating up unnecessary resources, I understand why they shipped the product with this as a default feature. But what I don't understand is, why didn't they ship a manually triggered version of it ), and that function will auto create all of your import statements at the top of the file )
- disabling validation and or disabling other unimportant baseline features and their engines
- in terms of using the search features within vscode, we will go over this in detail, setting a baseline in what is exlcuded from your results... will produce a massivaly more effecient searching event. Not only will the events duration decrese drastically, but if you don't set that baseline you can see a performance drop in other areas of vscode if you were to just let that search run while you continue to code 
- it truly boggles my mind why vscode does this, I think I found a solution for this but theres no way to actually test this though but anwyways disabling the auto preview of markdown docs. WHENEVER you are in a markdown document... vscode, whether or not you have the md render preview tab open beside it or not, will alwalys be rendering markdown content as if that preview tab was open... whyyy... that's such a stupid thing to fuck up on. Yes, for small markdown docs this won't even enter the thought process of a dev to consider this to be an issue, or even become one. For larger projects or larger markdown files, this will be an issue especially if you do not even have the preview open
- inline suggests of any kind and all types
- almost forgot this one, excluding files from watcher
- inline with the previous, but a lot more agressive to the point where I imagine less than 1% of devs will use it, files.exclude which exludes whatever values you place in here in its entirety to the point where it will not even display in the explorer pane when you are viewing files and folders

Now you may have noticed, that I didn't mention things like, disabling updates, disabling auto updating extensions and so on. This is because, these are events that trigger once and are done. These types of features, you don't have to worry about UNLESS you are experiencing massive initial load times. At which point, disable these types of features. And before you even think of it, yes... I HAVE found the setting to turn off the annoying toasts asking you if you would like recomendations from the extensions or projects creator whenever you open a project, I don't know why those bother me so much.

If you reach this point, congratulations! Seriously, now you have learned something that over 90% of devs do not know and who continue to provide advice even though, not one thing they stated was correct. Whenever I say things like this, I'm not putting down anyone in any way, everyone has different learning journeys and experiences based off of ones motivation and there are all manners of people at every different level. But whenever I see someone do something or learn something that the majority does not, I want you to be aware of that so you can feel good about it. But I would be lying if I said I wasn't annoyed and mad spending hours and hours researching, ONLY to find out that I couldn't trust 99% of the blogs that mention vscode, lol. That's the only reason I'm spending so much time on this, atleast NOW there is one source out there that is correct and will take the time to go over information, no one else will. 

<details closed><summary style="font-size: 1.2em;">How it is that this extension features the same level of functionlity of more than 100+ functions?</summary>

At this point, I wouldn't be surprised if you were asking yourself just how it is that this extension features the same level of functionlity of more than 100+ functions? After reading the above text, you may have noticed a theme in the occurance of issues that every user will face with vscode, as I have yet to meet a single user that has not installed more than 10 extensions. Some users will hit that performance wall earlier than others, in some instances I've seen it happen in the single digits. 

I've said this before, and I have no problem or shame admitting this, there were a couple of events that took place that were just shear luck. If it wasn't for those events, this extension would be no where near where it is today. Other then those events, and because I experienced these same performance issues that we talked about. Whenever there was a feature or function that I wanted, my thought process going into it was different then the average dev. I actively tried to NOT introduce any background processes into the code.

The only background processes that are currently within the code, across the entire codebase, only run once, these actual functions cannot be triggered again or by any other feature, and once they receive the values they are looking for, they're done by placing them into a extension wide context. Going off of memory alone,
- initializes the main part of the extension and all the values that are needed throughout each function across the entire codebase which include:
  - extension settings configured by the user
  - it grabs the value of the current logged in user, typcally the same email as github
  - does a couple of minor checks to the website, just comparing the email to see if you currently subscribing
  - it intializes the snippets, since these are workspace context
  - combines your workspace config and your global config
  - and in short, intializes a couple of other classes used for hovering and others
The only functions that are `active`, are reaction based. Which means, they aren't scanning anything they just sit there and wait for an event to trigger them. And I try to limit these to the absolute bare minimum.

With saying, it was only recently that, virtually, the entire extension was re-developed. Before that, the performance was still in a state of `exceeds expectiations`. Then when I decided to bite the bullet and strap in to redo the code, it was not only a complete redesign, but also covered a large area. Where as, the new code effects every single aspect of the extension. The performance increase... is insane. I never thought it would be able to get to its current level, even if it had half the features. 

The reason that warranted the redesign was, this entire extension was built one feature at a time. Let's be real, if anyone told you they were gonna build this as an extension, you would respond with, `What have you been smoking today?`. Because it was built piece by piece, the code was not effecient when you take a step back and look at it. Most features were requesting the same new values, each time a feature was used. There was no sharing of any kind or in any form between features. There was no prioritizaion of when functions loaded, not to mention every single feature, aside from helper functions, honest to god, was entirely in the extension.ts file. For the LONGEST time, I was paranoid about moving the features into their own files because when I wasn't as experienced whenever I did move a feature, it broke.

While it still performed great, in comparison to others, it got to a point where I just couldn't take it anymore in terms of performance. Initial loading time, I know I'm probably being anal about this, was just too long. Before I even started, I already knew I had one massive hurdle that could not be solved, which is because the partnering site is hosted on vercel ( Don't get me wrong or take this the wrong way when I say this one critisism about vercel, because after trying 10's of platforms. I truly beleive vercel to be one of the best, in virtually every aspect. I do not see a day, where I would use another provider in its place in terms of hosting a site. ) if the site isn't used for 15 minutes I think, the server goes into hibernation mode, and it takes a WHILE for it to come back online. With that one request to the site, it slows the entire intialization down. 

I solved it by prioritzing what loaded when, when the extension gets activated. Ever since I learned about this, I try to employ every chance I get. It's kinda like a cheat that googles snapchat used for uploading. From the user perspective, whenever you uploaded a photo, and inserted the caption and filled in the other fields, once the user pressed done or upload, the progress bar would just shoot across the page really quickly. While at first glance, they had upload times that... couldn't even be imagined by their competition, that's how much faster they were. What the user didn't see though, was as soon as you selected the photo to upload, before the user even went to type in a caption it was already uploading the picture to the database. By the time the user was done with the caption, in reality, the upload process was already done on the back end. When the user clicked done, the only data being transfered, was text data at that point. If the user canceled or backed out, they just deleted the picture off of the server.

Trying to emulate the same result, because the likelyhood of you clicking on a file tree item within the first 5 secs of it loading is so low that, no user will be clicking on it that quickly when vscode loads as there is a 1000 other things to click on in the ui. When the file tree loads in the sidebar it isn't entirely loaded to the point where it is actually in a useable state. You can even test this, if you were to click on a file tree item within the first 3-4 secs of it loading, it won't actually work. But if you didn't know this, you would just think it loaded extremely fast. While the other 13 extensions you have with one feature each, are bogging your system down.

As far as the redesign goes, that's the only smoke show as far as how it works with the code. All the other areas that were re-created were from the ground up and from an entirely new perspective. Everything in the redesign is no longer built with the idea of adding a new feature, instead the thought process was how can we code it in a way where every feature moving forward as well as all of its current features work as one in harmony instead of a `last man standing` basis. I also looked at how much can be removed from everything, to be replaced by the one function to rule them all.

Terminals: this was a fucking disaster when looking at it from this perspective. As each and every single instance a termnial was used... it was creating a brand new terminal. Not only did making one terminal engine, class, or whatever you want to name it, streamline all the terminals used through out the extension. It opened up the door for new functionality, like the layout engines idea was derived during the making of the terminal engine, giving user the ability to configure WHERE terminals actually open, and the list goes on and on. The most noticeable difference is, now whenever you click on several functions over a period of time, they will continue to use the same terminal over and over. Coupled with, a feature that no one else even has the chance to offer. With starting dev servers, because all the terminals are created through a single source, whenever you click on start dev server within the file tree, it first checks to see if there is a terminal instance already open, if it is and is currently running, it checks to see if it is running the same dev server commmand. If it is, it progmatically sends `ctrl + c` through to the terminal, proceeded by starting the new dev server. If there is a dev server already, but isn't the same, it then creates a new terminal and running the server command, so as to not bottle neck users who need more than one dev server running at any one time.

VFS provider: Before now, each item type was indivdually coded which was a pain, because it had to be coded in several spots and if any one aspect of the code was off by one in any of the spots, it wouldn't work. All of that was removed, in place there is one single `item` being created in the code base, which ultimately allows for a lot quicker prototyping of new items and testing of new items as well, as there is nothing really to do, virtually. A couple of items are now auto generated, to npm scripts, tasks, snippets... I know theres atleast one more... ya, in your settings folder, all of your currently available settings that are in your workspace file are also auto generated. Which removes the work load of you creating them. Especially when it comes to snippets, I'm always looking to improve that ux, since my first experience with them was so horrible. Another feature that, like lets be real, is unusable till you reach a certain level of knowledge in coding. 

I remember wanting to use that feature, trying it for hours, getting frustrated and just dropping it, not to touch it again for MONTHS. Which is why this extension has the same, probably higher, feature parity as enterprise / paid solutions. If you look at it purely from a ux perspective, no other snippet related feature / extension / app even comes close. I went from, creating a snippet... once every 5 minutes if I was lucky. To now being able to create the snippet and its config item, in under 12 secs from start to finish. Not to mention all the other new feautures that were recently added.

Feature / function execution: In its previous version, every feature executed its own items, in their own ways. From a maintainable view, is horrendous due to them being located all over the place. Now, a class was created specifically for that. To be honest, a version of that class has existed for a long time now, but was never really used due to just how far and wide spread all the functionality was. When you think about it, it is literally the same as coding 100+ individual extensions, in every aspect. To the point where I strived to create features, making the ux so intuitive and simple and coding it in a way where anyone who uses it, would get it. So as to not having to write long docs... like this one. The ONLY reason I'm spending the time on this... is because there is no other. I know because when I was experiencing these issues, the resources I did find, weren't that great, most blogs were a carbon copy of eachother stating the same things over and over again, and microsfts docs are so shit and because I was pretty new to coding, I could NOT make sense of them, not a single fucking thing made sense when I read those docs. Another great feature provided by microsoft that requires a certian level of experience in order to use. And I'm also the type of person to go out of my way to help people, despite the fact that, even to this day, this extension is built for the sole use of my own and it will continue to do so. The only reason I have put the effort into the other sections of the docs, was for my personal use only. The amount of times, I finished coding a feature and then go to the docs to create the readme section, only to learn that... I added last week. Or the amount of times, I use my own docs because I haven't used a feature for 2-3 months and forget how it works, lol, there are THAT many features in this extension.

You can thank claude for the improved docs, seriously. As this extension becomes more rediculous, and when I do use ai to help with certain parts of it and help me code more effeciently. There has been so many occasions, where it freaks out, shocked that the extension does what I state when prompting it to code a part of a feature in order for the new feature to fit in. Each time it asks, what else does the extension do, at which point it freaks out even more. Telling me that I'm not selling it enough, or why I'm not trying to go after users, and so on. 

Concurrent / chain: Chain hasn't really seen an update for a LONG time now. As each item type works flawlessly with it, and in my configs it is the most used item type. Concurrent on the other hand, just got ANOTHER redesign with the others, at the same time it also received new features. If you have a concurrent command that contains both powershell and bash commands, no matter how much you have of either type, it only opens two instances. One for powershell and the second for wsl debian, and all of the commands pipe through their respective instances while at the same time you have the ability to interact with each instance. If you were to run 10 dev servers in each, each dev server will output in its own color. If you were to press `ctrl+x`, it would send that kill command to all of its child instances, killing each dev server properly.

All in all, it was NOT a small task... and I'm still dealing with it even today. Take this doc for example, if it wasn't for that update this would have never got added. The end result, a much better code base to continue adding features all the while, you the user, experiences a much faster extension to work with. And don't worry, I am not even considering stopping in terms of adding features, or even updating the ones it already has. As I am always improving the ux, and due to the reasons why I even started coding, that will always be at the forefront of my focus, because I too use this extension. So much so that, the primary sidebar, is now on the right side and the extension occupies the left sidebar now. It gets that much more use, and honestly if microsoft wanted to steal and add it or most of it as a default, I wouldn't even be mad I would just say something along the lines of, about time... only took you 10 years. EVEN today I added a feature, in which I'm asking myself, how is this not a default feature since you already have and use the same functionality in other places in vscode. The ux of the new search editor I just added... my god, I can't wait to try it after I'm done this because I see myself using parts of it so much and will 100% replace all search functionality that vscode currently provides. Speaking of which, I truly hope you enjoyed learning about what we went over, and use this knowledge at some point in your future but due to the amount of things gone over, I would suggest re reading it again in the future. This is a self improvement tactic, that I only ever see the very best do, no matter the field that they are in. I too employed this tactic for years when I was in sales, I'm not contributing this one thing to my success in sales because, even at risk of sounding like an asshole douchebag, I was literally the best no matter where I work, or what field I was selling, even if I had no idea what it actually was I was selling. The reason being is that, the next time you read this, you yourself will be a different person. When you re-read it, you will pick up on things that you either missed the first time, or you will obsorb and interpret things different which will give you a whole new perspective when you take in what you are reading. Because there are parts of this doc, that honestly took my coding game from 4 and launching it past 10. I've even had one dev, yell at me telling me that I'm a liar for almost an hour, when I responded to the question of how long I've been programming for, lol. 

</details>


> [!TIP]
> To help you work with the global and workspace settings files, there are 2 shortcuts in the devstack quick pick menu. Whenever clicked it will open them in your current editor.
>
> To take it a step further, I have also placed shortcuts for your global devstack config AND your active workspaces config. It is on the to do list, but there will ALSO be an option when creating config items, to create a file type item that will direct you to that workspaces config file. Allowing you to enter each workspace, and create an item based off of that workspaces config file.
>
> I have thought about, instead of only creating that object based off of the current active workspace, but to provide a list of options. The only issue I see with the second option is that, in order to provide a human readable list, the function would first have to go into each workspace, grab the id from the .vscode folder and then at the same time also go into your package.json and grabbing that projects name so that you know why option is refrencing what project, performance wise that may not end up doing well. The ssecond issue is, while I store all of my workspaces in one folder I know not every dev does that, so unless I code it so you choose a folder to scan it probably won't materialize.

```json
{
  // ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★
  // placing this first so as to not forget about it, because it is worth mentioning as it may or may not, depending on loving or hating it, change your experience when using vscode. 
  // To be honest, and imo, it is a setting that is only viable for use with the layout engine or an extension with similar features. Because to get the most out of it, you have be pinning commonly used files, by not adopting the process of pinning files, setting this to true is just way too agressive for users.
  // BUT, if you properly set out a list of files to open and pin in your editor groups, this one feature is so awesome. 
  // It cleaned up a part of my workflow that I didn't even know there were options to do just that.
  // what it does: any file that is not currently being actively viewed, or pinned... closes. 
  // ie, you have been coding for an hour and 15 minutes and just below your menubar among your pinnned files you have open, you have 5-15 other files open but dirty or in other words, not saved. If you were to trigger save all, those same 5-15 files would automatically close once they are saved. Which is awesome because now, you no longer have the menial cleaning task of going through all your open tabs and individually closing them, every 2-3 hours or if you don't do it for the day or depending on what exactly you are editing that day, you may have more than 100 tabs to go through.
  "workbench.editor.enablePreview": true,
  // ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★
  "css.validate": false, // Disables CSS validation in *.css files
  "diffEditor.codeLens": false, // Hides CodeLens information in diff editors
  "debug.openDebug": "neverOpen", // Prevents debug view from automatically opening
  "debug.toolBarLocation": "hidden", // Hides the debug toolbar
  "debug.showInStatusBar": "never", // Removes debug status from the status bar
  "editor.inlineSuggest.enabled": false, // Disables inline suggestion features (like Copilot inline suggestions)
  "editor.inlayHints.enabled": "off", // Turns off inlay hints (inline type annotations, parameter names, etc.)
  "editor.parameterHints.enabled": false, // Disables parameter hints popup when typing function calls
  "editor.suggestOnTriggerCharacters": false, // Prevents suggestion popup when typing trigger characters (like ".")
  "editor.acceptSuggestionOnEnter": "off", // Disables accepting suggestions with Enter key
  "editor.acceptSuggestionOnCommitCharacter": false, // Prevents accepting suggestions when typing commit characters
  "editor.wordBasedSuggestions": "off", // Disables word-based suggestions from open files
  "editor.formatOnType": false, // Disables automatic formatting while typing
  "editor.formatOnPaste": false, // Disables automatic formatting when pasting code
  "editor.formatOnSave": false, // Disables automatic formatting when saving files
  "editor.semanticHighlighting.enabled": true, // Enables semantic syntax highlighting based on language server
  "editor.occurrencesHighlight": "off", // Disables highlighting of symbol occurrences
  "editor.selectionHighlight": true, // Enables highlighting of selected text matches
  "editor.codeLens": false, // Disables CodeLens (inline reference/implementation counts)
  "editor.lightbulb.enabled": "onCode", // Shows lightbulb (quick fixes) only when hovering over code
  "eslint.enable": true, // Enables ESLint integration
  "extensions.showRecommendationsOnlyOnDemand": true, // Only shows extension recommendations when explicitly requested
  "extensions.autoUpdate": false, // Disables automatic extension updates
  "extensions.ignoreRecommendations": true, // Ignores extension recommendations
  "files.watcherExclude": {}, // files excluded from file watcher
  "files.exclude": {}, // files excluded from file explorer
  "files.maxMemoryForLargeFilesMB": 4096, // Sets maximum memory allocation for large files to 4GB
  "git.mergeEditor.codeLens.enabled": false, // Disables CodeLens in merge editor
  "html.validate.scripts": false, // Disables JavaScript validation in HTML script tags
  "jsonc.validate.enable": true, // Enables validation for JSON with Comments files
  "json.validate.enable": true, // Enables validation for JSON files
  "merge-conflict.codeLens.enabled": false, // Disables CodeLens for merge conflicts
  "multiDiffEditor.experimental.enabled": false, // Disables experimental multi-file diff editor
  "markdown.validate.enable": false, // Disables Markdown validation
  "markdown.preview.automaticPreview": "never", // Never automatically opens Markdown preview
  "markdown.preview.fontSize": 12, // Sets Markdown preview font size to 12pt
  "markdown.validate.enabled": false, // Disables Markdown validation (duplicate of earlier setting)
  "markdown.updateLinksOnFileMove.enabled": "never", // Never updates Markdown links when files are moved
  "markdown.editor.pasteUrlAsFormattedLink.enabled": "always", // Always formats pasted URLs as Markdown links
  "markdown.extension.print.theme": "dark", // Sets dark theme for Markdown print extension
  "markdown.extension.tableFormatter.normalizeIndentation": true, // Normalizes indentation when formatting Markdown tables
  "markdown.extension.theming.decoration.renderParagraph": true, // Enables paragraph rendering decorations in Markdown
  "markdown.extension.toc.orderedList": true, // Uses ordered lists for table of contents in Markdown
  "markdown.server.log": "off", // Disables logging for Markdown language server
  "prisma.showPrismaDataPlatformNotification": false, // Disables Prisma Data Platform notifications
  "prettier.enable": true, // Enables Prettier code formatter
  "search.smartCase": true, // Enables smart case search (case-sensitive when using uppercase)
  "search.useIgnoreFiles": false, // Ignores .gitignore files when searching
  "search.exclude": {}, // No additional search exclusions
  "javascript.validate.enable": true, // Enables JavaScript validation
  "javascript.updateImportsOnFileMove.enabled": "always", // Always updates imports when moving JavaScript files
  "typescript.updateImportsOnFileMove.enabled": "always", // Always updates imports when moving TypeScript files
  "typescript.preferences.importModuleSpecifier": "project-relative", // Uses project-relative paths for TypeScript imports
  "typescript.tsserver.web.projectWideIntellisense.enabled": false, // Disables project-wide IntelliSense for TypeScript in web
  "typescript.validate.enable": true, // Enables TypeScript validation
  "workbench.editor.enablePreview": false, // Disables preview mode for editors (always opens files in persistent tab)
  // ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★
  // these 4 settings are the key:value pairs that remove the unicorn puke on your ui that is enabled by default. All the colors notifying you of, some sort of change made in comparison to your repo. Which means it removes all the colors found to the left of your editor by the line numbers, the gutter, removes the color from the tabs file names, and removes the colors from the explorer pane in relation to the folder and files tree view. If I'm missing something else it changes, it's because I have had these four disabled for so long I honestly do not remember what the default ui looks like with it enabled. 
  "git.diffEditor.renderGutterMenu": false, // Hides gutter menu in Git diff editor
  "git.decorations.enabled": false, // Disables Git decorations in file explorer
  "scm.diffDecorationsGutterAction": "none", // Disables gutter actions for source control diff decorations
  "scm.diffDecorations": "none", // Disables diff decorations in source control
  // ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★
  // The following sections go over key:value pairs that are purely based off of installed extensions. I know I touched on this already but, with every dev being too excited for ai. 
  // It feels as if everyone and their mums, are coding in ai into their products in some form, whether or not it even makes sense to have it, that's obivously up to debate on a product by product basis. 
  // But each introduction of an ai engine in your vscode instance, introduces VERY VERY heavy workloads. It is so bad, that if I were to install an extension knowing it has ai features before I even use vscode in any way, I'm taking an axe to that extensions settings. As you can see from the following settings, copilot is pretty much completely disabled unless I manually trigger an event. 
  // When releasing `prompt`, to prove just how effective it is in solving 99% of the issues you face with ai prompts. I downloaded, I want to say about 15-20 extensions solely featuring ai as a prompt. All of them, without exception, had inline code features, they all had the ai engine scanning not only your currently opened file but also your entire project, ALL the time, and the background process features don't end there. 
  // So if you were looking for good options, in terms of installing an ai prompt into your instance, these are my recomendations. I experienced all manner of issues and problems when using such a broad spectrum of extensions because I essentially downloaded every single option that was available at the time. If you install an option that isn't listed below, you will probably face atleast one issue before you actually end up using the ai prompt.
  // Funnily enough, the options below, except one other but is so bad I won't even mention it, were the only options that did NOT have some sort of issue in order to use it. There were extension where I went to sign up for an account in order to get the api key, I couldn't sign up in any way even after visiting their main site and manually trying to sign up. There were A LOT of issues with api keys. There were also times that even after doing everything the docs stated, it just didnt work. 
  // There is one listed below that you need to watch out for, unless you speak mandarin which is `codegeex`. I do not fucking speak mandarin, and had to learn it just to use it. At the time, and even today, it makes me laugh that an extension required me to learn a new language in order to use it. We all know, being tech people, how to navigate to a menu, and atleast access the setting to change it to the language you need in order to use it. I could not for the life of me find the setting while it was in mandarin, and I searched for well over 20 minutes for it. ONCE, its in english I liked using it the most.
  // There will be an ai prompt associated with this extension that will be available soon, its already coded and will be released soon. If you want to take advantage of all the benefits `prompt` offers, while adding literlly 0 steps to your day to day workflow with ai prompts while coding, keep an eye out on the site for it. This will be the best ai prompt for devs... period. Not only does prompt get results so good, I would rather use it in its current manual form, then not. Coupled with a ux design, not featured anywhere else that was developed solely for the a developers benefit. So in short not only does it improve your prompts success better then any other product, paid or not, but also removes any and all pain points in using any prompts ui.
  // ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★
  "github.copilot.enable": {
    "*": false, // Disables Copilot for all file types by default
    "plaintext": true, // Enables Copilot for plain text files
    "markdown": false, // Disables Copilot for Markdown files
    "scminput": false // Disables Copilot in source control input
  },
  "github.copilot.nextEditSuggestions.allowWhitespaceOnlyChanges": false, // Prevents Copilot from suggesting whitespace-only changes
  "github.copilot.chat.agent.thinkingTool": true, // Enables thinking/reasoning tool in Copilot chat
  "Codegeex.Chat.LanguagePreference": "English", // Sets CodeGeeX chat language to English
  "Codegeex.GenerationPreference": "line by line", // Sets CodeGeeX to generate code line by line
  "Codegeex.Privacy": false, // Disables CodeGeeX privacy/telemetry features
  "Codegeex.License": "", // CodeGeeX license key (empty)
  "codegeex.codeLens.functionQuickOptions": {
    "addComment": false, // Disables "add comment" CodeLens option for functions
    "ghostComment": false, // Disables ghost comment suggestions
    "fixBug": false, // Disables "fix bug" CodeLens option
    "generateUnitTest": false, // Disables "generate unit test" CodeLens option
    "reviewCode": false, // Disables "review code" CodeLens option
    "codeOptimization": false, // Disables "optimize code" CodeLens option
    "addDocString": false, // Disables "add docstring" CodeLens option
    "addExceptionHandling": false, // Disables "add exception handling" CodeLens option
    "printLogForDebugging": false, // Disables "add debug logging" CodeLens option
    "improveRunningEfficiency": false, // Disables "improve efficiency" CodeLens option
    "renameSymbols": false, // Disables "rename symbols" CodeLens option
    "newFileForDebugging": false, // Disables "new file for debugging" CodeLens option
    "tryANewApproach": false, // Disables "try new approach" CodeLens option
    "explainCode": false // Disables "explain code" CodeLens option
  },
  "codegeex.codeLens.classQuickOptions": {
    "explainCode": false, // Disables "explain code" CodeLens option for classes
    "ghostComment": false, // Disables ghost comment suggestions for classes
    "fixBug": false, // Disables "fix bug" CodeLens option for classes
    "generateUnitTest": false, // Disables "generate unit test" CodeLens option for classes
    "reviewCode": false, // Disables "review code" CodeLens option for classes
    "addDocStringForClass": false, // Disables "add class docstring" CodeLens option
    "addDocStringForMethods": false, // Disables "add method docstrings" CodeLens option
    "addComment": false // Disables "add comment" CodeLens option for classes
  },
  "geminicodeassist.chat.changeView": "Default diff view", // Sets Gemini Code Assist chat to use default diff view
  "geminicodeassist.displayInlineContextHint": false, // Disables inline context hints from Gemini Code Assist
  "geminicodeassist.enableTelemetry": false, // Disables telemetry for Gemini Code Assist
  "geminicodeassist.inlineSuggestions.enableAuto": false, // Disables automatic inline suggestions from Gemini Code Assist
  "geminicodeassist.localCodebaseAwareness": false, // Disables local codebase awareness for Gemini Code Assist
 
}
```

Now this isn't all the performance settings available to you, in the global settings.json section I outline, what I believe, to be the settings that took my optimization from 10 and maxed it to 100, these settings will be outlined at the bottom of that section starting at the stared divider.

</details>

<details closed><summary style="font-size: 1.2em;">editor</summary>

```json
{
 "editor.minimap.showRegionSectionHeaders": true, // Show region section headers in minimap
  "editor.minimap.autohide": true, // Automatically hide minimap when not needed
  "editor.minimap.enabled": true, // Enable the minimap code overview
  "editor.minimap.showSlider": "mouseover", // Show minimap slider on hover
  "editor.minimap.side": "left", // Position minimap on left side
  "editor.minimap.size": "fill", // Minimap fills available height
  "editor.minimap.renderCharacters": false, // Render blocks instead of actual characters
  "editor.minimap.maxColumn": 30, // this setting is apparently so niche that claude beleives this setting to be invalid, but it is valid. This is one of those settings that, really made a feature I did not care for, to actually loving it. This controls exactly, and I mean exactly how wide the minimap is to the pixel. If you do not use the minimap currently because it just takes up too much real estate, try this out because once you set it to 50 or below, it becomes small enough where it is worth while having. Coupled with changing to which side it resides on to left, that pairing of settings was the game changer that made me love the minimap feature because when you have two editors side by side, and your cursor is in the middle, with in a 50px span you can control, both files. When your actively coding, your cursor tends to be on the left side of the editor, making it a short distance to access the current files editor, if it isn't already within 100 px's of it. Changing the size to fill, was also a huge plus, as well as auto hide set to true and showslider set to mouse over, so as not to impede on the overall esthetic, or another way to look at it is, its one less thing that is visually trying to get your attention, we will discuss the last point more in themes.
  "editor.fontSize": 11, // Set editor font size to 11 pixels
  "editor.wordWrap": "on", // Enable word wrapping
  "editor.foldingStrategy": "auto", // Automatically determine folding strategy
  "editor.fontFamily": "JetBrains Mono", // Use JetBrains Mono font
  "editor.fontLigatures": true, // Enable font ligatures for special character combinations
  "editor.fontVariations": true, // Enable font variations support
  "editor.accessibilitySupport": "off", // Disable accessibility support optimizations
  "editor.showFoldingControls": "always", // Always show code folding controls
  "editor.lineNumbers": "relative", // Show relative line numbers
  "editor.scrollBeyondLastLine": false, // Prevent scrolling past last line
  "editor.foldingImportsByDefault": false, // Don't fold import statements by default
  "editor.renderWhitespace": "none", // Don't render whitespace characters
  "editor.renderControlCharacters": true, // Render control characters visibly
  "editor.folding": true, // Enable code folding
  "editor.glyphMargin": true, // Show glyph margin for breakpoints/icons
  "editor.stickyScroll.enabled": true, // Keep current scope visible at top while scrolling
  "editor.largeFileOptimizations": true, // Enable optimizations for large files
  "editor.stickyScroll.maxLineCount": 5, // Maximum lines to show in sticky scroll
  "editor.unicodeHighlight.invisibleCharacters": false // Don't highlight invisible Unicode characters

}
```
</details>

<details closed><summary style="font-size: 1.2em;">javascript</summary>

```json
{
  "javascript.updateImportsOnFileMove.enabled": "always" // aautomatically update import paths when moving files
}
```
</details>


<details closed><summary style="font-size: 1.2em;">terminal</summary>

```json
{
  "terminal.integrated.defaultLocation": "editor", // Open terminal in editor area instead of panel
  "terminal.integrated.suggest.suggestOnTriggerCharacters": true, // Show suggestions when typing trigger characters in terminal
  "terminal.integrated.fontFamily": "monospace", // Use monospace font family in terminal
  "terminal.integrated.stickyScroll.enabled": true, // Enable sticky scroll in terminal
  "terminal.integrated.fontSize": 12 // Set terminal font size to 12 pixels
}
```
</details>

<details closed><summary style="font-size: 1.2em;">workbench</summary>

```json
{
  "workbench.editor.alwaysShowEditorActions": true, // Always show editor action buttons
  "workbench.editor.enablePreviewFromQuickOpen": false, // Don't open files in preview mode from quick open
  "workbench.editor.focusRecentEditorAfterClose": false, // Don't focus most recent editor after closing a tab
  "workbench.editor.pinnedTabsOnSeparateRow": true, // Display pinned tabs on a separate row
  "workbench.editor.wrapTabs": true, // Wrap tabs to multiple rows when they don't fit
  "workbench.editor.limit.enabled": true, // Enable limit on number of open editors
  "workbench.panel.opensMaximized": "never", // Never open panel maximized
  "workbench.panel.defaultLocation": "bottom", // Position panel at bottom of window
  "workbench.secondarySideBar.showLabels": false, // // 
  "workbench.externalBrowser": "Opera", // Use Opera as external browser
  "workbench.activityBar.location": "right", // Position activity bar on right side
  "workbench.editor.showTabs": "multiple", // Show multiple editor tabs
  "workbench.statusBar.visible": true, // Show status bar at bottom
  "workbench.sideBar.location": "right", // Position sidebar on right side
  "workbench.commandPalette.history": 30, // Store 30 items in command palette history
  "workbench.remoteIndicator.showExtensionRecommendations": false, // Don't show extension recommendations in remote indicator
  "workbench.welcomePage.walkthroughs.openOnInstall": false, // Don't open walkthroughs after installing extensions
  "workbench.editor.restoreViewState": true // Restore editor view state when reopening files

}
```
</details>

<details closed><summary style="font-size: 1.2em;">window</summary>

```json
{
  "window.restoreWindows": "one", // Restore only one window on startup
  "window.openFilesInNewWindow": "default", // Use default behavior for opening files in new window
  "window.menuBarVisibility": "classic", // Show menu bar in classic style
  "window.commandCenter": true, // Enable command center in title bar
  "window.zoomLevel": -1 // Set window zoom level to -1 (zoomed out one level)
}
```
</details>


<details closed><summary style="font-size: 1.2em;">Other</summary>

This section is devoted to key:value pairs that do not have enough in quantity to warrant the creation of their own section.

```json
{
  "vsicons.dontShowNewVersionMessage": true, // Don't show new version message for VSIcons extension
  "telemetry.telemetryLevel": "off", // Disable telemetry data collection
  "extensions.autoCheckUpdates": false, // Don't automatically check for extension updates
  "security.workspace.trust.untrustedFiles": "newWindow", // Open untrusted files in a new window
  "update.enableWindowsBackgroundUpdates": false, // Disable background updates on Windows
  "update.mode": "none", // Disable automatic updates
  "update.showReleaseNotes": false, // Don't show release notes after updates
  "problems.visibility": false, // Hide problems panel visibility
  "breadcrumbs.enabled": false // Disable breadcrumb navigation
}
```
</details>

<details closed><summary style="font-size: 1.2em;">ocrmnavigator</summary>

```json
{
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
        "ocrmnavigator.devstack.site.snippets": true,
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
        "ocrmnavigator.devstack.site.colorWheel": true,
        "ocrmnavigator.lucideIcons": true,
        "ocrmnavigator.share": true,
        "ocrmnavigator.url": true,
        "ocrmnavigator.project.json.comments.remove": true,
        "ocrmnavigator.con": true,
        "ocrmnavigator.project.file.comments.remove": true,
        "ocrmnavigator.unusedFunctions": true,
        "ocrmnavigator.viewers": true,
        "ocrmnavigator.uiDashboard": true,
        "ocrmnavigator.devStackFunctions": true,
        "ocrmnavigator.leftOffNote.open": true,
        "ocrmnavigator.devstack.site.md.render": true,
        "ocrmnavigator.project.index.smart.create": true,
        "ocrmnavigator.devstack.site.tailwindConverter": true,
        "ocrmnavigator.remix.project2agnostic.convert": true,
        "ocrmnavigator.vfs.concurrent.execute": true,
        "ocrmnavigator.vfs.chain.execute": true
}
```

</details>

<details closed><summary style="font-size: 1.2em;">Global settings.json</summary>

These settings were taken from my global settings file that for one reason or another I did not include with my personal config. At the top of the list of reasons, there isn't enough of a benefit to warrant a workspace per workspace change in these settings, but still important enough to have them.

```json
{
  "workbench.quickOpen.preserveInput": true, // Preserve input in quick open when switching between modes
  "typescript.updateImportsOnPaste.enabled": false, // Don't automatically update TypeScript imports when pasting code
  "typescript.referencesCodeLens.enabled": true, // Show references CodeLens in TypeScript files
  "typescript.implementationsCodeLens.enabled": false, // Don't show implementations CodeLens in TypeScript files
  "typescript.implementationsCodeLens.showOnInterfaceMethods": false, // Don't show implementations CodeLens on interface methods
  "editor.suggestSelection": "recentlyUsed", // Select recently used suggestions first
  "editor.autoClosingQuotes": "languageDefined", // Auto-close quotes based on language configuration
  "editor.autoClosingBrackets": "languageDefined", // Auto-close brackets based on language configuration
  "editor.semanticHighlighting.enabled": true, // Enable semantic syntax highlighting
  "explorer.compactFolders": false, // Don't collapse single-child folders in explorer
  "workbench.tree.renderIndentGuides": "onHover", // Show tree indent guides only on hover
  "files.defaultLanguage": "TypeScript", // Set TypeScript as default language for new files
  "search.smartCase": true, // Use smart case matching in search (case-insensitive unless uppercase used)
  "files.associations": {
    ".env*": "dotenv" // Associate .env files with dotenv language
  },
  "editor.defaultFormatter": "vscode.typescript-language-features", // Use built-in TypeScript formatter as default
  "[typescriptreact]": {
    "editor.defaultFormatter": "vscode.typescript-language-features" // Use TypeScript formatter for TSX files
  },
  "[javascriptreact]": {
    "editor.defaultFormatter": "vscode.typescript-language-features" // Use TypeScript formatter for JSX files
  },
  "[typescript]": {
    "editor.defaultFormatter": "vscode.typescript-language-features" // Use TypeScript formatter for TS files
  },
  "[javascript]": {
    "editor.defaultFormatter": "vscode.typescript-language-features" // Use TypeScript formatter for JS files
  },
  "[json]": {
    "editor.defaultFormatter": "skyler.ocrmnav" // Use custom formatter for JSON files
  },
  "[jsonc]": {
    "editor.validate": true, // Enable validation for JSONC files
    "editor.defaultFormatter": "skyler.ocrmnav" // Use custom formatter for JSONC files
  },
  "[css]": {
    "editor.defaultFormatter": "vscode.css-language-features" // Use built-in CSS formatter
  },
  "[html]": {
    "editor.defaultFormatter": "vscode.html-language-features" // Use built-in HTML formatter
  },
  "[snippets]": {
    "editor.defaultFormatter": "vscode.json-language-features" // Use JSON formatter for snippet files
  },
    "git.enableSmartCommit": true, // Enable smart commit (commit all changes when no staged changes)
  "git.openRepositoryInParentFolders": "never", // Never open repository in parent folders
  "git.confirmSync": false, // Don't confirm before syncing
   "editor.tokenColorCustomizations": { // Customize token colors for different themes
    "[*Light*]": {
      "textMateRules": [
        {
          "scope": "ref.matchtext",
          "settings": {
            "foreground": "#000" // Set matched reference text to black in light themes
          }
        }
      ]
    },
    "[*Dark*]": {
      "textMateRules": [
        {
          "scope": "ref.matchtext",
          "settings": {
            "foreground": "#fff" // Set matched reference text to white in dark themes
          }
        }
      ]
    },
    "textMateRules": [
      {
        "scope": "keyword.other.dotenv",
        "settings": {
          "foreground": "#FF000000" // Set dotenv keywords to transparent
        }
      }
    ]
  },
    "editor.fontFamily": "Open Sans", // Set editor font to Open Sans
  "extensions.ignoreRecommendations": true, // Ignore extension recommendations
  "extensions.autoUpdate": false, // Don't automatically update extensions
  "workbench.enableExperiments": false, // Disable experimental features
  "workbench.settings.applyToAllProfiles": [ // Apply these settings to all workspace profiles
    "ntrsync.repo",
    "ntrsync.branch",
    "ntrsync.checkRemindersInterval",
    "ntrsync.owner",
    "ntrsync.remote",
    "ntrsync.repository",
    "ntrsync.isPriv",
    "ocrmnavigator.UPDATE_PROMPT_OBJECTS",
    "ocrmnavigator.CONVERT_README_DEV_MD",
    "ocrmnavigator.AUTORUN_SCRIPTS",
    "ocrmnavigator.AUTORUN_DIR",
    "ocrmnavigator.PRO7",
    "ocrmnavigator.ARCHIVER",
    "ocrmnavigator.DELETE_OLD_VSIX",
    "ocrmnavigator.AUTO_INSTALL_VSIX",
    "ocrmnavigator.RELOAD_INSTANCE",
    "ocrmnavigator.BE_QP",
    "ocrmnavigator.AUTO_FOLD_PKG",
    "ocrmnavigator.vscodeVersion",
    "ocrmnavigator.configPath",
    "ocrmnavigator.other"
  ],
  "workbench.editorAssociations": { // Associate file types with specific editors
    "*.html": "default", // Use default editor for HTML files
    "*.svg": "default" // Use default editor for SVG files
  },
  "workbench.editor.autoLockGroups": { // Configure which editor groups auto-lock
    "default": true, // Don't auto-lock default editors
    "mainThreadWebview-simpleBrowser.view": false, // Don't auto-lock simple browser view
    "mainThreadWebview-browserPreview": false // Don't auto-lock browser preview
  },
  "workbench.preferredHighContrastColorTheme": "Default Dark+", // Set high contrast theme to Default Dark+
  "workbench.preferredHighContrastLightColorTheme": "Default Dark+", // Set high contrast light theme to Default Dark+
  "workbench.preferredLightColorTheme": "Default Dark+", // Set light theme to Default Dark+
  "workbench.tree.enableStickyScroll": true, // Disable sticky scroll in tree views
  "workbench.externalBrowser": "Chrome", // Use Chrome as external browser
  "workbench.startupEditor": "none", // Don't show any editor on startup
  "window.autoDetectHighContrast": false, // Don't automatically detect high contrast mode
  "window.closeWhenEmpty": true, // Close window when no editors are open
  "window.newWindowProfile": "Default", // Use default profile for new windows
  "window.newWindowDimensions": "inherit", // Inherit window dimensions for new windows
  "window.customTitleBarVisibility": "windowed", // Show custom title bar in windowed mode
  // ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★
  // The following settings I credit to really optimizing my vscode instance, I think. It was a day that I was really frustrated, and was trying out different settings WHILE still actively coding. I beleive these are the final settings due to the fact that, while I didn't notice it that day due to anger managment issues, the days following my vscode instance went from `fuck this` to how is everything... just working. And I have not touched them since. Because out of all the settings in that file, these are the ones that are performance based. If you haven't already noticed settings, that are not mentioned anywhere else on the internet but here, you will in this section. I would say about half of the values I use were discovered from painstakingly using intellisense on every line and manually going through and toggling everything. Literally every single form of issue I was experiencing, has vanished while at the same time, keeping features I never imagined I was going to be able to use when deciding to keep them from a performance perspective.
  // - i still have either codelense or lightbulb, cant remember which but one of the two
  // - still have inline snippets
  // - still have validation active for a lot of different file types
  // in short, there is now not a single feature where I'm thinking, "I wish I had that"
  "files.exclude": {}, // No files excluded from file explorer
  "files.watcherExclude": { // Exclude these paths from file watcher
    "node_modules/**": true, // Don't watch node_modules directory
    "backup/**": true, // Don't watch backup directory
    "dist/**": true, // Don't watch dist directory
    "public/**": true, // Don't watch public directory
    "build/**": true, // Don't watch build directory
    "scripts/**": true, // Don't watch scripts directory
    "md/**": true, // Don't watch md directory
    "components/**": true, // Don't watch components directory
    "src/catalyst-ui/**": true, // Don't watch catalyst-ui directory
    "*.vsix": true, // Don't watch VSIX extension files
    "*.7z": true, // Don't watch 7z archives
    "*.png": true, // Don't watch PNG images
    "*.svg": true, // Don't watch SVG images
    "*.gif": true, // Don't watch GIF images
    ".pro7": true, // Don't watch .pro7 files
    "pnpm-lock.yaml": true, // Don't watch pnpm lock file
    "package-lock.json": true, // Don't watch npm lock file
    "package.dev.jsonc": true, // Don't watch dev package config
    "README.dev.md": true, // Don't watch dev readme
    "README.md": true, // Don't watch readme
    "navigator-workspace.json": true, // Don't watch navigator workspace config
    "global-navigator-config.json": true, // Don't watch global navigator config
    "components.json": true // Don't watch components config
  },
  "search.exclude": { // Exclude these paths from search results
    "": true, // 
    ".pro7": true, // Exclude .pro7 files from search
    "*.7z": true, // Exclude 7z archives from search
    "*.gif": true, // Exclude GIF images from search
    "*.png": true, // Exclude PNG images from search
    "*.svg": true, // Exclude SVG images from search
    "*.vsix": true, // Exclude VSIX files from search
    "backup/**": true, // Exclude backup directory from search
    "build/**": true, // Exclude build directory from search
    "components.json": true, // Exclude components config from search
    "components/**": true, // Exclude components directory from search
    "dist/**": true, // Exclude dist directory from search
    "global-navigator-config.json": true, // Exclude global navigator config from search
    "md/**": true, // Exclude md directory from search
    "navigator-workspace.json": true, // Exclude navigator workspace config from search
    "node_modules/**": true, // Exclude node_modules from search
    "public/**": true, // Exclude public directory from search
    "scripts/**": true, // Exclude scripts directory from search
    "src/catalyst-ui/**": true // Exclude catalyst-ui directory from search
  },
  "markdown.validate.enable": false, // Disable markdown validation
  "markdown.preview.automaticPreview": "never", // Never automatically open markdown preview
  "markdown.preview.fontSize": 12, // Set markdown preview font size to 12
  "markdown.validate.enabled": false, // Disable markdown validation (duplicate setting)
  "markdown.updateLinksOnFileMove.enabled": "never", // Never update markdown links when moving files
  "markdown.editor.pasteUrlAsFormattedLink.enabled": "always", // Always format pasted URLs as markdown links
  "markdown.extension.print.theme": "dark", // Use dark theme for markdown printing
  "markdown.extension.tableFormatter.normalizeIndentation": true, // Normalize indentation in markdown tables
  "markdown.extension.theming.decoration.renderParagraph": true, // Render paragraph decorations in markdown
  "markdown.extension.toc.orderedList": true, // Use ordered lists for table of contents
  "markdown.server.log": "off", // Disable markdown language server logging
  "[markdown]": { // Markdown-specific editor settings
    "editor.quickSuggestions": {
      "comments": false, // Don't show quick suggestions in comments
      "strings": false, // Don't show quick suggestions in strings
      "other": false // Don't show quick suggestions elsewhere
    },
    "workbench.editor.languageDetection": false, // Disable automatic language detection
    "editor.defaultFormatter": "yzhang.markdown-all-in-one", // Use Markdown All in One formatter
    "editor.suggest.snippetsPreventQuickSuggestions": true, // Prevent snippets from triggering quick suggestions
    "editor.acceptSuggestionOnEnter": "off", // Don't accept suggestions on Enter key
    "editor.suggest.showStatusBar": true, // Show suggestion status bar
    "editor.hover.enabled": "on", // Enable hover information
    "editor.renderWhitespace": "none", // Don't render whitespace characters
    "editor.renderControlCharacters": false, // Don't render control characters
    "editor.renderLineHighlight": "line", // Highlight entire current line
    "editor.matchBrackets": "always", // Always highlight matching brackets
    "editor.glyphMargin": true, // Show glyph margin for breakpoints/icons
    "editor.folding": true, // Enable code folding
    "editor.gotoLocation.multipleDefinitions": "gotoAndPeek", // Go to and peek when multiple definitions
    "editor.gotoLocation.multipleTypeDefinitions": "gotoAndPeek", // Go to and peek when multiple type definitions
    "editor.gotoLocation.multipleDeclarations": "gotoAndPeek", // Go to and peek when multiple declarations
    "editor.gotoLocation.multipleImplementations": "gotoAndPeek", // Go to and peek when multiple implementations
    "editor.gotoLocation.multipleReferences": "gotoAndPeek", // Go to and peek when multiple references
    "editor.links": true, // Enable clickable links
    "editor.occurrencesHighlight": "off", // Don't highlight occurrences of selected symbol
    "editor.selectionHighlight": true, // Highlight all occurrences of selected text
    "editor.semanticHighlighting.enabled": true, // Enable semantic highlighting
    "editor.showFoldingControls": "always", // Always show folding controls
    "editor.suggest.insertMode": "replace", // Replace text when accepting suggestions
    "editor.suggest.filterGraceful": false, // Use strict filtering for suggestions
    "editor.suggest.shareSuggestSelections": false, // Don't share suggestion selections across files
    "editor.suggest.showClasses": false, // Don't show class suggestions
    "editor.suggest.showColors": false, // Don't show color suggestions
    "editor.suggest.showConstants": false, // Don't show constant suggestions
    "editor.suggest.showConstructors": false, // Don't show constructor suggestions
    "editor.suggest.showCustomcolors": false, // Don't show custom color suggestions
    "editor.suggest.showDeprecated": false, // Don't show deprecated suggestions
    "editor.suggest.showEnumMembers": false, // Don't show enum member suggestions
    "editor.suggest.showEnums": false, // Don't show enum suggestions
    "editor.suggest.showEvents": false, // Don't show event suggestions
    "editor.suggest.showFields": false, // Don't show field suggestions
    "editor.suggest.showFiles": false, // Don't show file suggestions
    "editor.suggest.showFolders": false, // Don't show folder suggestions
    "editor.suggest.showFunctions": false, // Don't show function suggestions
    "editor.suggest.showInterfaces": false, // Don't show interface suggestions
    "editor.suggest.showIssues": false, // Don't show issue suggestions
    "editor.suggest.showKeywords": false, // Don't show keyword suggestions
    "editor.suggest.showMethods": false, // Don't show method suggestions
    "editor.suggest.showModules": false, // Don't show module suggestions
    "editor.suggest.showOperators": false, // Don't show operator suggestions
    "editor.suggest.showProperties": false, // Don't show property suggestions
    "editor.suggest.showReferences": false, // Don't show reference suggestions
    "editor.suggest.showSnippets": false, // Don't show snippet suggestions
    "editor.suggest.showStructs": false, // Don't show struct suggestions
    "editor.suggest.showTypeParameters": false, // Don't show type parameter suggestions
    "editor.suggest.showUnits": false, // Don't show unit suggestions
    "editor.suggest.showUsers": false, // Don't show user suggestions
    "editor.suggest.showValues": false, // Don't show value suggestions
    "editor.suggest.showVariables": false, // Don't show variable suggestions
    "editor.suggest.showWords": false, // Don't show word suggestions
    "editor.wordBasedSuggestions": "off", // Disable word-based suggestions
    "editor.wordBasedSuggestionsMode": "allDocuments", // Use all documents for word-based suggestions
    "editor.suggestSelection": "recentlyUsed", // Select recently used suggestions first
    "diffEditor.wordWrap": "inherit" // Inherit word wrap setting in diff editor
  },
  "debug.openDebug": "neverOpen", // Never automatically open debug view
  "debug.toolBarLocation": "hidden", // Hide debug toolbar
  "debug.showInStatusBar": "never", // Never show debug status in status bar

  "editor.formatOnPaste": false, // Don't format code when pasting
  "editor.formatOnType": false, // Don't format code while typing
  "editor.formatOnSave": false, // Don't format code on save
  "editor.codeLens": false, // Disable CodeLens
  "editor.quickSuggestions": {
    "strings": false, // Don't show quick suggestions in strings
    "other": false, // Don't show quick suggestions elsewhere
    "comments": false // Don't show quick suggestions in comments
  },
  "editor.inlineSuggest.enabled": false, // Disable inline suggestions (like GitHub Copilot)
  "editor.acceptSuggestionOnEnter": "off", // Don't accept suggestions on Enter key
  "editor.acceptSuggestionOnCommitCharacter": false, // Don't accept suggestions on commit characters (., (, etc.)
  "editor.parameterHints.cycle": false, // Don't cycle through parameter hints
  "editor.parameterHints.enabled": false, // Disable parameter hints
  "editor.wordBasedSuggestions": "off", // Disable word-based suggestions
  "editor.suggestOnTriggerCharacters": false, // Don't show suggestions on trigger characters
  "editor.inlayHints.enabled": "off", // Disable inlay hints
  "diffEditor.codeLens": false, // Disable CodeLens in diff editor
  "multiDiffEditor.experimental.enabled": false, // Disable experimental multi-diff editor
  "merge-conflict.codeLens.enabled": false, // Disable CodeLens for merge conflicts
  "sonarlint.disableTelemetry": true, // Disable SonarLint telemetry 
}
```

</details>

</details>

<details closed><summary  style="font-size: 1.4em;  color: #1447e6;">workbench.colorCustomizations</summary>

I do not know why, microsoft shipped a product with a feature where, so many people WILL want to use it. Depending on your level of experience, its a feature so horribly developed... its unsuable till you reach a certain level of knowledge, actually. 

One thing microsoft is the absolute best at, is developing the absolute worst ux bar none. And due to the resources they have at their disposal, no one can ever take this crown from them. 

I won't get into the reasons why, but one night I actually calculated, at global scale, how much time microsft wastes in terms of `time wasted per user, per day` using their products on a day to day work basis. The result was so horrible, I measured it in human years wasted, so a full 24 hours a day, 365 days a year wasted. In the same length / distance ( sure, we'll use that in this instance ) in time for me to experience day to day interactions... with dinosaurs, actually standing among and breathing the same air they are, is how much time... microsoft wastes if it isnt yearly, because I think its yearly its been a while, then it would be every 5 year cycle. EVEN if its every 5 years... that is truly insane. I could experience the birth of christ 1000's of times over and still have time on the clock to spare, I'm not religious so another example would be, I could break bread and on a philosophical level, argue with socrates, plato and aristotle as they live and breath about all matter of things... where I could visit them for dinner every single day of my life, coming back to present day for the remainder, and still have time on the clock. That would be kind of fucking cool actually, but it sounds rediculous and absurd and if you think I'm exaggerating, I kid you not, due to nature of compounding numbers along with calculating it at a global scale they waste a rediculous amount of our time as a provider. And when I did the calculations, I was so reserved in terms of actual time wasted per person per day, that I knew with 100% certainty that I was below the average used to calculate this. I won't calculate it again now because I remember it was not easy. If you do want to calculate it yourself, because it is an eye opening exercise, you have get the totals for... I want to say either outlook or 360 active accounts, the gaming division, I think there was one other statistic you needed, but anyways the numbers are very hard to come by but you can get these values.

ANYWAYS, to come back around, if you are a new dev, I highly suggest ( and I don't do this often ) to stop here, and come back later down the road. I'm not going to leave you high and dry. If you go to the theme builder you can build an amazing looking theme in less than 5 mins no matter your experience level because I removed the settings key:value pairs out of the equation when creating a theme for vscode. 

All you do is select the primary color, border color and foreground color, and click on copy to clipboard. Then the only step needed at this point is, pasting it into your .vscode/settings.json file in the `workbench.colorCustomizations` object like how it is below, and you too can have a custom built theme.

For the more experienced devs, in terms of theme builder and just how it does that exactly. I configured the same theme builder I used for tailwind themes, but had the color converters also provide the same values for "categories" of vscode settings. After grouping them up to apply colors accordingly, it turned a stupid headache of a process, into a exercise I have zero issues doing at any one point in time. If this isn't a process you hate doing and somehow you enjoy doing it currently, by organizing the values by category it will save you a huge amount of time instead of going through, line by line and setting each color value since there are so many. I will include the actual function to do just that after the settings

```json
{
  "workbench.colorCustomizations": {
    "background": "#020817", // Main background color (dark slate)
    "menubar.background": "#020817", // Menu bar background color
    "menubar.menu": "#020817", // // 
    "activityBar.background": "#020817", // Activity bar background color
    "terminal.background": "#020817", // Terminal background color
    "titleBar.inactiveBackground": "#020817", // Inactive title bar background color
    "titleBar.activeBackground": "#020817", // Active title bar background color
    "panel.background": "#020817", // Panel background color
    "terminalCommandDecoration.defaultBackground": "#020817", // Default terminal command decoration background
    "sideBar.background": "#020817", // Sidebar background color
    "sideBarSectionHeader.background": "#1E293B", // Sidebar section header background (lighter slate)
    "editor.background": "#020817", // Editor background color
    "editorGroup.emptyBackground": "#020817", // Empty editor group background color
    "statusBar.background": "#020817", // Status bar background color
    "editorGroupHeader.tabsBackground": "#020817", // Editor group header tabs background color
    "activityBar.border": "#020817", // Activity bar border color
    "menu.border": "#1E293B", // Menu border color
    "menu.separatorBackground": "#1E293B", // Menu separator background color
    "sideBar.border": "#1E293B", // Sidebar border color
    "tree.tableColumnsBorder": "#1E293B", // Tree table columns border color
    "tab.border": "#1E293B", // Tab border color
    "statusBar.border": "#1E293B", // Status bar border color
    "panel.border": "#1E293B", // Panel border color
    "menu.foreground": "#94A3B8", // Menu text color (slate gray)
    "foreground": "#94A3B8", // Default foreground/text color
    "menubar.foreground": "#94A3B8", // Menu bar text color
    "activityBar.foreground": "#F8FAFC", // Activity bar icon/text color (light)
    "sideBarSectionHeader.foreground": "#F8FAFC", // Sidebar section header text color
    "explorer.folderItem.foreground": "#1E293B", // Explorer folder text color
    "panelTitle.activeForeground": "#F8FAFC", // Active panel title text color
    "list.focusForeground": "#F8FAFC", // Focused list item text color
    "sideBar.foreground": "#94A3B8", // Sidebar text color
    "statusBar.foreground": "#94A3B8", // Status bar text color
    "editor.foreground": "#F8FAFC", // Editor text color
    "activityBar.inactiveForeground": "#94A3B8", // Inactive activity bar icon/text color
    "explorer.fileItem.foreground": "#94A3B8", // Explorer file text color
    "input.background": "#1E293B", // Input field background color
    "dropdown.background": "#1E293B", // Dropdown background color
    "button.background": "#3B82F6", // Button background color (blue)
    "button.hoverBackground": "#3B82F6", // Button hover background color
    "input.foreground": "#F8FAFC", // Input field text color
    "button.foreground": "#0F172A", // Button text color (dark)
    "menubar.selectionBackground": "#1E293B", // Menu bar selection background color
    "menu.selectionBackground": "#1E293B", // Menu selection background color
    "menubar.selectionForeground": "#F8FAFC", // Menu bar selection text color
    "menu.selectionForeground": "#F8FAFC", // Menu selection text color
    "list.activeSelectionBackground": "#1E293B", // Active list selection background color
    "list.activeSelectionForeground": "#F8FAFC", // Active list selection text color
    "input.border": "#1E293B", // Input field border color
    "inputOption.activeBorder": "#1D4ED8", // Active input option border color (darker blue)
    "focusBorder": "#1D4ED8", // Focus border color for focused elements
    "errorForeground": "#7F1D1D", // Error text color (dark red)
    "editor.lineHighlightBackground": "#1E293B", // Current line highlight background in editor
    "editor.selectionBackground": "#1E293B", // Text selection background in editor
    "editorCursor.foreground": "#F8FAFC", // Editor cursor color
    "editorIndentGuide.background1": "#1E293B", // Indent guide line color
    "editorWhitespace.foreground": "#1E293B", // Whitespace character color
    "list.focusBackground": "#1E293B", // Focused list item background color
    "list.hoverBackground": "#1E293B", // Hovered list item background color
    "list.highlightForeground": "#3B82F6", // Highlighted text color in lists (blue)
    "explorer.fileItem.hoverForeground": "#F8FAFC", // Hovered file item text color in explorer
    "explorer.folderItem.hoverForeground": "#F8FAFC", // Hovered folder item text color in explorer
    "tree.indentGuidesStroke": "#1E293B", // Tree view indent guide stroke color
    "tab.activeBackground": "#020817", // Active tab background color
    "tab.activeForeground": "#F8FAFC", // Active tab text color
    "tab.inactiveBackground": "#020817", // Inactive tab background color
    "tab.inactiveForeground": "#94A3B8", // Inactive tab text color
    "tab.activeBorder": "#020817", // Active tab border color
    "gitDecoration.deletedResourceForeground": "#7F1D1D", // Git deleted file decoration color (red)
    "gitDecoration.conflictingResourceForeground": "#3B82F6", // Git conflicting file decoration color (blue)
    "terminal.ansiBlack": "#020817", // Terminal ANSI black color
    "terminal.ansiBlue": "#3B82F6", // Terminal ANSI blue color
    "terminal.ansiCyan": "#29c3a0", // Terminal ANSI cyan color (teal)
    "terminal.ansiGreen": "#29c3a0", // Terminal ANSI green color (teal)
    "terminal.ansiMagenta": "#3B82F6", // Terminal ANSI magenta color (blue)
    "terminal.ansiRed": "#7F1D1D", // Terminal ANSI red color
    "terminal.ansiWhite": "#F8FAFC", // Terminal ANSI white color
    "terminal.ansiYellow": "#d29922", // Terminal ANSI yellow color (gold)
    "scrollbarSlider.hoverBackground": "#3B82F6", // Scrollbar slider hover color (blue)
    "scrollbarSlider.activeBackground": "#3B82F6", // Scrollbar slider active/pressed color
    "scrollbarSlider.background": "#3B82F620", // Scrollbar slider background color (blue with transparency)
    "activityBarBadge.background": "#3B82F6", // Activity bar badge background color (blue)
    "activityBarBadge.foreground": "#F8FAFC", // Activity bar badge text color
    "explorer.folderItem.selectedIconForeground": "#3B82F6", // Selected folder icon color in explorer (blue)
    "explorer.fileItem.conflictForeground": "#7F1D1D", // Conflicting file text color in explorer (red)
    "explorer.fileItem.errorForeground": "#7F1D1D", // Error file text color in explorer (red)
    "explorer.fileItem.warningForeground": "#d29922", // Warning file text color in explorer (yellow)
    "explorer.folderItem.iconForeground": "#F8FAFC", // Folder icon color in explorer
    "explorer.fileItem.selectedIconForeground": "#F8FAFC", // Selected file icon color in explorer
    "explorer.fileItem.modifiedForeground": "#29c3a0", // Modified file text color in explorer (teal)
    "list.dropBackground": "#02081740", // List drop target background color (transparent slate)
    "list.filterMatchBackground": "#02081720", // List filter match background color (transparent slate)
    "list.inactiveSelectionBackground": "#1E293B40", // Inactive list selection background color (transparent)
    "list.hoverForeground": "#F8FAFC", // List hover text color
    "statusBarItem.hoverBackground": "#1E293B", // Status bar item hover background color
    "gitDecoration.submoduleResourceForeground": "#F8FAFC" // Git submodule decoration color
  }
}
```


<details closed><summary  style="font-size: 1.4em;  color: #1447e6;">generateVSCodeTheme</summary>


```javascript
const generateVSCodeTheme = (twCss, gitDecorations = true, scmDiffDecorations = "all") => {
    const hexColors = {};
    Object.entries(twCss).forEach(([key, hslValue]) => {
        hexColors[key] = hslToHex(hslValue);
    });

    const theme = {
        "workbench.colorCustomizations": {
            // Backgrounds
            "background": hexColors["--background"],
            "menubar.background": hexColors["--background"],
            "menubar.menu": hexColors["--background"],
            "activityBar.background": hexColors["--background"],
            "terminal.background": hexColors["--background"],
            "titleBar.inactiveBackground": hexColors["--background"],
            "titleBar.activeBackground": hexColors["--background"],
            "panel.background": hexColors["--background"],
            "terminalCommandDecoration.defaultBackground": hexColors["--background"],
            "sideBar.background": hexColors["--background"],
            "sideBarSectionHeader.background": hexColors["--secondary"],
            "editor.background": hexColors["--background"],
            "editorGroup.emptyBackground": hexColors["--background"],
            "statusBar.background": hexColors["--background"],
            "editorGroupHeader.tabsBackground": hexColors["--background"],

            // Borders
            "activityBar.border": hexColors["--background"],
            "menu.border": hexColors["--border"],
            "menu.separatorBackground": hexColors["--border"],
            "sideBar.border": hexColors["--border"],
            "tree.tableColumnsBorder": hexColors["--border"],
            "tab.border": hexColors["--border"],
            "statusBar.border": hexColors["--border"],
            "panel.border": hexColors["--border"],

            // Foregrounds
            "menu.foreground": hexColors["--muted-foreground"],
            "foreground": hexColors["--muted-foreground"],
            "menubar.foreground": hexColors["--muted-foreground"],
            "activityBar.foreground": hexColors["--foreground"],
            "sideBarSectionHeader.foreground": hexColors["--foreground"],
            "explorer.folderItem.foreground": hexColors["--muted"],
            "panelTitle.activeForeground": hexColors["--foreground"],
            "list.focusForeground": hexColors["--foreground"],
            "sideBar.foreground": hexColors["--muted-foreground"],
            "statusBar.foreground": hexColors["--muted-foreground"],
            "editor.foreground": hexColors["--foreground"],
            "activityBar.inactiveForeground": hexColors["--muted-foreground"],
            "explorer.fileItem.foreground": hexColors["--muted-foreground"],

            // Interactive elements
            "input.background": hexColors["--input"] || hexColors["--background"],
            "dropdown.background": hexColors["--secondary"],
            "button.background": hexColors["--primary"],
            "button.hoverBackground": hexColors["--primary"],
            "input.foreground": hexColors["--foreground"],
            "button.foreground": hexColors["--primary-foreground"],

            // Selections
            "menubar.selectionBackground": hexColors["--accent"],
            "menu.selectionBackground": hexColors["--accent"],
            "menubar.selectionForeground": hexColors["--accent-foreground"],
            "menu.selectionForeground": hexColors["--accent-foreground"],
            "list.activeSelectionBackground": hexColors["--accent"],
            "list.activeSelectionForeground": hexColors["--accent-foreground"],

            // Focus and borders
            "input.border": hexColors["--border"],
            "inputOption.activeBorder": hexColors["--ring"],
            "focusBorder": hexColors["--ring"],
            "errorForeground": hexColors["--destructive"],

            // Editor specific
            "editor.lineHighlightBackground": hexColors["--muted"],
            "editor.selectionBackground": hexColors["--accent"],
            "editorCursor.foreground": hexColors["--foreground"],
            "editorIndentGuide.background1": hexColors["--border"],
            "editorWhitespace.foreground": hexColors["--border"],

            // Lists and trees
            "list.focusBackground": hexColors["--accent"],
            "list.hoverBackground": hexColors["--muted"],
            "list.highlightForeground": hexColors["--primary"],
            "explorer.fileItem.hoverForeground": hexColors["--foreground"],
            "explorer.folderItem.hoverForeground": hexColors["--foreground"],
            "tree.indentGuidesStroke": hexColors["--border"],

            // Tabs
            "tab.activeBackground": hexColors["--card"],
            "tab.activeForeground": hexColors["--card-foreground"],
            "tab.inactiveBackground": hexColors["--background"],
            "tab.inactiveForeground": hexColors["--muted-foreground"],
            "tab.activeBorder": hexColors["--background"],

            // Git decorations
            "gitDecoration.deletedResourceForeground": hexColors["--destructive"],
            "gitDecoration.conflictingResourceForeground": hexColors["--primary"],
            "gitDecoration.submoduleResourceForeground": hexColors["--foreground"],

            // Terminal colors
            "terminal.ansiBlack": hexColors["--background"],
            "terminal.ansiBlue": hexColors["--primary"],
            "terminal.ansiCyan": "#29c3a0",
            "terminal.ansiGreen": "#29c3a0",
            "terminal.ansiMagenta": hexColors["--primary"],
            "terminal.ansiRed": hexColors["--destructive"],
            "terminal.ansiWhite": hexColors["--foreground"],
            "terminal.ansiYellow": "#d29922",

            // Scrollbar customizations
            "scrollbarSlider.hoverBackground": hexColors["--primary"],
            "scrollbarSlider.activeBackground": hexColors["--primary"],
            "scrollbarSlider.background": hexColors["--primary"] + "20",

            // Activity bar badge
            "activityBarBadge.background": hexColors["--primary"],
            "activityBarBadge.foreground": hexColors["--foreground"],

            // Explorer customizations
            "explorer.folderItem.selectedIconForeground": hexColors["--primary"],
            "explorer.fileItem.conflictForeground": hexColors["--destructive"],
            "explorer.fileItem.errorForeground": hexColors["--destructive"],
            "explorer.fileItem.warningForeground": "#d29922",
            "explorer.folderItem.iconForeground": hexColors["--foreground"],
            "explorer.fileItem.selectedIconForeground": hexColors["--foreground"],
            "explorer.fileItem.modifiedForeground": "#29c3a0",

            // List customizations
            "list.dropBackground": hexColors["--background"] + "40",
            "list.filterMatchBackground": hexColors["--background"] + "20",
            "list.inactiveSelectionBackground": hexColors["--muted"] + "40",
            "list.hoverForeground": hexColors["--foreground"],

            // Status bar item
            "statusBarItem.hoverBackground": hexColors["--muted"]
        },
        "git.decorations.enabled": gitDecorations,
        "scm.diffDecorations": scmDiffDecorations
    };

    return theme;
};
```

</details>


</details>




<br /><br />

## Tips

> [!TIP] 
> The following settings cannot be active while using the layout engine. While it doesn't actually hurt anything the behaviours will be modified by these settings, ie the first setting will automatically close any and all files not yet pinned essentially undoing any file opening events done by the engine.
> - `workbench.editor.enablePreview` - will auto close files
> - `workbench.editor.limit.enabled` - will auto close files


> [!TIP] 
> Additional Resources
> - [VS Code Settings Reference](https://code.visualstudio.com/docs/getstarted/settings)
> - [VS Code API Documentation](https://code.visualstudio.com/api)
> - [Workspace Configuration](https://code.visualstudio.com/docs/editor/workspaces)

> [!TIP]
> Due to the nature of this feature, coupled with the fact it gets pretty deep in how far it goes and pretty nerdy. If you reading this now, whether you like it or not, your obviously more of a power user than the average. These will just be random bits of information that I use to help in all manner of things, and will be given in no real order. Whenever they come to mind, I'll come back and continue to add them as there is a lot of them, I can never just sit there and remember them all.
>
> - shortcut - `Add cursors to line ends`: `ctrl + g`
>   - this was created out of frustration and necessity, this is EXTREMELY useful when editing... honestly, more than one line. With this shortcut, I can within seconds modify json objs or files, 10 of thousands of lines long. I also have some wizardy for when the data you need to modify, is just as much in total lines, BUT because of the format you can't use this trick, I have it somewhere so when I find it I'll be sure to add it. What it does, using regex you search for a sepcfic string that will get your cursor on each line of the 10,000 lines allowing you to move with the arrow keys in order to move to where you need to edit.
> 
> - `"editor.lineNumbers": "relative",`
>   - Changing line numbers to relative, I didn't even know this could be done, till I was manually checking every single value for the layout engine. I wish I had this sooner. Honestly, static line numbers are so useless in comparison, ie say your creating a select and you have to manually transfer over the data from another list, counting or calculating the math on how many lines there are, to ensure your data pastes over the way you want to... I'm so happy I never have to do that again. But that event, while it only takes a min, or two, or three depending on how fast I'm going and whether or not I make a mistake. Over the course of a year, it adds up to a lot of time wasted. I seriously never used the line numbers as a refrence at all, in comparison to now. Not only getting that same value that I had to calculate before, to taking a second because you just look at the number. It also offers a VERY quick sanity check, in so many differnt forms. Copying over dating? Check the number when you copy it, when you paste make sure its the same number, you have an ai prompt droning away making lists for you, before now I had to manually check every fucking line, but now... when I grab the data, make a mental note on total lines, once I get the ai's result, paste it in to the file, even today it happened over a dozen times, I HAD to go back and be tell the ai "listen here fucker stop deleting line items", and then the next prompt had the correct amount of lines. The amount of times, because I did not catch it right away, to THEN have to back and check line by line to see what I'm missing, you get the point.
> 
> - the new search editor, be sure to check that tout and use, because it has a killer ux... omg... I pretty much carbon copied vscodes search editor in terms of looks but... each result will disaply ( my config anyways ) 4 of the previous lines and 9 of the lines following the result. With this feature you will be able to click ON THE SEARCH RESULT and remotely edit that file, for when you search something and instead of using find and replace all and you only need to edit that one item. This will save so much time. This pretty much removes the worst part of vscodes search in the explorer pane, coupled with some features vscode does not have.
> 
> - shortcut - `middle mouse button / scroll wheel` -> `enter`
> - shortcut - `left click scroll wheel` -> `scroll up`
> - shortcut - `right click scroll wheel` -> `scroll down`
>   - I made this change today, and I fucking love it and I can't beleive I didn't think of this before. But mouse buttons, vscode doesn't let you do anything with them. I noticed a conflict with one command in the project so I was going to start changing the naming convention from `ocrmnavigator.gitadd` -> `ocrmnavigator.git.add`, but doing this over and over and over again using the find and replace. It's a fucking pain because while copy paste is on one side of the keyboard, you need to hit enter as it is just the way you should do that process instead of dragging the mouse over to confirm, but that causes you to flail your arm around for whatever amount of time. Today just thought of it out of no where and tried it, as middle mouse click does nothing really, programming it as `enter` this was the fastest find all and replacing I have ever done. As it was copy, paste, click on replace all, immediately without moving any body part clicking middle mouse click as I start to move it back to the next value I need to copy. After some use, swapping from application to application was a bit of a pain, but I didn't have any profiles set up, and luckily enough the software I have hot swaps through all my profiles automatically based on your focused app. 
>   - The other weird thing I did, and I'll admit I love it so much more then the regular scrolling with the wheel,  the wheel actuator JUST broke on my mouse, but even when I replace it I won't go back to scrolling like that again. programming the left and right movements of the scroll wheel itself, if you have a regular office mouse, you won't be able to do this. If you want to try it, I would highly recommend it, as you are no longer actively hammering the wheel forward or backwards. Now it's just a passive event of click and hold. It is so much better it kinda blows my mind, that I have not seen a single person do that for scrolling in its place
> 

---

[🡄 Return](https://github.com/8an3/DevStack)

