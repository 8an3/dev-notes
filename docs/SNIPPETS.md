
## SNIPPETS

```markdown
/ DEVSTACK_SYSTEM_ROOT/
└── 📝 AUTHORING_SUITE /
    └── 📂 [SNIPPETS_AND_SNAPSHOTS](https://github.com/8an3/dev-notes/blob/main/docs/SNIPPETS.md)/
        ├── 📄 Code Snapshot .................. Snapshot selection to beautiful terminal window
        ├── 📄 Workspace Context .............. Context-aware code snippets
        ├── 📄 [Context Snippets](#context-snippets) ............... Editor context snippets that insert at cursor
        └── 📄 Best-In-Class Editor ........... Create snippets/VFS items in seconds
```
Workspace context snippet system built with Monaco editor for creating, editing, and viewing snippets

- Snippets are stored on a global and workspace level, enabling workspace context snippets
- follows inline with the current context system that has worked flawlessly 
- in the extensions explorer pane, snippet items now auto generate, populating the SNIPPETS folder so you no longer have to manually create items for snippets
- each snippet tooltip will feature the entire body of the snippet for review
- left clicking on any item will place that snippets body, into your clipboard
- customize snippet icons with any of vscodes 520+ available icons

**Editor Access:** Extensions title pane or navigate straight to the web GUI

**Features:**
- Full Monaco editor integration - offering a wide breadth of features you have already become familiar with through the vscode editor interface
- Create and edit snippets with syntax highlighting
- View all snippets in one place
- Fuzzy search capabilities
- Quick insertion workflow
- Automatic workspace synchronization
- automated item generation with the virtual filing system
- copies to clipboard whenever an snippet item is clicked
- incorporated a series of functions into the monaco editor interface to allow an end-user to edit / create snippets, extremely fast in comparison to vscodes implementation
  - `alt + n` creates a new snippet
  - at the time of using the above shortcut, whatever contents are currently in your clipboard automatically get pasted into the snippets body
  - automated prefix building via the snippet label ( that can be disabled )
    - whatever human readable value placed in the label, converts it so each capital becomes lower case and each space becomes an underscore in place of the typical dash ( allowing for a lot quicker process to copy the label into your clipboard, as the double mouse click selection process gets halted by dashses )
  - before saving, if a folder is selected, the save process not only saves the snippet BUT also creates a new snippet item to be placed in your devstack config that will be used within the virtual filing system
  - the web interface consists of a command ( to search, using fuse.js, and view as a scrollable list that does NOT reset to the first snippet once one is selected to view / edit ) and a monaco editor


> [!TIP] Remote access for viewing / editing / downloading / sharing
> Previously, whenever you use the web ui a workspace has to be currently open in your vscode instance in order for the web ui to communicate with it to view, save data on a workspace or global level.
>
> With the implementation of user profiles on the web ui, you can now login to view, edit and download your snippets, DevStack configuration and `to do, notes and reminders` all from the site. Allowing users easier to much more easily share and update different workspaces. 
>
> For example, if you wanted to use the same DevStack configuration that you use at home, at work, you can now just log into the web ui via the title pane button, once logged in you will see a `sync to local` button on your profile dashboard which will download your config, snippets and your `to do, notes and reminders` settings to your currently used vscode instance.
>
> There will also be a download button, allowing you to download those same items to do with as you wish. 
>
> Alongside a `share` button, instead of downloading all of your data, it will only download what you wish to share via the checkboxes. The downloaded zip will only contain what you selected, if you just wish to share your config, you can. If you would just like to share your snippets with a friend, you can. Or maybe you need to share the to do items with a colleague.


![Snippet Editor](https://raw.githubusercontent.com/8an3/dev-notes/main/snippets/snippet-monaco.jpg?raw=true)

### DevStack Snippets vs (Marketplace Leader)

| Feature | DevStack | (Leader) |
|---------|----------|-------------------|
| **Editor** |
| Full Monaco Editor Integration | ✅ | ❌ (Standard editor) |
| Syntax Highlighting | ✅ | ✅ |
| IntelliSense in Editor | ✅ | ✅ |
| **Creation & Workflow** |
| Quick Creation (`alt + n`) | ✅ | ❌ |
| Auto-paste Clipboard on Creation | ✅ | ❌ |
| Create from Selection | ✅ | ✅ |
| Create from Clipboard | ✅ | ✅ |
| Automated Prefix Generation | ✅ (Smart conversion) | ❌ (Manual only) |
| **Organization** |
| Tree File View System | ✅ | ✅ |
| Drag & Drop (Web UI) | ✅ | ✅ (VSCode UI) |
| Automated Item Generation | ✅ (Virtual filing system) | ❌ (Manual) |
| Folder Management | ✅ | ✅ |
| Reordering | ✅ (Move function) | ✅ (Drag/drop, Up/Down buttons) |
| Alphabetical Sorting | ✅ | ✅ |
| **Display & Access** |
| Tooltip Full Body Preview | ✅ (Entire body) | ❌ (Description only) |
| Context Menu Integration | ✅ | ❌ |
| Click to Copy to Clipboard | ✅ (Every click) | ❌ (Explicit action needed) |
| Fuzzy Search | ✅ (Fuse.js) | ✅ (Native search) |
| Non-resetting Scrollable List | ✅ | ❌ |
| **VSCode Integration** |
| All Native VSCode Snippet Features | ✅ | ✅ |
| IntelliSense Trigger | ✅ (Native) | ✅ (Custom key, default `>`) |
| Tab Completion | ✅ | ✅ |
| Command Palette Access | ✅ | ✅ |
| Insert Snippet Command | ✅ | ✅ |
| **Workspace & Scope** |
| Global Snippets | ✅ | ✅ |
| Workspace-Specific Snippets | ✅ (Tight integration) | ✅ (.vscode/snippets.json) |
| Automatic Workspace Sync | ✅ | ❌ |
| Language-Specific Binding | ✅ | ✅ |
| Language Icons | ✅ | ✅ |
| **Sync & Backup** |
| Remote Web UI Access | ✅ | ❌ |
| User Profile System | ✅ | ❌ |
| Cross-Machine Sync | ✅ (Any VSCode instance) | ✅ (VSCode Settings Sync only) |
| Sync Without Same Login | ✅ | ❌ (Requires same account) |
| Local Download | ✅ | ❌ |
| Import/Export JSON | ✅ | ✅ |
| Import from Other Editors | ✅ | ✅ (Cursor/Windsurf) |
| VCS Integration | ✅ | ✅ (Workspace folder option) |
| **Sharing & Collaboration** |
| Selective Sharing | ✅ (Config/Snippets/To-dos) | ❌ |
| Share via Download | ✅ | ❌ |
| Team Workspace Sharing | ✅ | ✅ (Via VCS only) |
| **Customization** |
| Custom Icons (520+ available) | ✅ | ✅ (Folder icons) |
| Custom Descriptions | ✅ | ✅ |
| Custom Prefix Per Snippet | ✅ | ✅ |
| Global Prefix for All Snippets | ✅ | ✅ |
| Snippet Variables | ✅ | ✅ (With "Resolve Syntax") |
| Tab Stops | ✅ | ✅ (With "Resolve Syntax") |
| **AI Integration** |
| GitHub Copilot Chat | ✅ (Native + auto-copy) | ✅ (Copy snippet to chat) |
| Cursor AI Pane | ✅ (Native + auto-copy) | ✅ (Copy snippet to chat) |
| Gemini Code Assist | ✅ (Native + auto-copy) | ✅ (Copy snippet to chat) |
| AI Prompt Storage | ✅ (Snippets work as prompts) | ✅ (Marketed as "integration") |
| **Additional Features** |
| Web GUI for Management | ✅ | ❌ |
| View/Edit/Download Remotely | ✅ | ❌ |
| Insert to Terminal | ✅ (Auto-copy + right-click, configurable terminal) | ✅ (Direct insert, fixed terminal) |
| Terminal Configuration | ✅ (Per-command basis, custom location) | ❌ |
| Drop into Editor | ✅ | ✅ |
| Undo/Redo in Editor | ✅ | ✅ |
| Copy/Paste Across Scopes | ✅ | ✅ |
| Action Buttons UI | ✅ (Context-aware right-click menus per item type) | ⚠️ (Added buttons to compensate for poor UX) |
| Troubleshoot Tool | ✅ (Not needed - no bugs to fix) | ⚠️ (Required to fix sync/move race conditions) |
| Searchable / Scrollable Snippets ( see below ) | ✅  | ❌ |

---

### Key Differentiators

### DevStack's Unique Advantages
1. **Remote Access Infrastructure**: Web UI with user profiles for viewing, editing, and downloading from anywhere
2. **Account-Agnostic Sync**: Sync to any VSCode instance without requiring same login (work vs personal email)
3. **Workflow Automation**: `alt + n` with auto-clipboard paste, smart prefix generation
4. **Virtual Filing System**: Automatic item generation eliminating manual setup
5. **Clipboard-First Design**: Every click copies to clipboard automatically
6. **Full Body Tooltips**: See entire snippet without opening
7. **Selective Sharing**: Choose exactly what to share (config/snippets/to-dos)


## Context Snippets

One of the fundamental problems with snippet systems is prefix recall - you create a snippet with a prefix three months ago, and when you need it, you can't remember what you called it. At that point, IntelliSense becomes useless, and you're forced to open your snippet manager, search for the snippet, find the prefix, navigate back to your editor, and then type it in. Or you just give up and write the code manually.
DevStack solves this with Context Snippets: a searchable quick pick accessible directly from your editor's context menu.
Access: Right-click → DevStack → Context Snippets
Features:

**Access:** Right-click → DevStack → Context Snippets

- Instant access to all your snippets without leaving the editor
- Search by name or scroll through the complete list
- Select and insert immediately - no prefix required
- IntelliSense still works perfectly when you remember prefixes
- Prefixes become optional convenience instead of required knowledge

Context Snippets transforms the snippet workflow from "hoping you remember the right prefix" to "always having instant access to exactly what you need." No navigation, no searching through files, no interruption to your coding flow.

![Context Snippets](https://raw.githubusercontent.com/8an3/dev-notes/main/snippets/context-snippets.jpg?raw=true)


---

[🡄 Return](https://github.com/8an3/DevStack)