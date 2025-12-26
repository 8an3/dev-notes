### Complete Example Configuration

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
          "label": "UNFOLD All", 
          "path": "editor.unfoldAll", 
          "type": "command", 
          "icon": "unfold" 
        },
        { 
          "label": "seed.ts", 
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
          "label": "Kill Terminals && Start DEV Server", 
          "path": "saveall, killterms, devApp", 
          "type": "chain" 
        },
        { 
          "label": "dev:all", 
          "path": "devApp, devCalc", 
          "type": "concurrent" 
        },
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
        },
        { 
          "label": "Open Settings", 
          "type": "command", 
          "path": "workbench.action.openSettings", 
          "args": ["editor.fontSize"] 
        },
        { 
          "label": "ARCHIVER", 
          "path": "ocrmnavigator.ARCHIVER", 
          "type": "settingsToggle", 
          "args": ["custom", "vsce"], 
          "icon": "settings" 
        },
        { 
          "label": "NPM Scripts", 
          "path": "ocrmnavigator.vfs.npmScripts", 
          "type": "settingsToggle", 
          "icon": "settings" 
        },
        { 
          "label": "Check API Status", 
          "path": "https://api.example.com/status", 
          "type": "apiCall", 
          "icon": "cloud", 
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
          "label": "console.log(", 
          "path": "regex pattern to find console.log(", 
          "type": "search", 
          "icon": "search" 
        },
        { 
          "label": "VLC w/ playlist", 
          "path": "cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' playlist.xspf", 
          "type": "debianCMD" 
        },
        { 
          "label": "Copy to clipboard", 
          "path": "Value to be copied into the clipboard", 
          "type": "copyValue" 
        },
        { 
          "label": "prisma.schema", 
          "path": "prisma/prisma.schema", 
          "type": "file" 
        },
        { 
          "label": "Snippet Name", 
          "path": "ocrmnavigator.code-snippets", 
          "type": "snippet" 
        },
        {
          "label": "DevStack Default",
          "path": "", 
          "type": "layout",
          "icon": "editor-layout",
          "args": [
            { "default": true },
            { "primarySidebar": "left" },
            { "quickInputPosition": "center" },
            { "modes": "center" },
            { "panelAlignment": "right" },
            { "sidebar": "Explorer" },
            { "devstack": true },
            { "zoomLevel": -1 },
            { "pinned": ["global-navigator-config.json"] },
            {
              "visibility": {
                "menuBar": true,
                "activityBar": true,
                "primarySidebar": true,
                "secondarySidebar": true,
                "panel": false,
                "statusBar": true
              }
            },
            {
              "tabs": [
                "src/extension.ts",
                "src/helpers/master.ts",
                "src/helpers/menus.ts",
                "src/helpers/workspace.ts",
                "src/extension/navigatorView.ts",
                "src/helpers/itemsActionsMenu.ts",
                "F:/devstackBackUp/global-navigator-config.json",
                "src/helpers/modular-commands.ts",
                "README.dev.md",
                "package.dev.jsonc",
                "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/global-navigator-config.json"
              ]
            },
            {
              "terminals": [
                { "name": "Server", "cmd": "npm run dev", "location": "editor" },
                { "name": "Logs", "cmd": "tail -f dev.log", "location": "panel" }
              ]
            },
            {
              "theme": {
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
      ]
    }
  ]
}
```



#### Usage

All item types share common actions:
- **Add**: Create new items through the interface
- **Edit**: Modify existing items
- **Remove**: Delete items from configuration
- **Trigger**: Click items in the extensions window to execute

Set item type in config object or click the plus icon in the title pane.

#### Previews

- **Navigation View**: [Image](https://raw.githubusercontent.com/8an3/dev-notes/main/ui/nav-view.jpg?raw=true)
- **Sequential Execution**: [Video](https://youtu.be/ySp83VqxQ8s) | [Image](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/vfs/SequentialExecution+.gif?raw=true)



---
[🡄 Return](https://github.com/8an3/DevStack)