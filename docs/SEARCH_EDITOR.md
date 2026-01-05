
### Search Editor

A powerful, VSCode-native search and replace interface with advanced filtering, real-time results, and inline editing capabilities.

## Features

### 🔍 Advanced Search Options
- **Regex Support**: Toggle regex pattern matching with the `.*` button
- **Case Sensitivity**: Control case-sensitive matching with the `Aa` button
- **Whole Word Match**: Match complete words only with the `Ab` button
- **Fuzzy Search**: Enable approximate matching with the `≈` button

### 🎯 Search Scopes
Click the scope button to cycle through:
- 📁 **Workspace**: Search entire workspace
- 📄 **Open Files**: Search only currently open editors
- 📝 **Current File**: Search active file only
- 🔀 **Git Changes**: Search only modified files in git

### 📂 File Filtering
- **Include Patterns**: Narrow search to specific file types
  - Examples: `**/*.ts`, `src/**/*`, `**/*.{js,jsx}`
- **Exclude Patterns**: Filter out unwanted files
  - Examples: `node_modules/**`, `**/*.test.ts`, `dist/**`
- **Use Settings**: Toggle to use your VSCode exclude settings (⚙️)
- **Save Patterns**: Save up to 10 frequently used patterns with 💾

### ⚡ Real-Time Results
- Results stream in as they're found (no waiting for completion)
- Live result counter shows matches across files
- Animated loading indicator during search

### ✏️ Inline Editing
- **Edit on Hover**: Click any result line to edit it inline
- **Individual Replace**: Replace button appears on hover for each match
- **Batch Replace**: Replace all matches at once
- **Save All**: `Ctrl+Shift+S` saves all open editors after changes

### ⌨️ Keyboard Shortcuts
- `Enter` in search box: Start search
- `Alt+J`: Navigate to previous result
- `Alt+L`: Navigate to next result
- `Alt+K`: Replace current result
- `Ctrl+Shift+S`: Save all changes
- `Ctrl+Click` on result: Multi-select results

### 📊 Search History
- Access previous searches via the **History** button
- Shows timestamp and result count for each search
- Click any history item to restore that search
- Clear history when needed

## Usage

### Basic Search
1. Type your search query in the search input
2. Results appear automatically as you type (300ms debounce)
3. Click any result to jump to that location in the file

### Search and Replace
1. Click the `›` chevron next to the search input to reveal replace field
2. Enter replacement text
3. Click **Replace All** or use inline replace buttons

### File Filtering
1. Click 📂 button to enable include patterns
2. Enter glob pattern (e.g., `**/*.ts` for TypeScript files only)
3. Click 💾 to save frequently used patterns
4. Click 🚫 button to enable exclude patterns
5. Use same glob syntax to exclude files/folders

### Pattern Examples
```
Include patterns:
  **/*.ts              - All TypeScript files
  src/**/*             - All files in src directory
  **/*.{js,jsx,ts,tsx} - All JS/TS files
  components/**/*.tsx  - TSX files in components

Exclude patterns:
  node_modules/**      - Exclude node_modules
  **/*.test.ts         - Exclude test files
  dist/**              - Exclude build output
  **/*.min.js          - Exclude minified files
```

## Performance

- **File Discovery**: Uses ripgrep via VS Code's `findFiles()` API
- **Text Search**: Attempts to use internal ripgrep API, falls back to optimized manual search
- **Streaming Results**: Results displayed in batches (every 10 files or 50 results)
- **Binary Detection**: Automatically skips binary files
- **Debounced Input**: 300ms delay prevents excessive searches while typing


## Future Enhancements

- [ ] Search within selection
- [ ] Multi-root workspace support
- [ ] Export results to file
- [ ] Regular expression builder/tester
- [ ] Search result folding by file
- [ ] Syntax highlighting in results
- [ ] Replace preview before applying

