## Markdown Tools

## Table of Contents

1. [Markdown Tools](#markdown-tools)
2. [Table of Contents](#table-of-contents)
   1. [MD Viewer/Renderer](#md-viewerrenderer)
   2. [MD Viewer/Renderer In VS Code](#md-viewerrenderer-in-vs-code)
   3. [Catalyst Editor](#catalyst-editor)
   4. [Convert MD File To Safe Inline String](#convert-md-file-to-safe-inline-string)

### MD Viewer/Renderer

Render markdown files directly in your browser with proper formatting and styling


**Access:** Right-click in editor → DevStack → Select option

**Features:**
- Custom CSS support
- Export options
- Theme customization
- Professional rendering

![MD Viewer](https://raw.githubusercontent.com/8an3/dev-notes/main/md/md-render-vscode.jpg?raw=true)


### MD Viewer/Renderer In VS Code

Side-by-side markdown preview within VS Code for seamless editing workflow


**Access:** Right-click in editor → DevStack → Select option

**Features:**
- Live editing with instant preview updates
- Synchronized scrolling between editor and preview
- Multiple split view configurations
- Native VS Code integration

![MD Viewer VS Code](https://raw.githubusercontent.com/8an3/dev-notes/main/md/md-render-vscode.jpg?raw=true)


### Catalyst Editor

A powerful multi-language editor built on Microsoft's Monaco Editor, originally designed for markdown but evolved to support comprehensive development workflows



**Supported Languages:**
- Markdown
- JavaScript & TypeScript
- HTML, CSS & SCSS
- JSON & YAML
- Python
- SQL
- XML
- Java, C#, C++
- PHP
- Rust & Go
- Shell scripts

**Core Features:**

**Editor Capabilities:**
- Multi-tab interface with auto-save
- Persistent settings stored locally
- Toggle minimap, line numbers, and line folding
- Custom folding rules with `#region` / `#endregion` support
- Markdown preview (full screen or split view)
- Full screen mode
- Format document
- Toggle line wrapping
- Find & replace
- Command palette

**Workspace Integration:**
- Access all markdown files in active workspace
- Open, edit, and delete files directly
- Place entire tab content into clipboard

**Keyboard Shortcuts:**
- `Alt + S` - Manual save
- `Alt + R` - Rename tab
- `Alt + P` - Toggle preview
- `Alt + N` - Create new tab
- `Alt + W` - Close current tab
- `Alt + F` - Search/find
- `Ctrl + +/-` - Zoom in/out
- `Alt + T` - Create new TypeScript tab
- `Alt + M` - Create new Markdown tab

**Sidebar Tools:**

**Outline**
- Dynamic table of contents with clickable navigation
- Auto-generated from document structure

**Markdown Reference Sheet**
- Click any item to copy its markdown format to clipboard
- 100% GitHub-flavored Markdown compatibility
- Comprehensive formatting examples
- Tables, code blocks, badges, and more

**File Explorer**
- Browse and select files from your file system
- Open and edit files directly in the editor

**README Generator**
- Pre-built sections for quick copying
- Table of contents generation
- Badge collections
- Speed up README creation workflow

**README Builder**
- Collection of professional templates
- Real-world README examples
- Customizable starting points
- Best practice methodologies

**Resources:**
- [Video Demo](https://youtu.be/nU5OB_oCrL0)
- [MD Reference](https://raw.githubusercontent.com/8an3/dev-notes/main/md/md-reference.jpg?raw=true)
- [MD Guide](https://raw.githubusercontent.com/8an3/dev-notes/main/md/mdGuide.JPG?raw=true)
- [Outline Example](https://raw.githubusercontent.com/8an3/dev-notes/main/md/md-outline.jpg?raw=true)
- [Sidebar Overview](https://raw.githubusercontent.com/8an3/dev-notes/main/md/md-sidebar.jpg?raw=true)
- [Full README Guide](https://raw.githubusercontent.com/8an3/dev-notes/main/md/mdGuide.jpg?raw=true)

**README Templates:**
- [Awesome Template](https://raw.githubusercontent.com/8an3/dev-notes/main/md/awesome-readme-template.md?raw=true)
- [Fresh Template](https://raw.githubusercontent.com/8an3/dev-notes/main/md/fresh-template.md?raw=true)
- [Markdownify Template](https://raw.githubusercontent.com/8an3/dev-notes/main/md/markdownify.md?raw=true)

</details>

### Convert MD File To Safe Inline String

Convert markdown file content into JSON-safe inline strings by escaping special characters and replacing line breaks with `\n`.


**Access Options:**
- Right-click on MD file in explorer
- Command palette with active editor open
- BE Quick Pick menu (status bar)
- Programmatically via file URL argument

**Use Cases:**
- Embedding markdown in configuration files
- API payloads requiring escaped content
- Template string generation
- Safe string serialization

**BE Quick Pick Access:** Select `Convert MD File To Safe Inline String` from the BE Quick Pick menu





---

[🡄 Return](https://github.com/8an3/DevStack)