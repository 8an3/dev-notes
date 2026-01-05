## Terminal and Multi Kernel Ngin


```markdown
/ DEVSTACK_SYSTEM_ROOT/
└── ⚙️ [TERMINAL_AND_MULTI_KERNEL_NGIN](https://github.com/8an3/dev-notes/blob/main/docs/VFS.md)/
    ├── 📂 VFS_CORE/
    │   ├── 📂 Item Types 
    │   │   ├── 📄 [file](#file) 
    │   │   ├── 📄 [md](#md)
    │   │   ├── 📄 [fileAtLine](#fileAtLine) 
    │   │   ├── 📄 [folder](#folder) 
    │   │   ├── 📄 [url](#url) 
    │   │   ├── 📄 [command](#command) 
    │   │   ├── 📄 [chain](#chain) 
    │   │   ├── 📄 [concurrent](#concurrent) 
    │   │   ├── 📄 [cmdChain](#cmdChain) 
    │   │   ├── 📄 [conditionalChain](#conditionalChain) 
    │   │   ├── 📄 [powershellCommand](#powershellCommand) 
    │   │   ├── 📄 [debianCMD](#debianCMD)
    │   │   ├── 📄 [snippet](#snippet) 
    │   │   ├── 📄 [copyValue](#copyValue)
    │   │   ├── 📄 [settingsToggle](#settingsToggle)
    │   │   ├── 📄 [search](#search) 
    │   │   ├── 📄 [apiCall](#apiCall) 
    │   │   ├── 📄 [layout](#layout) 
    │   │   ├── 📄 [tasks](#tasks)
    │   │   ├── 📄 [npmScripts](#npmScripts)
    │   │   └── 📄 [label](#label) 
    │   ├── 📄 Virtual Filing System .......... Core VFS Engine
    │   ├── 📄 Files & Navigation ............. File management and navigation
    │   ├── 📄 Commands & Automation .......... Command execution and automation workflows
    │   ├── 📄 Terminal Commands .............. Terminal command integration
    │   ├── 📄 Utilities ...................... Utility functions and helpers
    │   ├── 📄 Project Agnostic Setup ......... Framework-agnostic configuration
    │   ├── 📄 Remote Resource Mgmt ........... Profiles for configs: save/download/edit
    │   └── 📄 Auto-Generated Items ........... Automatically generated VFS items
    └── 📂 CONFIGURATION_AND_EXCEPTIONS/
        ├── 📄 Complete Example ............... Production configuration walkthrough
        ├── 📄 Usage .......................... Usage guidelines and examples
        ├── 📄 Getting Started w/ Chains ...... Chain automation guide
        ├── 📄 Extension Configuration ........ Extension settings overview
        ├── 📄 Configuration Settings ......... Detailed configuration options
        ├── 📄 Core Settings .................. Core extension settings
        ├── 📄 Feature Toggles ................ Feature flags and toggles
        ├── 📄 Example Configuration .......... Configuration examples
        ├── 📄 [Copy Path](#copy-path) ...................... Path copying utilities
        ├── 📄 [Reveal In Explorer](#reveal-in-explorer) ............. File explorer integration
        ├── 📄 [Search](#search) ......................... Search functionality for config items
        └── 📄 Remote Resource Mgmt ........... Profiles for configs: save/download/edit
```

## Item Types

### Files & Navigation

#### `file`
Quick access to frequently-used files with customizable labels and icons.
- Copy file paths from context menu
- Reveal files in explorer
- Set items as hidden
- Custom icon support via [VS Code icon library](https://code.visualstudio.com/api/references/icons-in-labels)

```json
{ "label": "prisma.schema", "path": "prisma/prisma.schema", "type": "file" }
```

> [!NOTE]
> UPDATE TO `FILE` AND `MD`
>
> This update includes something I didn't know ould be done before now, as well as a fix to pathing.
>
> 1. any time you open a doc through the `file`, and `md` item types they will now:
>   - Will not open in preview mode ( if you don't know what this means, there are a couple of different file opening events that can happen based on several factors, settings.json values being one of the, where and how you open the files and so on. As a default settings vscode opens all files through the explorer pane IN preview mmode, so if you ever experieneced opening a file, and then opening another before editing the first file, only to have that first file close when you opened the second. That's the garbage preview mode by setting any file you open in a `temp` state, or however you want to call it, and if you don't take it out of that `temp` state by making a file change ie edit any line in the doc, it closes whenever you open another file, its fucking stupid imo and NOW whenever you open a file through vfs in place of the explorer pane, you will not experience said garbage )
>   - docs will now open in the editor group of your choice, if you configure the extensions settings `ocrmnavigator.vfs.targetEditorGroup`, if you want to take advantage of the layout engine OR if you usually use more that one editor group you can ie, setting this value to 3 will now open all of your docs in the third editor group. ( I'm still playing around with hijacking the doc opening event, I may be able to get this done, I may not. Currently I'm testing a new approach in which I'm ACTUALLY hijacking the open doc event which would be a lot better than the first approach that has already been tested and confirmed to work the issue is, it does not actually hijack the event, instead it reacts to the open file event, then once the file is open it THEN checks to see which editor group is open and if it isn't in the correct editor group it closes the file in question to open in the correct group. Personally, I thought I would absolutely hate the fact that it opens, closes and reopens, but after testing it is so fast that I'm 100% fine with it. So at the very least the second option is available. Currently testing is unavailable due to working on the layout engine and the new way editor and terminal groups that I'm still working on. Anyways this update is good because it future proofs, IF I have to go with the second option )
>   - focuses the editor
> 2. the second update is to the file path value saved in your item config, for some reason, I don't know why, but apparently I had the tendency to use full paths instead of relative. Made a new config for a new workspace and non of my files were opening, and then looking at the code, was like shiitt, lol, so sorry if you ran into this problem but its fixed now and just so no ones configs break, you can supply either the full path or relative 

#### `md`
works the same as file does

#### `fileAtLine`
Open files at specific line numbers for immediate context.

```json
{ "label": "seed.ts", "path": "prisma/seed.ts:425", "type": "fileAtLine" }
```

**Path Format**: `relative/file/path:lineNumber`

#### `folder`
Organize items into collapsible groups.
- Set as global or workspace-specific
- Configure expanded/collapsed state on startup
- Hide folders when needed
- Add unlimited folders for either global or workspace
- UPDATE: can now create unlimited nested folders, where folders 2 deep would display

```json
{
  "label": "MAIN",
  "expanded": false,
  "type": "folder",
  "global": true,
  "hidden": false,
  "items": []
}
```

#### `url`
Access websites directly from the extensions pane.

```json
{ "label": "Google", "path": "https://www.google.com", "type": "url" }
```

### Commands & Automation

#### `command`
Execute any VS Code command with a single click. Access 550+ built-in VS Code commands plus 450+ DevStack functions.

```json
{ "label": "SAVE ALL", "path": "workbench.action.files.saveAll", "type": "command" }
```

**Creating Commands:**
- **Custom Input**: Enter any command manually
- **VS Code Commands List**: Browse 550+ built-in commands with descriptions and categories
- **DevStack Commands List**: Access 450+ extension functions (400+ currently have AI-generated descriptions as work in progress)
- Auto-updating command picker that refreshes with each extension build

**Advanced Usage**: 
- Chain commands
- Sequential execution
- Access cheat sheet with 1050+ commands
- Set arguments for commands

```json
{ 
  "label": "Open Settings", 
  "type": "command", 
  "path": "workbench.action.openSettings", 
  "args": ["editor.fontSize"] 
}
```

#### `chain` - Sequential Execution
Execute commands one after another in your specified order. When creating items through the interface, the concurrent/sequential creation process enters a for loop allowing you to add as many custom or listed commands as needed.

```json
{ 
  "label": "Kill Terminals && Start DEV Server", 
  "path": "saveall, killterms, devApp", 
  "type": "chain" 
}
```

**Advanced Usage**: Mixed sequential/concurrent flows, conditional execution

**Preview**: [Video](https://youtu.be/ySp83VqxQ8s) | [Image](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/vfs/SequentialExecution+.gif?raw=true)

#### `concurrent` - Parallel Execution
Run multiple commands simultaneously for maximum speed. Can run alongside sequential commands.

```json
{ 
  "label": "dev:all", 
  "path": "devApp, devCalc", 
  "type": "concurrent" 
}
```

**Concurrent Execution Features:**
- Two execution patterns:
  - **Sequential Execution**: Functions called with `await` for ordered execution
  - **Concurrent Execution**: `await` keyword omitted for parallel execution
- Commands pipe into a single terminal instance with:
  - Distinct color-coded output for each command
  - Interactive terminal for user input (e.g., canceling processes)
  - Terminal remains open as regular PowerShell after cancellation
- All other commands execute in separate environments with persistent terminal instances
- Failed command outputs remain available for review and debugging

**Advanced Usage**: Priority-based execution, resource management

**Enable**: Navigate to extension settings and toggle "Bleeding Edge" to `true`, or set `"ocrmnavigator.CONCURRENT": "bleeding-edge"` in settings

> [!TIP] `concurrent` && `chain` Optional creation process
> 
> The previous option to create an item with quickpick and inputs is available via the title pane dropdown and selecting `Add sequantial/concurrent/command chain via vscode` 
>
> There is now a new option if you select `Add item via Vscode` and select one of the three item types you wish to create.
> 
> INSTEAD of using quickpicks and inputs, this new process opens a jsonc file, in which you can, imo, much more easily create any of the three item types.
> Once started you will have a choice to add items of either:
> - using the new intellisense implementation, by `ctrl` + `space` within the path value of the parent object. 
>   - It scans your current vfs
>   - offers a dropdown displaying their labels. 
>   - once an option has been selected it wil add an object to the `chain` list that will be listed below the parent
> - the second option creates new objects within your config, you may copy the child object and paste it below to create a new object for your config
>   - any child item, whether you include it or not, will be given the value `hidden: true`
> Now you may use both systems, interchangeably in the case if you would like to add items exactly in the order you want them to execute in OR if you would like, add several options, not caring which order they are currently in. Once you have added all the items you wish, then cutting + pasting the objects in the execution order you would like them to happen
> All child items will execute in the order in which they are listed

#### `cmdChain`
Chain multiple VS Code or DevStack commands without building several config objects. Takes the value and executes each sequentially.

```json
{ "label": "Quick Setup", "path": "cmd1, cmd2, cmd3", "type": "cmdChain" }
```

> [!TIP] `cmdChain` Optional creation process
> 
> The same process will take place as `concurrent` && `chain`, the only difference is that whatever child items you add, WILL NOT be added to the config
>   - be sure you are only including `command` type items, because if you include any other item, the command will not work
> The intellisense options list has been replaced with dynamically acquiring vscodes currently available commands, to ensure the list is always update to date without my intervention
> There is a caveat with the auto generated commands list, the amount of available items it lists seems to be a lot less then the list that I can manually put together, by a lot. Because of this, if there is a command you wish to use but doesn't show up, don't worry, just paste it in and follow it with a command and space ie `, ` and move on to the next item
> I would rather include the entire list tbh, BUT whenever I can I create functions that take care of themselves due to the quantity of features available in this extension. If I were to have to manually groom this list constantly, I would never be able to get any other work done if every feature were like this. 
> There is however, a manually created list to view in the devstack quickpick menu `DevStack Cmds` and `VSCode Cmds` are both lists that dispaly commands that can be used with command chain. 
> VSCode cmds is a manually created list of vscode commands that were aquired via printing out every single available command that can be executed in my vscode instance. Then I took the time, to manually evaluate each item before deciding on whether to delete it or not. This process did not take long as I only have 2 other extensions active at any one time. Purely because I have not had the time to incorporate the functionality that I need from them into DevStack. The finished list came up to around 1830 options. Where as the dynamic list, comes up to 753, for me anyways
> The Devstack commands list IS dynmaically generated at the extensions build time to ensure that the list included is always up to date without my intervention
> The auto generated list does include, both vscode commands and commands avilable from this extension along with any other commands that are available to you within your OWN vscode instance. If you wanted to include commands from an extension you currently have installed, you may do so but be warned that whenever you go to use that `cmdChain` item it will only work if that extension is installed. Meaning if you configure that item at home, and then go to use it at work where you do not have that extension installed, it will not work.


#### `conditionalChain`
This has yet to be tested as the idea came to me while working in another project.

**Conditional Chain Guide**

1. Overview

The `conditionalChain` item type allows you to create intelligent automation workflows that execute different chains based on conditions. Unlike regular chains that always execute the same sequence, conditional chains can adapt based on success/failure states, configuration values, environment variables, file existence, and more.

2. Basic Structure

```json
{
  "label": "My Conditional Workflow",
  "path": "task1, task2, task3",
  "type": "conditionalChain",
  "args": [
    {
      "type": "conditionType",
      "executeChain": "chainToExecute"
    }
  ]
}
```

- **`path`**: The main chain of items to execute (comma-separated labels)
- **`args`**: Array of conditions that determine what happens next
- **`executeChain`**: The chain(s) to execute if the condition is met (can reference any item label in your config)

3. Condition Types
  - 1. **onSuccess** - Execute if main chain succeeds

```json
{
  "label": "Build and Deploy",
  "path": "lint, build, test",
  "type": "conditionalChain",
  "args": [
    {
      "type": "onSuccess",
      "executeChain": "deploy, notify-success"
    }
  ]
}
```

  - 2. **onFailure** - Execute if main chain fails

```json
{
  "label": "Build with Rollback",
  "path": "build, test, deploy",
  "type": "conditionalChain",
  "args": [
    {
      "type": "onFailure",
      "executeChain": "rollback, notify-failure, cleanup"
    }
  ]
}
```

  - 3. **always** - Always execute (useful for cleanup)

```json
{
  "label": "Test with Cleanup",
  "path": "setup, run-tests",
  "type": "conditionalChain",
  "args": [
    {
      "type": "always",
      "executeChain": "cleanup, generate-report"
    }
  ]
}
```

  - 4. **itemSuccess** - Check if specific item succeeded

```json
{
  "label": "Partial Deploy",
  "path": "build-frontend, build-backend, run-tests",
  "type": "conditionalChain",
  "args": [
    {
      "type": "itemSuccess",
      "itemLabel": "build-frontend",
      "executeChain": "deploy-frontend"
    },
    {
      "type": "itemSuccess",
      "itemLabel": "build-backend",
      "executeChain": "deploy-backend"
    }
  ]
}
```

**Note:** `itemLabel` can reference ANY item that was executed - including items from the main chain OR items executed by previous conditions!

  - 5. **itemFailure** - Check if specific item failed

```json
{
  "label": "Test with Debugging",
  "path": "unit-tests, integration-tests",
  "type": "conditionalChain",
  "args": [
    {
      "type": "itemFailure",
      "itemLabel": "integration-tests",
      "executeChain": "collect-logs, open-debugger"
    }
  ]
}
```

  - 6. **configValue** - Check VS Code configuration

```json
{
  "label": "Environment-Based Deploy",
  "path": "build, test",
  "type": "conditionalChain",
  "args": [
    {
      "type": "configValue",
      "configKey": "ocrmnavigator.environment",
      "operator": "equals",
      "value": "production",
      "executeChain": "deploy-prod"
    },
    {
      "type": "configValue",
      "configKey": "ocrmnavigator.environment",
      "operator": "equals",
      "value": "staging",
      "executeChain": "deploy-staging"
    }
  ]
}
```

**Available Operators:**
- `equals` or `==` - Loose equality
- `strictEquals` or `===` - Strict equality
- `notEquals` or `!=` - Not equal
- `strictNotEquals` or `!==` - Strictly not equal
- `greaterThan` or `>` - Greater than
- `greaterThanOrEqual` or `>=` - Greater than or equal
- `lessThan` or `<` - Less than
- `lessThanOrEqual` or `<=` - Less than or equal
- `contains` - String contains substring
- `notContains` - String does not contain substring
- `startsWith` - String starts with
- `endsWith` - String ends with
- `matches` - Regex match

  - 7. **envVariable** - Check environment variable

```json
{
  "label": "CI/CD Pipeline",
  "path": "build, test",
  "type": "conditionalChain",
  "args": [
    {
      "type": "envVariable",
      "envKey": "CI",
      "operator": "equals",
      "value": "true",
      "executeChain": "ci-deploy"
    },
    {
      "type": "envVariable",
      "envKey": "NODE_ENV",
      "operator": "equals",
      "value": "development",
      "executeChain": "start-dev-server"
    }
  ]
}
```

  - 8. **fileExists** - Check if file exists

```json
{
  "label": "Smart Install",
  "path": "check-dependencies",
  "type": "conditionalChain",
  "args": [
    {
      "type": "fileNotExists",
      "filePath": "node_modules",
      "executeChain": "npm-install"
    },
    {
      "type": "fileExists",
      "filePath": "package-lock.json",
      "executeChain": "npm-ci"
    }
  ]
}
```

**Note:** Paths can be absolute or relative to workspace root.

  - 9. **combined** - Multiple conditions with AND/OR logic

```json
{
  "label": "Advanced Deploy",
  "path": "build, test",
  "type": "conditionalChain",
  "args": [
    {
      "type": "combined",
      "logic": "AND",
      "conditions": [
        {
          "type": "onSuccess"
        },
        {
          "type": "envVariable",
          "envKey": "CI",
          "operator": "equals",
          "value": "true"
        },
        {
          "type": "configValue",
          "configKey": "ocrmnavigator.autoDeploy",
          "operator": "equals",
          "value": true
        }
      ],
      "executeChain": "deploy-production"
    }
  ]
}
```

**Logic options:**
- `AND` - All conditions must be true
- `OR` - At least one condition must be true

  - 10. **custom** - Custom JavaScript evaluation

```json
{
  "label": "Custom Logic",
  "path": "task1, task2, task3",
  "type": "conditionalChain",
  "args": [
    {
      "type": "custom",
      "expression": "results.filter(r => r.success).length >= 2",
      "executeChain": "partial-success-handler"
    }
  ]
}
```

**Available variables in custom expressions:**
- `results` - Array of all executed items with `{ label, success, result?, error? }`
- `success` - Boolean indicating if the main chain succeeded

3. Advanced Examples

  - Example 1: Complete CI/CD Pipeline

```json
{
  "label": "Full CI/CD",
  "path": "lint, build, unit-tests, integration-tests",
  "type": "conditionalChain",
  "args": [
    {
      "type": "onSuccess",
      "executeChain": "deploy-staging"
    },
    {
      "type": "itemSuccess",
      "itemLabel": "deploy-staging",
      "executeChain": "smoke-tests"
    },
    {
      "type": "itemSuccess",
      "itemLabel": "smoke-tests",
      "executeChain": "deploy-production, notify-slack"
    },
    {
      "type": "onFailure",
      "executeChain": "rollback, alert-team"
    },
    {
      "type": "always",
      "executeChain": "cleanup, generate-report"
    }
  ]
}
```

  - Example 2: Smart Testing Strategy

```json
{
  "label": "Smart Test Runner",
  "path": "quick-tests",
  "type": "conditionalChain",
  "args": [
    {
      "type": "itemFailure",
      "itemLabel": "quick-tests",
      "executeChain": "full-test-suite"
    },
    {
      "type": "combined",
      "logic": "AND",
      "conditions": [
        {
          "type": "itemSuccess",
          "itemLabel": "quick-tests"
        },
        {
          "type": "envVariable",
          "envKey": "CI",
          "operator": "equals",
          "value": "true"
        }
      ],
      "executeChain": "visual-regression-tests, performance-tests"
    }
  ]
}
```

  - Example 3: Environment-Aware Workflow

```json
{
  "label": "Context-Aware Build",
  "path": "prebuild, build",
  "type": "conditionalChain",
  "args": [
    {
      "type": "fileNotExists",
      "filePath": ".env",
      "executeChain": "copy-env-template"
    },
    {
      "type": "configValue",
      "configKey": "ocrmnavigator.buildMode",
      "operator": "equals",
      "value": "production",
      "executeChain": "optimize-assets, minify"
    },
    {
      "type": "configValue",
      "configKey": "ocrmnavigator.buildMode",
      "operator": "equals",
      "value": "development",
      "executeChain": "enable-source-maps, start-watch-mode"
    }
  ]
}
```

  - Example 4: Cascading Conditions

```json
{
  "label": "Multi-Stage Pipeline",
  "path": "stage1",
  "type": "conditionalChain",
  "args": [
    {
      "type": "onSuccess",
      "executeChain": "stage2"
    },
    {
      "type": "itemSuccess",
      "itemLabel": "stage2",
      "executeChain": "stage3"
    },
    {
      "type": "itemSuccess",
      "itemLabel": "stage3",
      "executeChain": "final-deploy"
    }
  ]
}
```

4. Tips & Best Practices

  - 1. **Order Matters**: Conditions are evaluated in order. Later conditions can check the success of items executed by earlier conditions.

  - 2. **Always Use Cleanup**: Add an `"always"` condition for cleanup tasks that should run regardless of success/failure.

  - 3. **Combine with Regular Chains**: Your `executeChain` can reference any item - including other conditional chains for complex nested logic.

  - 4. **Test Incrementally**: Start with simple conditions and build up to complex workflows.

  - 5. **Use Descriptive Labels**: Make item labels clear so conditions are easy to understand.

  - 6. **Leverage itemSuccess/itemFailure**: These are powerful for partial success scenarios where you want different actions based on which specific steps succeeded.

5. Common Patterns

  - Pattern: Deploy Only on Success
```json
{
  "type": "onSuccess",
  "executeChain": "deploy"
}
```

  - Pattern: Rollback on Failure
```json
{
  "type": "onFailure",
  "executeChain": "rollback"
}
```

  - Pattern: Environment-Based Routing
```json
{
  "type": "configValue",
  "configKey": "ocrmnavigator.env",
  "operator": "equals",
  "value": "prod",
  "executeChain": "prod-workflow"
}
```

  - Pattern: Conditional Install
```json
{
  "type": "fileNotExists",
  "filePath": "node_modules",
  "executeChain": "npm-install"
}
```

  - Pattern: Multi-Condition Gate
```json
{
  "type": "combined",
  "logic": "AND",
  "conditions": [
    { "type": "onSuccess" },
    { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true" }
  ],
  "executeChain": "deploy"
}
```

6. Troubleshooting

**Problem**: Condition not triggering
- **Solution**: Check that the `itemLabel` matches exactly (case-sensitive)
- **Solution**: Verify the condition type is spelled correctly
- **Solution**: Check that referenced items exist in your config

**Problem**: Custom expression failing
- **Solution**: Test your expression syntax - remember you have access to `results` and `success` variables
- **Solution**: Check the browser/extension console for evaluation errors

**Problem**: File path not found
- **Solution**: Use absolute paths or paths relative to workspace root
- **Solution**: Check for typos in file paths

7. Reference Item in Config

All the items referenced in `executeChain` must exist somewhere in your VFS configuration:

```json
{
  "items": [
    {
      "label": "My Workflow",
      "path": "build, test",
      "type": "conditionalChain",
      "args": [...]
    },
    {
      "label": "build",
      "path": "npm run build",
      "type": "powershellCommand"
    },
    {
      "label": "test",
      "path": "npm test",
      "type": "powershellCommand"
    },
    {
      "label": "deploy",
      "path": "npm run deploy",
      "type": "powershellCommand"
    }
  ]
}
```

### Terminal Commands

#### `powershellCommand`
Execute commands in Windows PowerShell as if typed directly.

```json
{ "label": "CRM", "path": "code-insiders -n f:/DevStack", "type": "powershellCommand" }
```

**Advanced Usage**: WSL integration, environment variables, complex workflows

> [!TIP] `pnpm run dev` | `npm run dev` | other dev server commands
>
> One of the nice features I was able to implement into the new terminal engine is that it automatically senses wether you are executing a dev server command or not, and react accordingly
> If you are, it scans currently open terminals for the dev server command you are trying to run, for example `pnpm run dev`, it grabs the port number out of your package .json and assign that terminal to that port number and dev server command
> IF there currently is a dev sever already running the command you are trying to execute, it will progmatically send `ctrl + c` to kill the process and execute the new dev server command
> This makes it slightly easier for you when creating items where you want to start a dev server, previously I had create a chain and execute kill all terminals, followed by the dev server command
> This not only creates more freedom in what you can execute when, but simplifies the items you need to create in order to get the extension to do what you want
> IF you are in a mono repo type project, or in a project where you need to run more than one dev server, any dev server command that you execute that does not currently have a window open, it will create a new terminal window to execute the command 

#### `debianCMD`
Run commands in Windows Debian WSL terminal environment. Execute programs with pre-programmed flags.

```json
{ 
  "label": "VLC w/ playlist", 
  "path": "cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' playlist.xspf", 
  "type": "debianCMD" 
}
```

**Advanced Usage**: WSL integration, environment variables, complex workflows

**Note**: The ability to set arguments for powershell and bash commands is in development.


### Utilities

#### `snippet`
Save snippets that copy to clipboard when clicked. Adds to the already included functionality of inline snippet insertion.

```json
{ "label": "Snippet Name", "path": "ocrmnavigator.code-snippets", "type": "snippet" }
```

#### `copyValue`
Place any predefined value into your clipboard.

```json
{ 
  "label": "Copy to clipboard", 
  "path": "Value to be copied into the clipboard", 
  "type": "copyValue" 
}
```

#### `settingsToggle`
Toggle VS Code settings between values. Defaults to toggle between true/false. If provided the args value, toggles through the array one by one.

```json
{ 
  "label": "ARCHIVER", 
  "path": "ocrmnavigator.ARCHIVER", 
  "type": "settingsToggle", 
  "args": ["custom", "vsce"],
  "icon": "settings" 
}
```

```json
{ 
  "label": "NPM Scripts", 
  "path": "ocrmnavigator.vfs.npmScripts", 
  "type": "settingsToggle", 
  "icon": "settings" 
}
```

#### `search`
Open search editors with predefined parameters. Opens in a new tab with context lines, case sensitive by default. Allows multiple search editors at once.

```json
{ 
  "label": "console.log(", 
  "path": "regex pattern to find console.log(", 
  "type": "search", 
  "icon": "search" 
}
```

#### `apiCall`
Execute HTTP API requests directly from the file tree.

**GET Request:**
```json
{
  "label": "Check API Status",
  "path": "https://api.example.com/status",
  "type": "apiCall",
  "icon": "cloud",
  "tooltipText": ""
}
```

**POST Request with Body:**
```json
{
  "label": "Deploy to Production",
  "path": "https://hooks.example.com/deploy",
  "type": "apiCall",
  "args": [
    { "method": "POST" },
    { "body": { "branch": "main", "environment": "production" } }
  ],
  "icon": "rocket"
}
```

When creating an api call from the title panes drop down menu a markdown doc will open that will help with the creation process as seen below:

```markdown
# API Call Configuration

# Required fields
label: ${label}
path: https://api.example.com/endpoint
type: ${itemType.value}

# Optional fields
icon: cloud
tooltipText: Description of this API call

# HTTP Configuration (optional)
args:
  - method: GET
  # For POST/PUT/PATCH requests with body:
  # - method: POST
  # - body:
  #     - key: value
  #     - another: value

# Headers (optional)
headers:
  - Content-Type: application/json
  # - Authorization: Bearer YOUR_TOKEN

# Instructions:
# - Fill in the required 'path' field with your API endpoint
# - Uncomment and modify optional sections as needed
# - Save this file to create the API call item
# - Close without saving to cancel
```


#### `layout`

[Layout Configuration Guide](./LAYOUT.md)


### Auto-Generated Items

#### `tasks`
Automatically generated from `tasks.json` when workspace initializes.

#### `npmScripts`
Automatically generated from `package.json` when workspace initializes.

#### `settingsToggle`

- scans workspace settings.json and auto generates items within `SETTINGS` folder placing them in `workspace` so as to not overwrite any items you currently have within the settings folder. The auto generated items will only work for settings that use the values `false` | `true`

> [!TIP] `settingsToggle` Optional creation process
>
> If you have a settings key that requires a different value then `false` | `true`, then you may create a settings toggle
> When creating the new item, at the step of placing the required values you may place them in as such
> - `true, false`
> - `top, botton, left, right`
> And the function will take care of the formatting for you
> IF you do not know the values for the desired settings key at the time of creation, or would rather do other things than looking up vscodes settings.json values in microsofts amazingly kept together documentation, you may leave this value blank
> When leaving this value blank the function will dynamically aquire the required values for you and create the item in your config


#### `snippet`

- snippets are now auto generated items within the vfs explorer pane
- You may also edit the items within this folder, as these auto generated items will not actually take up any space within the config file itself, if any labels match any label from the auto generated list, those items will not be included
- allowing you to create you organization system for your snippet files
- snippet files adopted the global / workspace system, making them workspace context intelligent, enabling you to organize your snippets at a workspace level so you could have a different config for each project 


> [!NOTE] Moving Items
>
> Previously I relied on the web ui to provide a way to move items for users, but... I am trying to move away from that medium. It IS a lot easier to create functionality through that medium where the end-user will not only find it easy but painless. As far as moving items, I think I have thought of the best solution to provide through the vscode interface.
>
> Right clicking on any item and selecting `move` will bring up a quickpick, populated with your current configs items. 
> Wheenver you select an item from this list, it will place the item you are moving ABOVE that config item and save your edited config.
>
> By comparison, whenever you `cut` a line within vscodes editor, then place your cursor where you would like that line to end up. Pasting that item inserts it in the line above, just like the move item process. 
>
> It's not easy creating the `perfect` function when developing something, especially with an extension as complicated as this one. You have to know your end-user, their habits, what they do on a day to day basis, what they do while they work, what level of knowledge they may or may not possess and what experience level they may or may not be at, edge cases, not to mention forecasting what may or may not change within the code in the future, so on and so forth. Ontop of all that madness, vscodes interface and its limited available options to provide to end users when creating functionality. It becomes... a rather challenging problem to face. I KNOW I'm not the only one that's facing this issue, as 99% of the extensions on the marketplace have horrendous ui's and force the user to adopt to a stupid process, if not the entire ui atleast some parts of it. As I'm always challenging myself, I find these puzzles fun because you are not only looking to provide a technical solution but also a user solution and how they interact with what you built.
> Hopefully, the newly created `create` and `move` functions completely replace the need for the web ui as far as config items go, and will disable it for the meantime.



> [!TIP] Philosophy: Empowering Developers
> This extension takes an unconventional approach by exposing every internal function directly to you. While this is rare in VS Code extensions, the reasoning is simple: these functions were already built for personal use, and automating their availability helps colleagues and the broader community with minimal additional effort.
>
> Development work involves countless time-consuming repetitive tasks. Unlike some industries where these inefficiencies are unavoidable, software development offers a unique advantage—we can program solutions to our own problems. This extension aims to eliminate those time sinks and help you focus on what matters: building great software.

#### Getting Started with Chains

> [!TIP] 
> The `chain` type is the most powerful feature in DevStack. It allows you to combine multiple commands into a single workflow, dramatically reducing the steps required for common development tasks.
>
> Example 1: Git Workflow with Version Bump
> This chain automates the complete process of committing, pushing, and incrementing your package version:
> ```text
> type: chain
> path: gitAdd, gitCom, gitPush, bumpVers, gitPush, gitPushTags
> ```
> **Required Component Commands:**
> ```text
> type: powershellCommand
> hidden: true
> path: git add *
> 
> type: powershellCommand
> hidden: true
> path: git commit -m "pushing local data"
> 
> type: powershellCommand
> hidden: true
> path: git push
> 
> type: powershellCommand
> hidden: true
> path: pnpm version patch
> 
> type: powershellCommand
> hidden: true
> path: git push
> 
> type: powershellCommand
> hidden: true
> path: git push --tags
> ```
> Previously, this was run as a single inline command, which had edge cases that caused failures. Breaking it into modular components solved those reliability issues completely.
>
> Example 2: Using Extension Commands
> You can achieve the same result using the extension's built-in commands:
> ```text
> type: cmdChain
> path: ocrmnavigator.gitAdd, ocrmnavigator.gitCom, ocrmnavigator.gitPush, 
>       ocrmnavigator.bumpPatchVersion, ocrmnavigator.gitPush, 
>       ocrmnavigator.gitPushTags
> ```
>
> 
> The extension automatically detects your package manager (npm, pnpm, yarn) and adjusts commands accordingly.
> 
>  Example 3: VS Code Extension Development Workflow
> 
> This comprehensive chain handles the entire build-and-reload process for VS Code extension development:
> 
> ```text
> type: cmdChain
> path: ocrmnavigator.saveAll, ocrmnavigator.killAll, 
>       ocrmnavigator.formatPackageJson, ocrmnavigator.md.convertReadme, 
>       ocrmnavigator.compileWithPackager, ocrmnavigator.installNow, 
>       ocrmnavigator.reloadWindow
> ```
> 
> **breakdoown:**
> 1. Saves all open editors
> 2. Terminates all terminal instances
> 3. Formats package.json files (supports dual package.json setup for automation)
> 4. Converts readme files for pre-processing
> 5. Compiles the extension using either:
>    - **vsce**: Creates local package and publishes to marketplace
>    - **Custom archiver**: Faster compilation with fewer restrictions (supports SVGs in readme, which vsce blocks)
> 6. Installs the extension locally
> 7. Reloads the current VS Code window
> 
>  Real-World Impact
> 
> The automation possibilities are extensive. For example, my icon library workflow is fully automated—I simply drop an SVG file into a folder, click one button in the DevStack explorer, and walk away. The entire process runs automatically:
> 
> - Icon creation and optimization
> - README updates
> - Project compilation and building
> - Git commit and push to GitHub
> - Version bump
> - NPM publication
> 
> Since my projects are interconnected, I've even created a single button that executes this workflow across all three projects simultaneously.
> 
> Going forward, the extension will embrace a more modular architecture. Previously, functionality was built either entirely in config files or as monolithic standalone functions. The modular approach demonstrated above provides better reliability, maintainability, and reusability.

#### `label`
a file item type to add a visual `title` or `seperator` in other words

```json
        {
          "label": "★ ━━━━ ☆ ━━━━           PROJECT              ━━━━ ☆ ━━━━ ★",
          "type": "label",
          "icon": "chrome-minimize"
        },
        {
          "label": "★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆",
          "type": "label",
          "icon": "chrome-minimize"
        },
```
The label portion can be stylized in any form you would like, when creating my own I hastily put together the above examples. The new monaco editor will have virtually all special characters that are available to us so you can use that to create a design any way you like with the available toolset.
This item type can also have its icon customized as well. 
In closing, just a quick warning when designing your label item types. Personally, I wanted to create all of my labels to be the same length. The above two examples, obviously do not share the same distance in length. In actuality, when vscode renders these two labels they end up, in fact, the same length. I do not know why vscodes file system / file tree renders it so much more differently but it is what it is. So if your looking at scratching your head as you look at your rendered design, your not alone

### Project Agnostic Configuration
 
Create configurations that work across workspaces or stay project-specific

#### Key Features
- Split configuration between global and workspace settings
- Configure folders as globally available or workspace-specific
- Support for hybrid configurations and per-project customization

### Complete Example

<details>
<summary>Config</summary>

```json
{
  "categories": [
 {
      "label": "EXAMPLES",
      "expanded": false,
      "type": "folder",
      "global": true,
      "items": [
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "Build and Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "onSuccess", "executeChain": "deploy, notify" },
            { "type": "onFailure", "executeChain": "rollback, alert" }
          ]
        },
        {
          "label": "Conditional Build",
          "path": "lint, test, build",
          "type": "conditionalChain",
          "args": [
            { "type": "itemSuccess", "itemLabel": "test", "executeChain": "deploy" }
          ]
        },
        {
          "label": "Environment-Based Deploy",
          "path": "build",
          "type": "conditionalChain",
          "args": [
            { "type": "configValue", "configKey": "ocrmnavigator.environment", "operator": "equals", "value": "production", "executeChain": "deployProd" },
            { "type": "configValue", "configKey": "ocrmnavigator.environment", "operator": "equals", "value": "staging", "executeChain": "deployStaging" }
          ]
        },
        {
          "label": "Conditional Install",
          "path": "checkDeps",
          "type": "conditionalChain",
          "args": [
            { "type": "fileNotExists", "filePath": "node_modules", "executeChain": "npmInstall" }
          ]
        },
        {
          "label": "Build with Cleanup",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "always", "executeChain": "cleanup, logResults" }
          ]
        },
        {
          "label": "Advanced Conditional",
          "path": "task1, task2, task3",
          "type": "conditionalChain",
          "args": [
            { "type": "custom", "expression": "results.filter(r => r.success).length >= 2", "executeChain": "partialSuccessHandler" }
          ]
        },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "Build with CI",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        { "label": "ciDeploy", "path": "dockerBuild, pushToRegistry, deployToK8s", "type": "chain" },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" },
            { "type": "itemSuccess", "itemLabel": "ciDeploy", "executeChain": "deployStaging" }
          ]
        },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "ciDeploy",
          "path": "dockerBuild, pushToRegistry",
          "type": "conditionalChain",
          "args": [
            { "type": "onSuccess", "executeChain": "deployStaging" }
          ]
        },
        {
          "type": "combined",
          "logic": "AND",
          "conditions": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true" },
            { "type": "onSuccess" }
          ],
          "executeChain": "ciDeploy"
        },
        { "label": "README.dev.md", "path": "README.dev.md", "type": "file", "icon": "markdown" },
        { "label": "Manage VS Extensions", "path": "https://marketplace.visualstudio.com/manage/publishers/skyler?auth_redirect=True", "type": "url" },
        { "label": "Scan File Imports", "path": "ocrmnavigator.imports.file.scan", "type": "command", "icon": "terminal-cmd" },
        { "label": "CRM", "path": "code-insiders -n f:/OpinionatedCRM", "type": "powershellCommand", "icon": "project" },
        { "label": "VLC w/ playlist", "path": "cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' 1Firreee.xspf", "type": "debianCMD" },
        { "label": "Format", "path": "formatfile, saveall", "type": "chain" },
        { "label": "Format", "path": "formatfile, saveall", "type": "concurrent" },
        { "label": "★ ━━━━ ☆ ━━━━ AUTORUN SCRIPTS ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆", "type": "label", "icon": "chrome-minimize" },
        { "label": "Prompt - Reusable Comps", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Tasks", "path": "ocrmnavigator.vfs.tasks", "type": "settingsToggle", "icon": "settings" },
        {
          "label": "ARCHIVER",
          "path": "ocrmnavigator.ARCHIVER",
          "type": "settingsToggle",
          "args": [
            "custom",
            "vsce"
          ],
          "icon": "settings"
        },
        {
          "label": "Create User",
          "path": "https://api.example.com/users",
          "args": [
            { "method": "POST" },
            { "headers": { "Content-Type": "application/json", "Authorization": "Bearer YOUR_TOKEN" } },
            { "body": { "name": "John Doe", "email": "john@example.com" } }
          ],
          "type": "apiCall",
          "icon": "person-add",
          "tooltipText": ""
        },
        {
          "label": "Deploy to Production",
          "path": "https://hooks.example.com/deploy",
          "args": [
            { "method": "POST" },
            { "body": { "branch": "main", "environment": "production" } }
          ],
          "type": "apiCall",
          "icon": "rocket"
        },
        {
          "label": "List Repos",
          "path": "https://api.github.com/users/yourname/repos",
          "args": [
            { "headers": { "Accept": "application/vnd.github.v3+json", "Authorization": "token YOUR_GITHUB_TOKEN" } }
          ],
          "type": "apiCall",
          "icon": "github",
          "tooltipText": ""
        },
        {
          "label": "Restart Dev Server",
          "path": "http://localhost:3000/api/restart",
          "args": [
            { "method": "POST" }
          ],
          "type": "apiCall",
          "icon": "debug-restart",
          "tooltipText": ""
        }
      ]
    }
  ]
}
```

</details>

<details>
<summary>Personal config if your interested</summary>

```json
{
  "categories": [
    {
      "label": "MAIN",
      "expanded": false,
      "type": "folder",
      "global": true,
      "items": [
        { "label": "CRM", "path": "code-insiders -n f:/OpinionatedCRM", "type": "powershellCommand", "icon": "project" },
        { "label": "Catalyst Software", "path": "code-insiders -n f:/playground", "type": "powershellCommand", "icon": "symbol-event" },
        { "label": "CatalystPOS", "path": "code-insiders -n f:/CatalystPOS", "type": "powershellCommand", "icon": "jersey" },
        {
          "label": "Dev Projects",
          "type": "folder",
          "expanded": true,
          "global": true,
          "items": [
            { "label": "DevStack", "path": "code-insiders -n f:/DevStack", "type": "powershellCommand", "icon": "symbol-event" },
            { "label": "icons", "path": "code-insiders -n f:/icons", "type": "powershellCommand", "icon": "symbol-event" },
            { "label": "Catalyst Editor", "path": "code-insiders -n f:/code-editor", "type": "powershellCommand", "icon": "project" },
            { "label": "dev notes", "path": "code-insiders -n f:/dev-notes", "type": "powershellCommand", "icon": "project" },
            {
              "label": "TO DO, NOTES, AND THINGS",
              "expanded": false,
              "type": "folder",
              "global": true,
              "items": [
                { "label": "Notes, To-Do And Things", "path": "code-insiders -n f:/ntrsync", "type": "powershellCommand", "icon": "notebook" },
                { "label": "Notes, To-Do And Things", "path": "code-insiders -n f:/mobilenrcsync", "type": "powershellCommand", "icon": "device-mobile" },
                { "label": "Notes, To-Do And Things - Website", "path": "https://www.ntrsync.dedyn.io/login", "type": "url", "icon": "device-mobile" }
              ]
            },
            {
              "label": "STACKS & MONOREPO",
              "expanded": false,
              "type": "folder",
              "global": true,
              "items": [
                { "label": "bane stack", "type": "powershellCommand", "path": "code-insiders -n f:/bane", "icon": "project" },
                { "label": "create remixv2", "type": "powershellCommand", "path": "code-insiders -n f:/create-remixv2", "icon": "project" },
                { "label": "bane-stack-monorepo", "type": "powershellCommand", "path": "code-insiders -n f:/bane-stack-monorepo", "icon": "project" }
              ]
            }
          ]
        }
      ]
    },
    {
      "label": "CMDS",
      "expanded": true,
      "type": "folder",
      "global": true,
      "icon": "terminal",
      "items": [
        { "label": "Scan File Imports", "path": "ocrmnavigator.imports.file.scan", "type": "command", "icon": "terminal-cmd" },
        { "label": "Toggle Zen Mode", "path": "workbench.action.toggleZenMode", "type": "command", "icon": "game" },
        { "label": "SAVE ALL", "path": "workbench.action.files.saveAll", "type": "command", "icon": "save-all" },
        { "label": "Search Editor", "path": "ocrmnavigator.searchEditor.open", "type": "command", "icon": "search" },
        { "label": "Search VSCode", "path": "", "type": "search", "icon": "search" },
        { "label": "Format", "path": "formatfile, saveall", "type": "chain" },
        { "label": "1 DEV", "path": "saveall, killterms, startDevServer", "type": "chain", "icon": "debug-start", "tooltipText": "SINGLE KILL Terminals && Start DEV Server" },
        { "label": "2 DEV", "path": "saveall, killterms, devApp", "type": "chain", "icon": "debug-start", "tooltipText": "MONO KILL Terminals && Start DEV Server" },
        {
          "label": "MORE",
          "type": "folder",
          "expanded": false,
          "icon": "ellipsis",
          "items": [
            { "label": "1", "path": "editor.foldLevel1", "type": "command", "icon": "fold-down" },
            { "label": "2", "path": "editor.foldLevel2", "type": "command", "icon": "fold-down" },
            { "label": "3", "path": "editor.foldLevel3", "type": "command", "icon": "fold-down" },
            {
              "label": "JSON",
              "type": "folder",
              "expanded": false,
              "icon": "json",
              "items": [
                { "label": "Format .json", "path": "ocrmnavigator.project.json.file.format", "type": "command", "icon": "json" },
                { "label": "TGL Json Errors", "path": "ocrmnavigator.performanceSwitch.json.validate.toggle", "type": "command", "icon": "json" },
                { "label": "TGL Jsonc Errors", "path": "ocrmnavigator.performanceSwitch.jsonc.validate.toggle", "type": "command", "icon": "json" }
              ]
            },
            {
              "label": "FOLD",
              "type": "folder",
              "expanded": true,
              "icon": "fold-down",
              "items": [
                { "label": "UNFOLD All", "path": "editor.unfoldAll", "type": "command", "icon": "unfold" },
                { "label": "4", "path": "editor.foldLevel4", "type": "command", "icon": "fold-down" },
                { "label": "5", "path": "editor.foldLevel5", "type": "command", "icon": "fold-down" },
                { "label": "6", "path": "editor.foldLevel6", "type": "command", "icon": "fold-down" },
                { "label": "7", "path": "editor.foldLevel7", "type": "command", "icon": "fold-down" }
              ]
            },
            {
              "label": "TOGGLE",
              "type": "folder",
              "expanded": true,
              "icon": "fold-down",
              "items": [
                { "label": "TGL #R 1", "path": "ocrmnavigator.vscode.region.1.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 2", "path": "ocrmnavigator.vscode.region.2.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 3", "path": "ocrmnavigator.vscode.region.3.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 4", "path": "ocrmnavigator.vscode.region.4.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 5", "path": "ocrmnavigator.vscode.region.5.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 6", "path": "ocrmnavigator.vscode.region.6.toggle", "type": "command", "icon": "fold-down" },
                { "label": "TGL #R 7", "path": "ocrmnavigator.vscode.region.7.toggle", "type": "command", "icon": "fold-down" }
              ]
            },
            {
              "label": " VSCODE CMDS",
              "type": "folder",
              "expanded": false,
              "icon": "json",
              "items": [
                { "label": "Window", "path": "formatfile, saveall, reloadWindow", "type": "chain", "icon": "debug-restart", "tooltipText": "Reload Window" },
                { "label": "Terminals", "path": "workbench.action.terminal.killAll", "type": "command", "icon": "debug-stop" },
                { "label": "editors", "path": "saveall, closeeditors", "type": "chain", "icon": "close" },
                { "label": "toggle 💻", "path": "workbench.action.terminal.toggleTerminal", "type": "command", "icon": "unfold" },
                { "label": "TS", "path": "formatfile, saveall, reloadWindow", "type": "chain", "icon": "refresh", "tooltipText": "Reload Window" },
                { "label": "DevTools", "path": "formatfile, saveall, reloadWindow", "type": "chain", "icon": "tools", "tooltipText": "Open DevTools" },
                { "label": "Kill PORT 3000", "path": "killPort3000", "type": "command", "icon": "x" }
              ]
            }
          ]
        },
        {
          "label": "MONOREPO",
          "type": "folder",
          "expanded": false,
          "items": [
            { "label": "dev:all", "path": "devApp, devCalc", "type": "concurrent" },
            { "label": "nuclear:all", "path": "nuclear:all", "type": "powershellCommand" },
            { "label": "dev:app", "path": "saveall, killterms, devApp", "type": "chain" },
            { "label": "patch:app", "path": "cd apps/app && git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags && cd ../..", "type": "powershellCommand" },
            { "label": "db:app", "path": "cd apps/app && pnpm run db:all && cd ../..", "type": "powershellCommand" },
            { "label": "clean:app", "path": "cd apps/app && foreach ($path in @('.cache', 'build', 'node_modules', 'pnpm-lock.yaml', 'public\\build' )) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } } && cd ../..", "type": "powershellCommand" },
            { "label": "clean:all", "path": "cleanApp, cleanProd, cleanCalc, cleanRoot", "type": "concurrent" },
            { "label": "i:all", "path": "iapp, iProd, iRoot, iCalc", "type": "concurrent" },
            { "label": "build:all", "path": "buildapp, buildProd, buildCalc", "type": "concurrent" },
            { "label": "patch:all", "path": "patchRoot, patchapp, patchProd, patchCalc", "type": "concurrent" },
            { "label": "push:all", "path": "pushCalc, pushProd, pushApp, pushRoot", "type": "concurrent" },
            { "label": "db:all local", "path": "saveall, dbAllLocal, dbCalc, dbApp", "type": "chain" },
            { "label": "db:all remote", "path": "saveall, dbAllRemote, dbCalc, dbApp", "type": "chain" },
            { "label": "db:prod", "path": "cd apps/prod && pnpm run db:all && cd ../..", "type": "powershellCommand" },
            { "label": "gen:all", "path": "genCalc, genApp", "type": "concurrent" },
            { "label": "gen:prod", "path": "cd apps/prod && pnpm run db:gen && cd ../..", "type": "powershellCommand" }
          ]
        },
        {
          "label": "SINGLE REPO",
          "type": "folder",
          "expanded": false,
          "items": [
            { "label": "dev", "path": "saveall, killterms, singlestrdev", "type": "chain" },
            { "label": "patch", "path": "saveall, singlestrpatch", "type": "chain" },
            { "label": "db:all local", "path": "saveall, killterms, dbAllLocal", "type": "chain" },
            { "label": "db:all remote", "path": "saveall, killterms, dbAllRemote", "type": "chain" },
            { "label": "i", "path": "saveall, killterms, terminalInstall", "type": "chain" },
            { "label": "fromScratch", "path": "saveall, killterms, singlestrfromScratch", "type": "chain" },
            { "label": "build", "path": "saveall, killterms, runBuild", "type": "chain" },
            { "label": "start", "path": "saveall, killterms, runStart", "type": "chain" },
            { "label": "clean", "path": "saveall, killterms, singlestrclean", "type": "chain" },
            { "label": "i:shadCN", "path": "saveall, killterms, singlestrshadCN", "type": "chain" },
            { "label": "i:component", "path": "saveall, killterms, singlestrcomponent", "type": "chain" },
            { "label": "db:gen", "path": "saveall, killterms, prismaGenerate", "type": "chain" },
            { "label": "db:seed", "path": "saveall, killterms, singlestrdbseed", "type": "chain" },
            { "label": "db:studio", "path": "singlestrdbstudio", "type": "chain" }
          ]
        },
        {
          "label": "DIVIDERS",
          "expanded": false,
          "type": "folder",
          "global": true,
          "items": [
            [
              { "label": "━━━━ ● ━━━━ ● ━━━━", "type": "label", "icon": "circle-dot" },
              { "label": "★ ━━━━ ☆ ━━━━ ━━━━ ☆ ━━━━", "type": "label", "icon": "star" },
              { "label": "━━━━ ◆ ━━━━ ◆ ━━━━ ◆ ━━━━ ◆ ━━━━", "type": "label", "icon": "diamond" },
              { "label": "━━━━ ☆ ━━━━━━━━━━━━━", "type": "label", "icon": "minus" },
              { "label": "═══════════════════", "type": "label", "icon": "grip-horizontal" },
              { "label": "▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬", "type": "label", "icon": "maximize-2" },
              { "label": "▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓", "type": "label", "icon": "grid-3x3" },
              { "label": "░░░░░░░░░░░░░░░░░░░░", "type": "label", "icon": "grid" },
              { "label": "┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄", "type": "label", "icon": "more-horizontal" },
              { "label": "┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈", "type": "label", "icon": "more-horizontal" },
              { "label": "┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉┉", "type": "label", "icon": "menu" },
              { "label": "━ ━ ━ ━ ━ ━ ━ ━ ━ ━", "type": "label", "icon": "minus" },
              { "label": "─ ─ ─ ─ ─ ─ ─ ─ ─ ─", "type": "label", "icon": "minus" },
              { "label": "● ● ● ● ● ● ● ● ● ●", "type": "label", "icon": "circle" },
              { "label": "○ ○ ○ ○ ○ ○ ○ ○ ○ ○", "type": "label", "icon": "circle" },
              { "label": "• • • • • • • • • •", "type": "label", "icon": "more-horizontal" },
              { "label": "★ ★ ★ ★ ★ ★ ★ ★ ★ ★", "type": "label", "icon": "star" },
              { "label": "☆ ☆ ☆ ☆ ☆ ☆ ☆ ☆ ☆ ☆", "type": "label", "icon": "star" },
              { "label": "◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆", "type": "label", "icon": "diamond" },
              { "label": "◇ ◇ ◇ ◇ ◇ ◇ ◇ ◇ ◇ ◇", "type": "label", "icon": "diamond" },
              { "label": "■ ■ ■ ■ ■ ■ ■ ■ ■ ■", "type": "label", "icon": "square" },
              { "label": "□ □ □ □ □ □ □ □ □ □", "type": "label", "icon": "square" },
              { "label": "▪ ▪ ▪ ▪ ▪ ▪ ▪ ▪ ▪ ▪", "type": "label", "icon": "square" },
              { "label": "▫ ▫ ▫ ▫ ▫ ▫ ▫ ▫ ▫ ▫", "type": "label", "icon": "square" },
              { "label": "→ → → → → → → → → →", "type": "label", "icon": "arrow-right" },
              { "label": "⇒ ⇒ ⇒ ⇒ ⇒ ⇒ ⇒ ⇒ ⇒ ⇒", "type": "label", "icon": "chevrons-right" },
              { "label": "➜ ➜ ➜ ➜ ➜ ➜ ➜ ➜ ➜ ➜", "type": "label", "icon": "arrow-right" },
              { "label": "← ← ← ← ← ← ← ← ← ←", "type": "label", "icon": "arrow-left" },
              { "label": "⬅ ⬅ ⬅ ⬅ ⬅ ⬅ ⬅ ⬅ ⬅ ⬅", "type": "label", "icon": "arrow-left" },
              { "label": "╭──────────────────╮", "type": "label", "icon": "corner-up-right" },
              { "label": "╰──────────────────╯", "type": "label", "icon": "corner-down-right" },
              { "label": "╒══════════════════╕", "type": "label", "icon": "frame" },
              { "label": "╘══════════════════╛", "type": "label", "icon": "frame" },
              { "label": "╓──────────────────╖", "type": "label", "icon": "frame" },
              { "label": "╙──────────────────╜", "type": "label", "icon": "frame" },
              { "label": "▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀", "type": "label", "icon": "align-justify" },
              { "label": "▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄", "type": "label", "icon": "align-justify" },
              { "label": "▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌▌", "type": "label", "icon": "align-left" },
              { "label": "▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐▐", "type": "label", "icon": "align-right" },
              { "label": "… … … … … … … …", "type": "label", "icon": "more-horizontal" },
              { "label": "· · · · · · · · · ·", "type": "label", "icon": "more-horizontal" },
              { "label": "━━━ ➔ ━━━", "type": "label", "icon": "arrow-right-circle" },
              { "label": "═══ ⇒ ═══", "type": "label", "icon": "fast-forward" },
              { "label": "● ━━━━ ☆ ━━━━━━━━━ ●", "type": "label", "icon": "circle-dot" },
              { "label": "★ ━━━━ ☆ ━━━━━━━━━ ★", "type": "label", "icon": "sparkles" },
              { "label": "┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊┊", "type": "label", "icon": "separator-vertical" },
              { "label": "┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋┋", "type": "label", "icon": "separator-vertical" },
              { "label": "‖ ‖ ‖ ‖ ‖ ‖ ‖ ‖ ‖ ‖", "type": "label", "icon": "pause" },
              { "label": " → ← ↑ ↓ ⇒ ⇐ ← → ➔ ➜ ➞ ➡ ⇒ ⟹ ⬅ ⇐ ⟸ ⬆ ⇑ ⬇ ⇓ ↓↑", "type": "label", "icon": "three-bars" },
              { "label": "╒ ╓ ╕ ╖ ╘ ╙ ╛ ╜ ╭ ╮ ╰ ╯ ", "type": "label", "icon": "three-bars" },
              { "label": " ┄ ┅ ┆ ┇ ┈ ┉ ┊ ┋ ", "type": "label", "icon": "three-bars" },
              { "label": " □ ▪ ▫ ● ○ ◆ ◇ ★ ☆", "type": "label", "icon": "three-bars" },
              { "label": "• · … ― ‖ • · … ― ‖ ", "type": "label", "icon": "three-bars" },
              { "label": " ▀ ▄ █ ░ ▒ ▓ ▌ ▐ ■", "type": "label", "icon": "three-bars" }
            ]
          ]
        },
        {
          "label": "HIDDEN",
          "expanded": false,
          "type": "folder",
          "global": true,
          "hidden": true,
          "items": [
            { "label": "gen2tsU", "path": "bun ./updaters/gen2.ts", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "BuildCatalystFunctionsU", "path": "bun ./updaters/build-catalyst-functions.ts", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "MDPreProcessor", "path": "ocrmnavigator.md.convertReadme", "type": "command", "icon": "markdown", "hidden": true },
            { "label": "pro7", "path": "ocrmnavigator.pro7.acrhive", "type": "command", "icon": "json", "hidden": true },
            { "label": "CopyAndRenameFilesps1U", "path": "powershell ./updaters/CopyAndRenameFiles.ps1", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "generateiconinventoryjsU", "path": "node ./updaters/generate-icon-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "generateuiinventoryjsU", "path": "node ./updaters/generate-ui-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "iconlibraryinventoryjsU", "path": "node ./updaters/icon-library-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "updatepromptfrommdU", "path": "node ./updaters/update-prompt-from-md.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "Buildpkgjson", "path": "ocrmnavigator.project.pkg.format", "type": "command", "icon": "json", "hidden": true },
            { "label": "CreatekgJsonCommandsQpMenu", "path": "ocrmnavigator.menu.items.pkg.scan.convert.items", "type": "command", "icon": "three-bars", "hidden": true },
            { "label": "↓↓ DOES NOT WORK ↓↓", "path": "saveall", "type": "command", "hidden": true },
            { "label": "pro7 - AR", "path": "node ./src/autorun/pro7.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "MD Pre-Processor - AR", "path": "node ./src/autorun/markdown-pre-processor.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "Build pkg.json - AR", "path": "node ./src/autorun/build-package-json.js", "type": "powershellCommand", "icon": "terminal-powershell", "hidden": true },
            { "label": "pnpmrunbuild", "path": "pnpm run build", "type": "powershellCommand", "icon": "versions", "hidden": true },
            { "label": "pnpmrungenerate", "path": "pnpm run generate", "type": "powershellCommand", "icon": "versions", "hidden": true },
            { "label": "Bump Patch", "path": "saveall, PatchVersion", "type": "chain", "icon": "versions", "hidden": true },
            { "label": "PatchVersion", "path": "ocrmnavigator.version.patch", "type": "command", "icon": "versions", "hidden": true },
            { "label": "compileWIthPackager", "path": "ocrmnavigator.project.compile", "type": "command", "icon": "archive", "hidden": true },
            { "label": "await5Secs", "path": "ocrmnavigator.await.5", "type": "command", "icon": "markdown", "hidden": true },
            { "label": "await4Secs", "path": "ocrmnavigator.await.4", "type": "command", "icon": "markdown", "hidden": true },
            { "label": "await3Secs", "path": "ocrmnavigator.await.3", "type": "command", "icon": "markdown", "hidden": true },
            { "label": "await1Secs", "path": "ocrmnavigator.await.1", "type": "command", "icon": "markdown", "hidden": true },
            { "label": "await2Secs", "path": "ocrmnavigator.await.2", "type": "command", "hidden": true },
            { "label": "reloadWindow", "path": "workbench.action.reloadWindow", "type": "command", "hidden": true },
            { "label": "generateAndBuild", "path": "ocrmnavigator.project.compile", "type": "command", "hidden": true },
            { "label": "genCalc", "path": "cd apps/calc && npx prisma generate && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "genApp", "path": "cd apps/app && npx prisma generate && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "dbCalc", "path": "cd apps/calc && npx tsx prisma/pre-seed.ts && npx prisma db push --force-reset && npx prisma db push && npx tsx prisma/seed.ts && npx prisma generate && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "dbApp", "path": "cd apps/app && npx tsx prisma/pre-seed.ts && npx prisma db push --force-reset && npx prisma db push && npx tsx prisma/seed.ts && npx prisma generate && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "devApp", "path": "cd apps/app && pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "devCalc", "path": "cd apps/calc && pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "pushRoot", "path": "git add * && git commit -m \"Cleaning w/ push\" && git push", "type": "powershellCommand", "hidden": true },
            { "label": "pushApp", "path": "cd apps/app && git add * && git commit -m \"Cleaning w/ push\" && git push && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "pushProd", "path": "cd apps/prod && git add * && git commit -m \"Cleaning w/ push\" && git push && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "pushCalc", "path": "cd apps/calc && git add * && git commit -m \"Cleaning w/ push\" && git push && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "patchRoot", "path": "git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags", "type": "powershellCommand", "hidden": true },
            { "label": "patchapp", "path": "cd apps/app && git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "patchProd", "path": "cd apps/prod && git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "patchCalc", "path": "cd apps/calc && git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "buildapp", "path": "cd apps/app && pnpm run build && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "buildProd", "path": "cd apps/prod && pnpm run build && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "buildCalc", "path": "cd apps/calc && pnpm run build && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "iRoot", "path": "pnpm i --prefer-offline --no-cache", "type": "powershellCommand", "hidden": true },
            { "label": "iapp", "path": "cd apps/app && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "iProd", "path": "cd apps/prod && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "iCalc", "path": "cd apps/calc && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "cleanRoot", "path": "foreach ($path in @('.cache', 'build', 'node_modules', 'pnpm-lock.yaml', 'public\\build' )) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }", "type": "powershellCommand", "hidden": true },
            { "label": "cleanApp", "path": "cd apps/app && foreach ($path in @('.cache', 'build', 'node_modules', 'pnpm-lock.yaml', 'public\\build' )) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }", "type": "powershellCommand", "hidden": true },
            { "label": "cleanProd", "path": "cd apps/prod && foreach ($path in @('.cache', 'build', 'node_modules', 'pnpm-lock.yaml', 'public\\build' )) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }", "type": "powershellCommand", "hidden": true },
            { "label": "cleanCalc", "path": "cd apps/calc && foreach ($path in @('.cache', 'build', 'node_modules', 'pnpm-lock.yaml', 'public\\build' )) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }", "type": "powershellCommand", "hidden": true },
            { "label": "iProd", "path": "cd apps/prod && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "iCalc", "path": "cd apps/calc && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "iApp", "path": "cd apps/app && pnpm install --ignore-workspace && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "devProd", "path": "cd apps/prod && pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "devCalc", "path": "cd apps/calc && pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "devApp", "path": "cd apps/app && pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "runBuild", "path": "ocrmnavigator.project.build", "type": "command", "hidden": true },
            { "label": "runStart", "path": "ocrmnavigator.project.start", "type": "command", "hidden": true },
            { "label": "singlestrclean", "path": "foreach ($path in @('.pnpm-cache','.pnpm-cache', 'node_modules', 'pnpm-lock.yaml', '.cache', 'public\\build', 'build')) { if (Test-Path $path) { Remove-Item -Path $path -Recurse -Force -ErrorAction SilentlyContinue } }", "type": "powershellCommand", "hidden": true },
            { "label": "singlestrshadCN", "path": "pnpm dlx shadcn@latest init", "type": "powershellCommand", "hidden": true },
            { "label": "singlestrcomponent", "path": "pnpm dlx shadcn@latest add", "type": "powershellCommand", "hidden": true },
            { "label": "prismaGenerate", "path": "ocrmnavigator.prisma.generate", "type": "command", "hidden": true },
            { "label": "prismaSeed", "path": "ocrmnavigator.prisma.seed", "type": "command", "hidden": true },
            { "label": "prismaStudio", "path": "ocrmnavigator.prisma.studio", "type": "command", "hidden": true },
            { "label": "singlestrfromScratch", "path": "str fromScratch", "type": "powershellCommand", "hidden": true },
            { "label": "terminalInstall", "path": "ocrmnavigator.project.install", "type": "command", "hidden": true },
            { "label": "dbAllLocal", "path": "ocrmnavigator.git.dbAllLocal", "type": "command", "hidden": true },
            { "label": "dbAllRemote", "path": "ocrmnavigator.git.dbAllRemote", "type": "command", "hidden": true },
            { "label": "prismaMigrateReset", "path": "ocrmnavigator.prisma.migrateReset", "type": "command", "hidden": true },
            { "label": "prismaReset", "path": "ocrmnavigator.prisma.reset", "type": "command", "hidden": true },
            { "label": "prismaPush", "path": "ocrmnavigator.prisma.push", "type": "command", "hidden": true },
            { "label": "singlestrdball", "path": "npx tsx prisma/pre-seed.ts && npx prisma db push --force-reset && npx prisma db push && npx tsx prisma/seed.ts && npx prisma generate", "type": "powershellCommand", "hidden": true },
            { "label": "singlestrpatch", "path": "git add * && git commit -m \"Cleaning w/ push\" && git push && pnpm version patch && git push && git push --tags", "type": "powershellCommand", "hidden": true },
            { "label": "singlestrdev", "path": "pnpm run dev", "type": "powershellCommand", "hidden": true },
            { "label": "generateroutes", "path": "pnpm run generate:routes", "type": "powershellCommand", "hidden": true },
            { "label": "methdbapp", "path": "cd apps/app && npx tsx prisma/pre-seed.ts && npx prisma db push --force-reset && npx prisma db push && npx tsx prisma/seed.ts && npx prisma generate && cd ../..", "type": "powershellCommand", "hidden": true },
            { "label": "killterms", "path": "workbench.action.terminal.killAll", "type": "command", "hidden": true },
            { "label": "startDevServer", "path": "ocrmnavigator.project.dev", "type": "command", "hidden": true },
            { "label": "saveall", "path": "workbench.action.files.saveAll", "type": "command", "hidden": true },
            { "label": "runbuildthendev", "path": "ocrmnavigator.project.build, ocrmnavigator.project.dev", "type": "cmdChain", "hidden": true },
            { "label": "plusversion", "path": "ocrmnavigator.git.add, ocrmnavigator.git.diffCached, ocrmnavigator.git.push, ocrmnavigator.version.patch, ocrmnavigator.git.push, ocrmnavigator.git.pushTags", "type": "cmdChain", "hidden": true },
            { "label": "commitpush", "path": "ocrmnavigator.git.add, ocrmnavigator.git.diffCached, ocrmnavigator.git.push", "type": "cmdChain", "hidden": true },
            { "label": "closeeditors", "path": "workbench.action.closeAllEditors", "type": "command", "hidden": true },
            { "label": "formatfile", "path": "editor.action.formatDocument", "type": "command", "hidden": true },
            { "label": "patchAndPublishToNPM", "type": "cmdChain", "path": "ocrmnavigator.git.add, ocrmnavigator.git.diffCached, ocrmnavigator.git.push, ocrmnavigator.version.patch, ocrmnavigator.git.push, ocrmnavigator.git.pushTags", "hidden": true },
            { "label": "npmPublishWithToken", "path": "npm publish --//registry.npmjs.org/:_authToken=${NPM_TOKEN}", "type": "powershellCommand", "hidden": true },
            { "label": "╒ ╓ ╕ ╖ ╘ ╙ ╛ ╜ ╭ ╮ ╰ ╯ ┄ ┅ ┆ ┇ ┈ ┉ ┊ ┋ ▀ ▄ █ ░ ▒ ▓ ▌ ▐ ■ □ ▪ ▫ ● ○ ◆ ◇ ★ ☆ → ← ↑ ↓ ⇒ ⇐ • · … ― ‖ ← → ➔ ➜ ➞ ➡ ⇒ ⟹ ⬅ ⇐ ⟸ ⬆ ⇑ ⬇ ⇓ ↓↑", "type": "label", "icon": "three-bars", "hidden": true }
          ]
        }
      ]
    },
    {
      "label": "UPDATERS",
      "type": "folder",
      "global": true,
      "expanded": false,
      "items": [
        { "label": "★ ━━━━ ☆ ━━━━ PROJECT ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "ICONS: Auto Build ", "path": "saveall, pnpmrungenerate, pnpmrunbuild, patchAndPublishToNPM", "type": "chain", "icon": "repo-push", "tooltipText": "One button does all to generate / build / update, compile, archive, push to github, push to npm " },
        { "label": "★ ━━━━ ☆ ━━━━ DEPENDENCIES ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "Update icons via pwrshell", "path": "pnpm update @catalystsoftware/icons", "type": "powershellCommand" },
        { "label": "★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆", "path": "ocrmnavigator.patchVersion", "type": "label", "icon": "chrome-minimize" },
        { "label": "Bump Patch", "path": "saveall, PatchVersion", "type": "chain", "icon": "versions" },
        { "label": "PkgJson+ → MDPP+ → CVSIX+ → INS", "path": "ocrmnavigator.order1", "type": "command", "icon": "versions", "tooltipText": "Build pkg.json → md pre-processer → build custom vsix → install" },
        { "label": "Commit And Push Current Dir", "path": "saveall, commitpush", "type": "chain", "icon": "repo-push" },
        { "label": "Patch and Publish to NPM", "path": "saveall, patchAndPublishToNPM", "type": "chain", "icon": "repo-push" },
        { "label": "★ ━━━━ ☆ ━━━━ EXECUTE ORDER ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "Order 1", "path": "ocrmnavigator.order1", "type": "command", "icon": "symbol-event", "tooltipText": "saveAll → pkg.dev.json → pkg.jsn → MD Pre-Proc → compile → +cvsix → install → R" },
        { "label": "Order 2", "path": "ocrmnavigator.order2", "type": "command", "icon": "symbol-event", "tooltipText": "order 1 → autorun" },
        { "label": "Order 3", "path": "ocrmnavigator.order3", "type": "command", "icon": "symbol-event", "tooltipText": "order 2 → updates all" },
        { "label": "Order 4", "path": "ocrmnavigator.order4", "type": "command", "icon": "symbol-event", "tooltipText": "order 2 → bump patch → build all projects → send vsix to marketplace" },
        { "label": "Order 5", "path": "ocrmnavigator.order5", "type": "command", "icon": "symbol-event", "tooltipText": "bum patch → md pre-processor → convert pkg.json → compile and archive → send vsix to marketplace" },
        { "label": "★ ━━━━ ☆ ━━━━ ARCHIVE ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "CVSIX", "path": "ocrmnavigator.project.compile", "type": "command", "icon": "archive" },
        { "label": "VSCE", "path": "vsce package", "type": "powershellCommand", "icon": "archive" },
        { "label": "pro7", "path": "ocrmnavigator.pro7.acrhive", "type": "command", "icon": "json" },
        { "label": "★ ━━━━ ☆ ━━━━ PROCESS FILE ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "PACKAGE.DEV.JSON: Build pkg.json", "path": "ocrmnavigator.project.pkg.format", "type": "command", "icon": "json" },
        { "label": "README.DEV.MD: MD Pre-Processor", "path": "ocrmnavigator.md.convertReadme", "type": "command", "icon": "markdown" },
        { "label": "MD: Update Prompt From md", "path": "node ./updaters/update-prompt-from-md.js", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "★ ━━━━ ☆ ━━━━ AUTORUN SCRIPTS ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "CATALYST-UI: Copy & Rename Files", "path": "powershell ./updaters/CopyAndRenameFiles.ps1", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "DEVSTACK: gen2 USE THIS TO BUILD DEVSTACKS FUNCTIONS", "path": "bun ./updaters/gen2.ts", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "DEVSTACK: Build Catalyst Functions", "path": "bun ./updaters/build-catalyst-functions.ts", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "DEVSTACK: Generate pkg.json cmds for quickpick menu items", "path": "ocrmnavigator.menu.items.pkg.scan.convert.items", "type": "command", "icon": "three-bars" },
        { "label": "DEVSTACK: Generate icons inventory", "path": "node ./updaters/generate-icon-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "DEVSTACK: Generate catalyst-ui inventory", "path": "node ./updaters/generate-ui-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "DEVSTACK: Generate icon library items for devstack functions", "path": "node ./updaters/icon-library-inventory.js", "type": "powershellCommand", "icon": "terminal-powershell" },
        { "label": "★ ━━━━ ☆ ━━━━ FULL AUTO ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "autorun.exe", "path": "ocrmnavigator.triggerAutorunFolder", "type": "command", "icon": "folder" },
        { "label": "updaters.exe", "path": "ocrmnavigator.autorun.updaters", "type": "command", "icon": "folder" },
        { "label": "Build All Extras", "path": "gen2tsU, BuildCatalystFunctionsU, MDPreProcessor, pro7, CopyAndRenameFilesps1U, generateiconinventoryjsU, generateuiinventoryjsU, iconlibraryinventoryjsU, updatepromptfrommdU, Buildpkgjson, CreatekgJsonCommandsQpMenu", "type": "chain", "icon": "folder", "tooltipText": "MD Pre-Processor → Build pkg json → update prompt from md → icon library inventory js → generate ui inventory js → Copy And Rename Files ps1 → pro7 → Build Catalyst Functions → gen2 → Create Pkg Json Commands QpMenu" }
      ]
    },
    {
      "label": "SETTINGS",
      "expanded": false,
      "type": "folder",
      "global": true,
      "icon": "settings",
      "items": [
        { "label": "Tasks", "path": "ocrmnavigator.vfs.tasks", "type": "settingsToggle", "icon": "settings" },
        { "label": "NPM Scripts", "path": "ocrmnavigator.vfs.npmScripts", "type": "settingsToggle", "icon": "settings" },
        {
          "label": "ARCHIVER",
          "path": "ocrmnavigator.ARCHIVER",
          "type": "settingsToggle",
          "args": [
            "custom",
            "vsce"
          ],
          "icon": "settings"
        },
        { "label": "UPDATE_PROMPT_OBJECTS", "path": "ocrmnavigator.UPDATE_PROMPT_OBJECTS", "type": "settingsToggle", "icon": "settings" },
        { "label": "AUTORUN_SCRIPTS", "path": "ocrmnavigator.AUTORUN_SCRIPTS", "type": "settingsToggle", "icon": "settings" },
        { "label": "CONVERT_README_DEV_MD", "path": "ocrmnavigator.CONVERT_README_DEV_MD", "type": "settingsToggle", "icon": "settings" },
        { "label": "PRO7", "path": "ocrmnavigator.PRO7", "type": "settingsToggle", "icon": "settings" },
        { "label": "DELETE_OLD_VSIX", "path": "ocrmnavigator.DELETE_OLD_VSIX", "type": "settingsToggle", "icon": "settings" },
        { "label": "AUTO_INSTALL_VSIX", "path": "ocrmnavigator.AUTO_INSTALL_VSIX", "type": "settingsToggle", "icon": "settings" },
        { "label": "OPEN_PUB_DASH", "path": "ocrmnavigator.OPEN_PUB_DASH", "type": "settingsToggle", "icon": "settings" },
        { "label": "RELOAD_INSTANCE", "path": "ocrmnavigator.RELOAD_INSTANCE", "type": "settingsToggle", "icon": "settings" },
        { "label": "AUTO_FOLD_PKG", "path": "ocrmnavigator.AUTO_FOLD_PKG", "type": "settingsToggle", "icon": "settings" },
        { "label": "BE_QP", "path": "ocrmnavigator.BE_QP", "type": "settingsToggle", "icon": "settings" }
      ]
    },
    {
      "label": "FILES",
      "type": "folder",
      "expanded": false,
      "global": true,
      "icon": "file",
      "items": [
        {
          "label": "CONFIGS",
          "expanded": false,
          "type": "folder",
          "global": true,
          "icon": "gear",
          "items": [
            { "label": "global-navigator-config backup", "path": "F:\\devstackBackUp\\global-navigator-config.json", "type": "file", "icon": "settings", "tooltipText": "" },
            { "label": "global-navigator-config USER", "path": "C:\\Users\\skyle\\AppData\\Roaming\\Code - Insiders\\User\\globalStorage\\skyler.ocrmnav\\global-navigator-config.json", "type": "file", "icon": "settings", "tooltipText": "" },
            { "label": "DevStack WS Config", "path": "C:\\Users\\skyle\\AppData\\Roaming\\Code - Insiders\\User\\globalStorage\\skyler.ocrmnav\\project-configs\\project-1744496862041-y866zpqtd9.json", "type": "file", "icon": "settings", "tooltipText": "" },
            { "label": "Catalyst-ui WS Config", "path": "C:\\Users\\skyle\\AppData\\Roaming\\Code - Insiders\\User\\globalStorage\\skyler.ocrmnav\\project-configs\\project-1757010936487-i30yr98a4p7.json", "type": "file", "icon": "settings", "tooltipText": "" }
          ]
        },
        { "label": "README.dev.md", "path": "README.dev.md", "type": "file", "icon": "markdown" },
        { "label": "README.md", "path": "README.md", "type": "file", "icon": "markdown" },
        { "label": "package.dev.jsonc", "path": "package.dev.jsonc", "type": "file", "icon": "json" },
        { "label": "package.json", "path": "package.json", "type": "file", "icon": "json" },
        { "label": "prisma.schema", "path": "prisma/prisma.schema", "type": "file" },
        { "label": "seed.ts", "path": "prisma/seed.ts", "type": "file" },
        { "label": "seed.ts", "path": "prisma/seed.ts:425", "type": "fileAtLine" }
      ]
    },
    {
      "label": "PROMPT",
      "expanded": false,
      "type": "folder",
      "global": true,
      "icon": "markdown",
      "items": [
        { "label": "Prompt - Reusable Comps", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - Templates", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - UI Lib Objs", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - Blocks", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - VSCode Extension", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - Remix-Run", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Prompt - Default", "path": "", "type": "copyValue", "icon": "markdown" }
      ]
    },
    {
      "label": "OTHER",
      "expanded": false,
      "type": "folder",
      "global": true,
      "items": [
        { "label": "Manage VS Extensions", "path": "https://marketplace.visualstudio.com/manage/publishers/skyler?auth_redirect=True", "type": "url" },
        { "label": "VLC w/ playlist", "path": "cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' 1Firreee.xspf", "type": "debianCMD" },
        { "label": "PGAdmin", "path": "& \"c:/Program Files/PostgreSQL/16/pgAdmin 4/runtime/pgAdmin4.exe\"", "type": "powershellCommand" },
        { "label": "PWSH - Admin", "path": "Start-Process powershell -Verb RunAs", "type": "powershellCommand" },
        { "label": "Libre - Draw", "path": "& \"c:/Program Files/LibreOffice/program/sdraw.exe\"", "type": "powershellCommand" },
        { "label": "🌐 Mixes", "path": "https://www.youtube.com/watch?v=KuvaMUDaS-4&list=PLYHhlbShmci2VzDsrtVwMIEx1vBYVk6bj&index=1", "type": "url" },
        { "label": "shad", "path": "https://ui.shadcn.com/docs/components/accordion", "type": "url" },
        { "label": "shad github examples", "path": "https://github.com/shadcn-ui/ui/tree/main/apps/www/app/(app)/examples", "type": "url" },
        { "label": "lucide", "path": "https://lucide.dev/icons/", "type": "url" },
        { "label": "vercel", "path": "https://vercel.com/eights-projects", "type": "url" },
        { "label": "radix", "path": "https://www.radix-ui.com/primitives/docs/components/dialog", "type": "url" },
        { "label": "gmail", "path": "https://mail.google.com/mail/u/0/#all", "type": "url", "filePath": "https://mail.google.com/mail/u/0/#all" }
      ]
    },
    {
      "label": "EXAMPLES",
      "expanded": false,
      "type": "folder",
      "global": true,
      "items": [
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "Build and Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "onSuccess", "executeChain": "deploy, notify" },
            { "type": "onFailure", "executeChain": "rollback, alert" }
          ]
        },
        {
          "label": "Conditional Build",
          "path": "lint, test, build",
          "type": "conditionalChain",
          "args": [
            { "type": "itemSuccess", "itemLabel": "test", "executeChain": "deploy" }
          ]
        },
        {
          "label": "Environment-Based Deploy",
          "path": "build",
          "type": "conditionalChain",
          "args": [
            { "type": "configValue", "configKey": "ocrmnavigator.environment", "operator": "equals", "value": "production", "executeChain": "deployProd" },
            { "type": "configValue", "configKey": "ocrmnavigator.environment", "operator": "equals", "value": "staging", "executeChain": "deployStaging" }
          ]
        },
        {
          "label": "Conditional Install",
          "path": "checkDeps",
          "type": "conditionalChain",
          "args": [
            { "type": "fileNotExists", "filePath": "node_modules", "executeChain": "npmInstall" }
          ]
        },
        {
          "label": "Build with Cleanup",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "always", "executeChain": "cleanup, logResults" }
          ]
        },
        {
          "label": "Advanced Conditional",
          "path": "task1, task2, task3",
          "type": "conditionalChain",
          "args": [
            { "type": "custom", "expression": "results.filter(r => r.success).length >= 2", "executeChain": "partialSuccessHandler" }
          ]
        },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "Build with CI",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        { "label": "ciDeploy", "path": "dockerBuild, pushToRegistry, deployToK8s", "type": "chain" },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" },
            { "type": "itemSuccess", "itemLabel": "ciDeploy", "executeChain": "deployStaging" }
          ]
        },
        {
          "label": "CI/CD Deploy",
          "path": "build, test",
          "type": "conditionalChain",
          "args": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true", "executeChain": "ciDeploy" }
          ]
        },
        {
          "label": "ciDeploy",
          "path": "dockerBuild, pushToRegistry",
          "type": "conditionalChain",
          "args": [
            { "type": "onSuccess", "executeChain": "deployStaging" }
          ]
        },
        {
          "type": "combined",
          "logic": "AND",
          "conditions": [
            { "type": "envVariable", "envKey": "CI", "operator": "equals", "value": "true" },
            { "type": "onSuccess" }
          ],
          "executeChain": "ciDeploy"
        },
        { "label": "README.dev.md", "path": "README.dev.md", "type": "file", "icon": "markdown" },
        { "label": "Manage VS Extensions", "path": "https://marketplace.visualstudio.com/manage/publishers/skyler?auth_redirect=True", "type": "url" },
        { "label": "Scan File Imports", "path": "ocrmnavigator.imports.file.scan", "type": "command", "icon": "terminal-cmd" },
        { "label": "CRM", "path": "code-insiders -n f:/OpinionatedCRM", "type": "powershellCommand", "icon": "project" },
        { "label": "VLC w/ playlist", "path": "cd /mnt/f/music && '/mnt/c/Program Files/VideoLAN/VLC/vlc.exe' 1Firreee.xspf", "type": "debianCMD" },
        { "label": "Format", "path": "formatfile, saveall", "type": "chain" },
        { "label": "Format", "path": "formatfile, saveall", "type": "concurrent" },
        { "label": "★ ━━━━ ☆ ━━━━ AUTORUN SCRIPTS ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
        { "label": "★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆", "type": "label", "icon": "chrome-minimize" },
        { "label": "Prompt - Reusable Comps", "path": "", "type": "copyValue", "icon": "markdown" },
        { "label": "Tasks", "path": "ocrmnavigator.vfs.tasks", "type": "settingsToggle", "icon": "settings" },
        {
          "label": "ARCHIVER",
          "path": "ocrmnavigator.ARCHIVER",
          "type": "settingsToggle",
          "args": [
            "custom",
            "vsce"
          ],
          "icon": "settings"
        },
        {
          "label": "Create User",
          "path": "https://api.example.com/users",
          "args": [
            { "method": "POST" },
            { "headers": { "Content-Type": "application/json", "Authorization": "Bearer YOUR_TOKEN" } },
            { "body": { "name": "John Doe", "email": "john@example.com" } }
          ],
          "type": "apiCall",
          "icon": "person-add",
          "tooltipText": ""
        },
        {
          "label": "Deploy to Production",
          "path": "https://hooks.example.com/deploy",
          "args": [
            { "method": "POST" },
            { "body": { "branch": "main", "environment": "production" } }
          ],
          "type": "apiCall",
          "icon": "rocket"
        },
        {
          "label": "List Repos",
          "path": "https://api.github.com/users/yourname/repos",
          "args": [
            { "headers": { "Accept": "application/vnd.github.v3+json", "Authorization": "token YOUR_GITHUB_TOKEN" } }
          ],
          "type": "apiCall",
          "icon": "github",
          "tooltipText": ""
        },
        {
          "label": "Restart Dev Server",
          "path": "http://localhost:3000/api/restart",
          "args": [
            { "method": "POST" }
          ],
          "type": "apiCall",
          "icon": "debug-restart",
          "tooltipText": ""
        }
      ]
    },
        {
      "label": "LAYOUTS",
      "expanded": false,
      "type": "folder",
      "global": false,
      "items": [
        {
          "$schema": "./schemas/layout-config-schema.json",
          "label": "DevStack Default",
          "path": "",
          "type": "layout",
          "icon": "editor-layout",
          "args": [
            {
              "default": true,
              "editorGrid": {
                "orientation": 0,
                "version": "classic",
                "editorFocus": "last",
                "groups": [
                  { "size": 0.2 },                  
                  { "size": 0.45 },
                  { "size": 0.45 }
                ],
                "files": [
                  { "path": ".vscode/ntrsync/10516_DevStack_todo.md", "group": 1, "pinned": true },
                  {
                    "group": 2,
                    "pinned": true,
                    "foldLevel": [1,2],
                    "path": [
                      "src/extension.ts",
                      "src/helpers/master.ts",
                      "src/helpers/menus.ts",
                      "src/context.ts",
                      "src/helpers/search.ts",
                      "src/extension/navigatorView.ts",
                      "src/helpers/itemsActionsMenu.ts"
                    ]
                  },
                  {
                    "group": 3,
                    "pinned": true,
                       "foldLevel": [1,2],
                    "path": [
                      "README.dev.md",
                      "package.dev.jsonc",
                      "F:/DevStack/docs/LAYOUT.md",
                      "src/helpers/search.ts",
                      "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/project-configs/project-1744496862041-y866zpqtd9.json",
                      "C:/Users/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/global-navigator-config.json"
                    ]
                  }
                ]
              },
              "terminalGrid": {
                "orientation": 0,
                "version": "classic",
                "terminals": [
                  {
                    "name": "Top-Left (API)",
                    "group": 1,
                    "cmd": "echo 'right'",
                    "location": "editor",
                    "priority": 1
                  },
                  {
                    "name": "Top-Right (UI)",
                    "group": 2,
                    "cmd": "echo 'right'",
                    "location": "editor",
                    "priority": 1
                  }
                ]
              },
              "keybindings": {
                "ocrmnavigator.menu.devstack": "alt+d",
                "ocrmnavigator.searchEditor.open": "alt+s",
                "ocrmnavigator.menu.icons": "alt+i",
                "ocrmnavigator.menu.catalystUi": "alt+u",
                "ocrmnavigator.menu.snippets": "alt+f",
                "ocrmnavigator.region.insert": "alt+r",
                "ocrmnavigator.endregion.insert": "alt+e",
                "ocrmnavigator.region.wrap": "alt+w",
                "ocrmnavigator.devstack.site.colorWheel": "alt+q",
                "ocrmnavigator.clipboardMgr.history.show": "alt+h",
                "ocrmnavigator.bookmarks.show": "alt+b",
                "ocrmnavigator.menu.github": "alt+g",
                "ocrmnavigator.project.pkg.open": "alt+p",
                "ocrmnavigator.project.readme.open": "alt+m"
              },
              "autorun": [
                {
                  "runPolicy": "once",
                  "label": "test",
                  "path": "echo 'autorun'",
                  "type": "powershellCommand"
                }
              ],
              "onClose": [
                {
                  "label": "npm run dev",
                  "path": "echo 'onClose'",
                  "type": "powershellCommand"
                }
              ],
              "git": {
                "branch": "dev",
                "onLoad": [
                  {
                    "label": "pnpm i & ini / push prisma & ini .env & run scaffolding",
                    "path": "echo 'git on load'",
                    "type": "powershellCommand"
                  }
                ],
                "onClose": [
                  {
                    "label": "pnpm i & ini / push prisma & ini .env & run scaffolding",
                    "path": "echo 'git on close'",
                    "type": "powershellCommand"
                  }
                ]
              },
              "performance": {
                "css.validate": false,
                "diffEditor.codeLens": false,
                "debug.openDebug": "neverOpen",
                "debug.toolBarLocation": "hidden",
                "debug.showInStatusBar": "never",
                "editor.inlineSuggest.enabled": false,
                "editor.inlayHints.enabled": "off",
                "editor.parameterHints.enabled": false,
                "editor.suggestOnTriggerCharacters": false,
                "editor.acceptSuggestionOnEnter": "off",
                "editor.acceptSuggestionOnCommitCharacter": false,
                "editor.wordBasedSuggestions": "off",
                "editor.formatOnType": false,
                "editor.formatOnPaste": false,
                "editor.formatOnSave": false,
                "editor.semanticHighlighting.enabled": true,
                "editor.occurrencesHighlight": "off",
                "editor.selectionHighlight": true,
                "editor.codeLens": false,
                "editor.lightbulb.enabled": "onCode",
                "eslint.enable": true,
                "extensions.showRecommendationsOnlyOnDemand": true,
                "extensions.autoUpdate": false,
                "extensions.ignoreRecommendations": true,
                "files.watcherExclude": {},
                "files.exclude": {},
                "files.maxMemoryForLargeFilesMB": 4096,
                "git.decorations.enabled": false,
                "git.diffEditor.renderGutterMenu": false,
                "git.mergeEditor.codeLens.enabled": false,
                "github.copilot.enable": {
                  "*": false,
                  "plaintext": true,
                  "markdown": false,
                  "scminput": false
                },
                "github.copilot.nextEditSuggestions.allowWhitespaceOnlyChanges": false,
                "github.copilot.chat.agent.thinkingTool": true,
                "Codegeex.Chat.LanguagePreference": "English",
                "Codegeex.GenerationPreference": "line by line",
                "Codegeex.Privacy": false,
                "Codegeex.License": "",
                "codegeex.codeLens.functionQuickOptions": {
                  "addComment": false,
                  "ghostComment": false,
                  "fixBug": false,
                  "generateUnitTest": false,
                  "reviewCode": false,
                  "codeOptimization": false,
                  "addDocString": false,
                  "addExceptionHandling": false,
                  "printLogForDebugging": false,
                  "improveRunningEfficiency": false,
                  "renameSymbols": false,
                  "newFileForDebugging": false,
                  "tryANewApproach": false,
                  "explainCode": false
                },
                "codegeex.codeLens.classQuickOptions": {
                  "explainCode": false,
                  "ghostComment": false,
                  "fixBug": false,
                  "generateUnitTest": false,
                  "reviewCode": false,
                  "addDocStringForClass": false,
                  "addDocStringForMethods": false,
                  "addComment": false
                },
                "geminicodeassist.chat.changeView": "Default diff view",
                "geminicodeassist.displayInlineContextHint": false,
                "geminicodeassist.enableTelemetry": false,
                "geminicodeassist.inlineSuggestions.enableAuto": false,
                "geminicodeassist.localCodebaseAwareness": false,
                "html.validate.scripts": false,
                "jsonc.validate.enable": true,
                "json.validate.enable": true,
                "merge-conflict.codeLens.enabled": false,
                "multiDiffEditor.experimental.enabled": false,
                "markdown.validate.enable": false,
                "markdown.preview.automaticPreview": "never",
                "markdown.preview.fontSize": 12,
                "markdown.validate.enabled": false,
                "markdown.updateLinksOnFileMove.enabled": "never",
                "markdown.editor.pasteUrlAsFormattedLink.enabled": "always",
                "markdown.extension.print.theme": "dark",
                "markdown.extension.tableFormatter.normalizeIndentation": true,
                "markdown.extension.theming.decoration.renderParagraph": true,
                "markdown.extension.toc.orderedList": true,
                "markdown.server.log": "off",
                "prisma.showPrismaDataPlatformNotification": false,
                "prettier.enable": true,
                "scm.diffDecorationsGutterAction": "none",
                "scm.diffDecorations": "none",
                "search.smartCase": true,
                "search.useIgnoreFiles": false,
                "search.exclude": {},
                "javascript.validate.enable": true,
                "javascript.updateImportsOnFileMove.enabled": "always",
                "typescript.updateImportsOnFileMove.enabled": "always",
                "typescript.preferences.importModuleSpecifier": "project-relative",
                "typescript.tsserver.web.projectWideIntellisense.enabled": false,
                "typescript.validate.enable": true
              },
              "customizeLayout": {
                "menubar.navigationControls": true,
                "menubar.share": true,
                "menubar.layoutControls": true,
                "menubar.customizeLayout": true,
                "primarySidebar.view": "Explorer",
                "secondarySidebar.view": "skyler.ocrmnav",
                "secondarySidebar.position": "left",
                "primarySidebar.display": true,
                "workbench.activityBar.visible": true,
                "secondarySidebar.display": true,
                "panel.display": false,
                "panel.alignment": "center",
                "panel.view": "output",
                "modes.centeredLayout": false,
                "modes.fullScreen": false,
                "modes.zenMode": true
              },
              "workspace": {
                "editor.minimap.showRegionSectionHeaders": true,
                "editor.minimap.showMarkSectionHeaders": false,
                "breadcrumbs.enabled": false,
                "editor.minimap.autohide": true,
                "editor.minimap.enabled": true,
                "editor.minimap.showSlider": "mouseover",
                "editor.minimap.side": "left",
                "editor.minimap.size": "fill",
                "editor.minimap.renderCharacters": false,
                "editor.minimap.maxColumn": "50",
                "editor.fontSize": 11,
                "editor.wordWrap": "on",
                "editor.foldingStrategy": "auto",
                "editor.fontFamily": "JetBrains Mono",
                "editor.fontLigatures": true,
                "editor.fontVariations": true,
                "editor.accessibilitySupport": "off",
                "editor.showFoldingControls": "always",
                "editor.lineNumbers": "relative",
                "editor.scrollBeyondLastLine": false,
                "editor.foldingImportsByDefault": false,
                "editor.renderWhitespace": "none",
                "editor.renderControlCharacters": true,
                "editor.folding": true,
                "editor.glyphMargin": true,
                "editor.stickyScroll.enabled": true,
                "editor.largeFileOptimizations": true,
                "editor.stickyScroll.maxLineCount": 5,
                "editor.unicodeHighlight.invisibleCharacters": false,
                "javascript.updateImportsOnFileMove.enabled": "never",
                "problems.visibility": false,
                "terminal.integrated.defaultLocation": "editor",
                "terminal.integrated.suggest.suggestOnTriggerCharacters": true,
                "terminal.integrated.fontFamily": "monospace",
                "terminal.integrated.stickyScroll.enabled": true,
                "terminal.integrated.fontSize": 12,
                "workbench.editor.alwaysShowEditorActions": true,
                "workbench.editor.enablePreviewFromQuickOpen": false,
                "workbench.editor.focusRecentEditorAfterClose": false,
                "workbench.editor.pinnedTabsOnSeparateRow": true,
                "workbench.editor.wrapTabs": true,
                "workbench.panel.opensMaximized": "never",
                "workbench.panel.defaultLocation": "bottom",
                "workbench.secondarySideBar.showLabels": false,
                "workbench.externalBrowser": "Opera",
                "workbench.activityBar.location": "right",
                "workbench.editor.showTabs": "multiple",
                "workbench.statusBar.visible": true,
                "workbench.sideBar.location": "right",
                "workbench.commandPalette.history": 30,
                "workbench.remoteIndicator.showExtensionRecommendations": false,
                "workbench.welcomePage.walkthroughs.openOnInstall": false,
                "workbench.editor.restoreViewState": true,
                "window.restoreWindows": "one",
                "window.openFilesInNewWindow": "default",
                "window.menuBarVisibility": "classic",
                "window.commandCenter": true,
                "window.zoomLevel": -1,
                "update.mode": "none",
                "update.showReleaseNotes": false,
                "vsicons.dontShowNewVersionMessage": true,
                "update.enableWindowsBackgroundUpdates": false,
                "telemetry.telemetryLevel": "off",
                "extensions.autoCheckUpdates": false,
                "security.workspace.trust.untrustedFiles": "newWindow",
                "ocrmnavigator.terminal.location": "editor",
                "ocrmnavigator.codesnap.windowControlStyle": "Windows",
                "ocrmnavigator.codesnap.showWindowTitle": true,
                "ocrmnavigator.codesnap.windowBorderRadius": "8px",
                "ocrmnavigator.codesnap.windowTitleStyle": "Filename",
                "ocrmnavigator.codesnap.showLineNumbers": true,
                "ocrmnavigator.codesnap.realLineNumbers": false,
                "ocrmnavigator.codesnap.transparentBackground": false,
                "ocrmnavigator.codesnap.trimEmptyLines": false,
                "ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2": false,
                "ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2_3": true,
                "ocrmnavigator.vfs.AUTO_FOLD_1": false,
                "ocrmnavigator.vfs.AUTO_FOLD_1_2": true,
                "ocrmnavigator.vfs.tasks": true,
                "ocrmnavigator.vfs.npmScripts": true,
                "ocrmnavigator.vfs.snippets": true,
                "ocrmnavigator.AUTO_FOLD_PKG": true,
                "ocrmnavigator.BE_QP": true,
                "ocrmnavigator.vscodeVersion": "Code - Insiders",
                "ocrmnavigator.AUTORUN_DIR": "src",
                "ocrmnavigator.UPDATE_PROMPT_OBJECTS": false,
                "ocrmnavigator.AUTORUN_SCRIPTS": true,
                "ocrmnavigator.CONVERT_README_DEV_MD": false,
                "ocrmnavigator.PRO7": false,
                "ocrmnavigator.CONCURRENT": "bleeding-edge",
                "ocrmnavigator.ARCHIVER": "custom",
                "ocrmnavigator.DELETE_OLD_VSIX": true,
                "ocrmnavigator.AUTO_INSTALL_VSIX": true,
                "ocrmnavigator.OPEN_PUB_DASH": true,
                "ocrmnavigator.RELOAD_INSTANCE": true,
                "ocrmnavigator.todo.branch": "main",
                "ocrmnavigator.todo.checkRemindersInterval": "10",
                "ocrmnavigator.todo.syncInterval": "20",
                "ocrmnavigator.todo.syncOnSave": true,
                "ocrmnavigator.todo.owner": "8an3",
                "ocrmnavigator.todo.repository": "8an3/mynotesrepo",
                "ocrmnavigator.todo.isPriv": false,
                "ocrmnavigator.vfs.item.hidden.toggle": true,
                "ocrmnavigator.strPrismaUpdater": true,
                "ocrmnavigator.commands": true,
                "ocrmnavigator.vscodecmdref": true,
                "ocrmnavigator.markdownViewer": true,
                "ocrmnavigator.snippets": true,
                "ocrmnavigator.snippetsInEditor": true,
                "ocrmnavigator.editorContextSnippets": true,
                "ocrmnavigator.formatters": true,
                "ocrmnavigator.trailingCommas": true,
                "ocrmnavigator.batchRename": true,
                "ocrmnavigator.eslintPrettier": true,
                "ocrmnavigator.remixUtils": true,
                "ocrmnavigator.theme": true,
                "ocrmnavigator.vscode.theme.blacked": true,
                "ocrmnavigator.vscode.theme.window.differentiator": true,
                "ocrmnavigator.shadCNComponents": true,
                "ocrmnavigator.repoMgr": true,
                "ocrmnavigator.openGithub": true,
                "ocrmnavigator.githubFunctions": true,
                "ocrmnavigator.prismaFunctions": true,
                "ocrmnavigator.remixComponents": true,
                "ocrmnavigator.clickToSchema": true,
                "ocrmnavigator.crudResolvers": true,
                "ocrmnavigator.fileNesting": true,
                "ocrmnavigator.revealExplorer": true,
                "ocrmnavigator.vfs.item.path.copy": true,
                "ocrmnavigator.bookmarks": true,
                "ocrmnavigator.searchBar": true,
                "ocrmnavigator.clipBoardHistory": true,
                "ocrmnavigator.colorWheel": true,
                "ocrmnavigator.lucideIcons": true,
                "ocrmnavigator.share": true,
                "ocrmnavigator.url": true,
                "ocrmnavigator.project.json.comments.remove": true,
                "ocrmnavigator.con": true,
                "ocrmnavigator.project.file.comments.remove": true,
                "ocrmnavigator.unusedFunctions": true,
                "ocrmnavigator.viewers": true,
                "ocrmnavigator.uiDashboard": true,
                "ocrmnavigator.devStackFunctions": true,
                "ocrmnavigator.openLeftOffNote": true,
                "ocrmnavigator.devstack.site.md.render": true,
                "ocrmnavigator.project.index.smart.create": true,
                "ocrmnavigator.devstack.site.tailwindConverter": true,
                "ocrmnavigator.remix.project2agnostic.convert": true,
                "ocrmnavigator.concurrent": true,
                "ocrmnavigator.autoSequencer": true
              },
              "workbench.colorCustomizations": {
                "background": "#020817",
                "menubar.background": "#020817",
                "menubar.menu": "#020817",
                "activityBar.background": "#020817",
                "terminal.background": "#020817",
                "titleBar.inactiveBackground": "#020817",
                "titleBar.activeBackground": "#020817",
                "panel.background": "#020817",
                "terminalCommandDecoration.defaultBackground": "#020817",
                "sideBar.background": "#020817",
                "sideBarSectionHeader.background": "#1E293B",
                "editor.background": "#020817",
                "editorGroup.emptyBackground": "#020817",
                "statusBar.background": "#020817",
                "editorGroupHeader.tabsBackground": "#020817",
                "activityBar.border": "#020817",
                "menu.border": "#1E293B",
                "menu.separatorBackground": "#1E293B",
                "sideBar.border": "#1E293B",
                "tree.tableColumnsBorder": "#1E293B",
                "tab.border": "#1E293B",
                "statusBar.border": "#1E293B",
                "panel.border": "#1E293B",
                "menu.foreground": "#94A3B8",
                "foreground": "#94A3B8",
                "menubar.foreground": "#94A3B8",
                "activityBar.foreground": "#F8FAFC",
                "sideBarSectionHeader.foreground": "#F8FAFC",
                "explorer.folderItem.foreground": "#1E293B",
                "panelTitle.activeForeground": "#F8FAFC",
                "list.focusForeground": "#F8FAFC",
                "sideBar.foreground": "#94A3B8",
                "statusBar.foreground": "#94A3B8",
                "editor.foreground": "#F8FAFC",
                "activityBar.inactiveForeground": "#94A3B8",
                "explorer.fileItem.foreground": "#94A3B8",
                "input.background": "#1E293B",
                "dropdown.background": "#1E293B",
                "button.background": "#3B82F6",
                "button.hoverBackground": "#3B82F6",
                "input.foreground": "#F8FAFC",
                "button.foreground": "#0F172A",
                "menubar.selectionBackground": "#1E293B",
                "menu.selectionBackground": "#1E293B",
                "menubar.selectionForeground": "#F8FAFC",
                "menu.selectionForeground": "#F8FAFC",
                "list.activeSelectionBackground": "#1E293B",
                "list.activeSelectionForeground": "#F8FAFC",
                "input.border": "#1E293B",
                "inputOption.activeBorder": "#1D4ED8",
                "focusBorder": "#1D4ED8",
                "errorForeground": "#7F1D1D",
                "editor.lineHighlightBackground": "#1E293B",
                "editor.selectionBackground": "#1E293B",
                "editorCursor.foreground": "#F8FAFC",
                "editorIndentGuide.background1": "#1E293B",
                "editorWhitespace.foreground": "#1E293B",
                "list.focusBackground": "#1E293B",
                "list.hoverBackground": "#1E293B",
                "list.highlightForeground": "#3B82F6",
                "explorer.fileItem.hoverForeground": "#F8FAFC",
                "explorer.folderItem.hoverForeground": "#F8FAFC",
                "tree.indentGuidesStroke": "#1E293B",
                "tab.activeBackground": "#020817",
                "tab.activeForeground": "#F8FAFC",
                "tab.inactiveBackground": "#020817",
                "tab.inactiveForeground": "#94A3B8",
                "tab.activeBorder": "#020817",
                "gitDecoration.deletedResourceForeground": "#7F1D1D",
                "gitDecoration.conflictingResourceForeground": "#3B82F6",
                "terminal.ansiBlack": "#020817",
                "terminal.ansiBlue": "#3B82F6",
                "terminal.ansiCyan": "#29c3a0",
                "terminal.ansiGreen": "#29c3a0",
                "terminal.ansiMagenta": "#3B82F6",
                "terminal.ansiRed": "#7F1D1D",
                "terminal.ansiWhite": "#F8FAFC",
                "terminal.ansiYellow": "#d29922",
                "scrollbarSlider.hoverBackground": "#3B82F6",
                "scrollbarSlider.activeBackground": "#3B82F6",
                "scrollbarSlider.background": "#3B82F620",
                "activityBarBadge.background": "#3B82F6",
                "activityBarBadge.foreground": "#F8FAFC",
                "explorer.folderItem.selectedIconForeground": "#3B82F6",
                "explorer.fileItem.conflictForeground": "#7F1D1D",
                "explorer.fileItem.errorForeground": "#7F1D1D",
                "explorer.fileItem.warningForeground": "#d29922",
                "explorer.folderItem.iconForeground": "#F8FAFC",
                "explorer.fileItem.selectedIconForeground": "#F8FAFC",
                "explorer.fileItem.modifiedForeground": "#29c3a0",
                "list.dropBackground": "#02081740",
                "list.filterMatchBackground": "#02081720",
                "list.inactiveSelectionBackground": "#1E293B40",
                "list.hoverForeground": "#F8FAFC",
                "statusBarItem.hoverBackground": "#1E293B",
                "gitDecoration.submoduleResourceForeground": "#F8FAFC"
              }
            }
          ]
        },
        {
          "$schema": "./schemas/layout-config-schema.json",
          "label": "Test Extensions",
          "path": "",
          "type": "layout",
          "icon": "editor-layout",
          "args": [
            {
              "extensions": {
                "enable": [
                  "tomoki1207.pdf"
                ],
                "disable": [
                  "github.copilot",
                  "AMiner.codegeex",
                  "jmanuels.do",
                  "NoThlnG.vscode-open-wsl",
                  "ban.spellright",
                  "tauri-apps.tauri-vscode",
                  "ms-vscode-remote.remote-wsl",
                  "google.geminicodeassist",
                  "JetBrains.jetbrains-ai-assistant"
                ],
                "install": []
              },
              "editorGrid": {
                "columns": 3,
                "rows": 2,
                "groups": [
                  {
                    "slot": [
                      0,
                      0
                    ],
                    "active": ".vscode/ntrsync/10516_DevStack_todo.md",
                    "pinned": true
                  },
                  {
                    "slot": [
                      0,
                      1
                    ],
                    "active": "src/helpers/context.ts",
                    "pinned": true
                  },
                  {
                    "slot": [
                      1,
                      0
                    ],
                    "active": "README.dev.md",
                    "pinned": true
                  },
                  {
                    "slot": [
                      1,
                      1
                    ],
                    "active": "README.md",
                    "pinned": true
                  },
                  {
                    "slot": [
                      2,
                      0
                    ],
                    "active": "package.dev.jsonc",
                    "pinned": true
                  }
                ],
                "files": [
                  {
                    "path": "src/helpers/master.ts",
                    "slot": [
                      1,
                      0
                    ],
                    "pinned": true,
                    "fold": [
                      1,
                      2,
                      3
                    ]
                  },
                  {
                    "path": "src/helpers/menus.ts",
                    "slot": [
                      1,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "src/extension/navigatorView.ts",
                    "slot": [
                      1,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "src/helpers/modular-commands.ts",
                    "slot": [
                      1,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "src/extension.ts",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "package.dev.jsonc",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "C:/User/skyle/AppData/Roaming/Code - Insiders/User/globalStorage/skyler.ocrmnav/global-navigator-config.json",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "F:/devstackBackUp/global-navigator-config.json",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "F:/devstackBackUp/project-configs/project-1744496862041-y866zpqtd9.json",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  },
                  {
                    "path": "F:/devstackBackUp/project-configs/project-1757010936487-i30yr98a4p7.json",
                    "slot": [
                      2,
                      0
                    ],
                    "pinned": true
                  }
                ]
              },
              "performance": {
                "css.validate": false,
                "diffEditor.codeLens": false,
                "debug.openDebug": "neverOpen",
                "debug.toolBarLocation": "hidden",
                "debug.showInStatusBar": "never",
                "editor.inlineSuggest.enabled": false,
                "editor.inlayHints.enabled": "off",
                "editor.parameterHints.enabled": false,
                "editor.suggestOnTriggerCharacters": false,
                "editor.acceptSuggestionOnEnter": "off",
                "editor.acceptSuggestionOnCommitCharacter": false,
                "editor.wordBasedSuggestions": "off",
                "editor.formatOnType": false,
                "editor.formatOnPaste": false,
                "editor.formatOnSave": false,
                "editor.semanticHighlighting.enabled": true,
                "editor.occurrencesHighlight": "off",
                "editor.selectionHighlight": true,
                "editor.codeLens": false,
                "editor.lightbulb.enabled": "onCode",
                "eslint.enable": true,
                "extensions.showRecommendationsOnlyOnDemand": true,
                "extensions.autoUpdate": false,
                "extensions.ignoreRecommendations": true,
                "files.watcherExclude": {},
                "files.exclude": {},
                "files.maxMemoryForLargeFilesMB": 4096,
                "git.decorations.enabled": false,
                "git.diffEditor.renderGutterMenu": false,
                "git.mergeEditor.codeLens.enabled": false,
                "github.copilot.enable": {
                  "*": false,
                  "plaintext": true,
                  "markdown": false,
                  "scminput": false
                },
                "github.copilot.nextEditSuggestions.allowWhitespaceOnlyChanges": false,
                "github.copilot.chat.agent.thinkingTool": true,
                "Codegeex.Chat.LanguagePreference": "English",
                "Codegeex.GenerationPreference": "line by line",
                "Codegeex.Privacy": false,
                "Codegeex.License": "",
                "codegeex.codeLens.functionQuickOptions": {
                  "addComment": false,
                  "ghostComment": false,
                  "fixBug": false,
                  "generateUnitTest": false,
                  "reviewCode": false,
                  "codeOptimization": false,
                  "addDocString": false,
                  "addExceptionHandling": false,
                  "printLogForDebugging": false,
                  "improveRunningEfficiency": false,
                  "renameSymbols": false,
                  "newFileForDebugging": false,
                  "tryANewApproach": false,
                  "explainCode": false
                },
                "codegeex.codeLens.classQuickOptions": {
                  "explainCode": false,
                  "ghostComment": false,
                  "fixBug": false,
                  "generateUnitTest": false,
                  "reviewCode": false,
                  "addDocStringForClass": false,
                  "addDocStringForMethods": false,
                  "addComment": false
                },
                "geminicodeassist.chat.changeView": "Default diff view",
                "geminicodeassist.displayInlineContextHint": false,
                "geminicodeassist.enableTelemetry": false,
                "geminicodeassist.inlineSuggestions.enableAuto": false,
                "geminicodeassist.localCodebaseAwareness": false,
                "html.validate.scripts": false,
                "jsonc.validate.enable": true,
                "json.validate.enable": true,
                "merge-conflict.codeLens.enabled": false,
                "multiDiffEditor.experimental.enabled": false,
                "markdown.validate.enable": false,
                "markdown.preview.automaticPreview": "never",
                "markdown.preview.fontSize": 12,
                "markdown.validate.enabled": false,
                "markdown.updateLinksOnFileMove.enabled": "never",
                "markdown.editor.pasteUrlAsFormattedLink.enabled": "always",
                "markdown.extension.print.theme": "dark",
                "markdown.extension.tableFormatter.normalizeIndentation": true,
                "markdown.extension.theming.decoration.renderParagraph": true,
                "markdown.extension.toc.orderedList": true,
                "markdown.server.log": "off",
                "prisma.showPrismaDataPlatformNotification": false,
                "prettier.enable": true,
                "scm.diffDecorationsGutterAction": "none",
                "scm.diffDecorations": "none",
                "search.smartCase": true,
                "search.useIgnoreFiles": false,
                "search.exclude": {},
                "javascript.validate.enable": true,
                "javascript.updateImportsOnFileMove.enabled": "always",
                "typescript.updateImportsOnFileMove.enabled": "always",
                "typescript.preferences.importModuleSpecifier": "project-relative",
                "typescript.tsserver.web.projectWideIntellisense.enabled": false,
                "typescript.validate.enable": true
              },
              "customizeLayout": {
                "menubar.navigationControls": true,
                "menubar.share": true,
                "menubar.layoutControls": true,
                "menubar.customizeLayout": true,
                "primarySidebar.view": "Explorer",
                "secondarySidebar.view": "skyler.ocrmnav",
                "secondarySidebar.position": "left",
                "primarySidebar.display": true,
                "workbench.activityBar.visible": true,
                "secondarySidebar.display": true,
                "panel.display": false,
                "panel.alignment": "center",
                "panel.view": "output",
                "modes.centeredLayout": false,
                "modes.fullScreen": false,
                "modes.zenMode": true
              },
              "workspace": {
                "editor.minimap.showRegionSectionHeaders": true,
                "editor.minimap.showMarkSectionHeaders": false,
                "breadcrumbs.enabled": false,
                "editor.minimap.autohide": true,
                "editor.minimap.enabled": true,
                "editor.minimap.showSlider": "mouseover",
                "editor.minimap.side": "left",
                "editor.minimap.size": "fill",
                "editor.minimap.renderCharacters": false,
                "editor.minimap.maxColumn": "50",
                "editor.fontSize": 11,
                "editor.wordWrap": "on",
                "editor.foldingStrategy": "auto",
                "editor.fontFamily": "JetBrains Mono",
                "editor.fontLigatures": true,
                "editor.fontVariations": true,
                "editor.accessibilitySupport": "off",
                "editor.showFoldingControls": "always",
                "editor.lineNumbers": "relative",
                "editor.scrollBeyondLastLine": false,
                "editor.foldingImportsByDefault": false,
                "editor.renderWhitespace": "none",
                "editor.renderControlCharacters": true,
                "editor.folding": true,
                "editor.glyphMargin": true,
                "editor.stickyScroll.enabled": true,
                "editor.largeFileOptimizations": true,
                "editor.stickyScroll.maxLineCount": 5,
                "editor.unicodeHighlight.invisibleCharacters": false,
                "javascript.updateImportsOnFileMove.enabled": "never",
                "problems.visibility": false,
                "terminal.integrated.defaultLocation": "editor",
                "terminal.integrated.suggest.suggestOnTriggerCharacters": true,
                "terminal.integrated.fontFamily": "monospace",
                "terminal.integrated.stickyScroll.enabled": true,
                "terminal.integrated.fontSize": 12,
                "workbench.editor.alwaysShowEditorActions": true,
                "workbench.editor.enablePreviewFromQuickOpen": false,
                "workbench.editor.focusRecentEditorAfterClose": false,
                "workbench.editor.pinnedTabsOnSeparateRow": true,
                "workbench.editor.wrapTabs": true,
                "workbench.panel.opensMaximized": "never",
                "workbench.panel.defaultLocation": "bottom",
                "workbench.secondarySideBar.showLabels": false,
                "workbench.externalBrowser": "Opera",
                "workbench.activityBar.location": "right",
                "workbench.editor.showTabs": "multiple",
                "workbench.statusBar.visible": true,
                "workbench.sideBar.location": "right",
                "workbench.commandPalette.history": 30,
                "workbench.remoteIndicator.showExtensionRecommendations": false,
                "workbench.welcomePage.walkthroughs.openOnInstall": false,
                "workbench.editor.restoreViewState": true,
                "window.restoreWindows": "one",
                "window.openFilesInNewWindow": "default",
                "window.menuBarVisibility": "classic",
                "window.commandCenter": true,
                "window.zoomLevel": -1,
                "update.mode": "none",
                "update.showReleaseNotes": false,
                "vsicons.dontShowNewVersionMessage": true,
                "update.enableWindowsBackgroundUpdates": false,
                "telemetry.telemetryLevel": "off",
                "extensions.autoCheckUpdates": false,
                "security.workspace.trust.untrustedFiles": "newWindow",
                "ocrmnavigator.terminal.location": "editor",
                "ocrmnavigator.codesnap.windowControlStyle": "Windows",
                "ocrmnavigator.codesnap.showWindowTitle": true,
                "ocrmnavigator.codesnap.windowBorderRadius": "8px",
                "ocrmnavigator.codesnap.windowTitleStyle": "Filename",
                "ocrmnavigator.codesnap.showLineNumbers": true,
                "ocrmnavigator.codesnap.realLineNumbers": false,
                "ocrmnavigator.codesnap.transparentBackground": false,
                "ocrmnavigator.codesnap.trimEmptyLines": false,
                "ocrmnavigator.markdownpreprocessor.variableSystem": true,
                "ocrmnavigator.markdownpreprocessor.sourcemapUpdater": true,
                "ocrmnavigator.markdownpreprocessor.tocUpdater": true,
                "ocrmnavigator.markdownpreprocessor.tocType": "roman",
                "ocrmnavigator.markdownpreprocessor.tableConversion": true,
                "ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2": false,
                "ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2_3": true,
                "ocrmnavigator.vfs.AUTO_FOLD_1": false,
                "ocrmnavigator.vfs.AUTO_FOLD_1_2": true,
                "ocrmnavigator.vfs.tasks": true,
                "ocrmnavigator.vfs.npmScripts": true,
                "ocrmnavigator.vfs.snippets": true,
                "ocrmnavigator.AUTO_FOLD_PKG": true,
                "ocrmnavigator.BE_QP": true,
                "ocrmnavigator.vscodeVersion": "Code - Insiders",
                "ocrmnavigator.AUTORUN_DIR": "src",
                "ocrmnavigator.UPDATE_PROMPT_OBJECTS": false,
                "ocrmnavigator.AUTORUN_SCRIPTS": true,
                "ocrmnavigator.CONVERT_README_DEV_MD": false,
                "ocrmnavigator.PRO7": false,
                "ocrmnavigator.CONCURRENT": "bleeding-edge",
                "ocrmnavigator.ARCHIVER": "custom",
                "ocrmnavigator.DELETE_OLD_VSIX": true,
                "ocrmnavigator.AUTO_INSTALL_VSIX": true,
                "ocrmnavigator.OPEN_PUB_DASH": true,
                "ocrmnavigator.RELOAD_INSTANCE": true,
                "ocrmnavigator.todo.branch": "main",
                "ocrmnavigator.todo.checkRemindersInterval": "10",
                "ocrmnavigator.todo.syncInterval": "20",
                "ocrmnavigator.todo.syncOnSave": true,
                "ocrmnavigator.todo.owner": "8an3",
                "ocrmnavigator.todo.repository": "8an3/mynotesrepo",
                "ocrmnavigator.todo.isPriv": false,
                "ocrmnavigator.vfs.item.hidden.toggle": true,
                "ocrmnavigator.strPrismaUpdater": true,
                "ocrmnavigator.commands": true,
                "ocrmnavigator.vscodecmdref": true,
                "ocrmnavigator.markdownViewer": true,
                "ocrmnavigator.snippets": true,
                "ocrmnavigator.snippetsInEditor": true,
                "ocrmnavigator.editorContextSnippets": true,
                "ocrmnavigator.formatters": true,
                "ocrmnavigator.trailingCommas": true,
                "ocrmnavigator.batchRename": true,
                "ocrmnavigator.eslintPrettier": true,
                "ocrmnavigator.remixUtils": true,
                "ocrmnavigator.theme": true,
                "ocrmnavigator.vscode.theme.blacked": true,
                "ocrmnavigator.vscode.theme.window.differentiator": true,
                "ocrmnavigator.shadCNComponents": true,
                "ocrmnavigator.repoMgr": true,
                "ocrmnavigator.openGithub": true,
                "ocrmnavigator.githubFunctions": true,
                "ocrmnavigator.prismaFunctions": true,
                "ocrmnavigator.remixComponents": true,
                "ocrmnavigator.clickToSchema": true,
                "ocrmnavigator.crudResolvers": true,
                "ocrmnavigator.fileNesting": true,
                "ocrmnavigator.revealExplorer": true,
                "ocrmnavigator.vfs.item.path.copy": true,
                "ocrmnavigator.bookmarks": true,
                "ocrmnavigator.searchBar": true,
                "ocrmnavigator.clipBoardHistory": true,
                "ocrmnavigator.colorWheel": true,
                "ocrmnavigator.lucideIcons": true,
                "ocrmnavigator.share": true,
                "ocrmnavigator.url": true,
                "ocrmnavigator.project.json.comments.remove": true,
                "ocrmnavigator.con": true,
                "ocrmnavigator.project.file.comments.remove": true,
                "ocrmnavigator.unusedFunctions": true,
                "ocrmnavigator.viewers": true,
                "ocrmnavigator.uiDashboard": true,
                "ocrmnavigator.devStackFunctions": true,
                "ocrmnavigator.openLeftOffNote": true,
                "ocrmnavigator.devstack.site.md.render": true,
                "ocrmnavigator.project.index.smart.create": true,
                "ocrmnavigator.devstack.site.tailwindConverter": true,
                "ocrmnavigator.remix.project2agnostic.convert": true,
                "ocrmnavigator.concurrent": true,
                "ocrmnavigator.autoSequencer": true
              }
            }
          ]
        }
      ]
    },
    {
      "label": "PRIMARY",
      "expanded": false,
      "global": false,
      "type": "folder",
      "items": [
        {
          "label": "master.ts",
          "path": "src/helpers/master.ts",
          "type": "file"
        },
        {
          "label": "menus.ts",
          "path": "src/helpers/menus.ts",
          "type": "file"
        },
        {
          "label": "extension.ts",
          "path": "src/extension.ts",
          "type": "file"
        },
        {
          "label": "navigatorView.ts",
          "path": "src/extension/navigatorView.ts",
          "type": "file"
        },
        {
          "label": "workspace.ts",
          "path": "src/helpers/workspace.ts",
          "type": "file"
        },
        {
          "label": "itemsActionsMenu.ts",
          "path": "f:\\DevStack\\src\\helpers\\itemsActionsMenu.ts",
          "type": "file",
          "icon": "file"
        },
        {
          "label": "yeet",
          "path": "f:\\DevStack\\src\\helpers\\yeet.ts",
          "type": "file",
          "icon": "arrow-circle-up"
        },
        {
          "label": "modular-commands.ts",
          "path": "f:\\DevStack\\src\\helpers\\modular-commands.ts",
          "type": "file",
          "icon": "symbol-function"
        }
      ]
    },
    {
      "label": "SECONDARY",
      "expanded": false,
      "type": "folder",
      "global": false,
      "items": []
    }
  ]
}
```

</details>

#### Resources
- [Visual Guide](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/vfs/SequentialExecution+.gif?raw=true)
- [Video Tutorial](https://youtu.be/NtnVq8CNJ7A)



## Reveal In Explorer

  
**Right-click any file → Reveal in Explorer**

Open file locations directly in Windows Explorer or macOS Finder from:
- DevStack sidebar
- Editor context menu
- Extensions pane

![Reveal in Explorer](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/reveal-in-explorer.jpg?raw=true)
  

## Copy Path


**Right-click any file → Copy Path**

Copy full or relative file paths to clipboard. Works with multiple path formats throughout the extension.

[Video Demo](https://youtu.be/FWa6o5FK3sU)


## Search
**Access:** Click title bar button

Powerful search functionality to find and execute any command you've created. Preview commands before execution to ensure you're running the right one.

![Search Feature](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/search.jpg)

[Video Demo](https://youtu.be/pRVv7UaY4qM)




## Configuration Settings

DevStack provides extensive configuration options to customize your development workflow. All settings are prefixed with `ocrmnavigator.` and can be configured in your VS Code settings.

---

#### File Opening Behavior

**`ocrmnavigator.vfs.onFileOpen`**
- **Type**: `string`
- **Default**: `"off"`
- **Options**: `"forceCenterFocus"`, `"openInSetCol"`, `"off"`
- **Description**: Controls how files open in the editor. See documentation in changelog for details.

**`ocrmnavigator.vfs.targetEditorGroup`**
- **Type**: `number`
- **Default**: `2`
- **Options**: `1-9`
- **Description**: Specifies which editor group (column) files should open in.

---

#### Advanced Search

**`ocrmnavigator.advancedSearch.contextLinesBefore`**
- **Type**: `number`
- **Default**: `4`
- **Description**: Number of lines to display before each search match for context.

**`ocrmnavigator.advancedSearch.contextLinesAfter`**
- **Type**: `number`
- **Default**: `10`
- **Description**: Number of lines to display after each search match for context.

**`ocrmnavigator.configPath`**
- **Type**: `string`
- **Default**: `".vscode/ocrmnavigator/search-config.json"`
- **Description**: Path to the search configuration file.

---

#### Auto-Folding

**`ocrmnavigator.vfs.AUTO_FOLD_1`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically fold code at level 1 when file opens.

**`ocrmnavigator.vfs.AUTO_FOLD_1_2`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically fold code at levels 1 and 2 when file opens.

**`ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2_3`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically fold package.json at levels 2 and 3 when file opens.

**`ocrmnavigator.vfs.AUTO_FOLD_PKGJSON_2`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically fold package.json at level 2 when file opens.

---

#### TODO & Highlighting

**`ocrmnavigator.todo.highlight.enable`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Enable color highlighting for TODO items and marked lines.

**`ocrmnavigator.todo.highlightColor`**
- **Type**: `string`
- **Default**: `"#3b82f6"`
- **Description**: Hex color code for highlighting TODO items.

**`ocrmnavigator.todo.highlightOpacity`**
- **Type**: `number`
- **Default**: `0.2`
- **Range**: `0-1`
- **Description**: Opacity for the highlight background.

**`ocrmnavigator.todo.borderOpacity`**
- **Type**: `number`
- **Default**: `0.5`
- **Range**: `0-1`
- **Description**: Opacity for the highlight border.

**`ocrmnavigator.todoNotesReminders`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enables TODO, notes, reminders, and post-it functionality. Disable for faster reload times when troubleshooting.

---

#### Markdown Preprocessor

**`ocrmnavigator.markdownpreprocessor.variableSystem`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enable variable system in markdown preprocessor.

**`ocrmnavigator.markdownpreprocessor.sourcemapUpdater`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enable source map creation in markdown preprocessor.

**`ocrmnavigator.markdownpreprocessor.tocUpdater`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enable table of contents updater in markdown preprocessor.

**`ocrmnavigator.markdownpreprocessor.tocType`**
- **Type**: `string`
- **Default**: `"roman"`
- **Options**: `"unorderd"`, `"ordered"`, `"roman"`, `"accordian"`
- **Description**: Format style for table of contents generation.

**`ocrmnavigator.markdownpreprocessor.tableConversion`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enable table conversion in markdown preprocessor.

---

#### VFS Explorer Folders

**`ocrmnavigator.vfs.tasks`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Display 'Tasks' folder in DevStack explorer. Auto-populated from tasks.json.

**`ocrmnavigator.vfs.npmScripts`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Display 'NPM Scripts' folder in DevStack explorer. Auto-populated from package.json scripts.

**`ocrmnavigator.vfs.snippets`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Display 'Snippets' folder in DevStack explorer.

**`ocrmnavigator.vfs.item.hidden.toggle`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Remove chain items from UI (can reveal when editing). Affects items with `hidden: true`.

---

#### Code Snapshot (CodeSnap)

**`ocrmnavigator.codesnap.backgroundPalette`**
- **Type**: `string`
- **Default**: `"pinky"`
- **Options**: `"magnum"`, `"pinky"`, `"passion"`, `"steel"`, `"tropic"`, `"forest"`, `"blueman"`, `"sand"`
- **Description**: Background gradient palette for code snapshots.

**`ocrmnavigator.codesnap.containerBackground`**
- **Type**: `string`
- **Default**: `""`
- **Description**: Custom background CSS. Overrides backgroundPalette when set.

**`ocrmnavigator.codesnap.boxShadow`**
- **Type**: `string`
- **Default**: `"rgba(0, 0, 0, 0.55) 0px 20px 68px"`
- **Description**: Box shadow for snapshot window.

**`ocrmnavigator.codesnap.containerPadding`**
- **Type**: `string`
- **Default**: `"3em"`
- **Description**: Padding around snapshot container.

**`ocrmnavigator.codesnap.windowBorderRadius`**
- **Type**: `string`
- **Default**: `"10px"`
- **Description**: Border radius for snapshot window.

**`ocrmnavigator.codesnap.windowControlStyle`**
- **Type**: `string`
- **Default**: `"Windows"`
- **Options**: `"None"`, `"OS X"`, `"Gray dots"`, `"Windows"`
- **Description**: Window control style (traffic lights or Windows controls).

**`ocrmnavigator.codesnap.showWindowTitle`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Show window title in snapshot.

**`ocrmnavigator.codesnap.windowTitleStyle`**
- **Type**: `string`
- **Default**: `"Workspace + Filename"`
- **Options**: `"Workspace + Filename"`, `"Filename"`, `"Custom"`
- **Description**: Window title display format.

**`ocrmnavigator.codesnap.windowTitleCustomStyle`**
- **Type**: `string`
- **Default**: `""`
- **Description**: Custom window title text (used when windowTitleStyle is 'Custom').

**`ocrmnavigator.codesnap.showLineNumbers`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Show line numbers in snapshot.

**`ocrmnavigator.codesnap.realLineNumbers`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Use actual line numbers from file instead of starting at 1.

**`ocrmnavigator.codesnap.transparentBackground`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Use transparent background for snapshot.

**`ocrmnavigator.codesnap.target`**
- **Type**: `string`
- **Default**: `"container"`
- **Options**: `"container"`, `"window"`
- **Description**: Snapshot target. Container includes background, window is code only.

**`ocrmnavigator.codesnap.trimEmptyLines`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Trim empty lines from beginning and end of snapshot.

---

#### GitHub Integration

**`ocrmnavigator.todo.repo`**
- **Type**: `string`
- **Default**: `""`
- **Description**: GitHub repository name.

**`ocrmnavigator.todo.owner`**
- **Type**: `string`
- **Default**: `""`
- **Description**: GitHub repository owner.

**`ocrmnavigator.todo.branch`**
- **Type**: `string`
- **Default**: `""`
- **Description**: Git branch name.

**`ocrmnavigator.todo.repository`**
- **Type**: `string`
- **Default**: `""`
- **Description**: Full repository path (owner/repo).

**`ocrmnavigator.todo.remote`**
- **Type**: `string`
- **Default**: `""`
- **Description**: Git remote URL.

**`ocrmnavigator.todo.autoSync`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Enable automatic syncing with repository.

**`ocrmnavigator.todo.isPriv`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Indicates if repository is private.

**`ocrmnavigator.todo.syncOnSave`**
- **Type**: `boolean`
- **Default**: `true`
- **Description**: Automatically sync when saving files.

**`ocrmnavigator.todo.syncInterval`**
- **Type**: `string`
- **Default**: `"30"`
- **Description**: Sync interval in minutes.

**`ocrmnavigator.todo.checkRemindersInterval`**
- **Type**: `string`
- **Default**: `"10"`
- **Description**: Reminder check interval in minutes.

---

#### Extension Control

**`ocrmnavigator.GBL_DISABLE`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: ⚠️ Global disable flag. Only modify if you understand its purpose.

**`ocrmnavigator.WS_DISABLE`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: ⚠️ Workspace disable flag. Only modify if you understand its purpose.

**`ocrmnavigator.F_DISABLE`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: ⚠️ Feature disable flag. Only modify if you understand its purpose.

**`ocrmnavigator.EXT_DISABLE`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: ⚠️ Extension disable flag. Only modify if you understand its purpose.

---

#### Build & Deploy

**`ocrmnavigator.CONCURRENT`**
- **Type**: `string`
- **Default**: `"stable"`
- **Options**: `"stable"`, `"bleeding-edge"`
- **Description**: Determines which concurrent function version to run.

**`ocrmnavigator.PKG_MGR`**
- **Type**: `string`
- **Default**: `"pnpm"`
- **Description**: Fallback package manager for extension operations.

**`ocrmnavigator.AUTORUN_SCRIPTS`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Enable automatic execution of Node.js scripts in specified folder during g4 and .vsix functions.

**`ocrmnavigator.AUTORUN_DIR`**
- **Type**: `string`
- **Default**: `"src"`
- **Description**: Directory containing autorun folder. Leave empty to use workspace root.

**`ocrmnavigator.ARCHIVER`**
- **Type**: `string`
- **Default**: `"custom"`
- **Description**: Archiver choice for g4 and .vsix functions.

**`ocrmnavigator.PRO7`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Enable secure archiving of secrets before pushing to GitHub.

**`ocrmnavigator.DELETE_OLD_VSIX`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Delete old .vsix archives during build process.

**`ocrmnavigator.AUTO_INSTALL_VSIX`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically install newly created .vsix archive.

**`ocrmnavigator.OPEN_PUB_DASH`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically open Microsoft publisher dashboard after build.

**`ocrmnavigator.RELOAD_INSTANCE`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Automatically reload VS Code after installing new archive.

**`ocrmnavigator.BE_QP`**
- **Type**: `boolean`
- **Default**: `false`
- **Description**: Enable BQ Quick Pick menu on status bar.

---

#### Feature Toggles

All feature toggles default to `true` unless otherwise specified and can be disabled to improve performance or remove unwanted functionality.

**Core Features:**
- `ocrmnavigator.commands` - VSCode commands
- `ocrmnavigator.vscodecmdref` - VSCode commands reference sheet
- `ocrmnavigator.markdownViewer` - Markdown viewer
- `ocrmnavigator.devstack.site.snippets` - Snippets editor and viewer
- `ocrmnavigator.snippetsInEditor` - Snippets via editor context menu
- `ocrmnavigator.editorContextSnippets` - Editor context snippets
- `ocrmnavigator.formatters` - Formatters and configurator
- `ocrmnavigator.trailingCommas` - Remove trailing commas function
- `ocrmnavigator.batchRename` - Batch rename via context menu
- `ocrmnavigator.eslintPrettier` - Add ESLint & Prettier configs

**Framework Utilities:**
- `ocrmnavigator.remixUtils` - Remix utilities via context menu
- `ocrmnavigator.remixComponents` - Remix components via context menu
- `ocrmnavigator.shadCNComponents` - ShadCN components via context menu
- `ocrmnavigator.prismaFunctions` - Prisma functions via context menu
- `ocrmnavigator.clickToSchema` - Click to schema object navigation
- `ocrmnavigator.crudResolvers` - Generate CRUD resolvers/REST endpoints
- `ocrmnavigator.strPrismaUpdater` - Auto-add Prisma scripts to package.json

**Theme & UI:**
- `ocrmnavigator.theme` - VSCode theme builder
- `ocrmnavigator.vscode.theme.blacked` - Blacked Out & Diff & Reset themes
- `ocrmnavigator.vscode.theme.window.differentiator` - Window differentiator
- `ocrmnavigator.devstack.site.colorWheel` - Color wheel tool
- `ocrmnavigator.uiDashboard` - UI Dashboard

**GitHub & Repository:**
- `ocrmnavigator.repoMgr` - GitHub repository management
- `ocrmnavigator.openGithub` - Open GitHub repo in browser
- `ocrmnavigator.githubFunctions` - GitHub editor functions

**File Management:**
- `ocrmnavigator.fileNesting` - File nesting configuration
- `ocrmnavigator.revealExplorer` - Reveal in explorer
- `ocrmnavigator.vfs.item.path.copy` - Copy path from navigation
- `ocrmnavigator.searchBar` - Search bar for navigation

**Code Quality:**
- `ocrmnavigator.project.json.comments.remove` - Remove JSON comments
- `ocrmnavigator.con` - Remove all console.logs
- `ocrmnavigator.project.file.comments.remove` - Remove all comments
- `ocrmnavigator.unusedFunctions` - Find unused functions

**Additional Features:**
- `ocrmnavigator.bookmarks` - Bookmarks system
- `ocrmnavigator.clipBoardHistory` - Clipboard history pro
- `ocrmnavigator.lucideIcons` - Lucide icons integration
- `ocrmnavigator.share` - Share with a friend
- `ocrmnavigator.url` - URL links in navigation
- `ocrmnavigator.viewers` - Viewers functionality
- `ocrmnavigator.devStackFunctions` - DevStack editor functions
- `ocrmnavigator.leftOffNote.open` - Left Off Note feature
- `ocrmnavigator.devstack.site.md.render` - Render MD in editor context menu
- `ocrmnavigator.project.index.smart.create` - Create folder smart index
- `ocrmnavigator.devstack.site.tailwindConverter` - Tailwind converter button
- `ocrmnavigator.remix.project2agnostic.convert` - Convert Remix routes to agnostic
- `ocrmnavigator.vfs.concurrent.execute` - Concurrent command feature
- `ocrmnavigator.vfs.chain.execute` - Chain command feature

---

#### Advanced Settings

**`ocrmnavigator.UPDATE_PROMPT_OBJECTS`**
- **Type**: `boolean`
- **Default**: `false`

**`ocrmnavigator.CONVERT_README_DEV_MD`**
- **Type**: `boolean`
- **Default**: `false`

**`ocrmnavigator.PROMPT_OBJECTS_DIR`**
- **Type**: `string`
- **Default**: `"F:/playground/md/"`
- **Description**: Path to markdown prompt objects directory.

**`ocrmnavigator.rootPath`**
- **Type**: `string`
- **Default**: `""`

**`ocrmnavigator.octokit`**
- **Type**: `string`
- **Default**: `""`

**`ocrmnavigator.ATAT`**
- **Type**: `string`
- **Default**: `""`

**`ocrmnavigator.notesDir`**
- **Type**: `string`
- **Default**: `""`

**`ocrmnavigator.other`**
- **Type**: `string`
- **Default**: `null`
- **Description**: Miscellaneous configuration option.

---

### Quick Configuration Tips

1. **For Better Performance**: Disable features you don't use by setting their toggle to `false`
2. **Debugging**: Set `ocrmnavigator.todoNotesReminders` to `false` for faster reload times
3. **Custom Workflows**: Use `ocrmnavigator.vfs.chain.execute` and `ocrmnavigator.vfs.concurrent.execute` for automation
4. **GitHub Integration**: Configure `ocrmnavigator.todo.*` settings for repository syncing
5. **Code Snapshots**: Customize appearance with `ocrmnavigator.codesnap.*` settings


#### Usage

All item types share common actions:
- **Add**: Create new items through the interface
- **Edit**: Modify existing items
- **Remove**: Delete items from configuration
- **Trigger**: Click items in the extensions window to execute

Set item type in config object or click the plus icon in the title pane.

#### Previews

- **Navigation View**: [Image](https://raw.githubusercontent.com/8an3/dev-notes/main/ui/nav-view.jpg?raw=true)
- **Sequential Execution**: [Video](https://youtu.be/ySp83VqxQ8s) | [Image](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/vfs/SequentialExecution+.gif?raw=true)




### Architecture Notes
This section provides a deep dive into the underlying systems of this extension. Understanding these architectural choices will help you write more effective configurations and leverage the full power of the codebase.

With the recent redesign, the project has moved toward an engine-based, object-oriented approach. By utilizing dedicated classes for core logic, the codebase is more efficient, modular, and easier to extend.

#### Core Architectural Priorities
The topics below are ranked by their impact on your development workflow. High-priority items focus on the modular systems you will interact with daily, while lower-priority items cover "under-the-hood" utilities.

1. Modular Engine Structure (High Priority) Learning how our engines and classes interact is the most valuable use of your time. This modularity allows you to hook into specific functionalities and customize the extension's behavior without rewriting core logic.

2. Custom VSIX Archiver (Low Priority) While the internal archiver is a vital component, you don't need to understand its inner workings to use the extension. However, it is included here because it offers significant advantages over the standard vsce tool:
   - Performance: Significantly faster execution times.
   - Flexibility: It is less restrictive than vsce, allowing you to bypass certain requirements that might otherwise block your workflow.
   - Compatibility: Provides an alternative archiving path for specialized environments where standard tools fail.

By centralizing these notes here rather than scattering them across individual README files, provide a single source of truth for the "how" and "why" behind the code. This bird's-eye view ensures you can build your config with a clear understanding of the underlying framework.


### Environment Variable Integration (.env)
To handle sensitive data—like NPM authentication tokens—the extension supports the use of .env variables directly within your configuration strings. This allows you to keep secrets out of your source code while automating authenticated commands.

#### Security First: Execution-Time Loading
For security reasons, the extension does not load environment variables when the extension starts. Instead, variables are resolved "just-in-time":
- Lazy Loading: The extension stores the raw string (e.g., ${NPM_TOKEN}) and only injects the actual value at the moment of execution.
- Scoped Access: Because variables are pulled at runtime, they are scoped to the .env file present in the active project, preventing cross-project credential leakage.

#### How it Works
At runtime, the extension performs a check for the `${` syntax.
- If a match is found: It attempts to resolve the variable name following the brace.
- If no value exists: The extension returns the original string untouched to ensure it doesn't break other commands that might naturally use those characters.

#### Configuration Example
Use the standard ${VARIABLE_NAME} syntax within your path or command strings:

```json
{
  "label": "npmPublishWithToken",
  "path": "npm publish --//registry.npmjs.org/:_authToken=${NPM_TOKEN}",
  "type": "powershellCommand",
  "hidden": true
},
```
> [!IMPORTANT] 
> This approach requires the .env file to be present in the root of the project where the command is being executed. While this limits global access, it ensures that sensitive tokens remain restricted to their intended environments.

### Modular Function Building
Previously, this extension was built on a "function-per-feature" basis—each tool was isolated, with no awareness of or connection to other features. The latest architecture moves away from this rigid structure in favor of modular, exposed functions.

By breaking core logic into independent, reusable methods, the extension essentially becomes a toolkit. This grants you the "absurd" level of freedom to chain functions together, effectively turning the extension into a manual CI/CD pipeline tailored to your specific workflow.

Git integration is the best example of this shift. Rather than having a single "Git Sync" button, I have now exposed the underlying atomic operations. You can call these directly within your configurations to build custom workflows:

- ocrmnavigator.git.diffCached
- ocrmnavigator.git.openRepo
- ocrmnavigator.git.openRepoAtFile
- ocrmnavigator.git.upgradeExtension
- ocrmnavigator.git.add
- ocrmnavigator.git.commit
- ocrmnavigator.git.diff
- ocrmnavigator.git.patch

- ocrmnavigator.git.pushTags
- ocrmnavigator.git.push

#### Total Workflow Freedom
While traditional extensions lock you into a specific UI or sequence, this modular approach allows for total variety. You can define a config item that stages files, commits with a specific message format, and pushes tags all in one click—or split them across different menu items based on your needs.

The Vision: This isn't just an extension; it's a suite of tools. What it lacks in automated triggers, it makes up for in total manual control and flexibility that you won't find in standard marketplace offerings.


### The Philosophy of Automation (or Lack Thereof)
In this extension, you will not find "passive" automation. Unless the benefit is astronomical, I will never implement a feature that runs in the background without user consent.

#### Why Passive Automation is Terrible
Most modern automation is unneeded. We have become accustomed to background processes constantly scanning, indexing, and eating CPU cycles. This is often a sign that a developer doesn't truly understand their user’s workflow. The result? Performance degradation and a tool that eventually becomes unusable.

My Rule: If a process can be a Triggered Activation Event, it should be. This gives you 100% of the power with 0% of the idle resource cost.

#### Examples of "Triggered" Power
To prove that triggered automation is superior to background bloat, here is how I manage my own massive devstack using this extension:
- Icon Library Automation: With one click, the system drops an SVG into a folder, converts it for React, bumps versions, compiles, updates the NPM README, commits to GitHub, and publishes. It’s so streamlined I often forget I haven't even opened a terminal.
- The 40,000+ Line package.json: Managing a file this size manually is impossible. I use a package.dev.jsonc with static markers. A triggered build script scans these markers and injects dynamically generated content instantly.
- Markdown Pre-processing: Documentation for 125+ extensions is handled via a README.dev.md. A single trigger converts variables, updates the TOC, maps sources, and transforms complex tables into GitHub-friendly inline HTML.
- Library Scanning: At build time, the extension scans 2,700+ components and templates, distributing that data to variables that power the Quick Picks and context menus in the editor.
- "The One Ring" Command: I have a single devstack line item that, when triggered, builds, compiles, and publishes every single one of my personal projects simultaneously.

#### The Performance Guarantee
Because everything is triggered, there are zero processes running in the background. We have all experienced VS Code performance issues where we had to start disabling extensions just to type smoothly. This extension rejects that reality. You get the functionality of a massive CI/CD suite, but it only exists when you ask for it.


### The Autorun System
The Autorun Folder is a unique architectural feature designed to let you execute custom logic at build time (or any other lifecycle stage) without polluting your codebase or your package.json scripts.

Instead of hardcoding new features or adding endless NPM scripts, you simply drop a standalone Node.js file into a specific folder. The extension handles the rest.

#### Key Benefits
- Rapid Implementation: Write a quick script, drop it in the folder, and it’s active. No need to ensure cohesion with the primary codebase.
- Cleaner package.json: Avoid "script bloat." You can have dozens of utility scripts without adding a single line to your manifest.
- Sequential Control: Scripts are executed alphabetically and sequentially. By naming your files (e.g., 01_setup.js, 02_process.js), you have total control over the execution order.

#### How to Implement
1. Create the Folder: By default, place a folder named autorun inside your src directory.
2. Custom Path: If your project uses a different structure (e.g., /app), update the setting:
  - `ocrmnavigator.AUTORUN_DIR`
3. Trigger the Scripts: To run all scripts within your autorun folder, call this command within your config:
  - `ocrmnavigator.autorun.trigger`

#### The "Updaters" Alternative
If you need a second, separate layer of scripts—perhaps for tasks you don't want running with your main build—you can use the Updaters folder:
- Location: Place a folder named updaters in your workspace root.
- Trigger: Use the command `ocrmnavigator.autorun.updaters.`

This provides a secondary, less-customized execution path for maintenance tasks, database migrations, or minor file updates that sit outside your core build logic.


### Dynamic Package Manager Detection
In modern development, switching between npm, pnpm, and yarn is common when jumping between projects. Most tools detect your package manager once when they load, which can lead to errors if you switch managers mid-session.

This extension takes a Just-In-Time (JIT) approach. Every time you trigger a command that requires a package manager (such as an NPM script or a build process), the extension performs a real-time check of your workspace.

- Zero Configuration: You don't need to tell the extension which manager you use. It looks for the presence of lockfiles (package-lock.json, pnpm-lock.yaml, or yarn.lock) at the moment of execution.
- Accuracy: If you migrate a project from npm to pnpm while VS Code is open, the very next command you run will automatically use pnpm without requiring a reload.
- Consistency: By checking at runtime rather than load time, we ensure that every command is executed with the toolchain your project actually expects.

#### Supported Managers:
The extension natively detects and executes commands for:
- npm
- pnpm
- yarn



### Intelligent Terminal & Command Engine
Most extensions spawn a new terminal instance every time you click a button, leading to a "terminal graveyard" by the end of the day. This extension uses a centralized Command Engine class to manage all terminal interactions through a single, intelligent interface.

#### The Smart Queue System
When you trigger a command, the engine performs a real-time status check:
- Idle Terminal: If the terminal is open and free, the command executes immediately.
- Busy Terminal: If a process is already running, the engine queues your next command. It will fire automatically as soon as the current task finishes.
- User Flow: This allows you to click multiple menu items in succession and return to your code, knowing the engine will handle the execution sequence in the background.

#### Self-Managing Dev Servers
The engine treats Dev Servers (persistent processes) differently than one-off scripts:
- Port Protection: If you trigger a dev server that is already running in an active terminal, the engine programmatically sends Ctrl+C to kill the old process before spawning the new one on the same port.
- Multi-Server Support: If you trigger a different dev server, the engine recognizes the port conflict isn't present and opens a dedicated terminal for that specific server.

#### The "Unified Switch" Architecture
Architecturally, every item type in your config—regardless of complexity—is routed through a single execution function. This unified logic powers the extension’s most advanced features:
- Nested Execution: Because the engine uses a recursive switch, you can nest Chains inside Concurrent items.
- Hybrid Workflows: You can create a "Launch" command that fires three tasks concurrently, while one of those tasks is actually a sequential "Chain" of three other scripts.
- Efficiency: This streamlined code path means less overhead, fewer bugs, and a consistent behavior across all command types.

#### The Unified Execution Engine
Historically, every command type had its own isolated function. The new architecture routes every single interaction through a Unified Switch. This is the "brain" of the extension that makes complex nesting possible.

By centralizing execution, the extension handles Chains (sequential) and Concurrent (parallel) tasks using the same core logic. This recursion is what allows for "absurd" configurations, like a concurrent block that triggers multiple independent chains.

#### Logic Preview (Simplified)
Here is a high-level look at how the engine processes your config items:

```typescript
export class TerminalManager {
  public async executeMaster(item: NavigatorItem | string, ctx, sequencer = false): Promise<void> {
    // the first check, is primarily for the use of the extensions internal functionality providing a quick and dirty way to fire off various vscode commands whenever needed.
    if (typeof item === "string") { await vscode.commands.executeCommand(item); return; }
    const workspaceFolder = vscode.workspace.workspaceFolders?.[0];
    if (!workspaceFolder) { vscode.window.showErrorMessage("No workspace folder found"); return; }
    const workspaceRoot = workspaceFolder.uri.fsPath;
    const storagePath = this.context.globalStorageUri.fsPath;
    switch (item.type) {
      case "file":
      case "md":
        // opens file in editor
        break;
      case 'snippet':
        // copies snippet to clipboard
        break;
      case 'url':
        // opens url in default browser
        break;
      case 'command':
        // executes vscode cmd
        break;
      case 'powershellCommand':
        // executes powershell command
        break;
      case 'debianCMD':
        // executes in specific debian enviroment
        break;
      case 'copyValue':
        // copies the value to clipboard
        break;
      case 'settingsToggle':
        break;
      case 'tasks':
        break;
      case 'layout':
        break;
      case 'apiCall':
        break;
      case 'search':
        break;
      case 'npmScripts':
        break;
      case 'fileAtLine':
        break;
      case 'label':
        break;
      case 'cmdChain':
        break;
      case 'chain':
        break;
      case 'concurrent':
        break;
      case 'folder':
        break;

    }

  }
}
```

#### Why this is a "Game Changer"
Because the engine is recursive (executeItem can call itself), the complexity you can achieve is limited only by your imagination.
- Sequential Chains: You can ensure that a "Test" command finishes successfully before the "Deploy" command even starts.
- Parallel Power: You can launch your frontend, backend, and database watcher simultaneously.
- Hybrid Nesting: You can create a Concurrent item where:
  - Task A starts immediately.
  - Task B is a Chain that runs a build script, then a cleanup script.
  - Task C starts a dev server (which the engine will smartly restart if it's already running).

This level of orchestration ensures that no matter how many tasks you trigger, the extension manages the terminal state, the sequence, and the resource overhead without you ever needing to intervene.

#### The Power of Nested Logic
If you look closely at the engine's execution flow, you’ll notice a "weird" behavior that is actually its greatest strength: Recursive Nesting.

Because the engine routes every item through the same centralized logic, you can create hybrid configurations that mix sequential and parallel execution in ways standard extensions don't allow.

#### A Developer’s Advantage
From a maintenance perspective, this "One Ring" function makes the extension incredibly lean:
- Centralized Logic: Every new item type added to the extension only needs to be defined in one place.
- Code Efficiency: We achieve massive functionality with a fraction of the code, leading to fewer bugs and a significantly smaller extension footprint.
- Infinite Flexibility: This isn't a locked-down UI; it's an execution engine. You aren't limited by how I think you should work, but by how you choose to nest your commands.

Bottom Line: By moving away from "one function per item" and toward a unified execution switch, the extension gains a level of "absurd" power and efficiency that makes it a true CI/CD-grade tool inside your editor.

#### Concurrent & Chain


### Autonomous Maintenance: Local Instance Scans
Maintaining an extension of this scale—covering the functionality of 125+ individual tools—would normally be an impossible chore. To solve this, the extension uses Autonomous Scanning to keep its data fresh without me ever having to lift a finger.

#### Real-Time vs. Hardcoded
Rather than relying on static lists that go out of date the moment a new version of VS Code or a library is released, I have implemented dynamic scanning strategies.

#### Example: VS Code Commands 
While there is a manual list of core VS Code commands, the extension also features a Live Instance Scanner. It queries your specific VS Code environment to generate a command list on the fly.
- As VS Code updates, your list updates.
- I never have to manually add new VS Code features to the codebase.
- Eventually, as these dynamic counters parts prove their reliability, the manual lists will be phased out entirely.

#### Other Self-Sustaining Systems:
- Icons QuickPick: Unlike the native VS Code icon picker, which is rarely updated, this extension scans the icon library at runtime. If a new icon is added to the source, it appears in your QuickPick immediately.
- Icons context menu
- Catalyst-UI Components Quickpick: The 2,700+ components and templates are managed via dynamic discovery. The extension scans the library and populates the inventory and display functions automatically.
- Catalyst-UI context menu
- Contextual Menu Options: The extension scans your local environment to ensure that the menu options presented to you are relevant to the tools you actually have installed and active.

### Naming Conventions: Functions & Settings
As this extension has grown to include over 1,500 commands, the risk of "naming collisions" (where two commands share the same name) has become a reality. To prevent these conflicts and make the API more intuitive, I am transitioning all internal and exposed functions to a hierarchical naming convention.

#### The Shift: From Flat to Hierarchical
Previously, commands followed a standard extension.function format. Moving forward, all commands are being recategorized into a taxonomic structure:
- Old Way: `ocrmnavigator.gitPush`
- New Way: `ocrmnavigator.git.push`

#### Benefits and reasons for the change
- Instant Debugging: If an error occurs, the command name itself now tells you exactly which module (Git, Archiver, UI, etc.) is responsible, without needing to search the entire codebase.
- API Discoverability: It is now much easier to guess or memorize functions. If you need a Git tool, you know it starts with ocrmnavigator.git.
- Future-Proofing: This structure allows us to merge large sub-extensions (like the recent "To-Do" extension integration) without worrying about breaking existing features.

#### Settings & Migration
This same logic is being applied to the Extension Settings.
- New Settings: Will follow the category.subcategory.setting format.
- Legacy Settings: To avoid breaking your existing settings.json files, current settings will remain as-is for now.

> [!CAUTION] 
> Work in Progress: 
> I am currently in the process of converting all 1,500+ commands. If you are referencing the old naming convention in your custom configs, be aware that these may stop working as they are migrated to the new system. If a command fails, check the logs—it has likely just moved to its new hierarchical home.


### pro7: Workspace Secrets & Encrypted Backups
Managing .env files and sensitive credentials across multiple workstations can be a headache. Standard practices often involve third-party "Secret Managers," but those often come with monthly costs or complex setups.

My solution—built directly into this extension—is a Password-Protected Archive workflow.

#### The Logic: Local Encryption, Global Access
Instead of relying on external platforms, this feature allows you to bundle your secrets into a password-protected ZIP archive before pushing your project to GitHub. This provides three major benefits:
- Portability: Your secrets travel with your repository. No matter which workstation you sit down at, your .env files are just a decryption away.
- Versioning: Your secrets are backed up alongside your code history.
- Zero Cost: No need for third-party subscriptions; the encryption is handled locally.

This functionality is easily accessible via the Devstack Quick Pick menu.

> [!CAUTION]
> Critical Warning for Extension Developers
> If you are using this feature while building VS Code extensions, there is one major caveat: Do not include your encrypted .7zip inside your final .vsix package.
> The VS Code Marketplace runs an automated virus scan on every upload. Because password-protected archives are encrypted, scanners cannot see inside them. To a security bot, an unreadable file is a high-risk threat.
> The Result: Your extension will fail the automated check and trigger a manual review (and rejection) from Microsoft.

The Fix: Ensure your archive is excluded from the build or listed in your .vscodeignore file before publishing.






### Context

### VSIX Archiver

### Publishing To Marketplace

###


#### Configuration Settings


All settings are prefixed with `ocrmnavigator.` and can be configured in your VS Code settings.

#### Core Settings

**Tasks & NPM Scripts**
- `tasks` (boolean, default: `true`) - Controls whether the 'Tasks' folder is displayed in DevStack explorer as a global folder. Items from tasks.json are automatically populated.
- `npmScripts` (boolean, default: `true`) - Controls whether the 'NPM Scripts' folder is displayed in DevStack explorer as a global folder. Items from package.json scripts are automatically populated.

**Performance Management**
- `todoNotesReminders` (boolean, default: `true`) - Enables initialization of todo, notes, reminders and post-its. Set to false to reload VS Code quicker when actively working on project issues, as this feature logs in and pulls a repo at initialization.
- `GBL_DISABLE` (boolean, default: `false`) - Global disable toggle. Do not set manually unless you need to change it back to false in settings.json.
- `WS_DISABLE` (boolean, default: `false`) - Workspace disable toggle. Do not set manually unless you need to change it back to false in settings.json.
- `F_DISABLE` (boolean, default: `false`) - File disable toggle. Do not set manually unless you need to change it back to false in settings.json.
- `EXT_DISABLE` (boolean, default: `false`) - Extension disable toggle. Do not set manually unless you need to change it back to false in settings.json.

#### Code Snapshot Settings

**Visual Appearance**
- `backgroundPalette` (enum, default: `"pinky"`) - Background gradient palette for code snapshots. Options: magnum, pinky, passion, steel, tropic, forest, blueman, sand
- `containerBackground` (string, default: `""`) - Custom background CSS that overrides backgroundPalette if set
- `boxShadow` (string, default: `"rgba(0, 0, 0, 0.55) 0px 20px 68px"`) - Box shadow for the snapshot window
- `containerPadding` (string, default: `"3em"`) - Padding around the snapshot container
- `windowBorderRadius` (string, default: `"10px"`) - Border radius for the snapshot window

**Window Controls**
- `windowControlStyle` (enum, default: `"Windows"`) - Window control style. Options: None, OS X, Gray dots, Windows
- `showWindowTitle` (boolean, default: `true`) - Show window title in snapshot
- `windowTitleStyle` (enum, default: `"Workspace + Filename"`) - Window title display format. Options: Workspace + Filename, Filename, Custom
- `windowTitleCustomStyle` (string, default: `""`) - Custom window title text (used when windowTitleStyle is 'Custom')

**Display Options**
- `showLineNumbers` (boolean, default: `true`) - Show line numbers in snapshot
- `realLineNumbers` (boolean, default: `false`) - Use real line numbers from editor (starts at actual line number in file)
- `transparentBackground` (boolean, default: `false`) - Use transparent background for snapshot
- `target` (enum, default: `"container"`) - Snapshot target. Options: container (includes background), window (just the code window)
- `trimEmptyLines` (boolean, default: `true`) - Trim empty lines from the beginning and end of snapshot

#### GitHub Integration

**Repository Configuration**
- `repo` (string, default: `""`) - Repository name (e.g., "DevStack")
- `owner` (string, default: `""`) - Repository owner username (e.g., "8an3")
- `branch` (string, default: `""`) - Branch name (e.g., "main")
- `repository` (string, default: `""`) - Full repository path (e.g., "8an3/DevStack")
- `remote` (string, default: `""`) - Remote repository URL (e.g., "https://github.com/8an3/DevStack.git")
- `ATAT` (string, default: `""`) - GitHub personal access token
- `octokit` (string, default: `""`) - Octokit configuration

**Sync Settings**
- `lastSyncTimestamp` (string, default: `""`) - Last synchronization timestamp
- `lastSHA` (string, default: `""`) - Last commit SHA
- `autoSync` (boolean, default: `true`) - Enable automatic synchronization
- `isPriv` (boolean, default: `false`) - Whether repository is private
- `syncOnSave` (boolean, default: `true`) - Sync on file save
- `syncInterval` (string, default: `"30"`) - Sync interval in minutes
- `checkRemindersInterval` (string, default: `"10"`) - Reminder check interval in minutes

#### Build & Automation Settings

**Package Management**
- `CONCURRENT` (string, default: `"stable"`) - Determines concurrent function mode. Options: 'stable', 'bleeding-edge'
- `PKG_MGR` (string, default: `"pnpm"`) - Fallback package manager for extension scanner

**Autorun Configuration**
- `AUTORUN_SCRIPTS` (boolean, default: `false`) - Within G4 & .vsix function, enables activation of all Node.js scripts in specified folder
- `AUTORUN_DIR` (string, default: `"src"`) - Directory containing the autorun folder (e.g., 'src' or 'app'). Leave empty to use workspace root.

**Build Options**
- `ARCHIVER` (string, default: `"custom"`) - Within G4 & .vsix function, chooses which archiver to use. Options: 'custom', 'vsce'
- `PRO7` (boolean, default: `false`) - Within G4 & .vsix function, enables secure archiving of secrets before pushing to GitHub
- `DELETE_OLD_VSIX` (boolean, default: `false`) - Within G4 & .vsix function, enables deletion of old vsix archives
- `AUTO_INSTALL_VSIX` (boolean, default: `false`) - Within G4 & .vsix function, enables auto-installing the archive
- `OPEN_PUB_DASH` (boolean, default: `false`) - Within G4 & .vsix function, enables auto-opening Microsoft's publisher dashboard
- `RELOAD_INSTANCE` (boolean, default: `false`) - Within G4 & .vsix function, enables auto-reload after installing newly created archive
- `UPDATE_PROMPT_OBJECTS` (boolean, default: `false`) - Updates prompt objects
- `CONVERT_README_DEV_MD` (boolean, default: `false`) - Converts README.dev.md to README.md during build

#### UI & Interface Settings

**Quick Pick Menus**
- `BE_QP` (boolean, default: `false`) - BE Quickpick menu found on the status bar

**Editor Behavior**
- `AUTO_FOLD_PKG` (boolean, default: `false`) - Auto fold level 2 when opening package.json
- `vscodeVersion` (string, default: `"Code"`) - VS Code version identifier. Use 'Code' for VS Code or 'Code - Insiders' for VS Code Insiders. Controls where settings files are pulled from.

**Navigation**
- `configPath` (string, default: `".vscode/ocrmnavigator/search-config.json"`) - Path to the search configuration file
- `toggleHiddenItems` (boolean, default: `true`) - Toggle visibility of chain items in UI (items with hidden: true)

#### Feature Toggles

**Development Tools**
- `commands` (boolean, default: `true`) - Enables VS Code commands
- `vscodecmdref` (boolean, default: `true`) - Enables VS Code commands reference sheet
- `markdownViewer` (boolean, default: `true`) - Enables markdown viewer
- `snippets` (boolean, default: `true`) - Enables snippets editor and viewer via nav
- `snippetsInEditor` (boolean, default: `true`) - Enables snippets via context menu in editor
- `editorContextSnippets` (boolean, default: `true`) - Enables Editor Context Snippets via context menu in editor
- `formatters` (boolean, default: `true`) - Enables formatters and configurator
- `trailingCommas` (boolean, default: `true`) - Enables removal function for trailing commas
- `batchRename` (boolean, default: `true`) - Enables batch rename via context menu in editor

**Framework-Specific Tools**
- `eslintPrettier` (boolean, default: `true`) - Enables adding ESLint & Prettier configs
- `remixUtils` (boolean, default: `true`) - Enables Remix utilities via context menu in editor
- `remixComponents` (boolean, default: `true`) - Enables Remix components via context menu in editor
- `shadCNComponents` (boolean, default: `true`) - Enables ShadCN Components via context menu in editor
- `convertToAgnostic` (boolean, default: `true`) - Enables Convert To Agnostic, converting a Remix Run route to your choice

**Theme & Appearance**
- `theme` (boolean, default: `true`) - Enables VS Code theme builder
- `blackedOut` (boolean, default: `true`) - Enables Blacked Out & Diff & Reset themes
- `windowDifferentiator` (boolean, default: `true`) - Enables Window Differentiator via context menu in editor
- `colorWheel` (boolean, default: `true`) - Enables color wheel tool

**Database & Backend**
- `prismaFunctions` (boolean, default: `true`) - Enables Prisma Functions via context menu in editor
- `clickToSchema` (boolean, default: `true`) - Enables click to schema object
- `crudResolvers` (boolean, default: `true`) - Enables Generate CRUD Resolvers / REST End Points via context menu in editor
- `strPrismaUpdater` (boolean, default: `true`) - Automatically adds scripts to package.json with specific custom commands. Runs when STR runs a task.

**Git & GitHub**
- `repoMgr` (boolean, default: `true`) - Enables GitHub Repo Management
- `openGithub` (boolean, default: `true`) - Enables 'Open GitHub Repo In Browser' via context menu in editor
- `githubFunctions` (boolean, default: `true`) - Enables Github Functions editor functions via context menu in editor

**File Management**
- `fileNesting` (boolean, default: `true`) - Enables file nesting
- `revealExplorer` (boolean, default: `true`) - Enables reveal in explorer via right-clicking items in nav
- `copyPath` (boolean, default: `true`) - Enables copy path via right-clicking items in nav
- `bookmarks` (boolean, default: `true`) - Enables bookmarks
- `searchBar` (boolean, default: `true`) - Enables the search bar function for the nav
- `createFolderSmartIndex` (boolean, default: `true`) - Enables Create Folder Smart Index (Registry)

**Utilities**
- `clipBoardHistory` (boolean, default: `true`) - Enables clipboard history pro
- `lucideIcons` (boolean, default: `true`) - Enables Lucide icons integration
- `share` (boolean, default: `true`) - Enables share with a friend
- `url` (boolean, default: `true`) - Enables URL links in the nav
- `viewers` (boolean, default: `true`) - Enables viewers functionality
- `uiDashboard` (boolean, default: `true`) - Enables UI Dashboard
- `tailwindConverter` (boolean, default: `true`) - Enables Tailwind Converter button within title bar menu

**Code Cleanup**
- `jsonComments` (boolean, default: `true`) - Enables removal function for JSON comments
- `con` (boolean, default: `true`) - Enables removal function for all console.logs from files
- `removeAllComments` (boolean, default: `true`) - Enables removal function for all comments from files
- `unusedFunctions` (boolean, default: `true`) - Enables unused function finder

**DevStack Features**
- `devStackFunctions` (boolean, default: `true`) - Enables DevStack editor functions via context menu in editor
- `concurrent` (boolean, default: `true`) - Enables the concurrent command feature set within DevStack
- `autoSequencer` (boolean, default: `true`) - Enables the chain command feature set within DevStack
- `openLeftOffNote` (boolean, default: `true`) - Enables Left Off Note
- `renderMd` (boolean, default: `true`) - Enables the render MD option within editor context menu

**Additional Settings**
- `PROMPT_OBJECTS_DIR` (string, default: `"F:/playground/md/"`) - MD prompt objects path
- `rootPath` (string, default: `""`) - Root path configuration
- `notesDir` (string, default: `""`) - Notes directory path
- `other` (string, default: `null`) - Other configuration options


