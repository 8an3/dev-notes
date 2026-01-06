### Clipboard History Pro

Multi-item clipboard manager that tracks and stores your clipboard history.

**Access:** Click `Clipboard++` on the status bar

**Features:**
- Track last 20 clipboard items
- Hover previews for quick reference
- Status bar access for convenience
- Persistent storage across sessions
- Quick paste from history

---

### Global Bookmarking System

Never lose your place in large projects again. The extension provides a persistent, global bookmarking system that allows you to tag specific lines of code and jump back to them instantly, even after restarting VS Code.

✨ Key Features
Persistent Storage: Bookmarks are saved to a bookmarks.json file in your global storage, ensuring they survive across sessions and workspaces.

Status Bar Integration: A permanent $(bookmark) Bookmarks item in your Status Bar provides one-click access to your list.

Quick-Access Navigation: Use the Quick Pick menu to search and filter your bookmarks. They are sorted by "most recent," so your latest work is always at the top.

Automatic Cleanup: To keep things fast and organized, the system maintains a rolling limit of 100 bookmarks, automatically removing the oldest ones as you add new ones.

Smart Updates: Adding a bookmark to a line that is already bookmarked will refresh its position to the top of your list.

#### Commands 

- ocrmnavigator.bookmarks.add
  - Adds the current line in the active editor to your bookmarks
  - Right-click line → DevStack → Add Bookmark
- ocrmnavigator.bookmarks.show
  - Bookmarks button in status bar

#### 🛠 Technical Details
Storage Location: %AppData%/Code/User/globalStorage/[extension-id]/bookmarks.json

Relative Paths: The navigation menu displays relative paths to make it easier to identify files within your current workspace.

#### Pro-Tip: How to Use
Place your cursor on a line you want to remember.

Right-click line → DevStack → Add Bookmark

Later, click the $(bookmark) Bookmarks icon in the Status Bar to see your history and jump back instantly.

![Bookmarks](https://raw.githubusercontent.com/8an3/dev-notes/main/bookmarks/bookmark.jpg?raw=true)

---


### Icons

A quick pick hosting every avialable icon from the icons library, that can be searched and each item is alphabetically organized

Once an item has been selected it either places it into your clipboard for use or auto inserts at cursor while placing the import function at the top of your file

too use you would need: `pnpm i @catalystsoftware/icons`


### DevStack Quick Pick

**Access:** Press `Alt + Shift + D`

A comprehensive quick-access menu for all DevStack features including formatters, database operations, and build processes.


```markdown
DEVSTACK_MENU_SYSTEM/
│
├── 📂 BUILD_&_GITHUB/
│   ├── 📄 G4 & .vsix .......................... Auto commit, push, upgrade & build VSIX
│   ├── 📄 Upgrade Patch Version ............... Bump patch version number
│   └── 📄 Custom VSIX Packager ................ Compile project with custom archiver
│
├── 📂 MARKDOWN/
│   └── 📄 Markdown Pre-Processor .............. Convert/process README files
│
├── 📂 SEARCH/
│   └── 📄 Search Editor PRO ................... Advanced search interface
│
├── 📂 VSCODE/
│   └── 📄 R Window ............................ Reload VSCode window
│
├── 📂 ENVIRONMENT/
│   ├── 📄 Open .dev.env ....................... Access development environment vars
│   ├── 📄 Set Local .env Var's ................ Configure local environment
│   └── 📄 Set Remote .env Var's ............... Configure remote environment
│
├── 📂 CONFIG/
│   ├── 📄 GBL DevStack Config ................. Global DevStack configuration
│   └── 📄 WS DevStack Config .................. Workspace DevStack configuration
│
├── 📂 SETTINGS/
│   ├── 📄 GBL Settings File ................... Global VSCode settings
│   └── 📄 WS Settings File .................... Workspace VSCode settings
│
├── 📂 MENUS/
│   ├── 📄 DevStack Config ..................... DevStack configuration menu
│   ├── 📄 Shortcuts ........................... Keyboard shortcuts reference
│   ├── 📄 VSCode .............................. VSCode-specific menu
│   ├── 📄 Catalyst-UI ......................... Catalyst UI component menu
│   ├── 📄 DevStack ............................ Main DevStack menu (recursive)
│   ├── 📄 DevStack Cmds ....................... DevStack commands catalog
│   ├── 📄 VSCode Cmds ......................... VSCode commands list
│   ├── 📄 VSCode Cmds Dynamic ................. Dynamic command browser
│   ├── 📄 Icons ............................... Icon selector/reference
│   ├── 📄 To do / Notes ....................... GitHub sync & todo settings
│   ├── 📄 GitHub .............................. GitHub automation menu
│   ├── 📄 Fold ................................ Code folding options
│   ├── 📄 File System ......................... File system operations
│   └── 📄 Prisma Functions .................... Database/Prisma utilities
│
├── 📂 CODE_SNAP/
│   └── 📄 Code Snap ........................... Take code screenshots
│
├── 📂 VSC_EXT_TESTING_SUITE/
│   ├── 📄 Test Set Config Command ............. Test configuration settings
│   ├── 📄 Get Config Command Value ............ Retrieve config values
│   ├── 📄 Test Set VSCode Context ............. Test context manipulation
│   └── 📄 Get Current Context State ........... View current context
│
├── 📂 ICONS_MENU/
│   └── 📄 [Dynamic Icon List] ................. Copy icon codes to clipboard
│
├── 📂 DEVSTACK_SUBMENU/
│   │
│   ├── 📂 SNIPPETS/
│   │   └── 📄 Import Snippets ................. Import code snippets
│   │
│   ├── 📂 PERFORMANCE_SWITCH/
│   │   ├── 📄 Toggle Current File Type Disable  Disable features for file type
│   │   ├── 📄 Toggle Workspace Disable ........ Workspace-level feature toggle
│   │   ├── 📄 Toggle Global Disable ........... Global feature toggle
│   │   ├── 📄 Toggle Extension Disable ........ Extension-level toggle
│   │   ├── 📄 Toggle Json Validation .......... JSON validation on/off
│   │   └── 📄 Toggle Jsonc Validation ......... JSONC validation on/off
│   │
│   ├── 📂 AUTOMATION/
│   │   └── 📄 Trigger Autorun Folder .......... Execute folder automation
│   │
│   ├── 📂 TOOLS/
│   │   ├── 📄 Tools ........................... Color wheel tool
│   │   ├── 📄 Catalyst Editor ................. Monaco MD editor
│   │   ├── 📄 Tailwind Converter .............. Tailwind utility converter
│   │   ├── 📄 Encoder ......................... Encoding utilities
│   │   └── 📄 RTE - Rich Text Editor .......... Rich text editing
│   │
│   └── 📂 UI_LIBRARY/
│       ├── 📄 Editor .......................... Code editor component
│       ├── 📄 Table ........................... Data table component
│       ├── 📄 Rich Text Editor ................ RTE component
│       ├── 📄 Event Calendar .................. Calendar component
│       ├── 📄 Appointment Scheduler ........... Scheduling component
│       ├── 📄 Messenger ....................... Chat/messaging component
│       └── 📄 Automotive Calculator ........... Auto calculation component
│
├── 📂 BUILD_PROJECT_MENU/
│   │
│   ├── 📂 AUTOMATION/
│   │   ├── 📄 G3 .............................. Auto commit & push
│   │   ├── 📄 G4 .............................. Auto commit, push & upgrade
│   │   ├── 📄 G4 & Push Vercel ................ Deploy to Vercel
│   │   ├── 📄 G4 & Pub To NPM ................. Publish to NPM registry
│   │   ├── 📄 Patch Version ................... Increment patch version
│   │   ├── 📄 Npm Publish ..................... NPM package publish
│   │   ├── 📄 Push Vsix Via Vsce .............. Publish extension via vsce
│   │   ├── 📄 Push Vsix Via Rest Api .......... Publish via REST API
│   │   ├── 📄 Bump Patch Version .............. Version bump (patch)
│   │   ├── 📄 Bump Minor Version .............. Version bump (minor)
│   │   ├── 📄 Bump Major Version .............. Version bump (major)
│   │   ├── 📄 Execute Order 1 ................. Workflow step 1
│   │   ├── 📄 Execute Order 2 ................. Workflow step 2
│   │   ├── 📄 Execute Order 3 ................. Workflow step 3
│   │   ├── 📄 Execute Order 4 ................. Workflow step 4
│   │   ├── 📄 Execute Order 5 ................. Workflow step 5
│   │   ├── 📄 Execute Order 6 ................. Workflow step 6
│   │   ├── 📄 Execute Order 7 ................. Workflow step 7
│   │   ├── 📄 Execute Order 8 ................. Workflow step 8
│   │   └── 📄 Execute Order 9 ................. Workflow step 9
│   │
│   ├── 📂 COMMANDS/
│   │   ├── 📄 Git Add ......................... Stage files for commit
│   │   ├── 📄 Git Com ......................... Create commit
│   │   ├── 📄 Git Push ........................ Push to remote
│   │   ├── 📄 Git Push Modular ................ Modular push workflow
│   │   └── 📄 Git Push Tags ................... Push tags to remote
│   │
│   └── 📂 BUILD_&_ARCHIVE/
│       ├── 📄 Pro7 Archiver ................... 7-Zip archive creation
│       └── 📄 Compile With Archiver ........... Build & archive project
│
├── 📂 TODO_SETTINGS_MENU/
│   │
│   ├── 📂 INITIAL_SETUP/
│   │   ├── 📄 Set All ......................... Configure all GitHub settings
│   │   ├── 📄 Set Branch ...................... Set target branch
│   │   ├── 📄 Set Private ..................... Set repository privacy
│   │   ├── 📄 Set Repo ........................ Set repository name
│   │   └── 📄 Set Access Token ................ Configure PAT
│   │
│   ├── 📂 REPO_OPTIONS/
│   │   ├── 📄 Create Repo ..................... Initialize new repository
│   │   ├── 📄 List Repo ....................... Browse repositories
│   │   ├── 📄 Sync ............................ Sync with remote
│   │   ├── 📄 Git Push ........................ Push changes
│   │   └── 📄 Change Repo ..................... Switch active repository
│   │
│   └── 📂 GITHUB_ACTIONS/
│       ├── 📄 Web GUI ......................... Open web interface
│       ├── 📄 Basic ........................... Basic GitHub operations
│       ├── 📄 ADV ............................. Advanced GitHub operations
│       └── 📄 Settings ........................ GitHub sync settings
│
├── 📂 GITHUB_BASIC_MENU/
│   ├── 📄 Commit .............................. Create commit
│   ├── 📄 Changes ............................. View changes
│   ├── 📄 Pull ................................ Pull from remote
│   ├── 📄 Push ................................ Push to remote
│   ├── 📄 Pull Push ........................... Pull then push
│   ├── 📄 Sync ................................ Synchronize with remote
│   ├── 📄 Branch .............................. Branch operations
│   ├── 📄 Remote .............................. Remote management
│   ├── 📄 Stash ............................... Stash operations
│   └── 📄 Tags ................................ Tag management
│
├── 📂 GITHUB_ADVANCED_MENU/
│   ├── 📄 Clone ............................... Clone repository
│   ├── 📄 Checkout ............................ Checkout branch/commit
│   ├── 📄 Fetch ............................... Fetch from remote
│   ├── 📄 Tags ................................ Advanced tag operations
│   └── 📄 Diff Cached ......................... View staged changes
│
├── 📂 GITHUB_SETTINGS_MENU/
│   ├── 📄 Patch Version ....................... Version management
│   ├── 📄 Share Repo .......................... Add collaborators
│   ├── 📄 Remove Collab ....................... Remove collaborators
│   ├── 📄 Set Access Token .................... Update PAT
│   ├── 📄 Show Access Token ................... Display current PAT
│   ├── 📄 Navigate To Token Gen ............... Open GitHub token page
│   ├── 📄 Configure Github Sync ............... Sync configuration
│   ├── 📄 Go to Settings File ................. Open settings JSON
│   ├── 📄 Place All Settings In Clipboard ..... Copy all settings
│   ├── 📄 Reload Ext .......................... Reload extension
│   ├── 📄 Toggle Auto Sync .................... Auto-sync on/off
│   ├── 📄 Reset Local Directory Pull Repo ..... Reset & re-pull
│   ├── 📄 Custom Cmd .......................... Execute custom command
│   └── 📄 Show Config ......................... Display configuration
│
├── 📂 FOLD_MENU/
│   ├── 📄 Fold Parents ........................ Collapse parent regions
│   ├── 📄 Fold Region Level 1 ................. Fold level 1 regions
│   ├── 📄 Fold Region Level 2 ................. Fold level 2 regions
│   ├── 📄 Fold Region Level 3 ................. Fold level 3 regions
│   ├── 📄 Fold Region Level 4 ................. Fold level 4 regions
│   ├── 📄 Fold Region Level 5 ................. Fold level 5 regions
│   ├── 📄 Fold Region Level 6 ................. Fold level 6 regions
│   ├── 📄 Fold Region Level 7 ................. Fold level 7 regions
│   ├── 📄 Toggle Region Level 1 ............... Toggle level 1 regions
│   ├── 📄 Toggle Region Level 2 ............... Toggle level 2 regions
│   ├── 📄 Toggle Region Level 3 ............... Toggle level 3 regions
│   ├── 📄 Toggle Region Level 4 ............... Toggle level 4 regions
│   ├── 📄 Toggle Region Level 5 ............... Toggle level 5 regions
│   ├── 📄 Toggle Region Level 6 ............... Toggle level 6 regions
│   └── 📄 Toggle Region Level 7 ............... Toggle level 7 regions
│
├── 📂 FILE_SYSTEM_MENU/
│   ├── 📄 Clean * ............................. Clean build artifacts
│   ├── 📄 Duke NUKEM .......................... Nuclear clean operation
│   ├── 📄 I ................................... Initialize project
│   └── 📄 build ............................... Build project
│
├── 📂 VSCODE_MENU/
│   │
│   ├── 📂 FORMAT/
│   │   ├── 📄 Format Json File ................ Format any JSON file
│   │   └── 📄 Format Current Json File ........ Format active JSON file
│   │
│   ├── 📂 VSCODE/
│   │   ├── 📄 Search Editor ................... Search extensions
│   │   ├── 📄 R EXT ........................... Reload extensions
│   │   ├── 📄 R TS ............................ Restart TypeScript server
│   │   └── 📄 DevTools ........................ Open developer tools
│   │
│   ├── 📂 VSIX/
│   │   └── 📄 Install Archive ................. Install VSIX from file
│   │
│   └── 📂 COMMANDS/
│       ├── 📄 Open Global Keybindings ......... Edit keybindings
│       ├── 📄 Auto Zombie Process Killer ...... Auto-kill zombie processes
│       └── 📄 Zombie Process Killer ........... Manual zombie killer
│
├── 📂 PRISMA_FUNCTIONS_MENU/
│   ├── 📄 * Remote ............................ All operations (remote)
│   ├── 📄 * Local ............................. All operations (local)
│   ├── 📄 Reset ............................... Reset database
│   ├── 📄 Push ................................ Push schema to database
│   ├── 📄 Seed ................................ Seed database
│   ├── 📄 Generate ............................ Generate Prisma client
│   ├── 📄 Studio .............................. Open Prisma Studio
│   └── 📄 Migrate Reset ....................... Reset migrations
│
├── 📂 SHORTCUTS_MENU/
│   ├── 📄 ALT + S → DevStack Search Editor .... Quick search interface
│   ├── 📄 ALT + D → DevStack QP ............... DevStack quick pick
│   ├── 📄 ALT + I → Icons ..................... Icon selector
│   ├── 📄 ALT + U → Catalyst UI QP ............ Catalyst UI menu
│   ├── 📄 ALT + S → Context Snippets .......... Snippet insertion
│   ├── 📄 ALT + R → Insert #region ............ Insert region marker
│   ├── 📄 ALT + E → Insert #endregion ......... Insert end marker
│   ├── 📄 ALT + W → Wrap W/ #region ........... Wrap with region
│   ├── 📄 ALT + Q → Web UI .................... Open web UI
│   ├── 📄 ALT + H → History ................... View history
│   ├── 📄 ALT + B → Bookmarks ................. Manage bookmarks
│   ├── 📄 ALT + G → GitHub Menu ............... GitHub operations
│   ├── 📄 ALT + P → Open Package.json ......... Open package file
│   └── 📄 ALT + M → Open Readme ............... Open README file
│
└── 📂 CATALYST_UI_MENU/
    ├── 📄 Open Tailwind Plugins Menu .......... Tailwind preset management
    ├── 📄 Create tailwind.css ................. Generate base CSS file
    ├── 📄 Create tailwind.config.js ........... Generate config file
    ├── 📄 Create base tailwind.config.js ...... Generate base config
    └── 📄 Create postcss.config.js ............ Generate PostCSS config
```
