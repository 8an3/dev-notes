# BIFRÖST

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Configuration Settings


All settings are prefixed with `ocrmnavigator.` and can be configured in your VS Code settings.

### Core Settings

**Tasks & NPM Scripts**
- `tasks` (boolean, default: `true`) - Controls whether the 'Tasks' folder is displayed in DevStack explorer as a global folder. Items from tasks.json are automatically populated.
- `npmScripts` (boolean, default: `true`) - Controls whether the 'NPM Scripts' folder is displayed in DevStack explorer as a global folder. Items from package.json scripts are automatically populated.

**Performance Management**
- `todoNotesReminders` (boolean, default: `true`) - Enables initialization of todo, notes, reminders and post-its. Set to false to reload VS Code quicker when actively working on project issues, as this feature logs in and pulls a repo at initialization.
- `GBL_DISABLE` (boolean, default: `false`) - Global disable toggle. Do not set manually unless you need to change it back to false in settings.json.
- `WS_DISABLE` (boolean, default: `false`) - Workspace disable toggle. Do not set manually unless you need to change it back to false in settings.json.
- `F_DISABLE` (boolean, default: `false`) - File disable toggle. Do not set manually unless you need to change it back to false in settings.json.
- `EXT_DISABLE` (boolean, default: `false`) - Extension disable toggle. Do not set manually unless you need to change it back to false in settings.json.

### Code Snapshot Settings

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

### GitHub Integration

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

### Build & Automation Settings

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

### UI & Interface Settings

**Quick Pick Menus**
- `BE_QP` (boolean, default: `false`) - BE Quickpick menu found on the status bar

**Editor Behavior**
- `AUTO_FOLD_PKG` (boolean, default: `false`) - Auto fold level 2 when opening package.json
- `vscodeVersion` (string, default: `"Code"`) - VS Code version identifier. Use 'Code' for VS Code or 'Code - Insiders' for VS Code Insiders. Controls where settings files are pulled from.

**Navigation**
- `configPath` (string, default: `".vscode/ocrmnavigator/search-config.json"`) - Path to the search configuration file
- `toggleHiddenItems` (boolean, default: `true`) - Toggle visibility of chain items in UI (items with hidden: true)

### Feature Toggles

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







#



<!-- 

First Ættr (Freyr's Ættr)

- ᚠ (Fehu) - Cattle, wealth, prosperity
- ᚢ (Uruz) - Aurochs, strength, vitality
- ᚦ (Thurisaz) - Thorn, giant, Thor's hammer, force
- ᚨ (Ansuz) - God, Odin, wisdom, communication
- ᚱ (Raidho) - Ride, journey, wheel, movement
- ᚲ (Kenaz) - Torch, knowledge, craft, transformation
- ᚷ (Gebo) - Gift, exchange, partnership
- ᚹ (Wunjo) - Joy, glory, perfection

Second Ættr (Heimdall's Ættr)

- ᚺ (Hagalaz) - Hail, disruption, transformation
- ᚾ (Nauthiz) - Need, necessity, constraint
- ᛁ (Isa) - Ice, stillness, stasis
- ᛃ (Jera) - Year, harvest, cycles, reward
- ᛇ (Eihwaz) - Yew tree, Yggdrasil, endurance
- ᛈ (Perthro) - Dice cup, mystery, fate, secrets
- ᛉ (Algiz) - Elk, protection, defense
- ᛊ (Sowilo) - Sun, success, wholeness, victory

Third Ættr (Tyr's Ættr)

- ᛏ (Tiwaz/Tyr) - Tyr, justice, honor, victory
- ᛒ (Berkano) - Birch, birth, growth, new beginnings
- ᛖ (Ehwaz) - Horse, partnership, movement, trust
- ᛗ (Mannaz) - Man, humanity, mind, memory
- ᛚ (Laguz) - Water, lake, flow, chaos, intuition
- ᛜ (Ingwaz) - Ing/Freyr, fertility, abundance, potential
- ᛞ (Dagaz) - Day, dawn, awakening, breakthrough
- ᛟ (Othala) - Inheritance, homeland, heritage, ancestral property


- Contained within the extension:
  - ᛒ BROKKR - layout ngin The dwarf craftsman who forged Mjölnir and other legendary items
  - ᛒ BIFRÖST - Terminal & Multi-Kernel Ngin
  - ᚨ ODIN - search editor 
  - ᚹ VALHALLA - data storage 
  - ᚱ RÚNAR - snippets
  - no name (Current: File Navigation System) World tree connecting all realms perfect for file/system navigation suggests "connecting everything"
  - ᚹ VÖLUNDR - 
  - ᚺ HUGINN & ᛗ MUNINN - Remix/Prisma utilities
  - ᛏ TYR - Port & Process/Errors
  - ᛜ FREYR - VS Code Styling/Theming
  - ᛊ SKÁLD - Catalyst Editor
  - ᚱ RATATOSKR - File Tree Builder/Visualization tool
  - ᚹ VIÐARR - Automation events
  - 𐌍 NEMESIS - Create Incoming Tunnel
  - 𐌇 HERACLES - Batch Rename
  - ☿ HERMÓÐR - API Secret Grabber
  - ᚺ HEIMDALLR - react preformance fucntions
  - ᚺ HÖFUÐ	- Intellisense Schema Ngin	
  - ᛊ SAGA - to dos notes and reminders
  - ᚷ GINNUNGAGAP - 
  - ᚢ URÐR - Snapshot Engine 
  - ᚹ VEÐRFÖLNIR - VSCInfo 

I need to name some of the other tools and things I have created before I continue on with the next item on the agenda
- ITEMS THAT HAVE ALREADY BEEN ASSIGNED A NAME
- NAMED APPS
  - consumer apps
    - ᚹ VALHALLA - Realtor CRM 
    - SLEIPNIR - Automotive Dealer CRM
    - FREYR - Restaurant POS
    - TYR - Store POS
    - FORSETI - Lawyer CRM
  - dev apps
    - a5gard - npm org / A5GARD github org
    - ᛚ LOKI - AI
    - ᛒ BIFRÖST - Template installer/creator
    - ᛒ BIFRÖST-PLUGIN - Plugin installer/creator
    - ᛇ YGGDRASIL - Central CLI hub (connects all tools)
    - ᛗ MIÐGARÐR - formerly know as Catalyst UI & @a5gard/migardr-ui is a npm libarry that will now get cahnged
    - ᚦ THOR - CSS/tailwind
    - ᛒ BALDR - @catalystsoftware/icons
    - ᛗ MÍMIR - DevArchive?
    - ᚨ ODIN - IDE Editor
    - GULLVEIG - Auto Finance Calculator
    - ᛊ SKÁLD - Catalyst Editor & Rich Text Editor
    - ᚱ RÚNAR - Snippets
    - ☿ HERMÓÐR - Messenger 
    - ᛊ SAGA - Appointment Scheduler
    - ᚢ URÐR - Event Calendar
    - GRÍÐR - table, wrapper for tanstacks table
  - 1. Have I followed the `MANDATORY DIRECTIVE` to 100% completion? [YES]
2. I have followed the `MANDATORY DIRECTIVE #2` and confirmed I have NO missing information [YES]
3. I understand what I am permitted to do as well as what I am NOT permitted to do... [YES]
4. I understand that it is required to ask myself specific questions before:
   1. starting each task and / or instruction... [YES]
   2. coding each function and / or component... [YES]
5. I have missing information and need to ask questions: [NO]
   - I have all information needed to proceed

---

| Item | Assigned Name | Rune | Rationale |
|---|---|---|---|
| dual sidebar | **JANUS** | — | Two-faced god; two sides |
| remix utilities | **MUNINN** | ᛗ | Memory/thought — framework recall utilities |
| color wheel picker | **ÍVALDI** | ᛁ | Master forger of treasures; crafting color |
| emoji picker | **HNOSS** | — | Freyja's daughter meaning "treasure/jewel" |
| react sandbox | **GINNUNGAGAP** | ᚷ | Primordial void of potential; modules born here |
| virtual list | **NIDHOGG** | — | Endlessly processes what's beneath the surface |
| async throttle | **SKOLL** | — | Wolf that chases but never catches |
| batch | **MAGNI** | — | Raw strength; moves many at once |
| queue | **URÐR** | ᚢ | That which has become — ordered, sequential fate |
| rate limiter | **HATI** | — | The wolf held just at bay |
| throttle | **VEÐRFÖLNIR** | ᚹ | Eagle atop Yggdrasil; watches, paces, controls |
| react app layer data store | **DRAUPNIR** | — | Odin's ring that self-replicates; reactive state |
| vanilla app layer data store | **GUNGNIR** | — | Odin's spear; precise, framework-agnostic |
| server + client layer data store | **YMIR** | — | Primordial source all things are built from |
| employee punch clock | **VÖLUNDR** | ᚹ | Master craftsman tracking labor |
| command (cmdk) | **HUGINN** | ᚺ | Odin's raven Thought; instant command recall |
| barcode / qr code | **HÖFUÐ** | ᚺ | Heimdallr's sword; the sharp edge of identification |
| heat map calendar | **VIÐARR** | ᚹ | Silent, observant; maps activity over time |
| lo-fi library | **SJÖFN** | — | Goddess of lightweight affection; gentle fidelity |
| pdf umbrella | **BRAGI** | — | God of poetry and written narrative |
| retail store cash drawer wizard | **ANDVARI** | — | Dwarf who hoards and controls gold |
| cash till manager | **GULLVEIG** | — | Gold-power; already in use? If conflict: **GEFION** |
| tracker | **MUNINN** | ᛗ | Memory — records everything that was |
| retail sales promotion engine | **FREYJA** | — | Goddess of desire and abundance |
| retail sales promotion manager | **GEFION** | — | The giver; distributes reward |
| in-app webpage instant messenger | **HERMÓÐR** | ☿ | Already named messenger |
| SMS / call center version | **BRIMIR** | — | The primordial voice that speaks across realms |
| SWR react | **RATATOSKR** | ᚱ | The messenger squirrel running up and down Yggdrasil revalidating |
| fusejs wrapper | **MÍMIR** | ᛗ | Keeper of knowledge; searches the well of wisdom |
| input group | **BROKK** | — | Dwarf craftsman assembling components together |
| reusable monaco editor | **ODIN** | ᚨ | Already named IDE editor |
| automotive finance calculator | **GULLVEIG** | — | Already named |
| github cli wrapper | **HEIMDALLR** | ᚺ | Gatekeeper of the bridge |
| platform installer | **BIFRÖST** | ᛒ | Already named |
| platform plugin system | **BIFRÖST-PLUGIN** | ᛒ | Already named |
| custom ci/cd | **VIÐARR** | ᚹ | Silent automation; acts without noise |
| Workbench Distribution | **SINDRI** | — | The dwarf's forge where master tools are distributed |
| loki deterministic AI compiler | **LOKI** | ᛚ | Already named |
| web page markdown renderer | **SKÁLD** | ᛊ | Already named storyteller/editor |
| encoder/decoder | **RÚNAR** | ᚱ | Already named snippets — runes encode meaning |
| readme template wizard | **SAGA** | ᛊ | Already named — tells the story of the project |
| turbo repo (terminal split) | **JÖRMUNGANDR** | — | The world serpent connecting everything below |
| turbo repo (concurrent terminal) | **HRAESVELGR** | — | The eagle whose wings drive concurrent winds |
| theme builder | **FREYR** | ᛜ | Already named theming tool |
| automotive service dept calendar | **URÐR** | ᚢ | Already named event calendar |
| automotive all-in-one suite | **SLEIPNIR** | — | Already named automotive CRM |
| suite of finance tools | **DVALIN** | — | Dwarf of deep time and accumulated wealth |
| BDC platform for automotive groups | **GEIRSKÖGUL** | — | Valkyrie who chooses who advances in battle |
| customer CSI engine | **VÖR** | — | Goddess of wisdom who misses nothing |
| sales automation | **HUGINN** | ᚺ | Thought that acts before you do |

- COMPONENTS, TOOLS, FEATURES, FUNCTIONS, AND OR LIBRARIES THAT NEED TO BE NAMED USING THE SAME NORSE GOD NAMING CONVENTION THAT IS NOT ALREADY IN USE
- Converted / recreated / created / broken down / reimagined libraries that need names, does not include tools featured on the site
  - dual sidebar
  - remix utilites
  - color wheel picker
  - emoji picker
  - react sandbox
  - virtual list
  - async throttle
  - batch
  - queue
  - rate limiter
  - throttle
  - react app layer data store - like redux
  - vanilla app layer data store - recreated the previous but its use without react
  - server and client layer data store - like tanstack and mbx combined
  - event calendar
  - appointment scheduler
  - employee punch clock
  - command aka cmdk
  - barcode / qr code
  - heat map calendar - the oine github uses
  - toast - kinda laready have a name that is tounge and cheek with mortal comabt as it uses a bunch of finishers sayings, kinda like how that dev did voice overs in the game 
  - lo-fi library
  - pdf generator - recreated pdfme
  - pdf editor
  - pdf viewer
  - pdf signature
  - pdf print
  - pdf template builder
  - pdf template generator
  - pdf label genrator and printer
  - retail store cash drawer wizard
  - cash till manager
  - tracker
  - retial sales promotion ngin
  - retails sales promotion manager
  - rich text editor
  - in app webpage instant messenger
  - a second version for sms for call centers
  - swr react
  - basically an umbrella for all the remix run functionality and hooks
  - fusejs
  - cc # validator // do not rename anything past this as im just compiling a list to take actual stock of everyhing
  - use-file-icon
  - use-file-upload
  - use-google-font
  - use-keyboard-shortcut
  - use-markdown-to-html
  - use-local-storage
  - use-session-storage
  - autocomplete
  - dropzone
  - use-export-file
  - signature
  - carousel
  - lofi-google-maps
  - react-video-player
  - youtube-player
  - tailwind
  - taiwlind preset ngin
  - prompt builder
  - input group
  - reusble monaco editor
  - automtive finance calculaor
  - github cli wrapper
  - platform installer
  - platform plugin system
  - custom ci/cd
  - Workbench Distribution
  - monaco editor
  - loki deterministic ai compiler
  - loki ai limitless
  - ui components / sdk
  - web page markdown renderer
  - encoder/decoder
  - readme tempalte wizard
  - turbo repo this was split into two, this one needs redoing but split it up between its use of the terminal and everything else
  - turbo repos use of concurently using the temrinal
  - vsce
  - vscodes snippets
  - theme builder
  - automotice service dept calendar and service scheduler
  - all in one solutino for automotive dealers, crm, vehichle ecommerce site, vehcile management system, client facing website including accessories ecommerce, sales crm, accesories crm, service crm, 
  - suite of finance related tools
  - bdc platform for automotice groups
  - customer csi engine
  - sales automoation

    AVAILABLE NAMES
    - ᚹ VÖLUNDR (Master smith/craftsman (Wayland the Smith)) for cleanup/refactoring/automation tools suggests "craftsmanship/maintenance"
    - ᚺ HUGINN
    - ᛗ MUNINN (Remix/Prisma utilities) Odin's ravens: Thought and Memory for framework utilities
    - ᛏ TYR (Current: Port & Process/Errors) God of law, justice, heroic glory for debugging/error handling suggests "order/resolution"
    - ᛜ FREYR (Current: VS Code Styling/Theming) For theming/beautification tools suggests "abundance/beauty"
    - ᛊ SKÁLD (Current: Catalyst Editor) Norse poets/storytellers for documentation/markdown/editing tools suggests "crafting stories/narratives"
    - ᛗ MÍMIR - DevArchive
    - ᚱ RATATOSKR - File Tree Builder/Visualization tool
    - ᛚ LOKI - AI
    - ᛁ ÍVALDI (The Master Forger) The Sons of Ívaldi were the dwarves who crafted the greatest treasures of the gods (Odin’s spear, Sif’s golden hair, Freyr’s ship). A UI library is essentially a collection of "master-crafted treasures" that other developers use to build their world. The Vibe: Industrial, precise, and foundational. 
    - ᚹ VIÐARR - Automation events
    - 𐌍 NEMESIS - Create Incoming Tunnel
    - 𐌇 HERACLES - Batch Rename
    - ☿ HERMÓÐR - API Secret Grabber
    - ᚺ HEIMDALLR - The Gatekeeper who controls who enters the bridge and when.
    - ᚺ HÖFUÐ	Intellisense Schema Ngin	Heimdallr's sword; represents the sharp, precise "edge" of your code intelligence.
    - ᛊ SAGA - Goddess who sits beside Odin and tells him stories Associated with history and remembering Perfect for notes that tell the "story" of your work Simple, memorable name
    - ᚷ GINNUNGAGAP- The primordial void where all potential exists Perfect: modules exist here before being "born" into projects - Rune: Gebo ᚷ gift/exchange
    - ᚢ URÐR for Snapshot Engine "That which has become" (one of the three Norns) She represents the PAST Norns control fate/destiny - snapshots control your project's fate Rollback = returning to the past Urðr governs
    - ᚹ VEÐRFÖLNIR for VSCInfo - Eagle atop Yggdrasil, sees EVERYTHING  oversight/monitoring from above viewing system continuously

DEV

AVAILABLE NORSE/MYTHOLOGICAL NAMES:
Major Gods/Figures:

SLEIPNIR (Odin's 8-legged horse)
FENRIR (The great wolf)
GERI & FREKI (Odin's wolves)
GUNGNIR (Odin's spear)
DRAUPNIR (Odin's ring)
MJÖLNIR (Thor's hammer)
SIF (Thor's wife, harvest goddess)
IDUNN (Youth goddess, keeper of apples)
BRAGI (Poetry god)
FORSETI (Justice god)
NJORD (Sea god)
ULLR (Archery/skiing god)
HODER (Blind god)
VALI (Avenger)
MAGNI (Thor's son - strength)
MODI (Thor's son - courage)
NANNA (Baldr's wife)
EIR (Healing goddess)
GEFION (Giver goddess)
VAR (Goddess of oaths)
VOR (Goddess of wisdom)
SYN (Guardian goddess)
HLIN (Protection goddess)
SNOTRA (Wisdom goddess)
GERSEMI (Freyja's daughter - precious)
HNOSS (Freyja's daughter - treasure)

Giants/Creatures:

HRUNGNIR (Stone giant)
JÖRMUNGANDR (World serpent)
NIDHOGG (Dragon gnawing roots)
RATATOSK (Already used)
HRAESVELGR (Eagle creating wind)
SKOLL (Wolf chasing sun)
HATI (Wolf chasing moon)
SURTR (Fire giant)
YMIR (Primordial giant)
THRYM (Frost giant king)
THIAZI (Storm giant)
GRENDEL (Monster)
FAFNIR (Dragon)
AUDUMBLA (Primordial cow)

Valkyries:

BRUNHILDE
SIGRUN
SVAFA
KARA
SKULD
GÖNDUL
HILDR
GEIRSKÖGUL
RANDGRID
RADGRID
REGINLEIF

Dwarves:

ANDVARI
BROKK
EITRI
DVALIN
ALFRIGG
BERLING
GRERR
SINDRI
DURIN

Other:

HEL (Death/underworld)
SIGYN (Loki's wife)
MODGUD (Bridge guardian)
HVERGELMIR (Source of rivers)
MUSPELHEIM (Fire realm)
NIFLHEIM (Ice realm)
ALFHEIM (Light elf realm)
SVARTALFHEIM (Dark elf realm)
JOTUNHEIM (Giant realm)
MIDGARD (Human realm)
ASGARD (God realm)
-->

<!-- 
## Complete Archaic Greek Alphabet Reference

- 𐌀 (Alpha) - A
- 𐌁 (Beta) - B
- 𐌂 (Gamma) - G
- 𐌃 (Delta) - D
- 𐌄 (Epsilon) - E
- 𐌅 (Digamma/Wau) - W/V
- 𐌆 (Zeta) - Z
- 𐌇 (Eta) - H/Ē
- 𐌈 (Theta) - Th
- 𐌉 (Iota) - I
- 𐌊 (Kappa) - K
- 𐌋 (Lambda) - L
- 𐌌 (Mu) - M
- 𐌍 (Nu) - N
- 𐌎 (Xi) - X
- 𐌏 (Omicron) - O
- 𐌐 (Pi) - P
- 𐌑 (San/Tsade) - Ts
- 𐌒 (Qoppa) - Q
- 𐌓 (Rho) - R
- 𐌔 (Sigma) - S
- 𐌕 (Tau) - T
- 𐌖 (Upsilon) - U/Y
- 𐌗 (Phi) - Ph
- 𐌘 (Chi) - Ch/Kh
- 𐌙 (Psi) - Ps
- 𐌚 (Omega) - Ō
- -->


