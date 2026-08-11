# BIFRÖST


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Reveal In Explorer

**Right-click any file → Reveal in Explorer**

Open file locations directly in Windows Explorer or macOS Finder from:
- DevStack sidebar
- Editor context menu
- Extensions pane

![Reveal in Explorer](https://raw.githubusercontent.com/8an3/midgardr-notes/main/vfs/reveal-in-explorer.jpg?raw=true)
  
## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Copy Path


**Right-click any file → Copy Path**

Copy full or relative file paths to clipboard. Works with multiple path formats throughout the extension.

[Video Demo](https://youtu.be/FWa6o5FK3sU)


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Search

**Access:** Click title bar button

Powerful search functionality to find and execute any command you've created. Preview commands before execution to ensure you're running the right one.

![Search Feature](https://raw.githubusercontent.com/8an3/midgardr-notes/main/vfs/search.jpg)

[Video Demo](https://youtu.be/pRVv7UaY4qM)



## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Configuration Settings

DevStack provides extensive configuration options to customize your development workflow. All settings are prefixed with `ocrmnavigator.` and can be configured in your VS Code settings.

---

#### File Opening Behavior

**`ocrmnavigator.vfs.onFileOpen`**
- **Type**: `string`
- **Default**: `"off"`
- **Options**: `"forceCenterFocus"`, `"openInSetCol"`, `"off"`
- **Description**: Controls how files open in the editor. See documentation in changelog for details.

**`ocrmnavigator.vfs.targetEditorGroup`**
- **Type**: `number`
- **Default**: `2`
- **Options**: `1-9`
- **Description**: Specifies which editor group (column) files should open in.

---

#### Advanced Search

**`ocrmnavigator.odin.contextLinesBefore`**
- **Type**: `number`
- **Default**: `4`
- **Description**: Number of lines to display before each search match for context.

**`ocrmnavigator.odin.contextLinesAfter`**
- **Type**: `number`
- **Default**: `10`
- **Description**: Number of lines to display after each search match for context.

**`ocrmnavigator.configPath`**
- **Type**: `string`
- **Default**: `".vscode/ocrmnavigator/search-config.json"`
- **Description**: Path to the search configuration file.

---

#### Auto-Folding

**`ocrmnavigator.vfs.AUTO_FOLD_1`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically fold code at level 1 when file opens.

**`ocrmnavigator.vfs.AUTO_FOLD_1_2`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically fold code at levels 1 and 2 when file opens.

**`ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2_3`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically fold package.json at levels 2 and 3 when file opens.

**`ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically fold package.json at level 2 when file opens.

---

#### TODO & Highlighting

**`ocrmnavigator.todo.highlight.enable`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Enable color highlighting for TODO items and marked lines.

**`ocrmnavigator.todo.highlightColor`**
- **Type**: `string`
- **Default**: `"#3b82f6"`
- **Description**: Hex color code for highlighting TODO items.

**`ocrmnavigator.todo.highlightOpacity`**
- **Type**: `number`
- **Default**: `0.2`
- **Range**: `0-1`
- **Description**: Opacity for the highlight background.

**`ocrmnavigator.todo.borderOpacity`**
- **Type**: `number`
- **Default**: `0.5`
- **Range**: `0-1`
- **Description**: Opacity for the highlight border.

**`ocrmnavigator.todoNotesReminders`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enables TODO, notes, reminders, and post-it functionality. Disable for faster reload times when troubleshooting.

---

#### Markdown Preprocessor

**`ocrmnavigator.markdownpreprocessor.variableSystem`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enable variable system in markdown preprocessor.

**`ocrmnavigator.markdownpreprocessor.sourcemapUpdater`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enable source map creation in markdown preprocessor.

**`ocrmnavigator.markdownpreprocessor.tocUpdater`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enable table of contents updater in markdown preprocessor.

**`ocrmnavigator.markdownpreprocessor.tocType`**
- **Type**: `string`
- **Default**: `"roman"`
- **Options**: `"unorderd"`, `"ordered"`, `"roman"`, `"accordian"`
- **Description**: Format style for table of contents generation.

**`ocrmnavigator.markdownpreprocessor.tableConversion`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enable table conversion in markdown preprocessor.

---

#### VFS Explorer Folders

**`ocrmnavigator.vfs.tasks`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Display 'Tasks' folder in DevStack explorer. Auto-populated from tasks.json.

**`ocrmnavigator.vfs.npmScripts`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Display 'NPM Scripts' folder in DevStack explorer. Auto-populated from package.json scripts.

**`ocrmnavigator.vfs.snippets`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Display 'Snippets' folder in DevStack explorer.

**`ocrmnavigator.vfs.item.hidden.toggle`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Remove chain items from UI (can reveal when editing). Affects items with `hidden: true`.

---

#### Code Snapshot (CodeSnap)

**`ocrmnavigator.codesnap.backgroundPalette`**
- **Type**: `string`
- **Default**: `"pinky"`
- **Options**: `"magnum"`, `"pinky"`, `"passion"`, `"steel"`, `"tropic"`, `"forest"`, `"blueman"`, `"sand"`
- **Description**: Background gradient palette for code snapshots.

**`ocrmnavigator.codesnap.containerBackground`**
- **Type**: `string`
- **Default**: `""`
- **Description**: Custom background CSS. Overrides backgroundPalette when set.

**`ocrmnavigator.codesnap.boxShadow`**
- **Type**: `string`
- **Default**: `"rgba(0, 0, 0, 0.55) 0px 20px 68px"`
- **Description**: Box shadow for snapshot window.

**`ocrmnavigator.codesnap.containerPadding`**
- **Type**: `string`
- **Default**: `"3em"`
- **Description**: Padding around snapshot container.

**`ocrmnavigator.codesnap.windowBorderRadius`**
- **Type**: `string`
- **Default**: `"10px"`
- **Description**: Border radius for snapshot window.

**`ocrmnavigator.codesnap.windowControlStyle`**
- **Type**: `string`
- **Default**: `"Windows"`
- **Options**: `"None"`, `"OS X"`, `"Gray dots"`, `"Windows"`
- **Description**: Window control style (traffic lights or Windows controls).

**`ocrmnavigator.codesnap.showWindowTitle`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Show window title in snapshot.

**`ocrmnavigator.codesnap.windowTitleStyle`**
- **Type**: `string`
- **Default**: `"Workspace + Filename"`
- **Options**: `"Workspace + Filename"`, `"Filename"`, `"Custom"`
- **Description**: Window title display format.

**`ocrmnavigator.codesnap.windowTitleCustomStyle`**
- **Type**: `string`
- **Default**: `""`
- **Description**: Custom window title text (used when windowTitleStyle is 'Custom').

**`ocrmnavigator.codesnap.showLineNumbers`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Show line numbers in snapshot.

**`ocrmnavigator.codesnap.realLineNumbers`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Use actual line numbers from file instead of starting at 1.

**`ocrmnavigator.codesnap.transparentBackground`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Use transparent background for snapshot.

**`ocrmnavigator.codesnap.target`**
- **Type**: `string`
- **Default**: `"container"`
- **Options**: `"container"`, `"window"`
- **Description**: Snapshot target. Container includes background, window is code only.

**`ocrmnavigator.codesnap.trimEmptyLines`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Trim empty lines from beginning and end of snapshot.

---

#### GitHub Integration

**`ocrmnavigator.todo.repo`**
- **Type**: `string`
- **Default**: `""`
- **Description**: GitHub repository name.

**`ocrmnavigator.todo.owner`**
- **Type**: `string`
- **Default**: `""`
- **Description**: GitHub repository owner.

**`ocrmnavigator.todo.branch`**
- **Type**: `string`
- **Default**: `""`
- **Description**: Git branch name.

**`ocrmnavigator.todo.repository`**
- **Type**: `string`
- **Default**: `""`
- **Description**: Full repository path (owner/repo).

**`ocrmnavigator.todo.remote`**
- **Type**: `string`
- **Default**: `""`
- **Description**: Git remote URL.

**`ocrmnavigator.todo.autoSync`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enable automatic syncing with repository.

**`ocrmnavigator.todo.isPriv`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Indicates if repository is private.

**`ocrmnavigator.todo.syncOnSave`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Automatically sync when saving files.

**`ocrmnavigator.todo.syncInterval`**
- **Type**: `string`
- **Default**: `"30"`
- **Description**: Sync interval in minutes.

**`ocrmnavigator.todo.checkRemindersInterval`**
- **Type**: `string`
- **Default**: `"10"`
- **Description**: Reminder check interval in minutes.

---

#### Extension Control

**`ocrmnavigator.GBL_DISABLE`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: ⚠️ Global disable flag. Only modify if you understand its purpose.

**`ocrmnavigator.WS_DISABLE`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: ⚠️ Workspace disable flag. Only modify if you understand its purpose.

**`ocrmnavigator.F_DISABLE`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: ⚠️ Feature disable flag. Only modify if you understand its purpose.

**`ocrmnavigator.EXT_DISABLE`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: ⚠️ Extension disable flag. Only modify if you understand its purpose.

---

#### Build & Deploy

**`ocrmnavigator.CONCURRENT`**
- **Type**: `string`
- **Default**: `"stable"`
- **Options**: `"stable"`, `"bleeding-edge"`
- **Description**: Determines which concurrent function version to run.

**`ocrmnavigator.PKG_MGR`**
- **Type**: `string`
- **Default**: `"pnpm"`
- **Description**: Fallback package manager for extension operations.

**`ocrmnavigator.AUTORUN_SCRIPTS`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Enable automatic execution of Node.js scripts in specified folder during g4 and .vsix functions.

**`ocrmnavigator.AUTORUN_DIR`**
- **Type**: `string`
- **Default**: `"src"`
- **Description**: Directory containing autorun folder. Leave empty to use workspace root.

**`ocrmnavigator.ARCHIVER`**
- **Type**: `string`
- **Default**: `"custom"`
- **Description**: Archiver choice for g4 and .vsix functions.

**`ocrmnavigator.PRO7`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Enable secure archiving of secrets before pushing to GitHub.

**`ocrmnavigator.DELETE_OLD_VSIX`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Delete old .vsix archives during build process.

**`ocrmnavigator.AUTO_INSTALL_VSIX`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically install newly created .vsix archive.

**`ocrmnavigator.OPEN_PUB_DASH`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically open Microsoft publisher dashboard after build.

**`ocrmnavigator.RELOAD_INSTANCE`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically reload VS Code after installing new archive.

**`ocrmnavigator.devstack.be`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Enable BQ Quick Pick menu on status bar.

---

#### Feature Toggles

All feature toggles default to `true` unless otherwise specified and can be disabled to improve performance or remove unwanted functionality.

**Core Features:**
- `ocrmnavigator.commands` - VSCode commands
- `ocrmnavigator.vscodecmdref` - VSCode commands reference sheet
- `ocrmnavigator.markdownViewer` - Markdown viewer
- `ocrmnavigator.devstack.site.snippets` - Snippets editor and viewer
- `ocrmnavigator.snippetsInEditor` - Snippets via editor context menu
- `ocrmnavigator.editorContextSnippets` - Editor context snippets
- `ocrmnavigator.formatters` - Formatters and configurator
- `ocrmnavigator.trailingCommas` - Remove trailing commas function
- `ocrmnavigator.batchRename` - Batch rename via context menu
- `ocrmnavigator.eslintPrettier` - Add ESLint & Prettier configs

**Framework Utilities:**
- `ocrmnavigator.remixUtils` - Remix utilities via context menu
- `ocrmnavigator.remixComponents` - Remix components via context menu
- `ocrmnavigator.shadCNComponents` - ShadCN components via context menu
- `ocrmnavigator.prismaFunctions` - Prisma functions via context menu
- `ocrmnavigator.clickToSchema` - Click to schema object navigation
- `ocrmnavigator.crudResolvers` - Generate CRUD resolvers/REST endpoints
- `ocrmnavigator.strPrismaUpdater` - Auto-add Prisma scripts to package.json

**Theme & UI:**
- `ocrmnavigator.theme` - VSCode theme builder
- `ocrmnavigator.vscode.theme.blacked` - Blacked Out & Diff & Reset themes
- `ocrmnavigator.vscode.theme.window.differentiator` - Window differentiator
- `ocrmnavigator.devstack.site.colorWheel` - Color wheel tool
- `ocrmnavigator.uiDashboard` - UI Dashboard

**GitHub & Repository:**
- `ocrmnavigator.repoMgr` - GitHub repository management
- `ocrmnavigator.openGithub` - Open GitHub repo in browser
- `ocrmnavigator.githubFunctions` - GitHub editor functions

**File Management:**
- `ocrmnavigator.fileNesting` - File nesting configuration
- `ocrmnavigator.revealExplorer` - Reveal in explorer
- `ocrmnavigator.vfs.item.path.copy` - Copy path from navigation
- `ocrmnavigator.searchBar` - Search bar for navigation

**Code Quality:**
- `ocrmnavigator.format.json.remove.comments.file` - Remove JSON comments
- `ocrmnavigator.con` - Remove all console.logs
- `ocrmnavigator.format.remove.comments.file` - Remove all comments
- `ocrmnavigator.unusedFunctions` - Find unused functions

**Additional Features:**
- `ocrmnavigator.bookmarks` - Bookmarks system
- `ocrmnavigator.clipBoardHistory` - Clipboard history pro
- `ocrmnavigator.lucideIcons` - Lucide icons integration
- `ocrmnavigator.share` - Share with a friend
- `ocrmnavigator.url` - URL links in navigation
- `ocrmnavigator.viewers` - Viewers functionality
- `ocrmnavigator.devStackFunctions` - DevStack editor functions
- `ocrmnavigator.leftOffNote.open` - Left Off Note feature
- `ocrmnavigator.devstack.site.md.render` - Render MD in editor context menu
- `ocrmnavigator.project.index.smart.create` - Create folder smart index
- `ocrmnavigator.devstack.site.tailwindConverter` - Tailwind converter button
- `ocrmnavigator.remix.project2agnostic.convert` - Convert Remix routes to agnostic
- `ocrmnavigator.vfs.concurrent.execute` - Concurrent command feature
- `ocrmnavigator.vfs.chain.execute` - Chain command feature

---

#### Advanced Settings

**`ocrmnavigator.UPDATE_PROMPT_OBJECTS`**
- **Type**: `boolean`
- **Default**: `false`

**`ocrmnavigator.CONVERT_README_DEV_MD`**
- **Type**: `boolean`
- **Default**: `false`

**`ocrmnavigator.PROMPT_OBJECTS_DIR`**
- **Type**: `string`
- **Default**: `"F:/playground/md/"`
- **Description**: Path to markdown prompt objects directory.

**`ocrmnavigator.rootPath`**
- **Type**: `string`
- **Default**: `""`

**`ocrmnavigator.octokit`**
- **Type**: `string`
- **Default**: `""`

**`ocrmnavigator.ATAT`**
- **Type**: `string`
- **Default**: `""`

**`ocrmnavigator.notesDir`**
- **Type**: `string`
- **Default**: `""`

**`ocrmnavigator.other`**
- **Type**: `string`
- **Default**: `null`
- **Description**: Miscellaneous configuration option.

---


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Usage


All item types share common actions:
- **Add**: Create new items through the interface
- **Edit**: Modify existing items
- **Remove**: Delete items from configuration
- **Trigger**: Click items in the extensions window to execute

Set item type in config object or click the plus icon in the title pane.

#### Previews

- **Navigation View**: [Image](https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/nav-view.jpg?raw=true)
- **Sequential Execution**: [Video](https://youtu.be/ySp83VqxQ8s) | [Image](https://raw.githubusercontent.com/8an3/midgardr-notes/blob/main/vfs/SequentialExecution+.gif?raw=true)


