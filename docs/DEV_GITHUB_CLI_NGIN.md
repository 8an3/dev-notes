
## Dev Github CLI Ngin

Full GitHub CLI surface exposed through a single class. Every command battle tested, zero failure rate.

### Setup

```typescript
const github = new api.DevGithubCLINgin()
```

### General

```typescript
github.check()          // validates config, checks repo, syncs
github.sync()           // git add, commit, pull, push
github.asgardGHSetup()  // installs GitHub CLI via winget and authenticates
```

### Config

```typescript
github.asgardConfig()        // launches config wizard
github.asgardConfigQuick()   // quick create config
github.asgardConfigCheck()   // validates and repairs config.asgard
github.asgardRepoCheck()     // checks if repo exists on GitHub
```

### Project

```typescript
github.asgardProjectCreate()           // full project wizard — readme, license, package.json, git init, repo create, push
github.asgardProjectCreateQuick()      // fast create with defaults, no wizard
github.asgardProjectCreateOffConfig()  // installs based on existing config.asgard
github.asgardProjectPublish()          // publishes local project to GitHub for the first time
github.asgardProjectUpload()           // sync and push
github.asgardProjectUploadPatch()      // sync, bump patch version, tag, push
github.asgardProjectUploadMinor()      // sync, bump minor version, tag, push
github.asgardProjectUploadMajor()      // sync, bump major version, tag, push
github.asgardProjectSave()             // commit and push with label
github.asgardProjectLoad()             // restore saved stash
github.asgardProjectDelete()           // permanently delete a stash entry
```

### Sources / Remotes

```typescript
github.sourceAdd()       // add a remote — browse GitHub or enter URL manually
github.souceSet()        // change the origin remote
github.sourceDelete()    // unlink a remote
github.sourceSync()      // sync with remote
github.sourceDownlaod()  // clone a repo to a selected destination
```

### Timelines / Branches

```typescript
github.asgardTimelineCreate()          // create and switch to new branch
github.asgardTimelineSwitch()          // switch to existing branch
github.asgardTimelineView()            // view all branches, select to switch
github.asgardTimelineCombine()         // merge a branch into current
github.asgardTimelineReplace()         // merge experiment into main, delete source branch
github.asgardTimelineDelete()          // permanently delete a branch
github.asgardRepairTimeline()          // kills lock files, aborts stuck processes, refreshes index
github.asgardMoveWorkToNewTimeline()   // emergency splinter — moves uncommitted work to a new branch, cleans main
github.asgardResolveConflicts()        // keep yours, take theirs, or open visual merge editor
```

### Versions / Tags

```typescript
github.asgardVersionView()     // browse all tags, restore or delete from the same menu
github.asgardVersionRestore()  // rewind project to a specific commit
github.asgardVersionDelete()   // remove a tag locally and optionally from GitHub
```

### Downloads

```typescript
github.asgardDownloadFile()    // grab a single file from a GitHub repo via raw URL
github.asgardDownloadFolder()  // sparse checkout a specific folder from a repo
```

### MIÐGARÐR SDK

```typescript
github.midgardrGlobal()       // npm i -g @a5gard/midgardr-cli
github.midgardrNgin()         // midgardr full-w-ngin
github.midgardrBasic()        // midgardr full-install
github.midgardrCompsLibs()    // midgardr comps-and-libs
github.midgardrTailwind()     // configure tailwind and postcss
github.midgardrTailwindFiles() // writes tailwind.css to workspace
github.midgardrSelect()       // select specific components to install
github.midgardrConfig()       // create midgardr config
github.midgardrHashImports()  // configures package.json imports and tsconfig paths
github.baldr()                // install @a5gard/baldr
```
