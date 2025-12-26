## Config Item Examples


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
- `customVsixPackager` - type: `command`, path: `ocrmnavigator.customVsixPackager`, hidden: `true`
- `installNow` - type: `command`, path: `ocrmnavigator.installNow`, hidden: `true`
- `await2Secs` - type: `command`, path: `ocrmnavigator.await2Secs`, hidden: `true`
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

---
[🡄 Return](https://github.com/8an3/DevStack)