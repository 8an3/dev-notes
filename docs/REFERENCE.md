## REFERENCE

## Table of Contents

- [Shortcuts](#shortcuts)
- [VSCode Commands Cheat Sheet](#vscode-commands-cheat-sheet)
- [Clipboard History Pro](#clipboard-history-pro)
- [Global Bookmarking System](#global-bookmarking-system)
- [Markdown Cheat Sheet](#markdown-cheat-sheet)
- [Color Wheel](#color-wheel)
- [Wizards Section](#wizards-section)
- [VSCode Icons](#vscode-icons)

### Shortcuts

Quick access to all DevStack extension keyboard shortcuts.

**Available Shortcuts:**

| Shortcut | Function |
|----------|----------|
| `alt + s` | Context Snippets |
| `alt + c` | Clipboard++ |
| `alt + b` | Show Bookmarks |
| `alt + d` | DevStack Quick Pick |
| `alt + a` | Open UI Dashboard |
| `alt + h` | Show Error History |
| `alt + x` | Catalyst UI Quickpick |
| `alt + v` | Icons Quickpick |

---

### VSCode Commands Cheat Sheet

Comprehensive reference guide with 360+ commonly used VSCode commands.

**Access:** Reference menu

**Features:**
- Browse complete command list
- Search and filter by category
- Quick copy functionality
- Organized by command type

![VSCode Commands Reference](https://raw.githubusercontent.com/8an3/dev-notes/main/reference/vscode-cmds-reference.jpg?raw=true)

---

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

- bookmarks.add
  - Adds the current line in the active editor to your bookmarks
  - Right-click line → DevStack → Add Bookmark
- bookmarks.show
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

### Markdown Cheat Sheet

Complete GitHub-flavored Markdown reference guide with examples.

**Access:** Web GUI

**What's Included:**
- Syntax examples
- Formatting options
- Table structures
- Code blocks
- List formats
- Link and image embedding

![Markdown Guide](https://raw.githubusercontent.com/8an3/dev-notes/main/reference/markdownguide.JPG?raw=true)

---

### Color Wheel

Advanced color picker with multiple format outputs, inspired by ShadCN design.

**Access:** Web GUI

**Features:**
- Interactive color selection
- Multiple format outputs (HEX, RGB, HSL)
- Copy to clipboard
- Real-time preview
- Color palette generation

![Color Wheel](https://raw.githubusercontent.com/8an3/dev-notes/main/shadcn/color-wheel.jpg?raw=true)

---

### Wizards Section

Command reference hub for creating custom workflows and automation.

**Access:** DevStack Quick Pick menu in status bar

**What You Can Create:**
- Custom commands
- PowerShell scripts
- Bash scripts
- Command chains
- Concurrent operations
- Integration workflows

**Features:**
- Browse categorized command list
- Automated updates
- Detailed descriptions for each command
- Custom workflow creation
- Extension integration support

**Note:** Recently redesigned with enhanced descriptions and automated maintenance to ensure up-to-date command listings.

---

### VSCode Icons

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
