## Dev Context Ngin

Gives you the resolved state of the current VSCode environment — editor settings, theme, sidebar positions, feature flags, secrets — everything that's already been read and resolved at startup. No need to call `vscode.workspace.getConfiguration()` yourself for the common stuff, it's already there.

On top of that you get two open objects — `store` and `workspace` — to put whatever you need in them. No restrictions on what goes in, no restrictions on how many keys. `store` persists globally, `workspace` is scoped to the current workspace.

### Setup

```typescript
const ngin = api.DevContextNgin.getInstance()
await ngin.init(context, workspaceRoot, userEmail, projectId)
```

### Usage

```typescript
ngin.getState()
// Returns full resolved state including editor config, theme, secrets, your objects

ngin.setState({ minimap: false })
// Partial update, persists and notifies subscribers

ngin.setStore('myKey', { whatever: true })
ngin.getStore('myKey')
// Global persistent key/value, survives sessions

ngin.setWorkspace('myKey', { whatever: true })
ngin.getWorkspace('myKey')
// Workspace scoped key/value, survives sessions

ngin.subscribe((state) => {
  // fires on any state change
})

ngin.getProjectId()
```

---


Every terminal interaction type the extension uses, exposed through a clean API. Under the hood it's the same execution engine — sequential chains, concurrent execution, conditional chains, dev server detection, debian/WSL support, all of it.

You never touch the item config shape directly. That's handled internally. You just call the method you need.

### Setup

```typescript
const terminal = api.DevTerminalNgin.getInstance()
terminal.init(terminalManager, ctx)
```

### Usage

```typescript
terminal.run('npm install')
terminal.runDebian('apt-get install curl')
terminal.runCmd('workbench.action.reloadWindow')

terminal.runInDir('npm install', '/path/to/dir')

terminal.openFile('/path/to/file.ts')
terminal.openFileAtLine('/path/to/file.ts', 42)
terminal.openUrl('https://example.com')

terminal.copyToClipboard('some value')
terminal.runNpmScript('dev')
terminal.runTask('build')

terminal.chain(['labelA', 'labelB', 'labelC'])
// sequential execution

terminal.concurrent(['labelA', 'labelB', 'labelC'])
// fires all at once

terminal.cmdChain(['editor.action.formatDocument', 'workbench.action.files.save'])
// vscode commands only, sequential

terminal.search('TODO', 'devShop', 'src/**', 'node_modules/**')

terminal.apiCall('https://api.example.com/data', 'POST', { 'Authorization': 'Bearer token' }, { key: 'value' })

terminal.toggleSetting('editor.minimap.enabled')
terminal.toggleSetting('editor.wordWrap', 'label', ['on', 'off', 'wordWrapColumn'])

terminal.wait('optional message')

await terminal.secret('GITHUB_TOKEN')
// checks vscode secrets first, falls back to .env automatically

await terminal.secret('GITHUB_TOKEN', 'your-token-value')
// stores to vscode secrets
```

---





The tools are here. What you do with them is on you.