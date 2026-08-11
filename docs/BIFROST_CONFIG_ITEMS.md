# BIFRÖST

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Item Types

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

#### `chain` 
##### Sequential Execution
Execute commands one after another in your specified order. When creating items through the interface, the concurrent/sequential creation process enters a for loop allowing you to add as many custom or listed commands as needed.

```json
{ 
  "label": "Kill Terminals && Start DEV Server", 
  "path": "saveall, killterms, devApp", 
  "type": "chain" 
}
```

**Advanced Usage**: Mixed sequential/concurrent flows, conditional execution

**Preview**: [Video](https://youtu.be/ySp83VqxQ8s) | [Image](https://raw.githubusercontent.com/8an3/midgardr-notes/blob/main/vfs/SequentialExecution+.gif?raw=true)

##### Unique Example #2

This one wont be as unique, but will demonstrate... just how far and how much can be automated through the terminal engine. Save on space, I won't include EVERY single item... as with this one there... is a lot to it.

- End result, have 4 of my personal projects, do whatever it is each needs to do in order to update, copy, paste, compile, push, delete, and a great many of other things
    - projects effects:
      1. devstack
      2. icons
      3. ui
      4. devstack command line
      5. css 
- Build Projs Nuke ( in my config, whenever I have a command that encompases all within the given context, using nuke for a shortened naming convention and typically having the explanation in the tooltip )
   - at this point, not only making it easier to build this command but also to allow me to trigger each command on its own each of the following projects does have an item associated with it allowing me to execute one whenever needed instead of all of them. Each of the main items are chain or concurrent item types
   1. devstack
      - each of the commands in this chain goes as follows:
      1. trigger auto run folder
      2. copy over ui libraries inventory objects
      3. copy over icon libraries inventory 
      4. create both ui and icon quickpick and editor context menus to ensure both lists are updated
      5. convert package.dev.json
      6. compile
      7. delete pro7 archive ( the only reason I take this step instead of relying on .vscodeignore, is because I have already talked to their security team because I had inadvertently included a password protected archive among the items that were pushed when creating the .vsix )
      8. create custom .vsix archive
      9. push new archive
      10. install new archive
      11. create new pro7 archive
      12. push to clean local repo
      13. bump minor
      14. push tags
**if it weren't for the autorun feature, this list would be a lot longer, but having it lets you dump... in whatever number you may need, scripts that run execution.**
  2. icons
     1. takes whatever svgs that are currently in the svg folder, create the react components needed to use them within a project
     2. compiles 
     3. scans the newly created items from the src folder, and with their filenames creating an unorded list between two markers set within the readme.md file after it deleting the entire section first
     4. pushes to github
     5. updates minor
     6. pushes tags
     7. push to npm ( this command I actually lost for a while, due to the fact of not knowing exactly how the new required commands / pat system worked with npm since they do not want you to progmatically update your libraries anymore, it seems. Adding pain to injury, I hope this has changed, but I must have read the docs day one of the new requirement... as there were virtually none on their site, aside from a banner notifying users of said new requirement. I do have to manually adjust this command... once every 90 days I think but atleast its only doing something manually once in that time instead of every single time with a newly created pat because, to my knowledge and hopefully I'm proved wrong in this regard, creating said pat manually on their site. Which is bulshit imo as far as secuirty is concerned. This is such a low point of entry for attackers, it is FAR easier to go after the user instead, once you have control of their accounts, the attacker... once every 90 days... can still go in and create their own token. )

Anyways... you get the point of taking chores that are required of us that take in some cases quite a while, but instead it runs itself with a click at which time I play a round of aram in lol as this command does effect a lot of projects. For you though, if you didn't want to create a nuke sized command like mine, but would still love to benefit from the same automation for any individual project you may have, executing one of the orders 1 through 11 will net the end result you are looking for. <a href="https://github.com/8an3/midgardr-notes/blob/main/docs/CUSTOM_FUNCTIONS.md">Custom functions</a> does a break down on them that will work in a great many variety of project structures and architectures, OR you can also build it out yourself with devstack since each function is built in a modular fashion and each of them are exposed to you to use.

#### `argChain`

Works virtually the same as chain aside from the fact it does not need items to be contained in the config in order to run as it takes chain value in args, allowing you to pass all the command objects through instead have to save them as config items

#### `argConcurrent`

The same as above but using concurrent in place of chain used in args

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


#### `conditional`

> [!NOTE]
> I know I should have built this a while back, but have been putting this off do to other things needing to get done, and I wasn't going to do this just yet but I just had another use case for it so... lets just get it done.
> 
> Also, the terminal ngins original architecture came in such beautiful ways to use with this new item type, since I was able to create it with UNLIMITED nesting capabilties... with zero tax in the form of coding it. If you wanted to, you can go 100 deep with no issue. Coupled with the two new item types pertaining to chain and concurrent... those three things turned this from requireing... 100's and 100's of lines of code, down to less than 50 I think it was.

I will leave conditionChain in the ngin as it is already coded, and to be fair if you want a quick and dirty way atleast you still have it. 

This one on the other hand, is quite a bit different since this item type can be housed within itself 100%, meaning you do NOT need to reference anything from your config if you don't wish to include those items. As this item type can include everything needed for it to run, as when it comes to command sequences like this it can get weird with edge cases, and include items that will never see use outside this one object.

conditionChain, if I'm remembering correctly, can only go one condition deep. Where as this item type, it is trully unlimited in terms of depth or in other words unlimited nesting capabilties.

## Condition Types Reference

| type | `path` | `args[0].value` |
|---|---|---|
| `fileExists` | absolute or workspace-relative file path | — |
| `fileNotExists` | absolute or workspace-relative file path | — |
| `folderExists` | absolute or workspace-relative folder path | — |
| `folderNotExists` | absolute or workspace-relative folder path | — |
| `configValue` | VS Code config key e.g. `editor.fontSize` | optional — value to match against, truthy check if omitted |
| `envVariable` | env var name e.g. `NODE_ENV` | optional — value to match against, truthy check if omitted |
| `commandOutput` | shell command to run | optional — stdout string to match against, truthy (any output) if omitted |
| `portInUse` | port number as string e.g. `"3000"` | — |
| `portNotInUse` | port number as string e.g. `"3000"` | — |
| `custom` | JS expression string evaluated in `vm.runInNewContext` with `workspaceRoot` in scope | — |


The `conditional` type executes an initial block (or evaluates a static condition) and then branches into `onSuccess`, `onFailure`, `always`, or other condition checks based on the result.

## Execution Flow

```
conditional item
│
├── [Root] — one of:
│     a) item.path → executed as powershellCommand
│     b) args[0].type = "argChain" → chains items in args[0].args sequentially
│     c) args[0].type = "argConcurrent" → runs items in args[0].args concurrently
│     d) args[0].type = "fileExists" / "fileNotExists" / "folderExists" /
│        "folderNotExists" / "configValue" / "envVariable" /
│        "commandOutput" / "portInUse" / "portNotInUse" / "custom"
│        → no execution, condition evaluated directly, result = true/false
│
└── [Branches] — remaining args[] evaluated in order:
      onSuccess   → exe[] runs if root succeeded / condition was true
      onFailure   → exe[] runs if root failed / condition was false
      always      → exe[] always runs regardless
      fileExists / fileNotExists / folderExists / folderNotExists /
      configValue / envVariable / commandOutput /
      portInUse / portNotInUse / custom
                  → exe[] runs if that condition evaluates to true
```

Every item inside any `exe[]` array — and inside `args[0].args` — is a full `NavigatorItem` shaped object passed through `createNavigatorItem` before `executeMaster`, meaning any supported type can be nested inside including another `conditional`.

 

---

## Full Nested Example

```json
{
  "label": "Deploy Pipeline",
  "type": "conditional",
  "icon": "rocket",
  "path": "npm run build",
  "args": [
    {
      "type": "onSuccess",
      "exe": [
        {
          "label": "Run Tests",
          "type": "conditional",
          "path": "npm run test",
          "args": [
            {
              "type": "onSuccess",
              "exe": [
                {
                  "label": "Check Port 3000 Free Before Deploy",
                  "type": "conditional",
                  "path": "",
                  "args": [
                    {
                      "type": "portNotInUse",
                      "path": "3000"
                    },
                    {
                      "type": "onSuccess",
                      "exe": [
                        {
                          "label": "Commit And Push",
                          "path": "saveall, commitpush",
                          "type": "chain",
                          "icon": "gitlab"
                        },
                        {
                          "label": "Check NODE_ENV Is Production",
                          "type": "conditional",
                          "path": "",
                          "args": [
                            {
                              "type": "envVariable",
                              "path": "NODE_ENV",
                              "args": [{ "value": "production" }]
                            },
                            {
                              "type": "onSuccess",
                              "exe": [
                                {
                                  "label": "Bump Patch Version",
                                  "path": "saveall, PatchVersion",
                                  "type": "chain",
                                  "icon": "gitlab"
                                }
                              ]
                            },
                            {
                              "type": "onFailure",
                              "exe": [
                                {
                                  "label": "Notify Wrong Env",
                                  "path": "echo NODE_ENV is not production, skipping version bump",
                                  "type": "powershellCommand"
                                }
                              ]
                            }
                          ]
                        }
                      ]
                    },
                    {
                      "type": "onFailure",
                      "exe": [
                        {
                          "label": "Kill Port 3000",
                          "path": "npx kill-port 3000",
                          "type": "powershellCommand"
                        }
                      ]
                    }
                  ]
                }
              ]
            },
            {
              "type": "onFailure",
              "exe": [
                {
                  "label": "Check If Test Report Exists",
                  "type": "conditional",
                  "path": "",
                  "args": [
                    {
                      "type": "fileExists",
                      "path": "coverage/lcov-report/index.html"
                    },
                    {
                      "type": "onSuccess",
                      "exe": [
                        {
                          "label": "Open Test Report",
                          "path": "coverage/lcov-report/index.html",
                          "type": "file"
                        }
                      ]
                    },
                    {
                      "type": "onFailure",
                      "exe": [
                        {
                          "label": "Notify No Report",
                          "path": "echo No test report found",
                          "type": "powershellCommand"
                        }
                      ]
                    }
                  ]
                }
              ]
            },
            {
              "type": "always",
              "exe": [
                {
                  "label": "Cleanup Temp",
                  "path": "rimraf .tmp",
                  "type": "powershellCommand"
                }
              ]
            }
          ]
        }
      ]
    },
    {
      "type": "onFailure",
      "exe": [
        {
          "label": "Notify Build Failed",
          "path": "echo Build failed, aborting pipeline",
          "type": "powershellCommand"
        }
      ]
    },
    {
      "type": "always",
      "exe": [
        {
          "label": "Write Build Log",
          "path": "echo Pipeline finished >> build.log",
          "type": "powershellCommand"
        }
      ]
    }
  ]
}
```

---

## What This Example Does Step By Step

1. **Root** — runs `npm run build` as a `powershellCommand`
2. **onFailure (root)** — if build fails, echoes a failure message and stops that branch
3. **always (root)** — regardless of build result, appends a line to `build.log`
4. **onSuccess (root)** — if build passes, enters a nested `conditional` that runs `npm run test`
5. **onSuccess (tests)** — if tests pass, enters another nested `conditional` that checks if port `3000` is free
6. **portNotInUse (3000) → onSuccess** — if port is free, chains `saveall, commitpush`, then enters another nested `conditional` checking `NODE_ENV === "production"`
7. **envVariable NODE_ENV → onSuccess** — bumps patch version
8. **envVariable NODE_ENV → onFailure** — echoes a warning that the env is wrong
9. **portNotInUse (3000) → onFailure** — if port is occupied, kills it via `npx kill-port 3000`
10. **onFailure (tests)** — if tests fail, checks if the coverage report file exists, opens it if it does, echoes a message if it does not
11. **always (tests)** — regardless of test result, cleans up `.tmp`



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

> [!TIP]
> We'll explain this one with a use case, your in one workspace, but you want to execute commands in another project / workspace that you do not currently have open. Previously there was really no way to cleanly do this automatically through the terminal ngin since it was changed to continously re-use the same terminal instance as you code, instead of creating a new instance each and every single command you execute.
> Placing `xPath` and its value, the projects folder you would like to run the desired command, within the args array will allow you to do just that.
> - cd's into the other project
> - executes command
> - cd's back into your workspace folder so as not to interrupt the terminal ngins flow of command execution
> `{ "label": "pnpmrungenerateBaldr", "path": "pnpm run generate", "args": [{ "xPath": "F:/baldr" }], "type": "powershellCommand", "icon": "versions", "hidden": true }`

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

##### Unique Example #1

As time goes on I will be sure to come back to include more unique examples as this was the first in which I had created in ways... that were never intended when I first built this item type.

```json
        {
          "label": "VSIX: Send to microsoft to update listing",
          "path": "https://marketplace.visualstudio.com/skyler/extensions/ocrmnav",
          "type": "apiCall",
          "icon": "json",
          "args": [
            { "method": "POST" },
            { "headers": { "Content-Type": "application/json;api-version=7.1-preview.1", "Authorization": "Bearer ${MS_PAT}", "Accept": "application/json;api-version=7.1-preview.1" } },
            {
              "body": {
                "version": "1.0.1",
                "assetTypes": [
                  "Microsoft.VisualStudio.Services.VSIXPackage"
                ],
                "files": [
                  { "assetType": "Microsoft.VisualStudio.Services.VSIXPackage", "source": "${MS_VSIX}" }
                ],
                "flags": "1"
              }
            }
          ]
        },
```

At the time, and at the mercy of the stupidity that is AI, I was trying figure out the http url for the rest api to update extension packages. I hate microsofts docs so I opted to obtain the information from an ai engine. It usually doesn't get it as wrong as it did this time as around, since a rest api doesn't even exist. BUT without taking this stupid journey I probably would have never used an api call this way... so atleast something cool came about it still.

As you have probably noticed thre are a couple of weird things, the first being that ${MS_PAT} is contained in double quotes. So as to not expose your enviroment secrets till the very last second, the terminal engine itself is responsible for grabbing the secret, placing it into the command, or http request in this case, just before execution. This method works on every single command type.

The second, more weirdly placed item, is the source of the vsix. As having to create a new item, for each and every single extension version would just be dumb, I knew at the time that it would be sent as base64 encoded string. Creating a new value in my .env file, placing the encoded string there allows me to swap it at will. This was about the time I decided to open the docs or else I would have taken it a step further, which you can do yourself if you find the need for it.

Taking it further by:
- creating a script grabbing the latest .vsix by date
- creating a bas64 encoded string off of it
- replacing the old string in the .env file 
- trigger the api call

And this is something you an actually do all on your own through a chain command, and completely automate the entire process of whatever use case your project needs. taking a rather mundane task that needs to be repeated, to a single click.

```md
# API Call Configuration

# Required fields
label: vsix rest api
path: https://marketplace.visualstudio.com/skyler/extensions/ocrmnav
type: apiCall

# Optional fields
icon: cloud
tooltipText: Description of this API call

# HTTP Configuration (optional)
args:
  - method: POST
  # For POST/PUT/PATCH requests with body:
  # - method: POST
- body:
       - version: 1.0.1
      - assetTypes: ["Microsoft.VisualStudio.Services.VSIXPackage"]
      - files:  [{ "assetType": "Microsoft.VisualStudio.Services.VSIXPackage", "source": ${MS_VSIX}$ }]
      - flags: 1

# Headers (optional)
headers:
  - Content-Type: application/json;api-version=7.1-preview.1
  - Authorization: Bearer ${MS_PAT}
  - Accept: application/json;api-version=7.1-preview.1
  # - Authorization: Bearer YOUR_TOKEN

# Instructions:
# - Fill in the required 'path' field with your API endpoint
# - Uncomment and modify optional sections as needed
# - Save this file to create the API call item
# - Close without saving to cancel
```

#### `layout`

[Layout Configuration Guide](./BROKKR.md)

#### `menu`

While working in a project, where its honestly kind of a pain to get around, not to mention it has 20-30 script files. I wanted to be able to click one item, and have it display all the options with a description, but I hate quick picks and hopefully I don't have to resort to that, since using the terminal I've already had to come up with weird solutions in order to get it working. 

When this item type is clicked it opens a terminal editor, opening at the menu screen. Moving up and down, moves your selected line or cursor, if you will. 
Beautifully, the terminal ngin is already in place and can be leveraged nicely in this use case, making it so that this item type remains persistent till you cancel it.
When ever you select a menu item, it fires it off to the ngin to take care, which... if you are triggering scripts like I am, it executes that script in a seperate terminal. Obviously I'll have to make changes in my own scripts to take advantage of this. But whenever you go to create them, if it needs paths or other values, I'll be coding mine in a way so that whenever it executes it prompts the user for whatever values are needed instead of constantly adjusting script files. 

You CAN place a menu type item... inside another menu type item, creating a nested menu structure with no restrictions in place. 

I may or may not be doing this myself but I will atleast try it. Since an item's path can either be the full path or relative, say you have 10 projects of scripts ( or whatever you want to place here ) that you want to place in the menu, the root level menu could be project names, while the second level features that projects scripts to run. Granting access to scripts to trigger no matter what workspace you are currently working in, as long as the main item is placed within a global folder ofcourse in the config.

There is no creator for this yet, so this will have to be created manually for the time being.

```json
        {
          "label": "BIFRÖST Menu",
          "path": "",
          "type": "menu",
          "icon": "menu",
          "args": [
            { "label": "Auto blocks", "path": "node ./F:/playground/scripts/auto-blocks.js", "type": "powershellCommand" },
            { "label": "backup-devstack-core-files", "path": "node ./F:/playground/scripts/backup-devstack-core-files.js", "type": "powershellCommand" },
          ]
        },
```

Nested Menus
```json
        {
          "label": "BIFRÖST Menu",
          "path": "",
          "type": "menu",
          "icon": "menu",
          "args": [
            { "label": "Auto blocks", "path": "node ./F:/playground/scripts/auto-blocks.js", "type": "powershellCommand" },
            { "label": "backup-devstack-core-files", "path": "node ./F:/playground/scripts/backup-devstack-core-files.js", "type": "powershellCommand" },
            {
              "label": "BIFRÖST Menu",
              "path": "",
              "type": "menu",
              "icon": "menu",
              "args": [
                { "label": "Auto blocks", "path": "node ./F:/playground/scripts/auto-blocks.js", "type": "powershellCommand" },
                { "label": "backup-devstack-core-files", "path": "node ./F:/playground/scripts/backup-devstack-core-files.js", "type": "powershellCommand" },
              ]
            },
          ]
        },
```

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

IF you want to try your hand at creating your own label, in the below accordian you will find a number of special chars to use. NOTE: I didn't spend too much time on it, but I KNOW some of these will not render in vscodes file tree. Once I found the above labels worked, I stopped there. Just wanted to warn you before you started, it won't negatively impact anything in any shape or form... it just won't render and it will be an empty line item and because of that feel free to test them all out. The easiest way to test these items, is editing the config so just be sure to save a copy as a backup before you do, and use r window in devstack quickpick menu to quickly restart the instance.


<details>
<summary>Label List...</summary>

```json
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
``` 

</details>

> [!TIP] 
>
> This unexpected feature will only be available by manually edting the workspace / global config files.
>
> You may nest line items together by placing an items array inside any config type, which will render a accodrian arrow beside the line item so that the config items functionality remains intact while also providing a means of group similarily funcitioned line items together for organization. Or simply put turning a line item into a folder that acts like a line item itself.
>
> I did not plan this and honestly only found out about it when I was testing a feature out and it perfectly deleted a section of my config making it so that a items array was placed inside another object. Amazingly, that perfect deletion didn't error out the config file and when it ran fine.
>
> A win through a mistake is still a win.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Using Dynamic Variables With Config Items

Currently there are two variables that the terminal ngin scans for and reacts by acquiring the required value in order for that function to operate correctly.

- .env Variables
- Dynamically setting ports for dev servers and such

### .env
For security reasons, the extension does not load environment variables when the extension starts. Instead, variables are resolved "just-in-time":
- Lazy Loading: The extension stores the raw string (e.g., ${NPM_TOKEN}) and only injects the actual value at the moment of execution.
- Scoped Access: Because variables are pulled at runtime, they are scoped to the .env file present in the active project, preventing cross-project credential leakage.


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

### ${PORT}

#### Configuration Example
Use ${PORT} any time you would like the terminal ngin to assign ports for you, to as many services as you need to run at any given time:

```json
{
  "label": "dev",
  "path": "npm run dev -p ${PORT}",
  "type": "powershellCommand"
},
```