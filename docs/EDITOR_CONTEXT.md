# 🖱️ Editor Context Menu Registry

> **File:** `EDITOR_CONTEXT.md`
> **Scope:** Surgical tools available directly within the active text editor buffer.

| Feature / Sub-Menu | Capability | UX / Implementation Details |
| --- | --- | --- |
| **Open Github Repo At File** | [ADD DESCRIPTION] | Instant deep-link to current line/file on GitHub. |
| **Open Github Repo in Browser** | [ADD DESCRIPTION] | Opens the root repository for the current project. |
| **Open Left Off Note** | [ADD DESCRIPTION] | Recall the specific session note for this workspace. |
| **Scan File Imports** | [ADD DESCRIPTION] | Mapping and validating all active imports in the buffer. |
| --- | --- | --- |
| 💎 **CATALYST-UI** | **Sub-Menu Core** | **One-click full-stack UI orchestration.** |
| ∟ Components Viewer | [ADD DESCRIPTION] | Visual gallery for library components. |
| ∟ Install Catalyst-UI | **Full Setup** | From blank project to working: Installs Tailwind, PostCSS, and Catalyst. Configures theme presets (2500+ comps) and 45+ fonts in one click. |
| ∟ Install (Exclude Configs) | **Surgical Setup** | Install library components into an existing environment without overwriting configs. |
| ∟ 23 Component Categories | **2500+ Components** | Inserts at cursor. Hover cards include 2 usage examples, props, and values. Eliminates the need for external docs. |
| --- | --- | --- |
| 🛠️ **DEVSTACK** | **Sub-Menu Core** | **Advanced Editor Controls & Logic.** |
| ∟ Render MD | [ADD DESCRIPTION] | standard Markdown rendering. |
| ∟ Render MD In VSCode | [ADD DESCRIPTION] | Native preview within the editor pane. |
| ∟ Context Snippets | [ADD DESCRIPTION] | Trigger snippets based on current file scope. |
| ∟ Import Snippets | [ADD DESCRIPTION] | Bulk import snippet libraries. |
| ∟ Create Custom .vsix | [ADD DESCRIPTION] | Archive and package current dev state. |
| ∟ Performance Switch | **Granular Toggle** | Disable/Enable per file or globally to optimize editor overhead. |
| ∟ Add File to DevStack | [ADD DESCRIPTION] | Register current file to the VFS logic. |
| ∟ Add Bookmark | [ADD DESCRIPTION] | Enterprise bookmarking at the line level. |
| ∟ Config Search | [ADD DESCRIPTION] | Direct search through DevStack configuration items. |
| --- | --- | --- |
| ✨ **FORMATTERS** | **Sub-Menu** | *Features found within this sub-menu: [ADD DESCRIPTION]* |
| 🐙 **GITHUB FUNCTIONS** | **Sub-Menu** | *Features found within this sub-menu: [ADD DESCRIPTION]* |
| ⬢ **PRISMA** | **Sub-Menu** | *Features found within this sub-menu: [ADD DESCRIPTION]* |
| 💿 **REMIX** | **Sub-Menu** | *Features found within this sub-menu: [ADD DESCRIPTION]* |
| ❄️ **SHADCN** | **Sub-Menu** | *Features found within this sub-menu: [ADD DESCRIPTION]* |


```text
EDITOR_CONTEXT_MENU/
├── 📄 Open Github Repo At file ............ [ADD DESCRIPTION]
├── 📄 Open Github Repo in Browser ......... [ADD DESCRIPTION]
├── 📄 Open Left Off Note .................. [ADD DESCRIPTION]
├── 📄 Scan File Imports ................... [ADD DESCRIPTION]
│
├── 📂 CATALYST-UI/
│   ├── 📄 Components viewer ............... [ADD DESCRIPTION]
│   ├── 📄 Install Catalyst-ui ............. 1-Click: Tailwind + PostCSS + 2500 Comps
│   ├── 📄 Install (Excl. Configs) ......... Install components without touching setup
│   └── 📂 23_CATEGORIES_OF_COMPONENTS/
│       └── 📄 2500+_Components ............ Hover cards: 2 usage examples + props + values
│
├── 📂 DEVSTACK/
│   ├── 📄 Render MD ....................... [ADD DESCRIPTION]
│   ├── 📄 Render MD In VSCode ............. [ADD DESCRIPTION]
│   ├── 📄 Context Snippets ................ [ADD DESCRIPTION]
│   ├── 📄 Import Snippets ................. [ADD DESCRIPTION]
│   ├── 📄 Create Custom vsix archive ...... [ADD DESCRIPTION]
│   ├── 📂 PERFORMANCE_SWITCH/
│   │   ├── 📄 Disable For Current File .... Kill overhead for active buffer
│   │   ├── 📄 Enable Everything ........... Global system activation
│   │   ├── 📄 Enable For Current File ..... Surgical activation
│   │   └── 📄 Disable everything .......... Full system dormancy
│   ├── 📄 Add File To DevStack ............ [ADD DESCRIPTION]
│   ├── 📄 Add Bookmark .................... [ADD DESCRIPTION]
│   └── 📄 DevStack Config Search .......... Search items within devstacks config
│
├── 📂 FORMATTERS/ ......................... [ADD DESCRIPTION]
├── 📂 GITHUB_FUNCTIONS/ ................... [ADD DESCRIPTION]
├── 📂 PRISMA/ ............................. [ADD DESCRIPTION]
├── 📂 REMIX/ .............................. [ADD DESCRIPTION]
└── 📂 SHADCN/ ............................. [ADD DESCRIPTION]
```


