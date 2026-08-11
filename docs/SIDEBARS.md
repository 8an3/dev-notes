

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> DevStack Menu

Essentially, taking vscodes fragmented menu system and consolidating it to a single sidebar, in addition to that also creating line items that vscode failed to include within their menu system.

A lot of the created menu items will trigger an extensions function despite having its very own vscode command. This is because the command has been bundled up with other commands to make that command more effecient. For example, there are a lot of commands in which you need to trigger a save or save all event for the command to result in the desired outcome. 

With saying that, in respect to the save all command being bundled with other commands. There is another more important and rather a lot more secritive reason for this. Well, vscode keeps it a secret but obviously thats not the case here. 

Virtually every single function is bundled with the save all function, this is due to ensure that the recovery system set in place by vscode remains up to date and creates as many versions of the file and its data as possible.

Here is a outline of the current root level menu options that you can expect from this sidebar, along with any section that is expanded by default:


<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/devstack-menu.jpg" />
</p>



If you are wondering, "where are all the UI element triggers?", do not worry... there is an entire sidebar view devoted to the ui, as it too consolidates the even more fragmented menu system that manipulates the ui and even creating a very long list of other toggles that vscode forgot to include with its UI entirely.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Data And File Recovery

A lot of people do not know of this feature but a lot of people know of versioning through github and typically rely on that for file and data recovery.

There are, as far as I know, 3 recovery methods we have at our disposal and will go over each listing from easiest and well known to slightly difficult and rarely known:
1. timeline view - shows file history including git commits and local history combined
2. Local History - VSCode's built-in timeline of local file edits
3. workspaceStorage and History folders - this one being the most unknown recovery option and requires the user to open a specific folder residing in the vscode file system on your workstation.



All three options have menu options that work with all three, even the last option. The last option first checks what os your currently running, then checks to see which version of vscode your running, whether it is code or code-insiders and then opens the required folder needed to view these files.

Once that folder has opened you will very quickly notice that vscode did not anticipate users to access this folder, as it's very cryptic with its naming convention of files that are found within your workspace.

Each folder represents a file in your workspace, within that folder there will be several files for you to go through. Each file represents a recovery save point for that specific file. Due to the cryptic naming convenstions implemented by vscode, it might takes a couple of minutes just for you to find the right folder that you are looking for that is relevant to the data that you are trying to recover.

After writing this... because of how stupid vscode implementation is I might look into creating a new sidebar view devoted to file recovery.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> ODIN Workspace Context File Versioning And History

Which is exactly what I did. The sidebar labeled ODIN: File versioning and history has been added. 


<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/file-history.jpg" />
</p>



<img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/sidebars/odin.jpg" width="32"  >

Making the tasks of file recovery and easy task to deal with in comparison to the default. Click on any one item and a quick pick will be presented with the following options:
- replace current file with this version
- copy contents to clipboard 
- delete from version history

It is as easy as that.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Clipboard History Pro

Multi-item clipboard manager that tracks and stores your clipboard history.

**Access:** Click `Clipboard++` on the status bar

Click on any one item for it to be placed back into your clipboard

**Features:**
- Track last 100 clipboard items
- Hover previews for quick reference
- Status bar access for convenience
- Persistent storage across sessions
- Quick paste from history

<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/bookmarks.jpg" />
</p>


---

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Global Bookmarking System

Never lose your place in large projects again. The extension provides a persistent, global bookmarking system that allows you to tag specific lines of code and jump back to them instantly, even after restarting VS Code.

✨ Key Features
Persistent Storage: Bookmarks are saved to a bookmarks.json file in your global storage, ensuring they survive across sessions and workspaces.

Status Bar Integration: A permanent $(bookmark) Bookmarks item in your Status Bar provides one-click access to your list.

Quick-Access Navigation: Use the Quick Pick menu to search and filter your bookmarks. They are sorted by "most recent," so your latest work is always at the top.

Automatic Cleanup: To keep things fast and organized, the system maintains a rolling limit of 100 bookmarks, automatically removing the oldest ones as you add new ones.

Smart Updates: Adding a bookmark to a line that is already bookmarked will refresh its position to the top of your list.

#### Commands 

- To add a bookmark
  - Adds the current line in the active editor to your bookmarks
  - Right-click line → DevStack → Add Bookmark
- Clicking on any bookmark in the sidebar will open the file at that line number

#### 🛠 Technical Details
Storage Location: %AppData%/Code/User/globalStorage/[extension-id]/bookmarks.json

Relative Paths: The navigation menu displays relative paths to make it easier to identify files within your current workspace.

#### Pro-Tip: How to Use
Place your cursor on a line you want to remember.

Right-click line → DevStack → Add Bookmark

Later, click the $(bookmark) Bookmarks icon in the Status Bar to see your history and jump back instantly.

![Bookmarks](https://raw.githubusercontent.com/8an3/midgardr-notes/main/bookmarks/bookmark.jpg?raw=true)

---


<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/clipboard.jpg" />
</p>


> [!NOTE]
>
> Whether it is product icons, file icons or themes, they need to activated via the file drop down menu > prefrences > themes > and selecting the desired option

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Custom Product Icons

Please refer to file icons sidebar for full list of custom icons to view, in addition to vscodes default file icons.

Selecting any menu option will copy the value to your clipboard to be used anywhere you would like.


<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/icons.jpg" />
</p>


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> File Icons
A variety of custom icons has been created for use within the explorer pane. Icons are styled the same as they were created by the original creators and even following the original color scheme, only deviating on a few select colors such as black for example. 

Despite using the original logo's, each svg was edited in order to obtain the most clarity out of each svg. Where applicable a black background was place behind the logo, in order for the text/logos to appear sharper when rendered while at the same time, not letting your current color scheme change the overall look of each of the icons.

Different colored icons were used when needed in order to seperate different file types, for example js and jsx extensions, while both javascript files two seperate colors were used to allow you to quickly discern which is which.

An idea that was adopted ( we'll see how this one goes, but seems to be working as intended ), vscode allows for a different icon to be used for open folders. Instead of following the norm in which the same color is used for both icons, I opted to instead use a different color which provides a stark contrast to its neibhouring folders. When quickly moving your cursor over to expand or collapse the desired folder allowing you to continue looking at what your working on and only identifying the folder out of the corner of your instead of having to follow the cursor over.

The color scheme that was implemented, again going against the norms, instead of having both light and dark themed icons in its place a single color was used. Using the entire span of the color wheel, but only using the 500 variant from each. Giving it a vibrant enough color that can be used with dark or light themes, while also allowing you to not only more quickly get used to the colors, since there are half of them to get used to, but also cuts down on the amount of time to become accustomed to the new color variations whenever you swap from light to dark themes and vice versa. But this point really only being important when a stock logo was unavailable for use with certain file extensions. Currently, I'm not worried about color collisions, as each folder is typically pretty well organized when it comes to containing file extensions. As you normally wouldn't host all of your image and video files along side all of your different files type catering to your code.

Lastly when a stock logo was unavailable for a specific file type, a specific placeholder was used instead for example for files ending in png, the icon used features a file with the capital letters PNG featured at the bottom. In addition to that, different colors were used for each file type in order to help quickly pick out by file type based on color alone.

png - teal #14b8a6
bmp - purple-600 #9333ea
txt - sky #0ea5e9
csv - green #22c55e
doc - blue-600 #2563eb
pdf - red #dc2626
gif - amber #f59e0b
ttf - yellow #eab308
jpg - emerald #10b981
zip - cyan #06b6d4

blue #3b82f6
orange #f97316
lime #84cc16
indigo #6366f1
violet #8b5cf6
purple #a855f7
fuschia #d946ef
pink #ec4899
rose #f43f5e


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> BALDR

A React icon library designed for simplicity and accuracy with a sensible naming convention.

**Installation ( You may also use the menu option found in Heimdallr Sidebar ):**

```bash
npm install @a5gard/baldr
# or
pnpm add @a5gard/baldr
```

**Usage:**

```javascript
import { Message } from '@a5gard/baldr'
```

**Features:**
- Clean, logical naming convention
- Filled variants available
- Customizable colors
- Flexible sizing options
- Designed for React applications

![NPM Icon Library](https://raw.githubusercontent.com/8an3/midgardr-notes/main/icons/npm-icon.jpg?raw=true)



<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/baldr-installer.jpg" />
</p>


---

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Icons Sidebar


Browse and insert icons from the @a5gard/baldr library directly in your editor


**Access:** Editor context menu → Catalyst → Icons

**Features:**
- Integrated search functionality
- Instant insertion at cursor position
- Complete library access
- Preview icons before insertion

**Naming Convention:**  
Icons follow a logical pattern: `[MainTheme][Container/Feature][Filled]`

**Example:** `MessageSquareFilled`, `UserCircle`, `SettingsGear`

> [!NOTE]
>
> You will now be able to search through vscodes file icons and the registered file icon theme pack that is registered through this extension that also contains a fuzzy search at the top of the sidebar to allow for easier filtering

 
## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> VSCode Icons

Visual reference for all available VSCode icons and their identifiers.

**Access:** DevStack Quick Pick menu in status bar

**Features:**
- Browse complete icon library
- Search by name or category
- Quick copy icon identifiers
- Visual preview of all icons
- Integration with custom commands

**Usage:** Perfect for customizing your extension commands, status bar items, and UI elements with the right visual indicators.

**Note:** Regularly updated to include new VSCode icon additions and improvements.


---

[🡄 Return](https://github.com/8an3/DevStack)



## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> SAGA
### Notes Manager & GitHub Sync Extension

A comprehensive VS Code extension for managing notes, todos, reminders, and post-it pads with GitHub synchronization capabilities.

> [!NOTE] 
> I thought I would mention this because, it didn't dawn on me the gravity of the situation when it comes to the level of issues, well lack of to be more precise since I haven't had a single reject push while using github as a source of truth. 
>
> If your thinking that I may be babying the system, far from it. At times I'll have 4 workspaces open, all have their own "instance" of the note app meaning that, they aren't linked to one another in any way, except the repo. I'll create a note in one, leave it unsaved, jump to another workspace create and save a new note, jump to another workspace create a new note but not for my current workspaces files, but for the one that still has an unsaved note open. Saving that note, jumping back to the original workspace to finish off that note and save it. 
>
> Meanwhile under the hood, every save event executes a custom push sequence where I have not experienced a single reject in 9-10 months. Not to mention, making matters worse, the UI is pretty sweet when it comes to the to do lists. This is due to the fact that you do not even need to open the file, to check or uncheck to do items, each check pushes the save to github and if you do 3 or 4 really fast... that's ok, because if one push were to be triggered before the current one finishes, it just gets added to a queue. Even when you trigger it 10 times, theres 10 items in the queue and they get done when they get done.



### Table of Contents

1. [Notes Manager & GitHub Sync Extension](#notes-manager--github-sync-extension)

2. [To-Do Extension Feature Comparison](#to-do-extension-feature-comparison)
   - [DevStack vs Marketplace Leaders](#devstack-vs-marketplace-leaders)
   - [Marketplace Leaders Overview](#marketplace-leaders-overview)
   - [Feature Comparison Table](#feature-comparison-table)

3. [Key Differentiators](#key-differentiators)
   - [DevStack To Do's Unique Advantages](#devstack-to-dos-unique-advantages)
   - [Why DevStack Doesn't Need Their "Features"](#why-devstack-doesnt-need-their-features)

4. [The Real Comparison](#the-real-comparison)
   - [What Each Extension Actually Does](#what-each-extension-actually-does)
   - [The Use Case Difference](#the-use-case-difference)

5. [Why The Comparison Is Misleading](#why-the-comparison-is-misleading)
   - [The Real Competitive Landscape](#the-real-competitive-landscape)

6. [Bottom Line](#bottom-line)

7. [Features](#features)
   - [📝 Note Management](#-note-management)
   - [✅ Todo/Checklist Management](#-todochecklist-management)
   - [⏰ Reminder System](#-reminder-system)
   - [📌 Post-It Pads](#-post-it-pads)
   - [🔄 GitHub Synchronization](#-github-synchronization)
     - [Core Sync Operations](#core-sync-operations)
     - [Repository Management](#repository-management)
     - [Git Operations](#git-operations)
     - [Advanced Features](#advanced-features)

8. [Getting Started](#getting-started)
   - [Personal Access Token Guide](#personal-access-token-guide)
   - [Configuration Options](#configuration-options)

9. [Usage](#usage)
   - [Creating](#creating)
   - [Editing](#editing)
   - [Deleting](#deleting)
   - [Code Highlighting](#code-highlighting)

10. [Troubleshooting & Advanced Commands](#troubleshooting--advanced-commands)

11. [To Do, Notes and Reminders PWA Web App](#to-do-notes-and-reminders-pwa-web-app)
    - [Architecture Overview](#architecture-overview)



<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/todo.jpg" />
</p>



### To-Do Extension Feature Comparison

### DevStack vs Marketplace Leaders
### Marketplace Leaders Overview
- **To Do 1** (6,773,736 installs) - Searches code for TODO/FIXME comments
- **To Do 2** (455,503 installs) - Manages TaskPaper-style todo files

---

| Feature | DevStack To Do | To Do 1 | To Do 2 |
|---------|------------------|-----------|-------|
| **Installation Base** | Growing | 6.7M | 455K |
| **Core Functionality** |
| Purpose | Full task management system | Code comment scanner | Todo file manager |
| Multiple Note Types | ✅ (Notes, Todos, Reminders, Post-Its) | ❌ (Comments only) | ✅ (Todos only) |
| Hierarchical Organization | ✅ (Priority, Normal, Completed, Trashed) | ✅ (By folder/tag) | ✅ (Projects) |
| Nested Checklists | ✅ (Unlimited depth with collapsible sections) | ❌ | ❌ |
| Label System | ✅ (Custom labels) | ⚠️ (Tags in comments) | ✅ (Tags) |
| **Storage & Sync** |
| File-Based Storage | ✅ (Markdown in `.vscode/ntrsync/`) | ❌ (Scans existing code) | ✅ (Custom format) |
| GitHub Sync | ✅ (Full bidirectional) | ❌ | ❌ |
| Cloud Backup | ✅ (GitHub as source of truth) | ❌ | ❌ |
| Offline Support | ✅ (Full offline capability) | ✅ (Local only) | ✅ (Local only) |
| Cross-Device Sync | ✅ (Automatic via GitHub) | ❌ | ❌ |
| **Access & Availability** |
| VSCode Interface | ✅ | ✅ | ✅ |
| Web UI | ✅ (Full PWA) | ❌ | ❌ |
| Mobile Access | ✅ (PWA on phone) | ❌ | ❌ |
| Offline Mobile Use | ✅ (Works with zero cell service) | ❌ | ❌ |
| Desktop App Access | ✅ (PWA) | ❌ | ❌ |
| Works Without VSCode | ✅ (Web UI always accessible) | ❌ (VSCode required) | ❌ (VSCode required) |
| **Reminders & Time** |
| Due Date Tracking | ✅ (Full date/time support) | ❌ | ⚠️ (Manual tags) |
| Reminder Categories | ✅ (Coming Up, Missed, etc.) | ❌ | ❌ |
| Active Reminder Notifications | ✅ (Triggers inside VSCode) | ❌ | ❌ |
| Time Estimates | ❌ (Not needed - GitHub tracks actual time) | ❌ | ✅ (`@est` tags) |
| Time Tracking | ✅ (GitHub commit timestamps & history) | ❌ | ⚠️ (Manual `@started` tags) |
| Overdue Notifications | ✅ | ❌ | ❌ |
| **Post-It Notes** |
| Post-It Pad Feature | ✅ (5 color-coded pads) | ❌ | ❌ |
| Auto-Save | ✅ (500ms debounce) | N/A | ⚠️ (On file save) |
| Quick Actions | ✅ (Copy, clear, delete all) | N/A | N/A |
| **GitHub Integration** |
| Push to GitHub | ✅ | ❌ | ❌ |
| Pull from GitHub | ✅ | ❌ | ❌ |
| Bidirectional Sync | ✅ | ❌ | ❌ |
| Create Repository | ✅ (From VSCode) | ❌ | ❌ |
| Branch Management | ✅ (Create, switch, rename, delete) | ❌ | ❌ |
| Collaborator Management | ✅ (Granular permissions) | ❌ | ❌ |
| Private Repositories | ✅ | ❌ | ❌ |
| Conflict Resolution | ✅ (Smart merge) | ❌ | ❌ |
| Auto-Sync | ✅ (Configurable interval) | ❌ | ❌ |
| **Git Operations** |
| Commit Management | ✅ (Standard, staged, amend, undo) | ❌ | ❌ |
| Stash Operations | ✅ (Create, apply, pop, drop) | ❌ | ❌ |
| Tag Management | ✅ (Create, delete, push) | ❌ | ❌ |
| Remote Management | ✅ (List, add, remove) | ❌ | ❌ |
| **Code Integration** |
| Find TODO in Code | ⚠️ (Coming soon) | ✅ (Main purpose) | ✅ (Embedded todos) |
| Highlight in Editor | ⚠️ (Coming soon) | ✅ (Configurable) | ✅ (Configurable) |
| Custom TODO Tags | ✅ (Unlimited markdown sections) | ✅ (Fully customizable) | ✅ (Fully customizable) |
| Regex Search | ❌ (Not needed - proper organization) | ✅ (ripgrep) | ✅ (ag/rg/js) |
| **Tree View & UI** |
| Tree View in Activity Bar | ✅ | ✅ | ✅ |
| Expand/Collapse Todo Lists | ✅ (Each file collapses/expands) | ✅ | ✅ |
| Expand/Collapse Nested Sections | ✅ (Sections act as folders) | ❌ | ❌ |
| Single-Click Complete | ✅ (Click checkbox = done + sync) | ❌ (Must open file) | ❌ (Must open file) |
| Single-Click Edit | ✅ (Click title = open file) | ✅ (Click = navigate to line) | ✅ (Click = open file) |
| Filter/Search | ✅ | ✅ | ✅ |
| Context Menu Actions | ✅ | ✅ | ✅ |
| Drag and Drop | ❌ (Not needed - context menus) | ❌ | ❌ |
| Status Bar Integration | ❌ (Full sidebar UI) | ✅ (Counts) | ✅ (Statistics) |
| **Advanced Features** |
| Custom Sections in Markdown | ✅ (Unlimited, any name you want) | ❌ | ⚠️ (Projects only) |
| Hierarchical Organization | ✅ (Files + nested collapsible sections) | ⚠️ (Folders only) | ⚠️ (Projects only) |
| Statistics | ❌ (GitHub provides better tracking) | ⚠️ (Basic counts) | ✅ (Detailed stats) |
| Time Tracking | ✅ (GitHub commit timestamps & history) | ❌ | ⚠️ (Manual `@started` tags) |
| Archive System | ✅ (Completed/Trashed folders) | ❌ | ✅ (Archive section) |
| Markdown Support | ✅ (Native markdown files) | ✅ (Markdown todos) | ⚠️ (Custom format) |
| Formatting | ✅ (Full markdown) | ❌ | ✅ (Bold, italic, code) |
| Multi-line Todos | ✅ | ✅ (Configurable) | ✅ |
| **Data Management** |
| Export Functionality | ✅ (Via GitHub) | ✅ (To file) | ❌ |
| Import Functionality | ✅ (Via GitHub) | ❌ | ❌ |
| Backup System | ✅ (GitHub) | ❌ | ❌ |
| Version Control | ✅ (Full Git history) | ❌ | ❌ |
| **Collaboration** |
| Team Sharing | ✅ (Via GitHub repo) | ❌ | ❌ |
| Permission Control | ✅ (GitHub collaborators) | ❌ | ❌ |
| Real-time Sync | ✅ (Configurable) | ❌ | ❌ |
| **Security** |
| Private Data Support | ✅ (Private repos) | ✅ (Local only) | ✅ (Local only) |
| Token Security | ✅ (VSCode secrets API) | N/A | N/A |
| Auto .gitignore | ✅ (`.vscode/ntrsync/`) | N/A | N/A |
| Encryption Support | ⚠️ (Via Pro7 tool) | ❌ | ❌ |
| **Progressive Web App** |
| Offline-First Architecture | ✅ | ❌ | ❌ |
| Local Caching | ✅ | ❌ | ❌ |
| Sync Queue | ✅ | ❌ | ❌ |
| Conflict Resolution | ✅ | ❌ | ❌ |
| Zero Data Loss | ✅ | N/A | N/A |
| Works on Plane/Subway | ✅ | ❌ | ❌ |

---

### Key Differentiators

### DevStack To Do's Unique Advantages

1. **True Cross-Platform System**
   - Works in VSCode, web browser, mobile, desktop
   - Fully functional offline (even with zero cell service)
   - Not locked to VSCode being open
   - **ONLY todo extension using GitHub as source of truth**

2. **Enterprise-Grade Architecture**
   - GitHub as source of truth
   - Bidirectional sync with conflict resolution
   - Private repository support
   - Team collaboration with granular permissions

3. **Perfect Tree View UX**
   - Single-click checkbox to complete (never open file)
   - Single-click title to edit (opens when you need it)
   - Collapsible todo lists (organized by filename)
   - Nested collapsible sections (folders within lists)
   - Hierarchical organization without complexity
   - Zero confusion - interface explains itself

4. **Complete Task Management**
   - Multiple note types (Notes, Todos, Reminders, Post-Its)
   - Hierarchical organization (Priority → Normal → Completed → Trashed)
   - Unlimited custom markdown sections (name them whatever you want)
   - Due date tracking with overdue detection
   - **Active reminder notifications inside VSCode**
   - Label system for categorization
   - GitHub provides automatic time tracking via commit history

5. **Git Integration**
   - Full repository management from VSCode
   - Branch operations, stash management, tag control
   - Collaborator management with permission levels
   - Complete commit workflow

### Why DevStack Doesn't Need Their "Features"

**Regex Search**: They need regex because their systems are disorganized. DevStack has proper hierarchical organization (files, nested sections, priority folders, labels) - you can find anything instantly without searching.

**Manual Time Tracking Tags**: They type `@started` and `@est(2h)` manually. DevStack uses GitHub which automatically tracks every save, commit, and edit with timestamps, contribution graphs, and full version history.

**Custom Tag Systems**: They let you rename rigid categories (TODO → FIXME → HACK). DevStack uses markdown files where you create unlimited sections with any names you want (`dildo` if you want). Complete freedom.

**Statistics Counters**: They show "You created 47 todos!" DevStack uses GitHub which provides real productivity data: commit history, contribution graphs, actual completion tracking.

**Drag and Drop**: Slow and imprecise. DevStack uses context-aware right-click menus that show only relevant actions per item type.

**Status Bar Counts**: Tiny counter showing "5 TODOs". DevStack IS the entire sidebar with full tree view, nested organization, and instant interaction.

**Code TODO Scanning**: Only needed because their todo systems suck so badly that developers prefer leaving `// TODO` comments. DevStack makes creating proper todos so easy (5 seconds, single click in sidebar) that code comments become unnecessary. *Note: Adding highlight feature anyway because it's nice UX.*

---

### The Real Comparison

### What Each Extension Actually Does

**To Do 1** is a **code comment scanner**. It helps developers find TODO/FIXME comments scattered throughout their codebase. It's not a task management system - it's a search tool.

**To Do 2** is a **plain text todo file manager**. It manages todo lists in dedicated files using a custom format. It's VSCode-only and local-only.

**DevStack To Do** is a **complete task management platform** that happens to integrate with VSCode. It's the only extension that:
- Works outside of VSCode
- Syncs across devices automatically
- Functions fully offline on mobile
- Uses GitHub for backup and collaboration
- Provides team collaboration features
- Has enterprise-grade architecture

### The Use Case Difference

**To Do 1 Users**: "I need to find all the TODO comments in my code"
- Scans existing codebase
- Highlights todos in editor
- Quick navigation to comments

**To Do 2 Users**: "I need a text-based todo list inside VSCode"
- Creates dedicated todo files
- Manages tasks in plain text
- Local-only workflow

**DevStack To Do Users**: "I need a complete task management system that works everywhere"
- Manages all types of notes/tasks/reminders
- Works on phone, tablet, laptop, desktop
- Functions offline in subway/plane/remote areas
- Syncs automatically across all devices
- Collaborates with team via GitHub
- Never loses data

---

### Why The Comparison Is Misleading

Comparing DevStack To Do to To Do 1 or To Do 2 is like comparing:
- **Notion** vs **grep** (they both find text, right?)
- **GitHub** vs **local Git** (they both version control, right?)
- **Google Drive** vs **File Explorer** (they both manage files, right?)

The marketplace "leaders" aren't actually competitors - they solve different problems:
- **To Do 1**: Development workflow tool for navigating code comments
- **To Do 2**: Lightweight text-based task list for developers
- **DevStack To Do**: Enterprise task management platform with offline-first PWA

### The Real Competitive Landscape

DevStack To Do competes with:
- **Todoist** (requires internet, no offline mobile)
- **Notion** (requires internet, limited offline)
- **Microsoft To Do** (requires internet, breaks offline)
- **Google Keep** (requires internet, no offline support)
- **Asana/Trello/Jira** (require internet, enterprise only)

And DevStack To Do beats all of them because:
1. Works fully offline (zero cell service)
2. Free (GitHub as backend)
3. Private (your data, your repo)
4. Integrated with development workflow
5. No vendor lock-in
6. Open data format (Markdown)

---

### Bottom Line

**To Do 1** has 6.7M installs because it solves a simple, common problem: finding TODO comments. It does one thing well.

**To Do 2** has 455K installs because it's a solid text-based todo manager for developers who want simplicity.

**DevStack To Do** is the only VSCode extension that provides:
- Full offline mobile access (works with zero cell service)
- Cross-device automatic sync
- **GitHub as source of truth (ONLY extension)**
- Active reminder notifications inside VSCode
- Works without VSCode being open
- Enterprise-grade architecture
- Progressive Web App functionality

The install count isn't something I track or prioritize. DevStack was built entirely for my own use—every feature exists because I needed it. The documentation only exists for two reasons: first, users somehow found and started using the extension even before any readme existed, and second, I needed a reference for myself to remember what's currently in DevStack and how it's configured. Without that unexpected user base, the docs would be far less detailed than they are now.

Honestly, I'm still baffled by how those initial users even discovered the extension. It had a confusing name that bore no relation to its functionality, and there was literally zero documentation. I only published it to the marketplace so I could easily install it across different machines where I code—I never anticipated anyone else downloading it. The only reason I included the above comparison, is because in regards to this extensions features, previously I was selling each feature short and not including enough reasons on why you should use it.

### Features

![Explorer pane](https://raw.githubusercontent.com/8an3/midgardr-notes/main/todo/main.jpg)

### 📝 Note Management
- **Multiple Note Types**: Support for regular notes, todos (checklists), and reminders
- **Hierarchical Organization**: Notes organized by priority (Priority, Normal, Completed, Trashed)
- **Label System**: Organize notes with custom labels
- **File-based Storage**: All notes stored as Markdown files in `.vscode/ntrsync/`

### ✅ Todo/Checklist Management
- **Nested Checklists**: Support for indented, hierarchical todo items
- **Check Item Tracking**: Toggle completion status for individual items
- **Auto-parsing**: Automatically parses Markdown checklist syntax (`- [ ]` and `- [x]`)
- **Tree View**: Visual representation with expand/collapse functionality

### ⏰ Reminder System
- **Due Date Tracking**: Set and track reminder due dates
- **Smart Categorization**: 
  - Coming Up (next 24 hours)
  - Missed (overdue)
  - Normal, Completed, Trashed
- **Date Format**: `DUE: YYYY-MM-DD HH:MM` in note content

### 📌 Post-It Pads
- **5 Color-Coded Pads**: White, Green, Blue, Indigo, Orange
- **Auto-Save**: Content saves automatically with 500ms debounce
- **Quick Actions**: Copy content, clear individual pad, delete all pads
- **Persistent Storage**: Content saved to workspace state

### 🔄 GitHub Synchronization

#### Core Sync Operations
- **Push**: Upload local changes to GitHub repository
- **Pull**: Download remote changes to local workspace
- **Sync**: Combined pull + push operation
- **Queue Management**: Prevents concurrent push operations

#### Repository Management
- **Create Repository**: Initialize new GitHub repos directly from VS Code
- **Select Repository**: Browse and connect to existing repositories
- **Branch Management**: Create, switch, rename, and delete branches
- **Privacy Control**: Support for both public and private repositories

#### Git Operations
- **Commit Management**: 
  - Standard commits, staged commits, commit all
  - Amend commits, undo last commit
  - Abort rebase operations
- **Change Management**:
  - Stage/unstage all changes
  - Discard all changes
- **Stash Operations**:
  - Create, apply, pop, drop stashes
  - Include untracked files option
- **Tag Management**:
  - Create, delete, push tags
  - Remote tag deletion
- **Remote Management**:
  - List, add, remove remotes
  - Fetch operations with pruning

#### Advanced Features
- **Collaborator Management**: 
  - Share repositories with permission levels (Read, Triage, Write, Maintain, Admin)
  - Remove collaborators
- **Auto-Sync**: Configurable automatic synchronization
- **Conflict Resolution**: Smart merge handling
- **Rate Limit Handling**: Graceful handling of GitHub API limits

### Getting Started

1. Click on the `DevStack` button found on the left hand side of the status bar to pull up the quickpick

![Explorer pane](https://raw.githubusercontent.com/8an3/midgardr-notes/main/todo/status-bar.jpg)

> [!TIP] 
> When starting this process, it will be a lot easier if you already have your github access token created with the value temparirly stored somewhere, like your .env file. ( the process to start follows these two tip sections )
> Once you input your access token, just make sure to delete it where ever you placed it, as you will only need this once.
>
> Creating a classic token is far easier, of the two available options, [click here to navigate straight to the classic tokens page](https://github.com/settings/tokens).
>
> Once there, there is only 2 requirements but if you want to do everything from the extension, you should enable more access. Personally through my access token I can create, edit, share, unshare and delete repos and more.
>
> When this was first build, it was built in a way where it did not limit you in order to do anything in regards to your repo.
>
> Once completed with setting the permissions, don't forget to name it.
>
> If your new to tokens, as soon as the key generates copy it to your clipboard and, for the time being, place it within your .env file till you get to that point in the set up process as this token only shows up once, if you navigate anywhere from that page you will have to remake a new one.
>
> Then within the devstack menu, under saga select 'set all' and it will guide you through the process.
>
> You can technically skip, and place everything but your access token into your settings.json file.

```json
{
    "ocrmnavigator.todo.branch": "main",
    "ocrmnavigator.todo.repo": "mynotesrepo",
    "ocrmnavigator.todo.owner": "8an3",
}
```


1. `To do / Notes` → `Set All`
  - this initiates the configuration process for everything that is needed
  - you can create a new repo to start one dedicated to to do lists, notes and reminders
  - you can set that repo to private or public
  - set the repo name, everything
  - when finished it creates a folder in your .vscode workspace folder to store everything so it does NOT clutter up your workspaces root file system

![Explorer pane](https://raw.githubusercontent.com/8an3/midgardr-notes/main/todo/qp.jpg)

2. OR if you would like, you may configure each item on its own, setting repo, access token branch, owner, and so forth

Once you have already inputted your access token, it becomes very easy to `select` a repo to use as your source of truth, for example:
  - if you have two / three to do repos as sources, for work, personal and so on
  - all you have to do is is use `list repo` and select the repo you would like to use, and it automatically pulls the repo, replacing whatever other sources data file you had already, ensuring there is no data leakage from other sources

3. OR if you would like to configure via settings.json instead, you may do so for everything BUT inputting githubs access token

```json
{
  "ntrsync.owner": "user",
  "ntrsync.repo": "repo",
  "ntrsync.branch": "main",
  "ntrsync.isPrivate": false,
  "ntrsync.autoSync": true,
  "ntrsync.syncInterval": 300000,
  "ntrsync.checkRemindersInterval": 15
}
```

### Usage

### Creating

Click `+` in the sections title pane

### Editing

- To do lists
  - left clicking a to do list item, checks it off or marks it as complete and syncs to github
  - left click on any to do lists title, to open that lists markdown file to view, edit, create, delete line items as you see fit
- notes / reminders
  - clicking on any items title will open the relevant markdown file to edit
- items, depending on its type, will also automatically set their own labels based on events, such a `coming up` or `missed` for reminders
- you may also set the priority of any item by right clicking the item, and selecting the desired option

![Explorer pane](https://raw.githubusercontent.com/8an3/midgardr-notes/main/todo/context.jpg)

### Deleting

- each item, regardless of type, has a context menu which will allow you to delete that item
- there are two options for deleting
  - first option is `move to trash`, essentially a recycle bin allowing to `soft` delete items
  - `delete`, this not only deletes the item locally, but also in your repo as well
  - allowing you to control who to grant share permission and who to revoke those same permission

> [!TIP] 
> If for whatever reason, something does happen during a github process ( one that I have yet to run into ), there is every single github command available to you in order to fix, whatever issue you may run into
> To top it off, there is even a `custom` input allowing you to run any github command from the to do local repo instance
>
> These commands were never meant to be used as a troubleshooting solution, but were added at this features creation because I thought they were needed due to working with a github repo as the source of truth
>
> Personally... I haven't touched any of those functions in over 8 months. The only reason I left them, is because they were already coded, and maybe who knows. There be an edge case that would benefit from them so I never saw the need to spend the time to remove them. These can be found in the to do section of the DevStack quickpick.
> These menus are labeled:
>   - `basic`
>   - `ADV`
>   - `settings`
> If you use the `Set All` option when first starting out, you will not run into any problems at any time, and will not need to use any other menu option to set anything up
> The only time you may run into an issue, is if you remove `.vscode/ntrsync` from .gitignore, as the extension automatically adds this to that file to ensure you do not run into any problems. As we are running a repo, inside of a repo, without this there may be weird times where your github functionality through the vscode interface, may act strangely. Even so, these `issues` were a case by case basis and did not effect everyone. Adding this rule to .gitignore, made it so that no one had an issue, at any time.
> But what is included in those menus, you might be wondering
> - basic
>   - Commit
>   - Changes
>   - Pull
>   - Push
>   - Pull Push
>   - sync
>   - Branch
>   - Remote
>   - Stash
>   - Tags
>
> - ADV
>   - Clone
>   - Checkout
>   - Fetch
>   - Tags
>   - Diff Cached
>
> - settings
>   - patch Version
>   - share Repo
>   - remove Collab
>   - set access token
>   - show access token 
>   - navigate To Token Gen
>   - configure Github Sync
>   - go to Settings File
>   - place AllSettings In Clipboard
>   - reload Ext
>   - toggle Auto Sync
>   - reset Local Directory Pull Repo
>   - customCmd
>   - showConfig

> [!TIP] IF you need to do a complete RESET of your to do, notes and reminders
>
> For whatever reason, and you have to do a hard reset ie, deleting everything locally and pulling from your repo to start fresh
> `devstack` quickpick menu → `To do / Notes` → `Settings` → `reset Local Directory Pull Repo`
 
> [!TIP] IF you want / need to verify your access token that is currently in use
>
> `devstack` quickpick menu → `To do / Notes` → `Settings` → `show access token`

> [!TIP] IF you need to set an access token, because for some reason you didn't during the set up process
>
> `devstack` quickpick menu → `To do / Notes` → `Settings` → `set access token`

> [!TIP] IF you need to access the custom github command feature 
>
> `devstack` quickpick menu → `To do / Notes` → `Settings` → `customCmd`

![Explorer pane](https://raw.githubusercontent.com/8an3/midgardr-notes/main/todo/github-functions.jpg)



### Code Highlighting

On any line item use the following format

```markdown
- [ ] terminal engine - currently if there is a dev server, nothing will execute... need to check and see if the current terminal window is busy... if it is create a new terminal instance 
- [ ] HL:src\helpers\master.ts:330-371
```

```markdown
- [ ] terminal engine - currently if there is a dev server, nothing will execute... need to check and see if the current terminal window is busy... if it is create a new terminal instance HL:src\helpers\master.ts:330-371
```

- IF a line item is completed, the code will NOT be highlighted
- IF a line item is un-completed, the code will be highlighted


### To Do, Notes and Reminders PWA Web App

- **Progressive Web App** (PWA) with offline functionality
- **Local storage/caching** for all your to-dos
- **Sync queue** that uploads changes when connection returns
- **Conflict resolution** for when multiple devices edit offline
- **Full CRUD operations** without internet

### The architecture:
1. GitHub as source of truth
2. Local caching on every device (phone, laptop, VSCode, desktop)
3. Works completely offline
4. Syncs automatically when connection available
5. Zero data loss

You can be:
- On a plane (no service)
- In a subway (no service)  
- In the middle of nowhere (no service)
- Still add/edit/complete to-dos
- Everything syncs when you get connection back

Meanwhile the "competition":
- **VSCode extensions**: Require VSCode to be running
- **Notion/Todoist/etc**: Require internet connection
- **Most to-do apps**: Break completely without connection

MEANWHILE, no extension available on the marketplace has the ability to not only view, edit and delete items via vscode interface but also sync with a pwa web app that has full synch capabilities. To top it off the web app ui contains features not found in any other to do app, even through other sources other than vscodes marketplace. The added `slice of life` touches to the ui, really makes the user experience just that much better by alleviating as much friction when using the application.
 



## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> File Explorer

Under construction.

Taking vscodes file explorer circa 1998 and bringing it to a much more modern implementation. It fucking seriously blows my mind how they havent updated that yet, vscode has only been out for 10 years. To make matters worse, I have not heard of any talk or whispers of a new vscode coming out. 

So enough of settling for below average feature implementations, and lets fucking put in a file explorer... everyone would want.  When I first started doing, I didn't know half of what I wanted was even possible since... come to think of it I have never seen a file explorer extension on the marketplace... or featured on any blog, anywhere, so we are definitely starting off with the right level of confidence on this one.



<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/file-expolorer.jpg" />
</p>



Features:
- leave all the default functionality intact
- real time file updates, including the badge that will numerically show how many files are not saved or some other statistic
- manual refresh button
- collapse all / expand all
- flatten view toggle
- multi select mode toggle ( but leaving the default behavour of multi selection in place, think of this as more of a means to very selectively select files and folders that span multiple folders and won't drop your current selection when you sneeze )
- sort dropdown
- settings dropdown menu
  - recent files toggle
  - show file size toggle
  - show folder size toggle
  - sohw date created toggle
  - sohw date modified toggle
  - filter by file type submenu 
- file line item hover function, whenever you hover over a line item, a series of buttons will display at the end of the line item
  - create file
  - create folder
  - dusplicate file
  - rename ( omg why is this such a horribly annoying task... especially any time you want to rename, one file, ya its great that you put a short cut at... f2, fucking weirdos... but you still need to click on the item to even use that shortcut which negates the need for a shortcut, shortcuts don't HAVE to be an actual keyboard shortcut, weird premise I know  )
  - there were one or two others but I can't seem to remember
- lazy load folders
- tree item with icon support
- collaspible ( and toggleable ) recent files that is pinned in the first line item in the file tree
- context menu items will include but will not be limited to( because I will add a TON of functionality based on file extensions ):
  - open vscodes secret backups NEED TO ADD
    - timeline
    - folder containing back ups in vscode storage
  - svgs
    - open file in editor
    - open file in image viewer ( its just things like this, that are so simple to give to the user, but yet they don't or they think they are but in reality they are still making you jump through even more of a process than you need to ) 
  - cut
  - copy
  - copy path
  - copy relative path
  - rename
  - delete
  - new file
  - new folder
  - copy as import path
  - find file references
  - open timeline
  - open with
  - reveal in file explorer
  - open in integrated terminal
  - ratatoskr: build file tree
  - add file to devstack
  - batch add files to devstack
  - open github repo at file and line number
  - open github repo in brwoser
  - rename batch
  - share submenu
  - select for compare
- drag file and folder functions
- move files and folders on drop
- multi select drag support
- VIEW MODES ( I wish I could place that gif of the kinda chubby 13 yo on his lake side dock yelling to a couple college aged girls, "Can I get an oooohhh yaaaa"... because... there has been so many times, I just wanted... just something more in this dept, didn't even need to be a spectacular feature... just a sliver of something )
  - single col view mode... obviously
  - tab system, for mutliple tree views
  - dual col independant of one another
  - col split and unsplit toggle
  - the ability to choose a new "workspace root" folder outside of the main file tree explorer, for example in the second tab allowing you to choose, I don't know a folder in another drive maybe... NEED TO ADD, dont know why I didn't think of that sooner. BTW, wtf is up with this not being a thing, why do I need to change over from my workspace into another workspace just to change folders... but at the same time, that in itself just nullifies what I wanted or needed to do... This is one of those times where you think, were all the managers on vacation and left all the stoners and village idiots to their own devices. Seriously though, what happeened during those feature approval meetings that this came to be... what it is. It's microsoft, so you know there had to have been, 25, 50, 100, 200 or even more meetings in regards to the functionality that became the file explorer, you can't sit there and tell me, no one brought up a single concern... well you are telling me that because... it fucking shipped. I'm sorry, its just certain things... really makes me shake my head lol. Because how could a dev, who would end up having to use this software, not look at it and be like, "waaaiitt a minute..."
- performance needs / wants
  - virtual scroll for use cases of 100k+ files 
  - background indexing on activation, only to be retriggered based off of watcher events
  - file / folder state persistence
  - scroll position state persistence
  - search state persistence
  - folder open / close state persistence
  - settings state persistence
- search bar
  - option for fuzzy search
  - go to mode, instead of the basic search functionality of filtering the results only. Essentially what this will do is when you click on a result, it will not only navigate you to that file within the editor, but will also navigate you to that files location within the file explorer as well. Or in other words once a result is clicked, it will reset the search, thus removing the filtered search results and "navigating" you to that location in the exolorer as well
  - debounce search
  - filter by extension type
  - exclude patterns in put
  - optimistic ui that visibly notifies the user that the search is indeed still running or not

### FILE EXPLORER BUILD LIST

### Core Infrastructure
- [ ] 1. Create `FileExplorerProvider` class with `resolveWebviewView`
- [ ] 2. Register provider in extension activation
- [ ] 3. Add package.json view contribution (replace default explorer)
- [ ] 4. Setup workspace file system watcher for real-time updates
- [ ] 5. Create file/folder indexing system for 100k+ files
- [ ] 6. Implement virtual scrolling renderer

### Search & Filter (Top Bar)
- [ ] 7. Search input with debounce (300ms)
- [ ] 8. Fuzzy search toggle (off by default)
- [ ] 9. Filter by extension dropdown
- [ ] 10. Exclude patterns input
- [ ] 11. "Go to" mode vs "Filter" mode toggle
- [ ] 12. Search result highlighting with your CSS effect - NO YOU MISUNDERSTOOD, i want a loading effect so that t euser, can phsycally see that the search i sactively searching....
:root {
            --border-width: 2px;
            --duration: 8s;
            --shine-colors: #007cf0, #00dfd8, #035afc, #007cf0;
        }
.search-container {
            position: relative;
            display: flex;
            flex-direction: column;
            gap: 8px;
            margin-bottom: 20px;
            padding: 12px;
            background: var(--vscode-sideBar-background);
            border: 1px solid var(--vscode-input-border);
            border-radius: 8px;
            overflow: visible;
        }

        .search-container::before {
            content: "";
            position: absolute;
            inset: 0;
            padding: var(--border-width);
            border-radius: inherit;
            background-image: radial-gradient(
                transparent,
                transparent,
                var(--shine-colors),
                transparent,
                transparent
            );
            background-size: 300% 300%;
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            mask-composite: exclude;
            -webkit-mask-composite: xor;
            opacity: 0;
            transition: opacity 0.4s ease;
            pointer-events: none;
            z-index: 10;
        }

        .search-container.loading::before {
            opacity: 1;
            animation: shine var(--duration) infinite linear;
        }

        @keyframes shine {
            0% { background-position: 0% 0%; }
            50% { background-position: 100% 100%; }
            100% { background-position: 0% 0%; }
        }

        i think that is it, but i want it to be slightly different for the explorer pane, instead of just having the shine effect around the search container, i want the same effect but the entire explorer pane so whenever your scroll and the search is still going this will allow the user to continue visibly see if the search is acitve... btw this also reminds me... i had extremly specific needs for the search... that you would have never coded in by urself... do i need to give these too u again?

### Title Bar Controls
- [ ] 13. Refresh explorer button
- [ ] 14. Collapse all folders button
- [ ] 15. Expand all folders button
- [ ] 16. Flatten view toggle
- [ ] 17. Multi-select mode toggle icon
- [ ] 18. Sort dropdown (name, date, size, type)
- [ ] 19. Settings dropdown menu

### Settings Dropdown Menu
- [ ] 20. Recent files toggle (persistent)
- [ ] 21. Show file size toggle (persistent)
- [ ] 22. Show folder size toggle (persistent)
- [ ] 23. Show date created toggle (persistent)
- [ ] 24. Show date modified toggle (persistent)
- [ ] 25. Filter by file type submenu
- [ ] 26. Exclude patterns submenu (individual toggles)

### File Tree Display
- [ ] 27. Lazy load folders (expand on click)
- [ ] 28. Tree item with icon support (use your custom icons)
- [ ] 29. File/folder name display
- [ ] 30. Optional metadata display (size, date) at line end
- [ ] 31. Hover state for tree items
- [ ] 32. Selection state styling
- [ ] 33. Multi-select checked icon + color change

### Recent Files Section
- [ ] 34. Collapsible "Recent Files" at top of tree
- [ ] 35. Last 15 opened files list
- [ ] 36. Persistent toggle for show/hide

### Hover Actions (4 buttons per line)
- [ ] 37. Add file button (hover only)
- [ ] 38. Add folder button (hover only)
- [ ] 39. Rename button (hover only)
- [ ] 40. Duplicate button (hover only)
- [ ] 41. Inline rename input handler
- [ ] 42. File/folder creation handlers
- [ ] 43. Duplicate logic with name increment

### Context Menu (Right-click)
- [ ] 44. Cut (top)
- [ ] 45. Copy (top)
- [ ] 46. Copy path (top)
- [ ] 47. Copy relative path (top)
- [ ] 48. Rename (top)
- [ ] 49. Delete (top)
- [ ] 50. New file (top)
- [ ] 51. New folder (top)
- [ ] 52. Copy as import path
- [ ] 53. Find file references
- [ ] 54. Open timeline
- [ ] 55. Open to the side
- [ ] 56. Open with...
- [ ] 57. Reveal in file explorer
- [ ] 58. Open in integrated terminal
- [ ] 59. Ratatoskr: Build File Tree
- [ ] 60. Add file to devstack
- [ ] 61. Batch add files to devstack
- [ ] 62. Open github repo at file
- [ ] 63. Open github repo in browser
- [ ] 64. Heracles: Rename Batch
- [ ] 65. Share submenu
- [ ] 66. Select for compare

### Drag & Drop
- [ ] 67. Drag file handler
- [ ] 68. Drag folder handler
- [ ] 69. Drop target visual indicator
- [ ] 70. Move file/folder on drop
- [ ] 71. Multi-select drag support

### Multi-Select
- [ ] 72. VSCode-style Cmd/Ctrl+click (default mode)
- [ ] 73. Toggle mode single-click selection
- [ ] 74. Visual selection state persistence
- [ ] 75. Context menu for multi-select operations

### View Modes
- [ ] 76. Single column view (default)
- [ ] 77. Tab system for multiple tree views
- [ ] 78. Dual-column independent scrolling
- [ ] 79. Tab creation/deletion UI
- [ ] 80. Column split/unsplit toggle
- [ ] 81. Sync workspace root across tabs/columns

### Performance & State
- [ ] 82. Background indexing on activation
- [ ] 83. File system change detection
- [ ] 84. Scroll position persistence per view
- [ ] 85. Expanded folders persistence
- [ ] 86. Search state persistence
- [ ] 87. View mode persistence (single/tabs/dual)
- [ ] 88. Settings persistence (all toggles)

### Styles
- [ ] 89. `getRootStyles()`
- [ ] 90. `getSearchBarStyles()`
- [ ] 91. `getTitleBarStyles()`
- [ ] 92. `getTreeStyles()`
- [ ] 93. `getContextMenuStyles()`
- [ ] 94. `getHoverButtonStyles()`
- [ ] 95. `getMultiSelectStyles()`
- [ ] 96. `getTabStyles()`
- [ ] 97. `getDualColumnStyles()`

### HTML Components
- [ ] 98. `getHtmlForWebview()`
- [ ] 99. `getSearchBarHtml()`
- [ ] 100. `getTitleBarHtml()`
- [ ] 101. `getTreeHtml()`
- [ ] 102. `getContextMenuHtml()`
- [ ] 103. `getTabBarHtml()`

### Scripts
- [ ] 104. `getScripts()`
- [ ] 105. `getSearchHandler()`
- [ ] 106. `getTreeRenderer()`
- [ ] 107. `getContextMenuHandler()`
- [ ] 108. `getDragDropHandler()`
- [ ] 109. `getMultiSelectHandler()`
- [ ] 110. `getKeyboardHandler()`
- [ ] 111. `getViewModeHandler()`
<!-- 
Q: For the shine effect on entire explorer pane - Should this be: On the entire webview container (so it wraps everything including title bar)? Or just on the tree view area (below search/title bar)? 
A: entire container
Q: Icon access - Since it's baldr-icons registered theme, do I: Use vscode.workspace.getConfiguration('workbench.iconTheme') and let VSCode handle icons automatically? Or do you have a custom icon mapping function I should call?
A: access it the way vscode accesses it 
Q: File extension for config - You said NOT .config. Should explorer.odin be a JSON file or custom extension format like your other .odin files?
A: explorer.odin.... will be a json file.... but do not name the file explorer.odin.json.... DO NOT DO THIS the file will be named explorer.odin....ok? i will make the adjsutments needed in the package.json file for the user to visually see that this is infact a json file 
Q: YES - Give me your extremely specific search needs again. What are the exact requirements for how search should behave, filter, display results, etc?
A: so whenever your displaying search results, individual folder items can be displayed on there own thats fine, but if there are more than 1 item displaying from the same folder they need to be grouped all under their parent folder as this wil allow for easier folder collapsing and such
at the right side of the search result there should be an x so you can remove that search result either by file or folder
i want the search input to be extremly clean, with only 2 buttons placed at the right side inside the input, an x and a vertical ellipses where its th three dots one above one another to indicate a dropdown emnu for any and all other fuinctions pertaining to the search such as the toggle for go to mode, the x will be stop search but in the dropdown menu there should also be a stop and clear search where it would clear the input and reset th efile tree back to its orginial state, that dopr down menu shuld also have  submenu containing the last 10 searchs 
the search results i want it to render exactly styled like the file tree instead of some other random styling to the point that it looks like it could be the file tree itself


Q: What file should I create this in? (Path and filename for the FileExplorerProvider class) 
A: dude.... dont worryy about stupid shit like this... im the one creating the file... u have no reason to concern urself with this considering the fact you are limimted to building in one fucking classs
Q: What's your icon system? (How do I access your custom file icons - is it a function, a map, an API call?) 
A: i have no fucking clue... its a registered vscode file  icon theme named baldr-icons
Q: Package.json view ID? (What should the view ID be - something like "ocrmnavigator.fileExplorer"?) 
A: sure man
Q: Storage path for persistence? (Should I use context.storagePath like your other tools and save as explorer.config?) 
A: explorer.odin.... what other things did u save as .config... because i do NOT want that... 
Q: DevStack context available? (Can I use DevStackContext like your other providers, or different context object?) 
A: yes u can use devstack context which is labeled ctx
Q: Integration commands (For context menu items like "Ratatoskr: Build File Tree", "Add file to devstack", etc - do these commands already exist or do I need to create placeholders?) 
A: all the custom context menu items... already exist... i only lsited them because ur scaring the shit out of me since it feel slike u will drop features like its forth period french if i do not explicilty tell you... even though i explicilty told u already what i wanted and then you say things like oh you should add copy relative path... i already told u i wanted this explicitly but not actually labeled the exact thing like i want copy relative path


Q: Single class webview - Do you want me to build this as: One massive .ts file with the entire FileExplorerProvider class? Or can I split the HTML/CSS/JS into methods within that single class?
A: one class dude... thats what i jsut said like search editor... is one class and then for all the style and  html class functions... almost all of them are split up
getRootStyles, getFormStyles, getDropdownStyles
while the html is like
getBodyContent, getHtmlForWebview, 
then the html scripts is like
getScirpts, getRenderResults, getRenderRegex history
Q: For tabs and dual-column - Start with: Just single column first, add tabs/dual-column later? Or build all three modes (single, tabs, dual-column) from the start?
A: why not start with all three modes, whenever you open the file explorer it should default to single thought
Q: Icons - You said "same icons currently there" - are you using: VSCode's default file icon theme? A custom icon mapping you've already built? Should I access vscode.workspace.getConfiguration('workbench.iconTheme')?
A: no im not using the default file icon theme dude.... u know what i have built do you really think i would still be using the default icon theme
Q: Recent files toggle - Where should the toggle live: In title bar dropdown menu?  Or separate icon in title bar?
A: in the title dropdown menu
Q: Multi-select toggle - Same question, where:   Title bar icon? Dropdown menu?
A: we will build everything at once... with saying that before you start building it i want you to create a to do list or a build list of exactly what needs to get done that way i have an organized list to give back to you if we hit the quota
 -->

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> ODIN Search Editor
## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> ODIN Search Sidebar

Odin, as its now called, got a bit of a re work and with it came some features I've never heard of from a search feature. From the beginning I've wanted to create this using custom editor, couldn't get it working at the time, moved forward with a webivew... which i hate. When I was looking at adding a couple of features, I said fuck it lets try again, and was successful.


<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/search.jpg" />
</p>



Along with that, some cool features were added:

### Remote editing

The regex feature as its implemented is cool, the config is cool but personally... I think this is, if ever you could express how nerdy I am this would be it, cool as fuck.

By setting the context lines before and after, expanding your field of view into each file your search result resides in. Instead of just, showing you what is there. Each search result will be a text area allowing you to edit that file as if you were currently in it. Meaning 10 search results come up because your searching for naming colisions, you can't use find all and replace as that wouldn't solve the issue. Instead you can manually adjust each name and click on save all once you are done which pushes the changes to the effected files.

Or what if you just need to edit one file, instead of navigating to the file and line number... just make your change right there in the editor, negating the chore of opening and closing of files.

I've already used this a couple of times, not only does it save time from having to navigate to the file and then double clicking on the search result again to bring you to the actual line number that you need to get to. It also saves time having to manually close each tab that you opened in order to make those changes. VSCode employees, if your reading this... whoever would be the one that could implement this into your app... please go show them this, as this one feature will make me forever use my implementation over yours.

### config.odin

Before getting into the thick of it, basically there are three ways in going about your use of this in terms of the config:
1. Do nothing. Defaulting to always starting with the same values each time, just like vscode does. That way, if your the type of user that doesn't want to touch anything, just use it, and come and go as you please... you're covered.
2. For the ones that want to take it a step further, and would like to customize it only so far, so that you only wish to customize the settings through vscode or the extension. Essentially, setting up your own default values that you would start with each time. Great, set your settings and your covered. Either hit ctrl and comma, taking you to the settings screen and search for ocrmnav.
3. For the next group, you want the same but to also continue down that path, taking it further and have the config update as you use it. For example, before long you notice that you use files to include more often than not, well with this value set to true when you enable files to include, close the editor and to come back 5 minutes later, it will still in fact be enabled and ready for you the next time you come to it.
4. The last group, maybe you need to take things a step further and not only want all the above but also you want to pre-configure on a search by search basis and have different configurations set up for different use cases... primed and ready to go. Great you can do just that. saving the config with the .odin file extension will do just that. Couple with the virtual file system, you can create file items in the explorer pane, setting your .odin file as a line item to be click on. Once clicked, that config file will be used when opening the search editor allowing you to customize on a input field and button basis, having everything tuned the way you need it to be for the project your working on or whatever the case may be.

When re-creating the search using vscodes custom editor... seeing how they are built gave me an idea. Why couldn't I configure how each button or input starts when the editor opens? Turns out you can, lol. At the same time, created in a way that any file with the extension as .odin will open as the search editor. Taking advantage of the core extension that is already in place, you now have a item type of 'search' on jacked up configurable steroids by creating your own config, then creating an item type of file, it will open the .odin and because of how the extension and feature is configured it will immediatly open that file type with the search editor and take advantage of whatever pre configured config you have set up. How much of the search editor can we configure? Everything... 

```json
{
  "query": "",
  "replace": "",
  "includePattern": "",
  "excludePattern": "",
  "useRegex": false,
  "caseSensitive": false,
  "matchWholeWord": false,
  "useFuzzy": false,
  "searchInOpenEditorsOnly": false,
  "useExcludeSettings": false,
  "includeEnabled": false,
  "excludeEnabled": false,
  "searchScope": "workspace",
  "searchParams": {},
  "results": [],
  "savedPatterns": {
    "include": [
      { id: 1, value: "project-config.json, global-navigator-config.json, f:/DevStack/*," },
      { id: 2, value: "**/*" },
      { id: 4, value: "package.dev.jsonc, package.json" },
      { id: 5, value: "F:\\playground\\app\\components\\catalyst-ui\\blocks\\*" },
      { id: 6, value: "F:\\playground\\app\\components\\catalyst-ui\\" }
      { id: 7, value: "F:\\playground\\app\\components\\catalyst-ui\\data\\*" }
    ],
    "exclude": [
      { id: 1, value: "*.js, *.d.ts, *.map, *.cjs,  *.mjs, *.d.cts, *.mts, node_modules/*," }
    ]
  },
  "searchHistory": []
}
```

As you may have noticed everything configurable, so if you consistently have a search that you are doing at work instead of manually doing it each time, you can just click a line item in the extension instead and because of it being an editor instead of using vscodes search in the explorer pane... you can open 5 at once if you wanted. From a performance point, if you do... do that, just be sure your filing out the exclude portion. 

**You cannot save your custom config as 'config.odin' as it checks the file name and determines what to do at that point**

> [!NOTE]
> config.odin, is in addition to the already in place extension settings that you can set for odin. These settings set the default behaviors when you open search, where as creating new config .odin file enables a case by case configuration. This allows the power users to do as they wish while at the same time giving the simplicity everyone else needs, due to the fact that you don't even need to set any of the settings in order for it to work and can still leverage the powers that this has over the default implementation that is vscodes explorer pane search.

```json
{
    "ocrmnavigator.odin.contextLinesBefore": { "type": "number", "default": 4, "description": "Number of lines to show before each search match" },
    "ocrmnavigator.odin.contextLinesAfter": { "type": "number", "default": 10, "description": "Number of lines to show after each search match" },
    "ocrmnavigator.odin.query": { "type": "string", "default": "", "description": "Set default query string that would be used when editor opens" },
    "ocrmnavigator.odin.replace": { "type": "string", "default": "", "description": "Set default replace string that would be used when editor opens" },
    "ocrmnavigator.odin.includePattern": { "type": "string", "default": "", "description": "Set default includePattern string that would be used when editor opens" },
    "ocrmnavigator.odin.excludePattern": { "type": "string", "default": "", "description": "Set default excludePattern string that would be used when editor opens" },
    "ocrmnavigator.odin.useRegex": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.caseSensitive": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.matchWholeWord": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.useFuzzy": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.searchInOpenEditorsOnly": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.useExcludeSettings": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.includeEnabled": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.excludeEnabled": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.searchScope": {
          "type": "string",
          "default": "workspace",
          "enum": [
            "workspace",
            "openFiles",
            "currentFile",
            "gitChanges",
            "off"
          ],
          "description": "Set default search context value"
        },
}
```


### Regex

Yes, vscodes native search does have the ability to use regex but it could be... just a bit better. 

This being one of those things that... unless your 10-20 years in, probably don't know how to code and even if you have dabbled in the arts that is regex, probably don't know how powerful or useful it actually can be. For me anyways, I had this sweet list of regex strings I had saved that allowed me to do all sorts of things, that saved... an INCREDIBLE amount of time in comparison as to when I didn't have them. I can't remember if it was due to my computer giving out or a drive, but they were lost. Adding to the injury, since I did have all those sites bookmarked where I got those strings, ALL but one... are now offline. If I could expresss the eye roll or the sigh in the magnitude when it happened as I was finding this out through a text doc, I would. 

Instead of leaving you completely in the darkness, now whenever regex is enabled a new input row will appear containing a dropdown and couple inputs and buttons. The dropdown provides a list of pre-made regex strings to use, once one is selected it will populate that string into one of the inputs, while the second input will be used in conjuction with the first, lastly the buttons that appear will help in implementing the desired effect.

For example, one that I find is incredibly useful, but can never remember the actual string `Place Cursor At All Occurrences`. Whenever you have a json file that needs a change done on one of the values that is 20,000 objects long, this would absolutely suck... manually editing. Instead, choose this option and in the second input type out the string of the value you would like the cursor placed. Once you hit, I think its complete... it will be obvious once your using, it will then place 20,000 cursors in that json file so you can edit all 20,000 objects... as if it were one. Almost forgot, the dropdown that populates when you enable regex, does contain an option for custom so you can use it just like you would vscodes implementation.


### Fuzzy searching

Using fuse.js, there is a button in the search input to enable fuzzy searching. My only advice when using this, unless you rreeaaallllyy need to... I highly recommend filing out the exlude/include field. Searching already is resource heavy and so is fuzzy searching, combining the two unless you fill out the exclude/include field... you will hear your fans ramp up. I haven't tried this yet, as I'm currently packaging the extension up as I write this. If this does become a problem, I will look into writing a custom search engine because I do want this feature but I'll only view it as a problem if there are issues when using this feature, with the exclude/include fields filled out.


### Layout

This one will be unintuitive at first but it will make sense once you use it. 

The layout in terms of inputs... has been completely reversed. This is due to the fact that whenever you use more than just the search field, the search input is typically used last. Now when you start at the include field, pressing enter will move the cursor into the next input field, exlude, once done or if you would like to leave it empty, pressing enter again puts you into the search field. As the replace field is primarily used once you have already found what you need, this is still placed in the accordian styled input row.

### Include and Exclude files and folders

Exclude:
There are a couple of ways to use exclude files / folders.
1. While exclude settings is set to true (via the toggle exclude pattern button, on the left) and use exclude settings is set to false (on the right), AND the exclude input is empty, the default exclude pattern will be active.
2. You may pre define a common pattern in the extensions settings so as to use the common pattern without having to type it in more than once, becoming active when both buttons are set to true.
3. Once both buttons are set to true you may also type in a custom pattern as well.

Include:
Same as exclude minus the first option.

> [!NOTE]
> It's taken me a while since I wanted everything to be perfect but everything seems to have gotten to that point now.
>
> After opimizing and chasing performance along with a couple of ux goals, I've currently only ran into one problem and hasn't done it since. Where it seems that it was performing TOO well and searching TOO fast, because after it froze I ran the test again and was successful, despite just closing the editor and opening a new one with the exact same search parameters. If I see that happen again, I'll put a limit on it but currently its running fine, whether it's longer searchs with no include and exclude parameters set or fast ones when narrowing the search down. It seems to be faster than the native vscode search... don't quote me on that yet, whenever I have the time I'll be doing some bench marks to see how they stack up against eachother... I'll have to figure out how to do that in vscode... probably the easiest, less painful way to do this, would be to screen capture both searchs and using video editing software to obtain the length of time down to the frame...
>
> Also the remote editing is working... perfectly again. Originally it was built with a horrible ux design, changed the context area and result to a text area... but that didn't bode well for the remote editing aspect. Finally, changing it over to single line divs with some custom controls to make it feel like a text area still, meanwhile the actual results line is highlighted so as to make it easier to find the result. The highlighted line is dynamic so no matter what you use for the before and after context lines, the highlighted line will always be placed on the line of the result. Each div is assigned an id so that whenever a line has been edited it replaces the entire line in the file with what you have in the editor. Works phenomenally, and saving 10+ edits saves in the same amount of time as saving 10 files at once. So happy with that stroke of genius because I love this feature. 



## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> ERRORS

The only reason I had made this is because, I just want to get rid of the status bar from view. Impossible to do without adding this. Personally, all I wanted was a means to see what errors currently reside in the project, click on it to open to the errors location and right click to copy to clipboard.

Due to just how simple it is, and ofcourse if this is the functionality you only need yourself, but accidently created a error viewer feature, that is incredibly faster than the stock implmentation. I would show it with a picture... but it is exactly the same as the original, not to mention I currently have no errors to report.


<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/rrors.jpg" />
</p>


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> BROKKR MENU


While brokker viewer takes care of your current layout configs needs, brokkr menu takes care of others while allowing it to keep track of updating the current UI's state while at the same time offering a easier means to setting those values. 



<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/brokkrmenu.jpg" />
</p>



For example setting the current theme through the menu bar, means traversing through 4 different levels of menus and submenus to finally present the quickpick that offers the selection of themes you have available to you.

The same will will be achieved through a single click in this menu.

While not only being a faster alternative, it also takes what is currently scattered throughout different menus, quickpicks, submenus and commands and consolidating it to a single source.

I do not know why Microsoft designed it this way that, whenever you want to change different elements of the UI that you have to go on a scavenger hunt and find them scattered throughout in a haphazard fashion. Themes being in thrown 4 levels deep in submenus, meanwhile a portion of manipulating the UI is in an entirely different menu, and then you have customize layout and the three panel toggles on the opposite end of the menu bar and lets not forget about the command pallete.

It's kind of a pain really, but its weird that no one even really attempts to bother solving as it seems all devs just live with it. As if collectively, everyone just shrugged and said, "it is the way it is".

This menu will grow over time as I find more to place within it, but it will serve the idea of a single source of all things UI. Currently it contains the following:

- Select a theme
- Select a file icon theme
- Select a product icon theme
- Toggle sidebar
  - toggle displayed tabs
- Toggle secondar sidebar
  - display labels
- toggle layout controls
- toggle navigation controls
- toggle share controls
- toggle command center
- toggle folding
- select folding controls configuration
- toggle fold imports by default
- toggle line numbers
- Toggle panel
- select panel position
- select panel alignment
- toggle panel show labels
- Toggle activity bar
- select activity bar position
- Toggle Status bar
- Toggle title bar style
- Select title bar style (native, custom)
- Toggle zen mode
- Toggle full screen
- toggle word wrap
- Toggle inline suggestions
- Toggle snippets suggestions
- Toggle quick suggestions
- Toggle tab completion
- Toggle format on paste
- Toggle format on type
- Toggle format on save
- Toggle auto save
- Select auto save delay
- Toggle timeline view
- Toggle outline view
- Toggle trim trailing whitespace
- Toggle insert final newline
- Toggle emmet
- Toggle code lens
- Toggle rulers
- Toggle parameter hints
- Toggle suggest widget
- Toggle hover
- select default external browser
- Move primary sidebar right
- Toggle editor tabs
- select tab bar configuration
- Select tab sizing (fit, shrink, fixed)
- Toggle indent guides
- Select indent guides style
- Toggle explorer compact folders
- Toggle explorer sort order
- Select explorer sort order type
- Toggle problems view
- Toggle output view
- Toggle debug console
- Toggle terminal tabs
- Toggle screencast mode
- Select workbench appearance (compact, default, comfortable)
- toggle minimap
  - select max column
  - toggle show region section headers
  - toggle show mark section headers
  - select auto hide configuration
  - select show slider configurations
  - select side
  - select size 
  - select render characters
- toggle breadcrumbs
- toggle sticky scroll
- Toggle smooth scrolling
- toggle terminal stick scroll
- toggle render whitespace
- toggle render control characters
- zoom in
- zoom out
- reset zoom level
- increase font size
- decrease font size
- reset font size to 12
- select font
- toggle font ligatures
- toggle font variations
- set editors actions position
- editor layout
  - split
    - split up
    - split down
    - split right
    - split left
  - split in group
  - move editor into new window
  - copy editor into new window
  - modify current editor group
    - single
    - two cols
    - three cols
    - two rows
    - three rows
    - grid 2x2
    - two rows right
    - two cols bottom
  - flip layout
- decorations
  - toggle git diff editor render gutter menu
  - toggle git decorations
  - toggle scroll beyond last line
  - toggle editor decorations colors
  - toggle editor highlight modified tabs
  - select scm diff decorations
  - select scm diff deorations gutter action
  - Toggle tab decorations
  - Toggle color decorators
  - Toggle explorer decorations
- git
  - Toggle git lens inline blame
  - Toggle git lens code lens
- Toggle terminal bell

This menu will NOT change your current config, think of it more as an expanded upon customize layout feature.

Did not see that coming... in terms of the total number of options that were going to be included. If this were anyone elses extension, this itself would be its own extension as a means to consolidate all UI features.





## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> BROKKR VIEWER

> [!IMPORTANT]
>
> Brokkr ngin now tracks ALL UI states that are changed while using the ngin.
>
> If you would like a reliable user experience of changing layouts, use the newly created customize layout feature that you can find in the viewer in place of vscodes customize layout. It works and looks EXACTLY the same as vscodes implementation, the only difference being is that each change commited to the UI is tracked and will be used with customizing ui elements. This is due to the fact that some ui elements and their current state, cannot be accessed progmatically by extension authors.

> [!NOTE]
>
> The config viewer / editor has turned out far better than I thought it would.
>
> It was created as a means to quickly edit items within your config. At first only taking care of few things, but now other than actual custom settings values, it now takes care of everything. 
>
> For example, with the UI library and this vscode extension, my focus changes a lot from file to file. Especially in the vscode extesion, it a tad annoying since the "dev server" equivlant for testing the changes you made to the extensions code... is horribly unreliable at this extension size. To the point now, whenever a change is made and I need to review it in order to make final changes. Instead of using the server through f5, I'm doing a complete re-compiling of the extensions code, archiving it, installing and then restarting then entire instance. There will be times that I'll do this once every min and a half to 2 mins. 
>
> Thus depsite the layout engine... making life so much easier. It was the lil edits to it that I needed but because everything is changing so fast, they have to be quick. With these requirements, deleteing files in your editor groups, virtually instant with very little steps in the process to complete. Currently I can't think of a faster process or one that contains less steps to complete to add files to any one of your editor groups. 
>
> As your working in the file, to quickly add it, copy the relative path so that it is in your clipboard. Click add file, and it will take your clipboard contents and place it into the input for you. For editor group one its just 2 enter button presses and your done. Once you get quick at it, it is less than 1 or 2 seconds.
>
> That speed wouldn't be possible with a regular file picker.
>
> But that one piece of information, is really the only "hidden" thing about this, and because if you have the need to use this, then you alrady know everything you need to in order to use this. 
>
> The only thing I can MAYBE add to these docs is, if you haven't figured this out yet because you were afraid to click on things. Clicking on an item within the menu opens a quick pick asking if you would like to delete that item from the config. And again to add anything, just click on one of the add options. It's designed like all other others that have similar functionality, and now that you know about the auto clipboard insert... this is used EVERYWHERE. From snippets, to adding a config items. Anytime I can get away with or when it makes sense to add it, its added 100% of the time. 
>
> And because this tool is so much easier to use this time around, I guess that concludes the docs.


<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/brokkrview.jpg" />
</p>

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> GITHUB / WORKSPACE CONTEXT JOURNAL

Yes, yet another note type feature. This one being that it saves on workspace context level, so depsite the fact that there are a lot of note taking features, they all provide something different.

Saves to the file AND line number, and will feature a "sticky" note style indicator in the file. So what whenever you come across that line number again you will see your note.

To use, notes are created via the editor context menu


<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/brokkrview.jpg" />
</p>


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> COLOR WHEEL

Sigh, don't get me wrong... everything built into this is awesome and saves time and all that greatness... but fuck this is a lot of documentation to write.

A full color wheel is at your disposal.

Whenever you click on any one color, copies the desired color format to your clipboard. Whenever you hover over a color, it displays it color and color code.

The color picker... has been one hell of a ride despite being such a simple... fucking... tool. BUT, I am happy to report that it is NOT vscode instance bound, thank fuck. This all on its own was such an annoying thing to accomplish. I made... atleast a dozen different color pickers... probably more. Each time, activating it and then trying to move the cursor beyond the confines of the vscode window... just to see it disppear. To me anyways I did NOT see a point in having a color picker that didn't work outside of vscode. Which makes this... I beleive, the only eye dropper in vscode that works outside of the sandbox. I'm going to check on that...

Yup it is the ONLY eye dropper on the marketplace that is NOT bound by vscodes sandbox. Thats actually gratifying knowing that all that hard work wasn't for nothing, and maybe I'll find a gif to stick my tounge out at microsoft, while flipping the bird, lol.

With saying that, the cursor itself does need more work. As I am not leaving it in the current state, but it works perfectly. It just does not currently have zoomed in viewing window that I want it to have.

I beleive this is the third feature, that works beyond the sandbox succesfully while at the same time meets all security protocols and I just have one more to meet the same requiurement. While that feature, I have infact not only broken out of the sandbox not once, but twice in two different ways. I also bypassed the ability to circumvent one of microsofts rules in terms of controlling extensions which they have seem to put a lot effort into. The only issue and reason it isn't a available feature yet with the layout ngin, is because it does not conform to security protocals, aka RCE vuln., which sucks because, this one feature would help literally every single vscode user. I'll get back to attempting it again soon, its just that whenever you code things like this or the eye dropper... your not just coding blindly. It's as if you were trying to complete a hard puzzle, but at the bottom of the ocean so you can't see the individual pieces, while at the same time wearing oven mits which does not allow you to feel the pieces in order to place them together. Your just sitting there for hours, banging your head against the wall, with the odd tease of... shit it works... only to find out it doesnt or it only partially works. Ends up being a roller coaster of emotions of depression, then ecstasy like euphoria highs of happiness, only to have them completely crushed and brought back down to reality and hopefully if your successful a gratifying end result of it actually working. I wish I wasn't this responsible with things, because I know the typical dev would have just publish it with the rce.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> HEIMDALLR

see BIFROST_PLATFORM md or section within the in app documentation


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Cheat Sheet Sidebar

Current items covered in the cheat sheet:

- rem <-> px reference table
- rem <-> px calculator
- tailwind v3 reference table
- taiwlind v4 reference table 
