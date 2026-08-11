# BIFRÖST

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Architecture Notes

This section provides a deep dive into the underlying systems of this extension. Understanding these architectural choices will help you write more effective configurations and leverage the full power of the codebase.

With the recent redesign, the project has moved toward an engine-based, object-oriented approach. By utilizing dedicated classes for core logic, the codebase is more efficient, modular, and easier to extend.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Core Architectural Priorities
The topics below are ranked by their impact on your development workflow. High-priority items focus on the modular systems you will interact with daily, while lower-priority items cover "under-the-hood" utilities.

1. Modular Engine Structure (High Priority) Learning how our engines and classes interact is the most valuable use of your time. This modularity allows you to hook into specific functionalities and customize the extension's behavior without rewriting core logic.

2. Custom VSIX Archiver (Low Priority) While the internal archiver is a vital component, you don't need to understand its inner workings to use the extension. However, it is included here because it offers significant advantages over the standard vsce tool:
   - Performance: Significantly faster execution times.
   - Flexibility: It is less restrictive than vsce, allowing you to bypass certain requirements that might otherwise block your workflow.
   - Compatibility: Provides an alternative archiving path for specialized environments where standard tools fail.

By centralizing these notes here rather than scattering them across individual README files, provide a single source of truth for the "how" and "why" behind the code. This bird's-eye view ensures you can build your config with a clear understanding of the underlying framework.

> [!NOTE] 
>
> There has since been an update to the extensions activate function, for newer devs the activate function is... the extensions brain or root level function as it is the extensions main function that activates everything contained within.
>
> Previously while developing a feature may slip by me that has a breaking change and this breaking change would make it so all the features that following that broken feature would not get loaded in. 
>
> Redesigning this main function to ensure that this does not happen moving forward. Making it so no matter what state any single feature is currently in, it will not effect any other feature found within the extension. Well, thats the intention anyways as my previous attempts at this proved... ineffective at acheiving this end result.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Environment Variable Integration (.env)
To handle sensitive data—like NPM authentication tokens—the extension supports the use of .env variables directly within your configuration strings. This allows you to keep secrets out of your source code while automating authenticated commands.

> [!NOTE]
>
> I created a nice little hack for myself a while back that allowed me to on the fly create config items and trigger them progmatically, essentially allowing me to create a config item and run it through the terminal ngin as if it was coming from your config, which will very neatly allow the following. As I was in the file that holds the extensions function for npm publish, I coudln't NOT edit it so everyone else can enjoy the function and benefit from it while doing nothing to set it up. Just run "ocrmnavigator.npm.publish" as you would any other vscode cmd and ensure you have your token set in your .env file with NPM_TOKEN, ie 'NPM_TOKEN=2345t3rt34rtw34'. When the command runs through the terminal ngin, the ngin pulls the env variable out at the very last second before sending it to the terminal.
>
> Same with pushing vsix's in place of using vsces publish command, execute 'ocrmnavigator.vsix.push' and having 'MS_TOKEN' placed in your env file. For anyone currently using this function, it will still work for you exactly as it does now. The only change was adding a check to see if there was a token saved, if not it runs vsce publish --packagePath vsixPath --pat pat, grabbing the pat from your env file as it gets executed. So with this function you can either save the token using vscodes secret states, or place it in you env file.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Security First: Execution-Time Loading

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
>
> [Link to video, showcasing the above command being executed and pulling the env var.](https://youtu.be/XwsO4DnEpRg)

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Modular Function Building

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


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> The Philosophy of Automation
(or Lack Thereof)
In this extension, you will not find "passive" automation. Unless the benefit is astronomical, I will never implement a feature that runs in the background without user consent.

### Why Passive Automation is Terrible
Most modern automation is unneeded. We have become accustomed to background processes constantly scanning, indexing, and eating CPU cycles. This is often a sign that a developer doesn't truly understand their user’s workflow. The result? Performance degradation and a tool that eventually becomes unusable.

My Rule: If a process can be a Triggered Activation Event, it should be. This gives you 100% of the power with 0% of the idle resource cost.

### Examples of "Triggered" Power
To prove that triggered automation is superior to background bloat, here is how I manage my own massive devstack using this extension:
- Icon Library Automation: With one click, the system drops an SVG into a folder, converts it for React, bumps versions, compiles, updates the NPM README, commits to GitHub, and publishes. It’s so streamlined I often forget I haven't even opened a terminal.
- The 40,000+ Line package.json: Managing a file this size manually is impossible. I use a package.dev.jsonc with static markers. A triggered build script scans these markers and injects dynamically generated content instantly.
- Markdown Pre-processing: Documentation for 125+ extensions is handled via a README.dev.md. A single trigger converts variables, updates the TOC, maps sources, and transforms complex tables into GitHub-friendly inline HTML.
- Library Scanning: At build time, the extension scans 2,700+ components and templates, distributing that data to variables that power the Quick Picks and context menus in the editor.
- "The One Ring" Command: I have a single devstack line item that, when triggered, builds, compiles, and publishes every single one of my personal projects simultaneously.

### The Performance Guarantee
Because everything is triggered, there are zero processes running in the background. We have all experienced VS Code performance issues where we had to start disabling extensions just to type smoothly. This extension rejects that reality. You get the functionality of a massive CI/CD suite, but it only exists when you ask for it.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> The Autorun System

The Autorun Folder is a unique architectural feature designed to let you execute custom logic at build time (or any other lifecycle stage) without polluting your codebase or your package.json scripts.

Instead of hardcoding new features or adding endless NPM scripts, you simply drop a standalone Node.js file into a specific folder. The extension handles the rest.

### Key Benefits
- Rapid Implementation: Write a quick script, drop it in the folder, and it’s active. No need to ensure cohesion with the primary codebase.
- Cleaner package.json: Avoid "script bloat." You can have dozens of utility scripts without adding a single line to your manifest.
- Sequential Control: Scripts are executed alphabetically and sequentially. By naming your files (e.g., 01_setup.js, 02_process.js), you have total control over the execution order.

### How to Implement

1. Create the Folder: By default, place a folder named autorun inside your src directory.
2. Custom Path: If your project uses a different structure (e.g., /app), update the setting:
  - `ocrmnavigator.AUTORUN_DIR`
3. Trigger the Scripts: To run all scripts within your autorun folder, call this command within your config:
  - `ocrmnavigator.autorun.trigger`

### The "Updaters" Alternative
If you need a second, separate layer of scripts—perhaps for tasks you don't want running with your main build—you can use the Updaters folder:
- Location: Place a folder named updaters in your workspace root.
- Trigger: Use the command `ocrmnavigator.autorun.updaters.`

This provides a secondary, less-customized execution path for maintenance tasks, database migrations, or minor file updates that sit outside your core build logic.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Dynamic Package Manager Detection

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



 

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Concurrent And Sequential Command Execution

The Terminal Engine was architected to support both sequential and concurrent execution across all of its command types. Working in tandem with its queue system, the engine systematically processes each command ensuring consistent, deterministic execution on every invocation regardless of the command type.

An emergent capability of this architecture — one not part of the original design — is the ability for concurrent and sequential commands to invoke one another, producing a chain reaction across different command types. This behavior is a natural consequence of how the Terminal Engine was constructed and how every command type, feature, and function within the extension interfaces with it.

When any function handling a command type is triggered, it passes its configuration object directly into the Terminal Engine, which determines the appropriate execution path via a switch statement, advancing through each case until a match is found and that case's logic is initiated.

For concurrent and sequential commands specifically, despite being routed through the Terminal Engine like any other command, each internally defined command within their configuration object is dispatched the same way any standalone feature would be. This means a concurrent command can dispatch all of its child commands simultaneously while delegating a subset of those commands to a sequential command — ensuring that operations with stateful dependencies are executed in strict order, with each step only triggering after the previous one has completed successfully. The result is a model where you benefit from the performance characteristics of concurrent execution without sacrificing the correctness guarantees that sequential execution provides.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Autonomous Maintenance

#### Local Instance Scans
Maintaining an extension of this scale—covering the functionality of 125+ individual tools—would normally be an impossible chore. To solve this, the extension uses Autonomous Scanning to keep its data fresh without me ever having to lift a finger.

### Real-Time vs. Hardcoded
Rather than relying on static lists that go out of date the moment a new version of VS Code or a library is released, I have implemented dynamic scanning strategies.

### Example: VS Code Commands 
While there is a manual list of core VS Code commands, the extension also features a Live Instance Scanner. It queries your specific VS Code environment to generate a command list on the fly.
- As VS Code updates, your list updates.
- I never have to manually add new VS Code features to the codebase.
- Eventually, as these dynamic counters parts prove their reliability, the manual lists will be phased out entirely.

### Other Self-Sustaining Systems:
- Icons QuickPick: Unlike the native VS Code icon picker, which is rarely updated, this extension scans the icon library at runtime. If a new icon is added to the source, it appears in your QuickPick immediately.
- Icons context menu
- Catalyst-UI Components Quickpick: The 2,700+ components and templates are managed via dynamic discovery. The extension scans the library and populates the inventory and display functions automatically.
- Catalyst-UI context menu
- Contextual Menu Options: The extension scans your local environment to ensure that the menu options presented to you are relevant to the tools you actually have installed and active.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Naming Conventions

#### Functions & Settings
As this extension has grown to include over 1,500 commands, the risk of "naming collisions" (where two commands share the same name) has become a reality. To prevent these conflicts and make the API more intuitive, I am transitioning all internal and exposed functions to a hierarchical naming convention.

### The Shift: From Flat to Hierarchical
Previously, commands followed a standard extension.function format. Moving forward, all commands are being recategorized into a taxonomic structure:
- Old Way: `ocrmnavigator.gitPush`
- New Way: `ocrmnavigator.git.push`

### Benefits and reasons for the change
- Instant Debugging: If an error occurs, the command name itself now tells you exactly which module (Git, Archiver, UI, etc.) is responsible, without needing to search the entire codebase.
- API Discoverability: It is now much easier to guess or memorize functions. If you need a Git tool, you know it starts with ocrmnavigator.git.
- Future-Proofing: This structure allows us to merge large sub-extensions (like the recent "To-Do" extension integration) without worrying about breaking existing features.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Settings & Migration

This same logic is being applied to the Extension Settings.
- New Settings: Will follow the category.subcategory.setting format.
- Legacy Settings: To avoid breaking your existing settings.json files, current settings will remain as-is for now.

> [!CAUTION] 
> Work in Progress: 
> I am currently in the process of converting all 1,500+ commands. If you are referencing the old naming convention in your custom configs, be aware that these may stop working as they are migrated to the new system. If a command fails, check the logs—it has likely just moved to its new hierarchical home.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> pro7

### Workspace Secrets & Encrypted Backups
Managing .env files and sensitive credentials across multiple workstations can be a headache. Standard practices often involve third-party "Secret Managers," but those often come with monthly costs or complex setups.

My solution—built directly into this extension—is a Password-Protected Archive workflow.


### Local Encryption 
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





## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Context

At this point in time, it feels as if vscodes entire context data set has been recreated for use within this extension, since the last major addition to the context data set was vscodes UI states.

This is due to the fact that, despite exposing so many data points to developers to use during extension developement for some weird reason they have kept out several states for us to track.

In addition to vscodes states, the extension also keeps track of a all the configurable settings that are available for you to edit, as well as currently logged in users to vscodes instance, along with a exhastive list of other data sets in order for all the features to work cohesively. 

Centralizing the data through the use of a context system akin to something you would find in a react app, despite the extension featuring what is now 175+ worth of extensions features, the amount of calls each feature does is kept to a minimum as it can acquire the needed data that was already obtained by the function that controls the context and all of its data, as it distributes to all features extension wide. 

Obviously, in an extension such as this, this provides a huge boost to performance in comparison to how extension are typically built.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Extension Architectural Overview

To provide a birds eye view I will try my best at re-creating an overview of the overall structure of the extension as it currently stands:

```markdown
╭─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│                                                    DEVSTACK                                                         │
├─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                                     │  
│                                                                                                                     │  
│                                                    ACTIVATE                                                         │  
│                                                        ↓                                                            │  
│                    ┍─ ← FEATURE 1 ─┑                   ↓                   ┍─ FEATURE 8  → ─┑                       │  
│                    ┝─ ← FEATURE 2 ─┥                CONTEXT                ┝─ FEATURE 9  → ─┥                       │  
│                    ┝─ ← FEATURE 3 ─┥                   ↓                   ┝─ FEATURE 10 → ─┥                       │  
│                    ┝─ ← FEATURE 4 ─┥                   ↓                   ┝─ FEATURE 11 → ─┥                       │  
│                    │               ┝───←────←──── FEATURE HUB ───→───→─────┥                │                       │  
│                    ┝─ ← FEATURE 5 ─┥                                       ┝─ FEATURE 12 → ─┥                       │  
│                    ┝─ ← FEATURE 6 ─┥                                       ┝─ FEATURE 13 → ─┥                       │  
│                    ┝─ ← FEATURE 7 ─┥                                       ┝─ FEATURE 14 → ─┥                       │  
│                    ┝─ ← FEATURE 8 ─┙                                       ┕─ FEATURE 15 → ─┥                       │  
│                    ↓                                                                        ↓                       │ 
│                    ↓                                                                        ↓                       │ 
│                    ┕────────→─────────→───────── TERMINAL NGIN ─────────←─────────←─────────┙                       │ 
│                                                                                                                     │ 
│                                                                                                                     │ 
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯

```

When you boil it down to its core its essentially works like the above diagram. The end result does not allow performance bottle necks due to feature re calling the same data over and over again, it does not allow the littering of your ui with terminal windows, while at the same time keeping every nicely organized in order to not go completely crazy looking for a feature that is currently not working or currently has some sort of bug to fix.

I do not foresee this structure changing again any time soon as it ticks all the boxes needed for this extension to run as it does, as it achieves many things, no other extension can come close to. 

Not just in terms of performance which is clearly evident whenever you download and have 13+ extensions active at any one time. 
Its ability for context switching as perfectly as it does while other extensions that attempts a go at this I have not yet found a single one where they they did NOT have a restore type feature in case something were to go wrong, which there is no such feature in this extension, since nothing goes wrong.
Among other things but I'll end it with one more, its use of using github as a source of truth for features and its data. The to do list, notes, reminders uses github as a single source of truth for not only the use of it within vscode but also the accompanying webapp, which no other to do, notes or reminders extension does... at all.
I'm not going over these points to boast about any one thing, but more as points to prove that an extension doesn't have to be created the way they currently are. As it seems that virtually every single extension suffers from the same problems when you look at them as a whole. If your peer has issues with his or her software, why not atleast try a different method when creating your own. 

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> VSIX Archiver

Was going to add yet another use case to the custom vsix archiver but it would seem I forgot to finish this section SO with that said...

While the current industry norm is to use vsce... across the board, it seems to be incredily rare to come across a custom archiver. Although I doubt other devs run into the same issues I seem to run into from time to time. 

Vsce, while shrouded with mystery on what it does or how it works, everyone just seems content with using it as a solution and deal with its requirements despite vsce's requirements actually being more strict than what is needed.

For example, did you know microsft actually allows the use of svgs in your readme? That fact is so little known to everyone that even AI engines consider it a fact that microsoft does NOT allow svgs to be included with your readme... but that fact is wrong.

Vsce, simply, is just an archiving tool that produces a like .zip archive that is not password protected. Along with adding a two very simple files... that's all it does at its basic functionality. Vsce complicates the process by including a check list against its requirements which are long and ensures your extension meets those requirements in order to be packaged.

Because of its exhausting list of checks, its also a lot longer of a process then it needs to be, really.

The custom archiver that is included does not copy that list of requirements... since it doesn't need to. In actuality the list of requirements is very small which entails:
- readme.md
- license.md
- changelog.md
- and that you have the package.json script that compiles your extension

Thats it really, even if you do not have a license.md or changelog, it makes one for you, if I remember correctly. Thus making the function complete the process in much quicker times, as all it does is compiles the extension, copies over the extension based on what is included in your .vscodeignore and creates the two files needed that microsoft requires. That is it.

Use cases to use over vsce:
- when you want to include the use of svgs in markdown files
- the inclusion of simple files contained within your src folder ( this is the current use case I'm in now as vsce, simply ignores my list of what to include and exclude with my extension when packaging it, as I've spent the last hour trying to diagnose this and just remembering that I have my own god damn archiver that works perfectly fine and to my very unsurprised reaction... worked perfectly the first execution )
- There were several more, but happened to me so long ago that I just don't remember at this time

If vsce gives you any issue at all, or would like faster archiving times, just try the custom archiver as it seems to be the go to any time I have ever had an issue with vsce. The archives are always accepted by microsoft despite the very short list of requirements

I will be expanding the feature set of the archiver to include a means to copy files to where ever indicated as I'm currently relying on scripts to carry out this functionality, where as I see no reason not to include it within the archiver itself for all to benefit and even for myself as adding it as an option would be a lot quicker then adjusting my scripts.
