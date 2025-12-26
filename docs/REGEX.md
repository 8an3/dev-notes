# VS Code Find & Replace Regex Reference

## Multi-Cursor Patterns

### Every Second Line
**Find:** `^(.*)$\n.*$`
**Replace:** Leave empty or use `$1`
**Action:** Alt+Enter to select all matches
**Use:** Place cursors on alternating lines

### Every Third Line
**Find:** `^(.*)$\n.*$\n.*$`
**Action:** Alt+Enter
**Use:** Select every 3rd line

### Start/End of Every Line
**Find:** `^` (start) or `$` (end)
**Action:** Alt+Enter
**Use:** Place cursor at beginning/end of all lines

---

## Text Transformation

### Add Quotes Around Words
**Find:** `(\w+)`
**Replace:** `"$1"`
**Use:** Wrap all words in quotes

### Swap First and Last Name
**Find:** `(\w+)\s+(\w+)`
**Replace:** `$2, $1`
**Use:** Convert "John Doe" to "Doe, John"

### Add Line Numbers
**Find:** `^`
**Replace:** `$1. ` (use with capture groups in context)
**Use:** Number all lines

### Remove Duplicate Lines
**Find:** `^(.*)$\n\1$`
**Replace:** `$1`
**Use:** Remove consecutive duplicate lines

### Convert Snake_Case to camelCase
**Find:** `_(\w)`
**Replace:** `${1:/upcase}`
**Use:** Convert `user_name` to `userName`

### Convert camelCase to snake_case
**Find:** `([a-z])([A-Z])`
**Replace:** `$1_${2:/downcase}`
**Use:** Convert `userName` to `user_name`

---

## Code Formatting

### Add Semicolons to End of Lines
**Find:** `([^;])$`
**Replace:** `$1;`
**Use:** Add missing semicolons

### Remove Trailing Whitespace
**Find:** `\s+$`
**Replace:** (empty)
**Use:** Clean up line endings

### Convert Single Quotes to Double Quotes
**Find:** `'([^']*)'`
**Replace:** `"$1"`
**Use:** Change quote style

### Remove Empty Lines
**Find:** `^\s*$\n`
**Replace:** (empty)
**Use:** Collapse blank lines

### Remove Multiple Empty Lines
**Find:** `\n\n+`
**Replace:** `\n\n`
**Use:** Keep only one blank line between content

### Indent All Lines
**Find:** `^`
**Replace:** `    ` (4 spaces or `\t` for tab)
**Use:** Add indentation

### Convert Tabs to Spaces
**Find:** `\t`
**Replace:** `    ` (4 spaces)
**Use:** Standardize indentation

---

## Array/List Manipulation

### Array Items to Separate Lines
**Find:** `,\s*`
**Replace:** `,\n`
**Use:** Format arrays vertically

### Lines to Array Items
**Find:** `^(.*)$`
**Replace:** `"$1",`
**Use:** Convert list to array syntax

### CSV to JSON Array
**Find:** `^(.*),(.*)$`
**Replace:** `{"col1": "$1", "col2": "$2"},`
**Use:** Quick CSV to JSON conversion

### Remove Last Comma in Lists
**Find:** `,(\s*[}\]]))`
**Replace:** `$1`
**Use:** Clean up trailing commas

---

## HTML/XML

### Add Class to HTML Tags
**Find:** `<div>`
**Replace:** `<div class="container">`
**Use:** Bulk add attributes

### Extract Text from HTML Tags
**Find:** `<[^>]+>([^<]+)</[^>]+>`
**Replace:** `$1`
**Use:** Strip HTML tags, keep content

### Convert HTML to Self-Closing Tags
**Find:** `<(\w+)([^>]*)></\1>`
**Replace:** `<$1$2 />`
**Use:** Shorten empty tags

### Wrap Lines in HTML Tags
**Find:** `^(.+)$`
**Replace:** `<p>$1</p>`
**Use:** Wrap each line in tags

---

## Data Extraction

### Extract Email Addresses
**Find:** `\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b`
**Action:** Alt+Enter to select all
**Use:** Find all emails in document

### Extract URLs
**Find:** `https?://[^\s]+`
**Action:** Alt+Enter
**Use:** Select all URLs

### Extract Numbers
**Find:** `\d+`
**Action:** Alt+Enter
**Use:** Select all numeric values

### Extract Hex Colors
**Find:** `#[0-9A-Fa-f]{6}\b`
**Action:** Alt+Enter
**Use:** Find all hex color codes

### Extract IP Addresses
**Find:** `\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b`
**Action:** Alt+Enter
**Use:** Find all IP addresses

---

## Log File Processing

### Extract Timestamps
**Find:** `\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}`
**Action:** Alt+Enter
**Use:** Select all timestamps

### Filter Lines with ERROR
**Find:** `^(?!.*ERROR).*$\n`
**Replace:** (empty)
**Use:** Keep only error lines

### Remove Log Timestamps
**Find:** `^\[\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}\]\s*`
**Replace:** (empty)
**Use:** Clean log format

### Extract Stack Traces
**Find:** `^\s+at .*$`
**Action:** Alt+Enter
**Use:** Select stack trace lines

---

## String Manipulation

### Remove All Spaces
**Find:** `\s+`
**Replace:** (empty)
**Use:** Compact text

### Collapse Multiple Spaces
**Find:** ` {2,}`
**Replace:** ` `
**Use:** Normalize spacing

### Title Case (First Letter)
**Find:** `\b(\w)`
**Replace:** `${1:/upcase}`
**Use:** Capitalize first letters

### Add Prefix to Lines
**Find:** `^`
**Replace:** `TODO: `
**Use:** Add prefix to all lines

### Add Suffix to Lines
**Find:** `$`
**Replace:** `;`
**Use:** Add suffix to all lines

### Reverse Order of Words
**Find:** `(\w+)\s+(\w+)\s+(\w+)`
**Replace:** `$3 $2 $1`
**Use:** Reverse word order

---

## JSON/JavaScript

### Convert Object Properties to Quoted
**Find:** `(\w+):`
**Replace:** `"$1":`
**Use:** Add quotes to object keys

### Remove Quotes from Object Keys
**Find:** `"(\w+)":`
**Replace:** `$1:`
**Use:** Remove quotes from keys

### Format Console Logs
**Find:** `console\.log\((.+)\)`
**Replace:** `console.log('DEBUG:', $1)`
**Use:** Add debug prefix

### Convert to Template Literals
**Find:** `'([^']*)' \+ (\w+) \+ '([^']*)\'`
**Replace:** `` `$1${$2}$3` ``
**Use:** Modernize string concatenation

---

## Markdown/Documentation

### Convert URLs to Markdown Links
**Find:** `(https?://[^\s]+)`
**Replace:** `[$1]($1)`
**Use:** Auto-link URLs

### Add Markdown List Bullets
**Find:** `^(.+)$`
**Replace:** `- $1`
**Use:** Convert lines to list

### Convert Headers to Title Case
**Find:** `^(#+)\s+(.+)$`
**Replace:** Use with manual editing
**Use:** Format headers

### Extract Markdown Links
**Find:** `\[([^\]]+)\]\(([^\)]+)\)`
**Replace:** `$2`
**Use:** Get just URLs from links

---

## SQL/Database

### Add Quotes to Column Values
**Find:** `(\w+)`
**Replace:** `'$1'`
**Use:** Quote string values

### Convert INSERT Values to Rows
**Find:** `\),\s*\(`
**Replace:** `),\n(`
**Use:** Format INSERT statements

### Extract Column Names from CREATE
**Find:** `^\s*(\w+)\s+.*,$`
**Replace:** `$1,`
**Use:** Extract column names

---

## Advanced Patterns

### Match Nested Parentheses (Simple)
**Find:** `\([^()]*\)`
**Use:** Find simple nested structures

### Remove Comments (C-style)
**Find:** `//.*$`
**Replace:** (empty)
**Use:** Strip single-line comments

### Remove Block Comments
**Find:** `/\*[\s\S]*?\*/`
**Replace:** (empty)
**Use:** Strip multi-line comments

### Extract Function Names
**Find:** `function\s+(\w+)\s*\(`
**Replace:** `$1`
**Use:** List all function names

### Match Balanced Brackets
**Find:** `\{[^{}]*\}`
**Use:** Find simple object literals

---

## VS Code Specific Capture Groups

### Case Modifiers
- `${1:/upcase}` - Convert to UPPERCASE
- `${1:/downcase}` - Convert to lowercase
- `${1:/capitalize}` - Capitalize first letter
- `${1:/pascalcase}` - Convert to PascalCase
- `${1:/camelcase}` - Convert to camelCase

### Conditional Replacements
**Find:** `(foo)|(bar)`
**Replace:** `${1:+FOO}${2:+BAR}`
**Use:** Conditional text based on capture

---

## Tips

1. **Enable Regex**: Click the `.*` icon in Find dialog
2. **Alt+Enter**: Select all matches (creates multi-cursor)
3. **Capture Groups**: Use `()` to capture, `$1`, `$2` to reference
4. **Test First**: Use Find before Replace to verify matches
5. **Case Sensitive**: Toggle with `Aa` icon
6. **Whole Word**: Toggle with `Ab|` icon
7. **Preserve Case**: VS Code can preserve case in replacements
8. **Multi-line Mode**: Use `[\s\S]` instead of `.` for multi-line matches

---

## Common Regex Symbols

- `^` - Start of line
- `$` - End of line
- `.` - Any character (except newline)
- `*` - 0 or more
- `+` - 1 or more
- `?` - 0 or 1 (optional)
- `\d` - Digit
- `\w` - Word character
- `\s` - Whitespace
- `[abc]` - Character class
- `(...)` - Capture group
- `(?:...)` - Non-capturing group
- `|` - OR operator
- `\b` - Word boundary



---

[🡄 Return](https://github.com/8an3/DevStack)