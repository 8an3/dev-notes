# DevShop

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Overview

A growing number of ngins pulled out of the extension and exposed for your use. You get the same implementation that powers the extension itself — not a watered down version, not a wrapper around a wrapper. The actual thing.

1. Terminal Ngin
2. Context Ngin
3. Github CLI Ngin
4. Workspace Context Ngin
5. NEW: Context Ngin Viewer ( see section for details )
6. NEW: Utils Ngin / Class ( see section for details )
7. NEW: BIFROST Ngin ( see section for details )

<!-- #region -->

> [!NOTE]
>
> As promised, here are the tools that a lot of people seem to have troubles or issues with in one form or another. Going over them for the remainder of this talking point, I'm sure I'm going to sound llike a pompoous ass hat, but theres no getting around that.
>
> Not only do I wish I had something like this to access, as it would have saved me from hours of headaches and what felt like the equivlant of my hand in waffle griddle while somone held it down. Because when it comes to features like these, if there are even docs out there... they suck, lets be real. I can't sit here and say microsofts strong point is their documentation and everyone should model themselves after them with the exemplary standard they set forth. lol, not to mention vscodes UNDOCUMENTED quirks, because those are always fun running into at which point your developing blindy. It's like poking a bear with blindfold on, but the bear will random swat back at you.
>
> If you have ever used anything I've built, I truly do hate setting limitations in any and all forms. Because of that, I've literally coded it in such a way that, it's as if its in your own code base. You all the benefits, with none of the negatives. You didn't have to figure it out, you don't have to maintain it, you don't have to think about updates, or adding features and all the testing that comes along with it.
>
> Essentially handing you the keys to the best examples that can be found on the marketplace in their given categories. I dont even know if any other dev has done something like this through a vscode extension.
>
> SO NOT ONLY, do you get prebuilt, pretested, and in some cases I intentiontlly hammered them and brought hell down on them essentially to get them to break and fix them if they do.
>
> That reminds me, jotting this down so I don't forget to actually add this to the workshop. The to do, reminders and notes back end implementation using github as a single source of truth. This is one feature... that I have... not held back in any way LOL, butttt it IS in a state that it never enters any thought process of what needs to be done, or looked out for. As you can, perfectly too keep that in mind, open to do lists, reminders and notes in one workspace. Open a new workspace, leaving the previous in a DIRTY state, because who needs the save feature. To THEN open them AGAIN, in the new workspace... because I don't want to tab over to use them in the previous window... do some edits, save... then open another workspace, while the first still have unsaved data. Close that workspace, to open another and again opening even more items in this workspace... editing them... leaving those unsaved too. To go back to the first workspace... see that I didn't save... save it finally and on and on the I carry out torturing a system a lot of people would be absolutely paranoid if this were happening. That was an EASY testing session. There have been times, I've done that times 3 in additiion to trying to open as many workspaces as I possibly can... just to try to break it. Now that I've thought about it I'll make sure that is also available shortly, because coding these features, were surprisngly quick. Everything is already built, I guess. 
>
> Oh, I failed to mention... My confidence being so high with that system, and going about it treating it like dirt with not a care in the world of whether the push to github was successful or not. Its use of github as a source of truth... well its not JUST a source of truth, as this feature doesn't even have a local copy to back up off of if something does go wrong... but it doesn't meanwhile, even lately, seeing devs talk about such features as if they're going to break as they talk about them and not interacting with them and going so far as creating recovery wizards as standard default functionality. If you have a friend like this... tell them to keep an eye out for it so they finally not stress about it and sigh in releif that, its taken care of.
>
> Not only getting the, now 4 features, but I have for a while now been coding the extension in a composable and as modular of a design as far as I can take it. Last I checked, this extension was exposing 2700+-3000+ functions. Now, a lot of those are due to the components library but even so, they are all in your grasp to do... whatever it is you want to do. As I abolutely hate whe people put walls, or guards up or anything in any resstrictive manner and impede you with what you want to do. Each feature, was originally built with that in mind and trying to bring that surface area to non-existant as much as I possibly could. While coding the exposure of these features, I can say... there is not a single restriction put in place. If that makes you uneasy, thats fine everyone can have their own opinion on any subject they want, with saying that... were devs, we will break shit, but the best thing about being a dev is after breaking it... we can fix it. 
>
> It's probably that mentality that helps me deal in areas, like not having the proper documentation in order to get something done and working. As I have no problem sitting there, coding away, prodding at it and trying to find a solution and make it work. It does not couple well with the fact that, I will not stop till it works the way I need / want it to, and even take a feature that I've spent days on... and just delete it to start over in order to get it where it needs to be.
>
> The current feature set you can access:
> - Context Ngin - every ui element is tracked which you have access to and it was coded so that you have full read / write access to do as you wish and even providing a couple of objects that... are 100% yours to add data in whatever amount you need to it
> - Workspace Context Ngin - Literally, the exact implementation that I use in this extension, yours free to do as you wish. This one being the only feature so far that I couldn't give straight access to due to the way its coded into the extension. When I built it... I never forsaw this being a feature that would end up becoming a reality. With saying that, it is a 1-1 clone. Every single function is the same, how it discerns workspaces between one another, how it merges the configs before the user get its data to work with in whatever capacity that you want
> - Terminal Ngin - Not only giving you direct access, but over time I've built myself some cheats and hacks to use it in all manner of ways accross the wide surface of this extension. Rebuilt them so that... you literally cannot make a mistake with them. The originals were built with that in mind, the oringinals... just looked ugly more than anything, since these functions are pieces of code I never thought would ever get shared
>
> The terminal ngin, while imo just as powerful as the context ngin, does offerr a lot more without having to think of anything too much. As you now have:
> - file
> - fileAtLine
> - url 
> - command 
> - powershellCommand
> - debianCommand
> - snippet
> - chain
> - concurrent, and because you are directly accessing the terminal ngin, you also get all the new recent nice updates it just got. Auto port ngin, env variables, the complete rewrite of concurrent and all the other goodies
> - copyValue
> - cmdChain
> - settingsToggle
> - apiCall
> - label
> - search
> - layout
> - folder
> - npmScripts
> - tasks
> - md
> - conditionalChain
> - wait
>
> Yes, you have progmatic access to the layout, you can even build your own version of it if you wanted.
>
> Shortly, there will also be a ngin for gitub as well. I'm sure I'll think of more, but these features being... I believe and hope to be the most impactful that could have been chosen out of the toy chest of features out of this extension. As I did think a lot about which features to expose and why one over another. It just weirdly happens to be the fact that, these features a lot of devs to find challenging to the point, that they loose interest in continuing with it. And it just so happens to be the strongest parts of my code, as each of the three are so ahead of the other marketplace offerings to the point where they are in a class all on their own and each of them would be the sole focus of an extension all on their own, if it were any other dev that built them. 
> 
> In addition to the exposed tools, I will also be making a guide for anyone interested in reading it. The portion will entirely be disucssing vscode, how it was built, how its underlying code functions, going into how and why every single blog is wrong when they discuss any one thing in terms of vscodes performance, and how you can improve your vscode today. 
> 
> Every single user encounters performance issues when using this software, and while yes just deleting the installed extensions will give some of that performance back... even though they state, that itself is the issue... it is not. I will be keeping in a lot of the material that was written previously as it goes into optimizing the settings vscode has in order not only get that performance back, but ensures moving forward you do not run into those issues ever again. 
> 
> For example, recently as I was testing Loki AI limitless and in order to conduct te testing as quickly as I could and across as big as a focus group that I could get my hands on, I ended up installing, it was well over 20 different ai extensions. Yes, it rendered my vscode instance to a grinding halt that... I could not do a single thing because of how each of these extensions sets their defaults. BUT, after optimzing them I was able to run all the ones that actually worked... all running at the same time, in addition to this extension along with whatever else I had installed at the time. So there was A LOT happening in terms of processes and even then my instance ran perfectly. No hiccups, no weirdness, but if it weren't for optimizing the settings... No computer would be able to handle that. While the original information is up and can be viewed, I haven't yet even went over it yet. Despite that fact, just learning how vscode is actually built and how to optimize it, will go a long way in terms of developing extenions as you will know what could or should be done or in some cases, what shouldn't be implemented in your code.
 
<!-- #endregion -->


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Setup — Run In This Order


These three engines depend on each other. Initialize them in this exact order inside your extension's `activate` function:

```typescript
import * as vscode from 'vscode'

export async function activate(context: vscode.ExtensionContext) {
  const ext = vscode.extensions.getExtension('skyler.ocrmnav')
  const api = await ext.activate()

  const workspaceFolder = vscode.workspace.workspaceFolders?.[0]
  const workspaceRoot = workspaceFolder.uri.fsPath

  // 1. Workspace context first — resolves projectId and config layers
  const wsCtx = api.DevWorkspaceContextNgin.getInstance()
  await wsCtx.init(context, workspaceRoot)

  // 2. State manager second — needs projectId and workspaceRoot from step 1
  const devCtx = api.DevContextNgin.getInstance()
  await devCtx.init(context, workspaceRoot, userEmail, wsCtx.getProjectId())

  // 3. Terminal engine last — needs the fully resolved ctx object from the extension
  // ctx is the DevStackContext object provided by the extension at runtime
  const terminal = api.DevTerminalNgin.getInstance()
  terminal.init(ctx)

  // --- from here you have full access to all four engines ---

  // DevContextNgin — read or write resolved VSCode state
  const editorState = devCtx.getState()
  console.log(editorState.colorTheme)

  // DevContextNgin — store anything you need globally
  devCtx.setStore('myExtensionKey', { initialized: true, version: '1.0.0' })

  // DevTerminalNgin — run a terminal command
  await terminal.run('npm install')
}
```

Your `package.json` needs this or the extension may not be activated before yours:

```json
"extensionDependencies": ["skyler.ocrmnav"]
```

---


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Utils Ngin

> [!NOTE]
> ... I get the feeling this is going to receive lots of updates, I'll try my best to keep the docs as up to date as I can, but till they get updated I'll atleast put the props up so you know what is needed, since its obvious from their names as to what each returns:
> - setSettingsValue(key: string, value: any)
> - getAllVSCodeSettings
> - getVSCodeVers
> - getGBSettingsPath
> - getHistoryPath
> - getTmpPath
> - getDbPath
> - getHomePath
> - getUsersSettings
> - detectPackageManager ( the reason for the addition here is that, ctx's pkg mgr value might be stale because of when it is added to the context. The only use case this value would be be stale is if the user changes package managers in their session, as the next session the new pkg mgr will be correct in the value, but for the remainder of that session it will be stale. SO if you NEED the absolute 100% current value of what pkg manager is used than you could use this to call pkg mgr every single time, detect pkg mgr has also just got an update in terms that it now checks 7 different sources for what pkg manager is being, lol )
>   - checkPackageJson ( these are helper functions for detect pkg mgr, no point in actually using them individually )
>   - checkWorkspaceFiles
>   - checkVSCodeSettings
> - fileExists(filePath: string)
> - getAsgardConfig(projectPath: string = null)
> - getBifrostConfig(projectPath: string = null)
> - to name a few... Since I have made, so many different features, and now that I'm also exposing as much as I can functionality wise... This would be perfect for someone starting out with developing extensions and looking to get into it. As there is, OBVIOUSLY, nothing like this out there but even in terms of a resource of information, ya there are some good ones that talk sepcifically about things. But in order to get all the required knowledge, it just takes time within this stupid context. Why do you have to make it so hard for people to access information. I am really jelouse right now because this would have been perfect to start off with. Helper functions for getting files, and json files using vscodes api instead of fs, or grab clipbaord, paste clipboard, paths to all sorts of files and configraution settings files, the setting and gettting of not just applications settings, but also the current landscapes state, A CONTEXT STATE MANAGMEENT SYSTEM JUST ALREADY PLUGGED AND READY TO GO, pffft that last one... I wish, LOL. Anyways between the 2500+ extensions functions PLUS vscodes... i think 900-1100 AND now all the functionality to help kick off any style of extension. I'm not lying when I say that either, this would have been nice. The amount of searching alone... for the stupidiest of things... Oh and I totally forgot, since I coded it a while back. But this extension already contains, better docs of microsfts apis, than what microsoft currently has. Which reminds me, I need to finish that guide.

>
> None of them features the use of the OS module form node. Any time where there amy be a different enviroment in question... say the users global settings file. This will be in a different location depending on the OS your using, obviously. This function not only checks what your current version of vscode your using but also your operating system and adjusts accordingly.

> Again didn't go too far out of my way in order to make this happen, as I cleaning the codebase and consolidating all the helper functions half way through, I thought, why not? It won't hurt, if anything a lot of you will probably find it useful as a lot of the functions found within the tools, you do have to use when building extensions. 
>
> As I was doing the above coding chore, I found a feature that I had totally forgot about. It was activated and working, and in working order. The extension is just that big, and I had not moved the feature from the bleeding edge menu I have, which anyone can access it as long as you set the config to true.
>
> Anyways, the lost in translation feature is a complete context viewer that allows you to see every value currently stored within it. So, if your creating something and wish you could just fucking see what value is being stored exactly... now you can. It's a quick pick thats accessible through the utilities, since there is no command for it, but hooked the two classes up so that it can be called when ever you need it.
>
> As for an itemized list of utilities that can be found within the class:

### run proxy

There are three if statements, for various reasons but it ensures that no matter what you throw into the command / cli, it will run through the terminal ngin

```jsx
await runProxy(`${pkgMGR} i @a5gard/baldr`, this.ctx, workspaceRoot)
```

Which reminds me... I'll add the pkg.mgr to the utilties too.

### vscCmdArray 

For better code maintainability, along with house cleaning and whatever, instead of listing a vscode cmd one after another with the entire vscode function call. This lets you put them into an array that gets fired off one by one.

```jsx
const syncCmds = [{ cmd: "workbench.action.files.saveFiles" }, { cmd: `ocrmnavigator.asgard.git.config.check` }, { cmd: "ocrmnavigator.asgard.git.repo.check" }, { cmd: "ocrmnavigator.asgard.git.sync" }]

await um.vscCmdArray(syncCmds)
```

> Haha, it's going to take me a lot longer to write the docs than it was the classes. 

### xeqTermArray 

Same idea as the previous, just with terminal commands.

```jsx
const syncCmds = [{ cmd: "git add -A -- ." }, { cmd: `git commit -m "Auto-sync: ${new Date()}"` }, { cmd: "git pull --tags" }, { cmd: "git push" }]

await um.xeqTermArray(syncCmds, ctx)
```

### getNonce 

```jsx
const nonce = um.getNonce();
```

### asyncSafeExecute 

There are two versions to this, one with async and one without. It's essentially just a try catch wrapper, but coded in such a way that it doesn't halt the entire function, it just fails, logs the error message and continues on with the rest of the function.

```jsx
let brokkrProvider: BrokkrMenuProvider | null = null
await um.asyncSafeExecute("BrokkrMenuProvider", async () => {
  brokkrProvider = new BrokkrMenuProvider(context, ctx)
  vscode.window.registerTreeDataProvider("brokkr.viewer.menu", brokkrProvider)
})
```

### safeExecute 

```jsx
um.safeExecute("ServerProvider", () => ServerProvider(ctx))
```

### getJsonFile 

```jsx
const packageJson = await this.um.getJsonFile('/path/to/project', 'package.json')
```

### writeJsonFile 

```jsx
await this.um.writeJsonFile( this.um.ctx.workspaceRoot,  'config.asgard',  { theme: 'dark', fontSize: 14 } )
```

### getFile 

```jsx
const readme = await this.um.getFile(this.um.ctx.workspaceRoot, 'README.md')
```

### writeFile 

```jsx
await this.um.writeFile('.gitignore', this.um.ctx.workspaceRoot, 'node_modules/\ndist/\n.env')
```

### ensureDirExists 

```jsx
this.um.ensureDirExists(path.join(this.um.ctx.workspaceRoot, 'src/components'))
```

### copyWSyntaxHL 

This utility copies the currently selected text into you clipboard, but with syntax highlighting.

```jsx
await this.um.copyWSyntaxHL()
```

### grabClipboard 

Just grabs what ever value is currently in the clipboard to be used how you want. If you were wondering how I'm able to create a ux so much faster than the average... this is the secret.

```jsx
const clipboardText = await this.um.grabClipboard()
```

### copyToClipboard 

```jsx
await um.copyToClipboard(template);
```

### setGetATAT 

```jsx
// With the token functions being multifunctional, meaning that the same function serves to GET and also SET their relevant token, as all of them have been made in the same fashion. The first example gets the token, first by checking the context secrets where they are securely stored within the vscode sandbox. If there is no value there, it then checks the .env file for GITHUB_TOKEN, MS_TOKEN and OVSX_TOKEN respectively. 
// GETS TOKEN
 const atat = await  um.setGetATAT(ctx)

// Whenever you are trying to save one of these values, obviously calling on the right one, you pass the token in as the second value and it will store it in the context secrets value, within vscodes secure storage.
// SETS TOKEN IN STORAGE
 const atat = await  um.setGetATAT(ctx, patToken)

```

### setGetMSToken 

```jsx
const msToken = await  um.setGetMSToken(ctx)
const msToken = await  um.setGetMSToken(ctx, patToken)
```


### setGetOVSXToken 

```jsx
const ovsxToken = await  um.setGetOVSXToken(ctx)
const ovsxToken = await  um.setGetOVSXToken(ctx, patToken)
```


### repoExists 

```jsx
await um.repoExists(owner, repo, patToken)
```


### SetSettingsValue 
alows the setting of any desired setting with whatever value you need.
```jsx
const result1 = await this.um.SetSettingsValue('editor.minimap.enabled', false)
const result2 = await this.um.SetSettingsValue('files.autoSave', 'afterDelay')
const result3 = await this.um.SetSettingsValue('editor.fontSize', '16')
```


### getAllVSCodeSettings 

Gets ALL of the currently available settings that are available in your own workspace.

```jsx
const allSettings = await this.um.getAllVSCodeSettings()
// Filter settings by category
const editorSettings = allSettings.filter(s => s.category === 'editor')
console.log('Editor settings:', editorSettings)
    
// Find specific setting
const fontSizeSetting = allSettings.find(s => s.key === 'editor.fontSize')
if (fontSizeSetting) {
  console.log('Font size default:', fontSizeSetting.default)
  console.log('Font size type:', fontSizeSetting.type)
}
```


### getReadmeTemplate 

Needing the value of the prefered template and ctx, it returns the template for it to be written to a file as you can see here, I'll also provide those lists.



```jsx
this.um.writeFile("README.md", workspaceRoot, `${this.um.getReadmeTemplate(a.readmeTemplate, this.ctx)}`)
```

### getLicense 

- boost
- mit
- apache
- mozilla
- LGPLv3
- GPLv3
- AGPLv3
- unlicense

```jsx
this.um.writeFile("LICENSE.md", workspaceRoot, `${this.um.getLicense(asgardData.license, asgardData)}`)

```

### getChangelog 

```jsx
this.um.writeFile("CHANGELOG.md", workspaceRoot, `${this.um.getChangelog(asgardData.changelog, asgardData)}`)

```

### readmeArray 

- none
- awesome
- fresh
- markdownify
- ai
- go
- redis
- javascript
- kotlin
- litellm
- mlops
- ollama
- postgres
- python-v0.5.87
- python
- readmeai
- rust-c
- sqlmesh
- typescript

### changelogArray 

- none
- keepachangelog
- github-release-notes
- react-style
- vue-style
- nextjs-style


### getLatestVsixPath 

```jsx
const vsixPath = await getLatestVsixPath()
const pat = await getOrRequestToken(ctx.context)
if (pat) {
  return await ctx.terminalManager.executeTerminal(`vsce publish --packagePath ${vsixPath} --pat ${pat}`)
} else {
  const item = createNavigatorItem({
    label: "label",
    path: "vsce publish --packagePath " + vsixPath + " --pat ${MS_TOKEN}",
    type: "powershellCommand",
  })
  await ctx.terminalManager.executeMaster(item, ctx)
}
```


### getUserEmail 

Simple enough, just gets the email of whatever account is currently logged into vscode.

```jsx
  const email = await um.getUserEmail();
```


### pascalCase 

```jsx
// Convert kebab-case to PascalCase
const componentName = this.um.pascalCase(dashCase)
```


### getDelayForItemType 

```jsx
/**
 *     const delays: Record<string, number> = {
          powershellCommand: 1000,
          debianCMD: 1000,
          command: 800,
          default: 500,
       }
*/
 const delay = this.um.getDelayForItemType(cmd.type)
      
// Execute command
console.log(`Executing: ${cmd.cmd} (waiting ${delay}ms)`)
      
// Wait appropriate time
await this.um.delay(delay)
```


### delay 

```jsx
 const delay = this.um.getDelayForItemType(cmd.type)
      
// Execute command
console.log(`Executing: ${cmd.cmd} (waiting ${delay}ms)`)
      
// Wait appropriate time
await this.um.delay(delay)
```






## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Context Ngin Viewer

### Context Interface 

```jsx
export interface DevStackContext {
  // CORE / MASTER
  // #region ==================================
  context: vscode.ExtensionContext
  globalState: vscode.Memento
  projectId: string
  terminalManager: TerminalManager
  webviewManager: WebviewManager
  appliedAt?: Date
  transitionInProgress: boolean
  lastError?: string
  customData?: Record<string, any>
  navigatorProvider: NavigatorProvider
  authService: AuthService
  contextMenuManager: ContextMenuManager
  onCloseHooks?: any[]
  gitOnCloseHooks?: any[]
  isPremium?: boolean
  onboarding?: boolean
  // ICONS
  baldrIcons?: boolean
  // #endregion ===============================
  // #region ==================================
  runarRepo?: string
  runarOwner?: string
  runarBranch?: string
  // #endregion
  // LAYOUT STATE
  // #region ==================================
  currentLayout?: string
  previousLayout?: string
  layoutHistory?: string[]
  // Appearance
  colorTheme?: string
  iconTheme?: string
  productIconTheme?: string
  quickInputPosition?: boolean
  menuBarVisible?: boolean
  menuBarMode?: "classic" | "compact" | "hidden" | "toggle"
  menuBarCommandCenter?: boolean
  activityBarVisible?: boolean
  activityBarPosition?: "left" | "right" | "default"
  primarySidebarVisible?: boolean
  primarySidebarPosition?: "left" | "right"
  primarySidebarView?: string
  secondarySidebarVisible?: boolean
  secondarySidebarView?: string
  panelVisible?: boolean
  panelPosition?: "bottom" | "left" | "right"
  panelAlignment?: "left" | "center" | "right" | "justify"
  panelMaximized?: boolean
  panelView?: string
  fullScreen?: boolean
  zenMode?: boolean
  centered?: boolean
  statusBarVisible?: boolean
  shareEnabled?: boolean
  layoutControlEnabled?: boolean
  layoutControlType?: string
  editorFontVariations?: boolean
  externalBrowser?: string
  remoteIndicatorShowExtensionRecommendations?: boolean
  commandPaletteHistory?: number
  restoreWindows?: string
  editorAutoLockGroups?: boolean
  editorCloseEmptyGroups?: boolean
  editorPinnedTabSizing?: string
  editorTabSizing?: string
  editorTabSizingFixedMaxWidth?: number
  editorTabSizingFixedMinWidth?: number
  panelShowLabels?: boolean
  navigationControlEnabled?: boolean
  gitDiffEditorRenderGutterMenu?: boolean
  gitDecorationsEnabled?: boolean
  scmDiffDecorationsGutterAction?: string
  scmDiffDecorations?: string
  // Minimap
  minimap?: boolean
  minimapAutohide?: string
  minimapShowMarkSectionHeaders?: boolean
  minimapShowRegionSectionHeaders?: boolean
  minimapShowSlider?: string
  minimapSide?: string
  minimapSize?: string
  minimapRenderCharacters?: boolean
  minimapMaxColumn?: number
  // Terminal appearance
  terminalLocation?: string
  terminalFontSize?: number
  // Editor appearance
  editorZoomLevel?: number
  editorFontSize?: number
  editorBreadcrumbs?: boolean
  editorTabBar?: string
  editorEditorsActionPosition?: string
  editorWordWrap?: string
  editorFontFamily?: string
  editorFontLigatures?: boolean
  editorFoldingImportsByDefault?: boolean
  editorAccessibilitySupport?: string
  editorShowFoldingControls?: string
  editorShowTabs?: string
  editorAlwaysShowEditorActions?: boolean
  editorEnablePreviewFromQuickOpen?: boolean
  editorFocusRecentEditorAfterClose?: boolean
  editorPinnedTabsOnSeparateRow?: boolean
  editorWrapTabs?: boolean
  editorLimit?: boolean
  editorLineNumbers?: string
  editorScrollBeyondLastLine?: boolean
  editorUpdateImportsOnPaste?: boolean
  editorRestoreViewState?: boolean
  editorRenderWhitespace?: string
  editorRenderControlCharacters?: boolean
  editorFolding?: boolean
  editorGlyphMargin?: boolean
  editorStickyScrollEnabled?: boolean
  editorStickyScrollMaxLineCount?: number
  // Editor grid
  editorGridOrientation?: number
  editorGridGroups?: any[]
  editorOpenFiles?: Array<{
    path?: string
    group?: number
    pinned?: boolean
  }>
  editorActiveGroup?: number
  editorActiveFile?: string
  // Terminals
  terminals?: Array<{
    location?: "panel" | "editor"
    cwd?: string
    active?: boolean
  }>
  // #endregion ===============================
  // CONFIG STATE
  // #region ==================================
  workspaceRoot: string
  configPath: string
  storagePath: string
  projectConfigsDir: string
  workspaceConfigPath: string
  globalConfigPath: string
  globalSnippetsFilePath: string
  globalSnippetsPath: string
  workspaceSnippetsPath: string
  snippetsPath?: string
  devStackConfig: any
  globalConfig: ProjectConfig
  workspaceConfig: ProjectConfig
  workspaceId?: string
  userEmail: string
  // #endregion ===============================
  // FEATURE FLAGS
  // #region ==================================
  onFileOpen?: string
  GBL_DISABLE: boolean
  F_DISABLE: boolean
  WS_DISABLE: boolean
  EXT_DISABLE: boolean
  toggleHiddenItems: boolean
  strPrismaUpdater: boolean
  commands: boolean
  vscodecmdref: boolean
  markdownViewer: boolean
  snippets: boolean
  snippetsInEditor: boolean
  editorContextSnippets: boolean
  formatters: boolean
  trailingCommas: boolean
  batchRename: boolean
  eslintPrettier: boolean
  remixUtils: boolean
  theme: boolean
  blackedOut: boolean
  windowDifferentiator: boolean
  shadCNComponents: boolean
  repoMgr: boolean
  openGithub: boolean
  githubFunctions: boolean
  prismaFunctions: boolean
  remixComponents: boolean
  clickToSchema: boolean
  crudResolvers: boolean
  fileNesting: boolean
  revealExplorer: boolean
  copyPath: boolean
  bookmarks: boolean
  searchBar: boolean
  clipBoardHistory: boolean
  colorWheel: boolean
  lucideIcons: boolean
  share: boolean
  url: boolean
  jsonComments: boolean
  con: boolean
  removeAllComments: boolean
  unusedFunctions: boolean
  viewers: boolean
  uiDashboard: boolean
  devStackFunctions: boolean
  openLeftOffNote: boolean
  renderMd: boolean
  createFolderSmartIndex: boolean
  tailwindConverter: boolean
  convertToAgnostic: boolean
  concurrent: boolean
  autoSequencer: boolean
  tasks: boolean
  npmScripts: boolean
  autoSnippets: boolean
  todoNotesReminders: boolean
  AUTO_FOLD_1: boolean
  AUTO_FOLD_1_2: boolean
  AUTO_FOLD_PKGJSON_2: boolean
  AUTO_FOLD_PKGJSON_2_3: boolean
  // #endregion ===============================
  // BUILD & DEPLOYMENT
  // #region ==================================
  AUTORUN_SCRIPTS: boolean
  AUTORUN_DIR: string
  autorunDir: string
  PRO7: boolean
  CONCURRENT: string
  ARCHIVER: string
  DELETE_OLD_VSIX: boolean
  AUTO_INSTALL_VSIX: boolean
  OPEN_PUB_DASH: boolean
  RELOAD_INSTANCE: boolean
  BE_QP: boolean
  AUTO_FOLD_PKG: boolean
  PROMPT_OBJECTS_DIR: string
  UPDATE_PROMPT_OBJECTS: boolean
  CONVERT_README_DEV_MD: boolean
  // #endregion ===============================
  // TODO/NOTES INTEGRATION
  // #region ==================================
  repo: string
  owner: string
  branch: string
  repository: string
  remote: string
  isPriv: boolean
  syncInterval: number
  syncOnSave: boolean
  autoSync: boolean
  lastSyncTimestamp: string
  lastSHA: string
  checkRemindersInterval: number
  rootPath: string
  octokit?: Octokit
  ATAT: string
  notesDir: string
  // #endregion ===============================
  // MARKDOWN PREPROCESSOR
  // #region ==================================
  variableSystem: boolean
  sourcemapUpdater: boolean
  tocUpdater: boolean
  tableConversion: boolean
  tocType: string
  // #endregion ===============================
  // CODE SNAP
  // #region ==================================
  backgroundPalette: "magnum" | "pinky" | "passion" | "steel" | "tropic" | "forest" | "blueman" | "sand"
  containerBackground: string
  boxShadow: string
  containerPadding: string
  windowBorderRadius: string
  windowControlStyle: "None" | "OS X" | "Gray dots" | "Windows"
  showWindowTitle: boolean
  windowTitleStyle: "Workspace + Filename" | "Filename" | "Custom"
  windowTitleCustomStyle: string
  showLineNumbers: boolean
  realLineNumbers: boolean
  transparentBackground: boolean
  target: "container" | "window"
  trimEmptyLines: boolean
  // #endregion ===============================
  // SNIPPETS
  // #region ==================================
  devStackSnippets: SnippetsRoot
  // #endregion ===============================
  // OTHER
  // #region ==================================
  other: string
  // #endregion ===============================
}


```

Obviously it holds... a lot of values but in doing so, it makes handling a couple of other things that needs to be passed around ALL the time, just that much easier. If you missed, it's ok it's a huge list, but also contains values like context to namem one of them. Allowing you to only have to worry about passing a single value from function to function to ensure everything gets what it needsm, when it needs and not having to spider your way back till you finally have access to the context value to then having to go back through the maze of functions in order to get it where you need it. Making life easier it even contains globalState and terminalManager so you don't even have to declare the new classes if you don't want to.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Context Ngin 


- `getInstance`
- `initialize`
- `isInitialized`
- `getInitialState`
- `loadPersistedState`
- `persistState`
- `getState`
- `setState`
- `toggleStateValues`
- `subscribe`
- `notifyListeners`
- `deepMerge`
- `isObject`
- `startLayoutTransition`
- `completeLayoutTransition`
- `isTransitioning`
- `exportState`
- `importState`



## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Terminal Ngin 

### `TerminalManager`

Methods:

- `executeWait`
- `executeMaster`
- `isDevServerCommand`
- `loadEnvVariables`
- `replaceEnvVariables`
- `evaluateCondition`
- `executeTerminal1`
- `executeTerminal`
- `executeDevServerTerminal`
- `executeDebian`
- `executeDevDebian`
- `getTerminal`
- `getDevServerTerminal`
- `getDebianTerminal`
- `createTerminal`
- `createDebianTerminal`
- `createDevServerTerminal`
- `layoutFunction`
- `applyExtensions`
- `editVscdb`
- `applyExtensions1`
- `editVscdb1`
- `applyFolding`
- `executeConcurrent`
- `executeConcurrentBun`
- `setupHub`
- `createColoredProcess`
- `version1`
- `versoin2`
- `extractPortFromPackageJson`
- `fireTerminal`
- `executeCommandWithoutAwait`
- `interruptCommand`
- `suspendCommand`
- `shouldReuseTerminal`
- `shouldReuseDebianTerminal`
- `getWorkspaceRoot`
- `disposeCurrentTerminal`
- `disposeCurrentDebianTerminal`
- `delay`
- `dispose`
- `isTerminalExecuting`
- `getCurrentTerminal`
- `clearTerminal`
- `focusTerminal`
- `convertItems`
- `generateId`
- `setupResultWatcher`
- `executeItem`
- `cleanupMenu`

Despite the massive list of functions that the class has, you only use one of them, executeMaster. That's because none of the functions are actually for us to use, it just that is what is needed in order for everything to work as it does, even though that list does not contain the items needed for the concurrent config type.

When the function is trigger it first checks to see if you sent an object or a string, if a string was sent then it passews that tring to

```jsx
await vscode.commands.executeCommand(item)
```

Executing a vscode command, if it is an object we continue on.

2 more checks to see if we need to get either a env var or if we need to assign a port number to it.

Then starts the command switch:
- file
- md
- snippet
- url
- command
- wait
- powershellCommand
- debianCMD
- copyValue
- settingsToggle
- tasks
- layout
- apiCall
- search
- npmScripts
- fileAtLine
- label
- cmdChain
- chain
- argChain
- concurrent
- argConcurrent
- folder
- conditionalChain
- menu

Ensuring that each object that is passed through executes correctly without fail while at te same time, giving us the ability to manipulate the process with certain behaviours for example queueing.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Github CLI Ngin 

Methods:

- `check`
- `sync`
- `baldr`
- `midgardr`
- `midgardrGlobal`
- `midgardrNgin`
- `midgardrBasic`
- `midgardrCompsLibs`
- `midgardrTailwind`
- `midgardrTailwindFiles`
- `midgardrSelect`
- `midgardrConfig`
- `midgardrHashImports`
- `asgardConfig`
- `asgardConfigQuick`
- `asgardConfigCheck`
- `asgardRepoCheck`
- `asgardResolveConflicts`
- `asgardRepairTimeline`
- `asgardMoveWorkToNewTimeline`
- `asgardProjectCreate`
- `asgardProjectUpload`
- `asgardProjectUploadPatch`
- `asgardProjectUploadMinor`
- `asgardProjectUploadMajor`
- `asgardProjectDelete`
- `asgardProjectPublish`
- `asgardProjectLoad`
- `asgardProjectSave`
- `asgardProjectCreateQuick`
- `asgardProjectCreateOffConfig`
- `sourceAdd`
- `souceSet`
- `sourceDelete`
- `sourceSync`
- `sourceDownlaod`
- `asgardTimelineCombine`
- `asgardTimelineCreate`
- `asgardTimelineDelete`
- `asgardTimelineReplace`
- `asgardTimelineView`
- `asgardTimelineSwitch`
- `asgardVersionDelete`
- `asgardVersionRestore`
- `asgardVersionView`
- `asgardDownloadFile`
- `asgardDownloadFolder`
- `asgardGHSetup`

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Github CLI Ngin 


Methods:

- `check`
- `sync`
- `baldr`
- `midgardr`
- `midgardrGlobal`
- `midgardrNgin`
- `midgardrBasic`
- `midgardrCompsLibs`
- `midgardrTailwind`
- `midgardrTailwindFiles`
- `midgardrSelect`
- `midgardrConfig`
- `midgardrHashImports`
- `asgardConfig`
- `asgardConfigQuick`
- `asgardConfigCheck`
- `asgardRepoCheck`
- `asgardResolveConflicts`
- `asgardRepairTimeline`
- `asgardMoveWorkToNewTimeline`
- `asgardProjectCreate`
- `asgardProjectUpload`
- `asgardProjectUploadPatch`
- `asgardProjectUploadMinor`
- `asgardProjectUploadMajor`
- `asgardProjectDelete`
- `asgardProjectPublish`
- `asgardProjectLoad`
- `asgardProjectSave`
- `asgardProjectCreateQuick`
- `asgardProjectCreateOffConfig`
- `sourceAdd`
- `souceSet`
- `sourceDelete`
- `sourceSync`
- `sourceDownlaod`
- `asgardTimelineCombine`
- `asgardTimelineCreate`
- `asgardTimelineDelete`
- `asgardTimelineReplace`
- `asgardTimelineView`
- `asgardTimelineSwitch`
- `asgardVersionDelete`
- `asgardVersionRestore`
- `asgardVersionView`
- `asgardDownloadFile`
- `asgardDownloadFolder`
- `asgardGHSetup`


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> BIFROST Ngin 

Methods:

- `createNewProject`
- `installViaConfig`
- `getTemplates`
- `installViaTemplate`
- `submitProject`
- `addToRegistry`
- `createPlugin`
- `submitPlugin`
- `getPlugins`
- `installPlugin`
- `pluginDirectory`
- `pluginName`
- `pluginDescription`
- `pluginPlatform`
- `pluginTags`
- `pluginLibraries`
- `pluginFiles`
- `pkgValues`
- `projectConfigCreate`
- `projectConfigCreateQuick`
- `projectConfigCreateQuickNegative`
- `projectDesc`
- `projectName`
- `projectDir`
- `projectPlatform`
- `projectPkgMgr`
- `projectRepo`
- `projectOwner`
- `projectBranch`
- `projectPrivate`
- `projectLicense`
- `projectReadme`
- `projecChangelog`
- `projectAutoPushRepo`
- `projectBaldr`
- `installBaldr`
- `projectPostCss`
- `createPostCss`
- `projectTailwind`
- `installTailwind`
- `configureHashImports`
- `createTailwindConfig`
- `projectInstallPostInit`
- `projectPresetNgin`
- `projectMidgardr`
- `installMidgardr`
- `installPlatform`
- `autoPushRepo`
- `installPostInit`
- `executeGitOrder66`
- `finished`
- `createGitignore`
- `loadRemoteRegistry`
- `detectGitHubRepo`
- `csvToArray`
- `detectPackageManager`
- `detectPlatform`
- `detectPackageManager`
- `getPackageManagerCommand`
- `getDirname`
- `getBifrostConfigPath`
- `getAsgardConfigPath`
- `detectTagsFromStack`
- `detectPlatformFromStack`
- `toValidPackageName`
- `isValidPackageName`
- `getPkgpath`
- `parseRef`
- `verifyPublicRepo`
- `validateProjectName`
- `formatToValidName`
- `extractTags`
- `resolveTemplate`

