# Layout Configuration Guide

#### The Workspace Layout Engine, a sophisticated orchestrator that allows you to define and switch between entire development environments with a single click. It doesn't just change a theme; it reconfigures the entire VS Code UI, opens your project files in specific grid positions, and prepares your terminal environment.

Designed for developers who switch contexts frequently—moving from heavy feature development to a focused debugging session or a minimal writing environment. It automates the tedious process of rearranging your editor every time you start a task.

This guide explains how to configure custom workspace layouts using the DevStack layout system. Each layout defines how VS Code appears when activated, including UI elements, editor tabs, terminals, and color themes.

> [!IMPORTANT] 
> UPDATE, yes already... well more like a complete re-write, nothing was wrong with it... I just, apparently enjoy torturing myself as I chase perfection or atleast something close to it.
>
> Although if you thought, this was a rediculously awesome configurable feature, well it's about to get a lot better, and more rediculously awesome so get ready to delete your current config, LOL trust me it'll be worth it. Looking at right now, as I was trying to think of something, this would be a really effecient way to get a new hires workspace up and running... instantly. That is another new feature btw, you will have remote access to your configs, not to mention, from the vscode instance, you will be able to save profiles that will get pushed to the web ui allowing you to download from anywhere, you just need to log in via github with the same email you saved it under when you were using vscode. If you were a manager, you could set your entire team up with different configs for when people get hired, or if your current devs just want a better experience.

> [!NOTE] 
> NEW ARGS VALUES:
> - default  ➜  true | false, same as before
> - keybindings   ➜  we can now configure entire shortcut maps on a per config basis, if you wanted to continously use the same shortcut keys, but used in different contexts... now you can, or use it within the parameters of a workspace context, literally whatever you can think of
> 
>     <details closed><summary>Keybindings config</summary>
>
>     ```json
>     "keybindings": { 
>            "ocrmnavigator.showActionsMenu": "alt+d",
>            "ocrmnavigator.insertIcon": "alt+i",
>            "ocrmnavigator.catalystUIQuickPick": "alt+u",
>            "ocrmnavigator.contextSnippets": "alt+s",
>            "ocrmnavigator.insertR3g10n": "alt+r",
>            "ocrmnavigator.insertEndR3g10n": "alt+e",
>            "ocrmnavigator.wrapWithR3g10n": "alt+w",
>            "ocrmnavigator.openUi": "alt+q",
>            "clipboardManager.showHistory": "alt+h",
>            "bookmarks.show": "alt+b",
>            "ocrmnavigator.showGithubMenu": "alt+g",
>            "ocrmnavigator.openPkgJson": "alt+p",
>            "ocrmnavigator.openReadme": "alt+m"
>          },
>     ```
> 
>      </details>
> 
> - autorun  ➜  during creating one of the new objects instead of re-inventing my own wheel, each every category or items in the layout engine I'm be adopting the extension as a whole, which means if you are already familiar with the extension, the learning curve will be very very small unlike the first config. this object takes in vfs item configs, with a twist as it will have one different parameter available, "runPolicy": "once", // "once" | "onLoad" | "onReload", allowing you to not only execute what you want and need when you load into your instance, but also choose what runs when
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
>           "path": "ocrmnavigator.scanFileImports",
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
> - onClose  ➜  same as autorun but when you go to close vscode these will run, no special parameters in this object
>
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
> - editorGrid  ➜  this is completely different, and much easier this time around while also providing EVEN more options on how to layout your editors. Now you can do a 2x2 in a single editor group, or you can have a t-bone layout, new parameters are lineNumber and fold on a per file basis
>
>      <details closed><summary>editorGrid config</summary>
>
>     ```json
>         "editorGrid": {
>           "columns": 2,
>           "rows": 2,
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
> 
> - terminalGrid  ➜  same as above, these two are very reminiscent of stacking and configuring linux terminals
> 
>    <details closed><summary>terminalGrid config</summary>
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
> - git  ➜  values are branch, onload and onclose
>
>    <details closed><summary>git config</summary>
>
>     ```json
>        "git": {
>         "branch": "dev",
>         "onLoad": [
>           {
>             "label": "pnpm i & ini / push prisma & ini .env & run scaffolding",
>             "path": "install, iniPrisma, iniEnv, scaffolding",
>             "type": "chain"
>           }
>         ],
>         "onClose": [
>           {
>             "label": "pnpm i & ini / push prisma & ini .env & run scaffolding",
>             "path": "install, iniPrisma, iniEnv, scaffolding",
>             "type": "chain"
>           }
>         ]
>       },
>     ```
> 
>      </details>
> 
> - extensions  ➜  yes I know this extension is the best in terms of performance to feature parity ratio, but that doesn't mean I cannot control other peoples extensions and make them suck just that much less. This I wish I had before I started my own extension. On workspace context, or per config basis, or however you will end up using your layout engine, you will be able to control exactly which extensions will be active or disabled when you open your instance. It may not seem like much, but when 80-90% of the userbase can only have 10-20 extensions running at ANY given time, theres no point on installing more... but now you could have 50... shitty extensions installed but with a single click switch from actively coding to debugging for example, and completely swap out your active extensions. Opening the door to just how many tools you have access to at all times.
>
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
> 
> - workbench.colorCustomizations  ➜  same as before, no changes> 
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
> - performance  ➜  these next three, have completely changed and because of it also the entire layout engine did as well... which then lead me on to all the above changes, might as well if I'm already changing things. Anyways performance and workspace are both now dumping grounds for settings.json key:value pairs, I kept both so you could atleast have some organization. What ever settings you put in these two will overwrite any current settings within your workspaces settings.json file, no completely but if you have a setting in your config, meanwhile you already have it in settings.json, it will overwrite it. Whatever values you already have set in your, that will not be getting changed, stay the same
> - workspace  
> - customizeLayout  ➜  the items in this are a requirement, I would suggest just copying this object over into your config and set the values to whatever you need.
>
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
> The reason for the change, while everything worked, there were a few very annoying... they weren't bugs, or glitches... it's just with how vscode does NOT allow access to the ui's current context values, there were a couple of items that pissed me off enough to warrant all the work that I am now putting myself through again. Honeslty I'm glad I did this now because of all the new items that came from it. What this means moving forward though, the layout engine will not be relying on customize layout for anything, and only using it for the VERY few things... that you cannot do through any other feature. So any changes you want to do through the ui, will be through the settings.lson key:value pairs. I know how much of a pain, these fucking settings are, and because of just how much easier the layout engine has become, instead of creating a huge guide on each item I will instead, do a small guide to finish this off, BUT go over what I have personally done to change my ui. Because it is a dick of a chore to sit down and go through, even ai prompts will flat out tell you... thatthe majority of your key:value pairs are wrong, only to check the actual docs myself and dig through them not only did it happen once, or twice but 11 times today alone, each time it wasn't just one setting, but groups of them. Where the ai, straight up said, "no that is invalid, you are a dumb human" essentially. Finding out, the EXACT key and value pairs, with the same casing and everyhting, were infact correct. It's excuse, "it was too perfect of a naming convention, and because of that, and only that, it couldn't be correct", I kid you fucking not. Imagine your fucking colleague saying that to you, haha, HR would be of no help in that situation.




## Configuration Approachs

#### The quick and dirty method
Technically speaking... you can literally dump all the values you want / need to control within the `settings.workspace` object. As this object was created as a `dumping` ground for any and all vscode settings values. If all you want to use this for is a theme and very basic layout control, the only item you will need to configure is settings, by placing your values in either theme and workspace or both.

#### For ALOT more granular control



## Example Configs

<details closed><summary>The "T-Bone" Layout</summary>

```json
{ "name": "Big Terminal", "slot": [0, 1], "span": [2, 1] } 
// Starts at 0,1 and is 2 columns wide, 1 row high.
```

</details>


<details closed><summary>4x4 Terminal Grid Contained Within A Single Editor Group</summary>

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

<details closed><summary>Base Config</summary>

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
                    "group": 2,
                    "pinned": true,
                    "path": [
                      "src/extension.ts",
                      "src/helpers/master.ts",
                      "src/helpers/menus.ts",
                      "src/helpers/workspace.ts",
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
                      "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/global-navigator-config.json",
                      "F:/devstackBackUp/global-navigator-config.json",
                      "src/helpers/workspace.ts",
                      "F:/devstackBackUp/project-configs/project-1744496862041-y866zpqtd9.json",
                      "F:/devstackBackUp/project-configs/project-1757010936487-i30yr98a4p7.json"
                    ]
                  }
                ]
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
                "typescript.validate.enable": true,
                "workbench.editor.enablePreview": false 
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
                "editor.minimap.maxColumn": 50,
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
                "editor.minimap.renderCharacters": false,
                "editor.unicodeHighlight.invisibleCharacters": false,
                "editor.minimap.maxColumn": "50",
                "editor.minimap.size": "fill",
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
                "workbench.panel.opensMaximized": "always",
                "workbench.panel.defaultLocation": "bottom",
                "workbench.secondarySideBar.showLabels": false,
                "workbench.externalBrowser": "Opera",
                "workbench.activityBar.location": "right",
                "workbench.editor.showTabs": "multiple",

                "workbench.statusBar.visible": true,
                "workbench.sideBar.location": "right",
                "workbench.panel.defaultLocation": "bottom",
                "workbench.commandPalette.history": 30,
                "workbench.remoteIndicator.showExtensionRecommendations": false,
                "workbench.welcomePage.walkthroughs.openOnInstall": false,
                "workbench.panel.opensMaximized": "never",
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
                "window.openFilesInNewWindow": "default"
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
<br /><br />

> [!TIP] Additional Resources
> - [VS Code Settings Reference](https://code.visualstudio.com/docs/getstarted/settings)
> - [VS Code API Documentation](https://code.visualstudio.com/api)
> - [Workspace Configuration](https://code.visualstudio.com/docs/editor/workspaces)

---

[🡄 Return](https://github.com/8an3/DevStack)
