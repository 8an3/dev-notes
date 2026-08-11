## Dev Workspace Context Ngin

The biggest problem extension devs run into is reliable workspace context. Which workspace is open, what config belongs to it, how do you persist settings that are global vs workspace-specific without stepping on yourself.

This engine solves it the same way it's solved internally — a unique ID gets written to `.vscode/ocrmnavigator/id.txt` for each workspace. That ID is used to load the correct workspace config from global storage. A global config layer sits on top of it. The two get merged and served as one cohesive config. Every workspace feels isolated, every global setting bleeds through automatically.

Your files live here:

```
C:\Users\{user}\AppData\Roaming\Code\User\globalStorage\skyler.ocrmnav\devShop\
├── global-navigator-config.dev
├── project-configs\
│   └── {projectId}.dev
```

### Setup

```typescript
const ctx = api.DevWorkspaceContextNgin.getInstance()
await ctx.init(context, workspaceRoot)
```

### Usage

```typescript
ctx.get()
// Returns the merged global + workspace config

await ctx.set({ categories: [...] })
// Writes back, automatically splits global vs workspace and persists both

ctx.subscribe((config) => {
  // fires whenever config changes
})

ctx.getProjectId()
// Returns the current workspace's unique identifier
```

---
