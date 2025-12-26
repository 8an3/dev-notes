## VFS

## Table of Contents

- [Project Agnostic Configuration](#project-agnostic-configuration)
- [The ".env" Context Swapper (envProfile)](#the-env-context-swapper-envprofile)
- [DevStack Quick Pick](#devstack-quick-pick)
- [Pro7 Archiver](#pro7-archiver)
- [BE Quick Pick](#be-quick-pick)
- [Reveal In Explorer](#reveal-in-explorer)
- [Copy Path](#copy-path)
- [Search](#search)
 

### Project Agnostic Configuration
 
Create configurations that work across workspaces or stay project-specific

#### Key Features
- Split configuration between global and workspace settings
- Configure folders as globally available or workspace-specific
- Support for hybrid configurations and per-project customization

#### Example Configuration

```json
{
  "label": "MAIN",
  "expanded": false,
  "type": "folder",
  "global": true,
  "items": []
}
```

#### Resources
- [Visual Guide](https://raw.githubusercontent.com/8an3/dev-notes/blob/main/vfs/SequentialExecution+.gif?raw=true)
- [Video Tutorial](https://youtu.be/NtnVq8CNJ7A)


 


### The ".env" Context Swapper (envProfile)

- Manual .env editing is a nightmare because one typo breaks the whole app.
- The Pain: Opening .env, commenting out 10 lines of "Prod" vars, uncommenting 10 lines of "Dev" vars, and repeating this for every microservice.
- The Fix: Create a type that swaps entire sets of variables.
- How it works: 
  - two .env files one labeled `.env` and the other `.dev.env` 
  - two values each in the `.dev.env` file to differiantiate the two they will be in the following format
    - `LOCAL_enviroment='development'`
    - `REMOTE_enviroment='production'`
    - `LOCAL_DATABASE_URL="postgres://postgres:owner@localhost:5432/server"`
    - `REMOTE_DATABASE_URL="postgresql://owner:server@server/db?sslmode=require"`
    - `LOCAL_SESSION_SECRET='local-secret'`
    - `REMOTE_SESSION_SECRET='remote-session-secret'`
    - `LOCAL_PADDLE_CLIENT_TOKEN="api-token"`
    - `REMOTE_PADDLE_CLIENT_TOKEN="api-token"`
    - `LOCAL_PADDLE_SERVER_TOKEN="api-token"`
    - `REMOTE_PADDLE_SERVER_TOKEN="api-token"`
  - if either value is missing in the `.dev.env.` file still invlude it in `.env`but the variable is set to empty ie:
    - `DATABASE_URL=""`
  - in a quickpick tha tis already built i will provide two buttons one `Set Local .env Var's` and `Set Remote .env Var's`
  - no matter what the current state is, it will always grab the the corresponding values of which is triggered and set them in .env so as to never error out


### DevStack Quick Pick

  

**Access:** Press `Alt + Shift + D`

A comprehensive quick-access menu for all DevStack features including formatters, database operations, and build processes.

![DevStack Quick Pick](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/devstack-quickpic.jpg?raw=true)

- Test Set Config Command 
  - Test VSCodes config api, takes in a key and value pair for hot / live updates to test key / value pairs
- Get Config Command Value
  - providing the key, responds with the value
- Test Set VSCode Context
  - test key / value pairs with vscodes context api
- Get VSCode Context
  - providing the key, responds with the value
- G4 & .vsix
  - saves all → if user settings true for each of the follow ending at archive, the following with execute, auto run folder → update md files → markdown pre-preprocessor → deletes 7zip archives → compiles and packages new archive based on users settings either with vsce or custom vsix archiver → pushes repo → bumps patch → if user settings true, opens microsoft marketplace in default browser is using custom archiver and if you do not have a PAT submitted, then reveals the folder in which it was created in, installs locally and restarts that instance
- Upgrade Patch Version
- Custom VSIX Packager
  - custom vsix package, builds smaller, with just as much config as vsce, less restrictive in terms of both sending the vsix archive via http request and the actual build of the archive itself
  - vsce does NOT allow the packaging of svgs, that are to be used in your readme along with a couple of other items
  - same with the upload process
- CODE SNAP
  - a very quick and easy way to take snap shots of code snippets, downloads as an image with a terminal style theme
  - dynamically loads whatever you highlight as the code snippet to display
- Markdown Pre-Processor
  - processes markdown files granting the following functionality upgrades:
    - variables system, ie takes 
- R Window
  - restarts the active vscode instance 
- Set Local .env Var's
  - sets the vars within the .env file to the local state, uses .dev.env as the source of truth
- Set Remote .env Var's
- GBL Settings File
  - just a short cut to the global settings file
- DevStack Search
  - opens a quick pic to search through your config instead of using your explorer pane
- Shortcuts reference
- VSCode  
  - various vscode functions
    - format json file
    - format current json file
    - search editor
    - reload extensions
    - reload typescript server
    - open devtools, this ONLY opens devstools if you are currently use certain items, I can't for the life of figure out the api on forcing the call, its so stupid
    - opens gbl settings file
    - opens workspace settings file
    - install archive
    - open global keybindings
    - auto zombie process killer
    - zombie process killer provides top 5 dev server ports to kill along with an input to insert custom port
- DevStack
  - varioes devstack vscode commands to execute and or urls for the site
- DevStack Cmds
  - searchable list to reference when building your items if you would like to include functionality from the extension for example if you had the use case to progmatically execute auto create schema, in with some prisma automation build... you can which is kinda cool, wish other extensions did this
- VSCode Cmds
  - lists categorically with a search function listing ALL 1500+ vscode commands that are currently available to users through the api, a lot of them even have descriptions. Sadly, makes it better resource then microsoft ever provided, LOL
- Icons
  - lists ALL available icons to use within devstack / vscode, again better implementation than microsoft provides, not to mention I don't know of a single extension that offers either one of these, nevermind BOTH 
- To do / Notes
  - menu items to configure and set up to do, notes, reminders and post its
- GitHub  
  - various guthub functionality
- Fold
  - a bunch of folds and toggles
- File System
  - various file system functions
- Prisma Functions
  - various prisma functions

This section gets updated WAY to much to even try... to make this look pretty so... 


### Pro7 Archiver
Secure sensitive files in password-protected archives before pushing to GitHub, ensuring safe version control for proprietary code.

### BE Quick Pick

Do not rely on the documentation in regards to what items are actually populated within this menu, as this changes even more then the previous. You need to have the bleeding edge setting set to true for this to even be viewable. I needed a place to store command triggers that was easy to get to, didn't take up room any where else while also being quick to get up, going and test. Your more than welcome to use the functions within this menu, but they may not always work. Right now, if I remember correctly everything is working in there, and I need to move them to more user accessible parts of the extension. The ONLY thing I haven't tested much, is the regex helper, guide... I don't know what to call it. It helps you build regex patterns, and also has a small list of predefined regex statements for emails, phone numbers and such. If you want's heres a [regex cheatsheet](https://github.com/8an3/dev-notes/blob/main/docs/REGEX.md)


### Reveal In Explorer

  
**Right-click any file → Reveal in Explorer**

Open file locations directly in Windows Explorer or macOS Finder from:
- DevStack sidebar
- Editor context menu
- Extensions pane

![Reveal in Explorer](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/reveal-in-explorer.jpg?raw=true)
  

### Copy Path


**Right-click any file → Copy Path**

Copy full or relative file paths to clipboard. Works with multiple path formats throughout the extension.

[Video Demo](https://youtu.be/FWa6o5FK3sU)


### Search


**Access:** Click title bar button

Powerful search functionality to find and execute any command you've created. Preview commands before execution to ensure you're running the right one.

![Search Feature](https://raw.githubusercontent.com/8an3/dev-notes/main/vfs/search.jpg?raw=true)

[Video Demo](https://youtu.be/pRVv7UaY4qM)


---

[🡄 Return](https://github.com/8an3/DevStack)
  