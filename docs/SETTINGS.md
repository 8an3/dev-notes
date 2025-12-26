#### Configuration Settings


All settings are prefixed with `ocrmnavigator.` and can be configured in your VS Code settings.

#### Core Settings

**Tasks & NPM Scripts**
- `tasks` (boolean, default: `true`) - Controls whether the 'Tasks' folder is displayed in DevStack explorer as a global folder. Items from tasks.json are automatically populated.
- `npmScripts` (boolean, default: `true`) - Controls whether the 'NPM Scripts' folder is displayed in DevStack explorer as a global folder. Items from package.json scripts are automatically populated.

**Performance Management**
- `todoNotesReminders` (boolean, default: `true`) - Enables initialization of todo, notes, reminders and post-its. Set to false to reload VS Code quicker when actively working on project issues, as this feature logs in and pulls a repo at initialization.
- `GBL_DISABLE` (boolean, default: `false`) - Global disable toggle. Do not set manually unless you need to change it back to false in settings.json.
- `WS_DISABLE` (boolean, default: `false`) - Workspace disable toggle. Do not set manually unless you need to change it back to false in settings.json.
- `F_DISABLE` (boolean, default: `false`) - File disable toggle. Do not set manually unless you need to change it back to false in settings.json.
- `EXT_DISABLE` (boolean, default: `false`) - Extension disable toggle. Do not set manually unless you need to change it back to false in settings.json.

#### Code Snapshot Settings

**Visual Appearance**
- `backgroundPalette` (enum, default: `"pinky"`) - Background gradient palette for code snapshots. Options: magnum, pinky, passion, steel, tropic, forest, blueman, sand
- `containerBackground` (string, default: `""`) - Custom background CSS that overrides backgroundPalette if set
- `boxShadow` (string, default: `"rgba(0, 0, 0, 0.55) 0px 20px 68px"`) - Box shadow for the snapshot window
- `containerPadding` (string, default: `"3em"`) - Padding around the snapshot container
- `windowBorderRadius` (string, default: `"10px"`) - Border radius for the snapshot window

**Window Controls**
- `windowControlStyle` (enum, default: `"Windows"`) - Window control style. Options: None, OS X, Gray dots, Windows
- `showWindowTitle` (boolean, default: `true`) - Show window title in snapshot
- `windowTitleStyle` (enum, default: `"Workspace + Filename"`) - Window title display format. Options: Workspace + Filename, Filename, Custom
- `windowTitleCustomStyle` (string, default: `""`) - Custom window title text (used when windowTitleStyle is 'Custom')

**Display Options**
- `showLineNumbers` (boolean, default: `true`) - Show line numbers in snapshot
- `realLineNumbers` (boolean, default: `false`) - Use real line numbers from editor (starts at actual line number in file)
- `transparentBackground` (boolean, default: `false`) - Use transparent background for snapshot
- `target` (enum, default: `"container"`) - Snapshot target. Options: container (includes background), window (just the code window)
- `trimEmptyLines` (boolean, default: `true`) - Trim empty lines from the beginning and end of snapshot

#### GitHub Integration

**Repository Configuration**
- `repo` (string, default: `""`) - Repository name (e.g., "DevStack")
- `owner` (string, default: `""`) - Repository owner username (e.g., "8an3")
- `branch` (string, default: `""`) - Branch name (e.g., "main")
- `repository` (string, default: `""`) - Full repository path (e.g., "8an3/DevStack")
- `remote` (string, default: `""`) - Remote repository URL (e.g., "https://github.com/8an3/DevStack.git")
- `ATAT` (string, default: `""`) - GitHub personal access token
- `octokit` (string, default: `""`) - Octokit configuration

**Sync Settings**
- `lastSyncTimestamp` (string, default: `""`) - Last synchronization timestamp
- `lastSHA` (string, default: `""`) - Last commit SHA
- `autoSync` (boolean, default: `true`) - Enable automatic synchronization
- `isPriv` (boolean, default: `false`) - Whether repository is private
- `syncOnSave` (boolean, default: `true`) - Sync on file save
- `syncInterval` (string, default: `"30"`) - Sync interval in minutes
- `checkRemindersInterval` (string, default: `"10"`) - Reminder check interval in minutes

#### Build & Automation Settings

**Package Management**
- `CONCURRENT` (string, default: `"stable"`) - Determines concurrent function mode. Options: 'stable', 'bleeding-edge'
- `PKG_MGR` (string, default: `"pnpm"`) - Fallback package manager for extension scanner

**Autorun Configuration**
- `AUTORUN_SCRIPTS` (boolean, default: `false`) - Within G4 & .vsix function, enables activation of all Node.js scripts in specified folder
- `AUTORUN_DIR` (string, default: `"src"`) - Directory containing the autorun folder (e.g., 'src' or 'app'). Leave empty to use workspace root.

**Build Options**
- `ARCHIVER` (string, default: `"custom"`) - Within G4 & .vsix function, chooses which archiver to use. Options: 'custom', 'vsce'
- `PRO7` (boolean, default: `false`) - Within G4 & .vsix function, enables secure archiving of secrets before pushing to GitHub
- `DELETE_OLD_VSIX` (boolean, default: `false`) - Within G4 & .vsix function, enables deletion of old vsix archives
- `AUTO_INSTALL_VSIX` (boolean, default: `false`) - Within G4 & .vsix function, enables auto-installing the archive
- `OPEN_PUB_DASH` (boolean, default: `false`) - Within G4 & .vsix function, enables auto-opening Microsoft's publisher dashboard
- `RELOAD_INSTANCE` (boolean, default: `false`) - Within G4 & .vsix function, enables auto-reload after installing newly created archive
- `UPDATE_PROMPT_OBJECTS` (boolean, default: `false`) - Updates prompt objects
- `CONVERT_README_DEV_MD` (boolean, default: `false`) - Converts README.dev.md to README.md during build

#### UI & Interface Settings

**Quick Pick Menus**
- `BE_QP` (boolean, default: `false`) - BE Quickpick menu found on the status bar

**Editor Behavior**
- `AUTO_FOLD_PKG` (boolean, default: `false`) - Auto fold level 2 when opening package.json
- `vscodeVersion` (string, default: `"Code"`) - VS Code version identifier. Use 'Code' for VS Code or 'Code - Insiders' for VS Code Insiders. Controls where settings files are pulled from.

**Navigation**
- `configPath` (string, default: `".vscode/ocrmnavigator/search-config.json"`) - Path to the search configuration file
- `toggleHiddenItems` (boolean, default: `true`) - Toggle visibility of chain items in UI (items with hidden: true)

#### Feature Toggles

**Development Tools**
- `commands` (boolean, default: `true`) - Enables VS Code commands
- `vscodecmdref` (boolean, default: `true`) - Enables VS Code commands reference sheet
- `markdownViewer` (boolean, default: `true`) - Enables markdown viewer
- `snippets` (boolean, default: `true`) - Enables snippets editor and viewer via nav
- `snippetsInEditor` (boolean, default: `true`) - Enables snippets via context menu in editor
- `editorContextSnippets` (boolean, default: `true`) - Enables Editor Context Snippets via context menu in editor
- `formatters` (boolean, default: `true`) - Enables formatters and configurator
- `trailingCommas` (boolean, default: `true`) - Enables removal function for trailing commas
- `batchRename` (boolean, default: `true`) - Enables batch rename via context menu in editor

**Framework-Specific Tools**
- `eslintPrettier` (boolean, default: `true`) - Enables adding ESLint & Prettier configs
- `remixUtils` (boolean, default: `true`) - Enables Remix utilities via context menu in editor
- `remixComponents` (boolean, default: `true`) - Enables Remix components via context menu in editor
- `shadCNComponents` (boolean, default: `true`) - Enables ShadCN Components via context menu in editor
- `convertToAgnostic` (boolean, default: `true`) - Enables Convert To Agnostic, converting a Remix Run route to your choice

**Theme & Appearance**
- `theme` (boolean, default: `true`) - Enables VS Code theme builder
- `blackedOut` (boolean, default: `true`) - Enables Blacked Out & Diff & Reset themes
- `windowDifferentiator` (boolean, default: `true`) - Enables Window Differentiator via context menu in editor
- `colorWheel` (boolean, default: `true`) - Enables color wheel tool

**Database & Backend**
- `prismaFunctions` (boolean, default: `true`) - Enables Prisma Functions via context menu in editor
- `clickToSchema` (boolean, default: `true`) - Enables click to schema object
- `crudResolvers` (boolean, default: `true`) - Enables Generate CRUD Resolvers / REST End Points via context menu in editor
- `strPrismaUpdater` (boolean, default: `true`) - Automatically adds scripts to package.json with specific custom commands. Runs when STR runs a task.

**Git & GitHub**
- `repoMgr` (boolean, default: `true`) - Enables GitHub Repo Management
- `openGithub` (boolean, default: `true`) - Enables 'Open GitHub Repo In Browser' via context menu in editor
- `githubFunctions` (boolean, default: `true`) - Enables Github Functions editor functions via context menu in editor

**File Management**
- `fileNesting` (boolean, default: `true`) - Enables file nesting
- `revealExplorer` (boolean, default: `true`) - Enables reveal in explorer via right-clicking items in nav
- `copyPath` (boolean, default: `true`) - Enables copy path via right-clicking items in nav
- `bookmarks` (boolean, default: `true`) - Enables bookmarks
- `searchBar` (boolean, default: `true`) - Enables the search bar function for the nav
- `createFolderSmartIndex` (boolean, default: `true`) - Enables Create Folder Smart Index (Registry)

**Utilities**
- `clipBoardHistory` (boolean, default: `true`) - Enables clipboard history pro
- `lucideIcons` (boolean, default: `true`) - Enables Lucide icons integration
- `share` (boolean, default: `true`) - Enables share with a friend
- `url` (boolean, default: `true`) - Enables URL links in the nav
- `viewers` (boolean, default: `true`) - Enables viewers functionality
- `uiDashboard` (boolean, default: `true`) - Enables UI Dashboard
- `tailwindConverter` (boolean, default: `true`) - Enables Tailwind Converter button within title bar menu

**Code Cleanup**
- `jsonComments` (boolean, default: `true`) - Enables removal function for JSON comments
- `con` (boolean, default: `true`) - Enables removal function for all console.logs from files
- `removeAllComments` (boolean, default: `true`) - Enables removal function for all comments from files
- `unusedFunctions` (boolean, default: `true`) - Enables unused function finder

**DevStack Features**
- `devStackFunctions` (boolean, default: `true`) - Enables DevStack editor functions via context menu in editor
- `concurrent` (boolean, default: `true`) - Enables the concurrent command feature set within DevStack
- `autoSequencer` (boolean, default: `true`) - Enables the chain command feature set within DevStack
- `openLeftOffNote` (boolean, default: `true`) - Enables Left Off Note
- `renderMd` (boolean, default: `true`) - Enables the render MD option within editor context menu

**Additional Settings**
- `PROMPT_OBJECTS_DIR` (string, default: `"F:/playground/md/"`) - MD prompt objects path
- `rootPath` (string, default: `""`) - Root path configuration
- `notesDir` (string, default: `""`) - Notes directory path
- `other` (string, default: `null`) - Other configuration options


#### Example Configuration

```json
{
  // Code Snapshot
  "ocrmnavigator.codesnap.windowControlStyle": "Windows",
  "ocrmnavigator.codesnap.showWindowTitle": true,
  "ocrmnavigator.codesnap.windowBorderRadius": "8px",
  "ocrmnavigator.codesnap.windowTitleStyle": "Filename",
  "ocrmnavigator.codesnap.showLineNumbers": true,
  "ocrmnavigator.codesnap.realLineNumbers": false,
  "ocrmnavigator.todoNotesReminders": true,
  "ocrmnavigator.codesnap.transparentBackground": false,
  "ocrmnavigator.codesnap.trimEmptyLines": false,

  // To do, notes, reminders and post its
  "ocrmnavigator.todo.repo": "mynotesrepo",
  "ocrmnavigator.todo.branch": "main",
  "ocrmnavigator.ATAT": "ghp_token",
  "ocrmnavigator.todo.checkRemindersInterval": "10",
  "ocrmnavigator.todo.syncInterval": "20",
  "ocrmnavigator.todo.syncOnSave": true,
  "ocrmnavigator.todo.owner": "8an3",
  "ocrmnavigator.todo.remote": "https://github.com/8an3/mynotesrepo.git",
  "ocrmnavigator.todo.repository": "8an3/mynotesrepo",
  "ocrmnavigator.todo.isPriv": false,

  // DevStack automation functionality
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

  // BE Quick Pick Menu
  "ocrmnavigator.BE_QP": true,

  // Auto fold on file open
  "ocrmnavigator.AUTO_FOLD_PKG": true,
  "ocrmnavigator.vscodeVersion": "Code - Insiders",
  "ocrmnavigator.configPath": ".vscode/ocrmnavigator/search-config.json",

  // Function Toggles
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
  "ocrmnavigator.autoSequencer": true
}
```
 
---

[🡄 Return](https://github.com/8an3/DevStack)