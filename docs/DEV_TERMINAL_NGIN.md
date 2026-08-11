

## Dev Terminal Ngin

> OMG, crisis averted. I created a workaround / hack for the terminal ngin so that I could progmatically use it anywhere throughout the codebase. Luckily, I thought creating the classes was easy enough so that an ai could take care of this without issue. Never underestimate the stupidity that is ai, despite having the term intelligence within its own name, it is anything but that. 
>
> The first issue, and to be honest it's almsot a good thing the ai fucked up as bad as it did. I had given it the terminal hack I used... hundreds of times, and I quickly saw the code it had used for it, and was like that ain't right. The class that the ai provided to me, it was like one of those pictures that... the longer you stare at it, it just gets worse, lol.
>
> The class was SO bad, not only was I cratching my head and was like what the... but it actually made me question myself and if I EVEN knew how it worked, by the time I got to cmd and concurrent. The life choices I was questioning at that point... staring at them... this won't work. 
>
> Now personally, I use AI to generate ideas by bouncing ideas off of them, all the time. It's first reason was... well, I guesss were dropping those features... and it just continued doing what it was doing. I guess it just... viewed tackling this issue SO hard, it just gave up before it even started. I don't think I've seen that before.
>
> Since I hacked the terminal before, why couldn't I do it again. The end result was anything but hacky, as it turned out... really clean, so clean these two are becoming new commands that remove the need for the config entirely now. As before now, whenever you triggered a chain or concurrent, it would take the string of ids you pass it, along with grabbing the entire config before it started executing each config item. There was no way around this, till now. The use cases are there for it, instead of relying on items found in your config, passing it seither chain or conurrent of items you would like to execute. This takes care of chain and concurrent use cases that are comprised of weird one off command sequences, and donn't have to create config objects for them anymore.
>
> The command objects in either chain or concurrent still need to be the same format as what is needed for the config, as everything single object goes through a function ensuring that you cannot fuck up the required object format that is needed.
>
> OR in terms of how YOU AS A DEV will interact with it is quite simple as the majority of them just require a single prop, even the two new chain and concurrent item types that were made just for you.


## Dev Terminal Ngin

Every terminal interaction type the extension uses, exposed through a clean API. Under the hood it's the same execution engine — sequential chains, concurrent execution, dev server detection, debian/WSL support, all of it.

### Setup

```typescript
const terminal = api.DevTerminalNgin.getInstance()
terminal.init(ctx)
```

### Usage

```typescript
terminal.run('npm install')
terminal.runDebian('apt-get install curl')
terminal.runCmd('workbench.action.reloadWindow')

terminal.runInDir('npm install', [{ xPath: '/path/to/dir' }])

terminal.openFile('/path/to/file.ts')
terminal.openFileAtLine('/path/to/file.ts', 42)
terminal.openUrl('https://example.com')

terminal.copyToClipboard('some value')
terminal.runNpmScript('dev')
terminal.runTask('build')

terminal.cmdChain('editor.action.formatDocument,workbench.action.files.save')
// vscode commands only, sequential, comma separated string

terminal.wait('optional message')

terminal.search('TODO', [{ include: 'src/**', exclude: 'node_modules/**' }])

terminal.apiCall('https://api.example.com/data', [{ method: 'POST', headers: { 'Authorization': 'Bearer token' }, body: { key: 'value' } }])

terminal.toggleSetting('editor.minimap.enabled')
```

### chain and concurrent

Both accept an array of config objects using the same format as the regular config items:

```typescript
terminal.chain([
  { label: 'save files', path: 'workbench.action.files.saveFiles', type: 'command' },
  { label: 'run build', path: 'npm run build', type: 'powershellCommand' },
  { label: 'open output', path: '/path/to/output.js', type: 'file' },
])

terminal.concurrent([
  { label: 'dev server', path: 'npm run dev', type: 'powershellCommand' },
  { label: 'worker', path: 'npm run worker', type: 'powershellCommand' },
])
// pass { ngin: 'bleedingEdge' } as second arg to use bun concurrent runner
terminal.concurrent([...], { ngin: 'bleedingEdge' })
```

### secrets

```typescript
await terminal.secret('GITHUB_TOKEN')
// checks vscode secrets first, falls back to .env automatically

await terminal.secret('GITHUB_TOKEN', 'your-token-value')
// stores to vscode secrets
```

---

The tools are here. What you do with them is on you.
