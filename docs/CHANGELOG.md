### <img src="https://media2.giphy.com/media/QssGEmpkyEOhBCb7e1/giphy.gif?cid=ecf05e47a0n3gi1bfqntqmob8g9aid1oyj2wr3ds3mg700bl&rid=giphy.gif" width="25"  style="vertical-align: middle; margin-bottom: 4px;"> **ROADMAP**

<!-- ✓ in readme -->
<!-- ✓✓ in readme and tested -->

#### ✓ Concurrent and VFS base code
- trying out several different terminals to execute code in
  - one of them being a terminal hack due to vscodes use of powershell cmds through their api, this creates a temp file in the system temp folder once created the system moves onto executing the next command allowing each command to wait till the one prior has completed
  - i hated... how the previous echos into the termnial, created and testing another version where more manual code is needed, this version if it works should wait till the command has completed before moving
  - created another 2 version incase the previous did not work
- the base code for the explorer pane has gone through a ground up redesign, if it works this will make this will make things extremely easy moving forward, especially in terms of creating new item types in which just setting the new type within the interface will suffice
- to ensure each item is created perfectly, a helper function was created to push all items through as they are created
- in doing so, performance has increased meanwhile providing a much better platform to conitinue building off of. added benefit that was not aimed for, compile times have dropped
- new function that creates a single point of executing every item type

#### ✓ File Link Jumper 
  - nav links that can be placed within any file to navigate to any other file, if including a line number also navigates to that file at the specified line
  - added variant where it navigates to the first mention of the referened string

#### ✓ monaco editer  
  - save editors settings to local storage, enabling edits to persist
  - more items added to reference sections

#### ✓ readme generator
  - seem to have broken some of the functionality when swapping the sidebar out for the new version. The readme template dropdown isn't displaying any valuees to choose, but everything else works


#### ✓ encoders
  - added the following encoders:
  - png to svg
  - ico to svg
  - jpg to svg

#### To do, Notes, Reminders
  - merged into devstack
  - added post it notes section


#### The "Global Search Shortcut" (savedSearch)
- The Pain: You find yourself searching for the same things over and over: TODO:, console.log(, FIXME:, or a specific @deprecated tag. VSCode's search doesn't "save" these queries well.
- The Fix: A searchPreset type.
- How it works: You define a label ("Find all Logs") and a regex. Clicking it instantly triggers the workbench.extensions.search ( or global search sidebar if workbench.extensions.search does not take in a arg) with that regex pre-filled and executed. 
- obj example - `{ "label": "console.log(", "path": "regex pattern to find console.log(", "type": "search", "icon": "search" },

#### ✓ Dependency "Deep Link" (packageSearch)
- The Pain: You need to check the documentation or the README of a specific library in your node_modules. Finding it in the VSCode file explorer is like looking for a needle in a haystack.
- The Free Fix: A "Jump to Package" item.
- Time Saved: No more scrolling through thousands of folders in the sidebar.
- user interface: On imports from within the file you are importing intom, hovering will provide clickable links for package.json and readme.md and the packages entry point for its code 'entering' the project

#### ✓ The "Zombie Process Killer" (portReaper)
- The Pain: You try to start your dev server, but it says Error: EADDRINUSE: address already in use :::3000. You have to run lsof -i :3000, find the PID, and then kill -9 <PID>.
- The Fix: A portKill type.
- How it works: It scans the package.json file for your dev script, grabbing the port number defined. When clicked, it runs a shell script: fuser -k 3000/tcp (or the cross-platform equivalent).
- provide a vscode command register function that takes in a port number as avaraible to allow me to create a quickpick that displays 5 of the most common dev ports and a custom option at the top allowiing the user to enter a port number tha tisnt listed

#### ✓ item type `layout`: Save and restore editor states.
- Utility: When you click "Debug Mode," it closes all tabs, opens your 3 specific controllers, splits the screen, and opens the integrated terminal.
- or have set context layouts for each project, where it opens the most commonly used files you set whenever that workspace opens



#### ✓ The ".env" Context Swapper (envProfile)
- Manual .env editing is a nightmare because one typo breaks the whole app.
- The Pain: Opening .env, commenting out 10 lines of "Prod" vars, uncommenting 10 lines of "Dev" vars, and repeating this for every microservice.
- The Fix: Create a type that swaps entire sets of variables.
- How it works: 
  - two .env files one labeled `.env` and the other `.dev.env` 
  - two values each in the `.dev.env` file to differiantiate the two they will be in the following format
    - `LOCAL_enviroment='development'`
    - `REMOTE_enviroment='production'`
    - `LOCAL_DATABASE_URL="postgres://postgres:Ch3w8acca66@localhost:5432/catalyst"`
    - `REMOTE_DATABASE_URL="postgresql://neondb_owner:npg_mfHjL51BCRlg@ep-solitary-glade-adoppzpt-pooler.c-2.us-east-1.aws.neon.tech/neondb?sslmode=require"`
    - `LOCAL_SESSION_SECRET='9k7mN2pQ8xR4vL6wE3tY1zH5jC0bF8dG7aS4nM9qK2uI6oP3vX8wR1eT5yH7jN0m'`
    - `REMOTE_SESSION_SECRET='9k7mN2pQ8xR4vL6wE3tY1zH5jC0bF8dG7aS4nM9qK2uI6oP3vX8wR1eT5yH7jN0m'`
    - `LOCAL_UI_CHECKOUT='/Catalyst/UI/code/list/all'`
    - `REMOTE_UI_CHECKOUT='/Catalyst/UI/code/list/all'`
    - `LOCAL_PADDLE_CLIENT_TOKEN="live_79e842b9aee2a289dc3431d8967"`
    - `REMOTE_PADDLE_CLIENT_TOKEN="live_79e842b9aee2a289dc3431d8967"`
    - `LOCAL_PADDLE_SERVER_TOKEN="pdl_live_apikey_01k4v3y240x0t4v8t39ytj7swr_yAAtEFKtVdpaYCqYHVBvyt_Aln"`
    - `REMOTE_PADDLE_SERVER_TOKEN="pdl_live_apikey_01k4v3y240x0t4v8t39ytj7swr_yAAtEFKtVdpaYCqYHVBvyt_Aln"`
  - if either value is missing in the `.dev.env.` file still invlude it in `.env`but the variable is set to empty ie:
    - `DATABASE_URL=""`
  - in a quickpick tha tis already built i will provide two buttons one `Set Local .env Var's` and `Set Remote .env Var's`
  - no matter what the current state is, it will always grab the the corresponding values of which is triggered and set them in .env so as to never error out

#### ✓ VSCode commands has been rebuilt
- with the addition of referencing EVERY SINGLE VSCODE cmd at your disposal for the item creating process, I might as well recreate this and have it perform better
- list will now comprise of over 1550+ vscode commands, ONTOP of ALL of devstacks commands
- as of now devstacks cmd count is at 2700+, BUT that is due to the ui migrations scripts, theyre being too restrictive and are not including every single component, ONCE I fix that it should be sitting around 4000+ cmds, with saying that there will be a large part of them that will be "sectioned" off in where they will have their own search function so as to not include them with the other available commands. This is due to the components ui library representing a large portion of the commands being created for the extension. 
- With saying that, moving forward I will be adopting a new approach whenever building functionality into the extension because I have decided to move in the direction a more modular approach in creating each of the functions that I into the extension, which means A LOT more cmds will be created because I will go back and break as much of it as I can
- What this means for you, is that you will have access to functionality that you will not find in any other extension, not to mention I don't know of one other extension that drops their entire functions table to the user but whatever
- thus giving you the absolute freedom when creating items for your use case for example:
  - whenever going through the process of git add, git commit and so on, it was always coded in a way where users could not access those functions, to add on that it was coded as a "block" instead of modular pieces that the user can then take and do whatever they want with them
  - instead if I were to build that processs now it would look like the following
  - `ext.gitAdd` 
  - `ext.gitCommit`
  - `ext.gitPush`
  - and so forth, where you can reference and use those commands in your config / items... you get the point
  - before you ask, each items creation process that CAN use a vscode / devstack cmd already have all the commands available to browse and select during that process along with the new icons that are avialable. The new process is pretty streamlined and is a very, very easy process especially when you compare it to other extensions
  - not to mention, this is the ONLY extension that I know of that even references vscode commands in excess of 5-10 items never mind 5500+ combined cmds to use, I probably have better documentation then fucking microsoft on a bunch of these cmds... 



#### Intelligent JSON Schema Support

#### item type `settings`

#### item type `label`

#### snapshot engine

#### persistant bookmarks

### clipboard 
- upgrade to 100 items, add hover preview
- global
- hover preview now displaying markdown


<!-- #region in readme -->

#### ✓✓ VFS
  - [x] items and folders can now be set with custom icons
  - [x] every available icon via vscodes `icons-in-labels`, is available to be selected via the add / edit item
#### ✓✓ DevStack Quickpick Menu
  - added several items and rearranged overall structure currently has the following items:
  - gs and vsix
  - update patch version
  - custom vsix packager
  - reload extensions
  - reload ts server
  - reload window
  - open devtools
  - search devstack
  - shortcuts reference
  - to do / notes menu
  - github menu
  - fold menu
  - format and errors menu
  - performance switch menu
  - file system menu
  - prisma functions menu
#### ✓✓ Bleeding Edge Menu
  - activate quickpick menu via setting the global or workspace settings via `"ocrmnavigator.BE_QP": true,`
  - features that need longer testing and contains the following items currently
  - auto create schema
  - g4 and vsix - different feature set than the one in the devstack menu
  - trigger autorun folder
  - convert md file to safe inline string
  - toggle regex review
  - toggle regex gm
  - open regex helper
  - reload window
  - open gbl settings file
  - open ws settings file
  - display full gh token
#### ✓✓ performance switch
  - completely redone as the previous version was... too agressive
#### ✓✓ autorun folder
  - when using any g4 function, executes any node .js script contained with in the folder
#### ✓✓ Code snap
  - highlight desired code section, then `alt + d`, activate function via quickpick menu option
  - creates a terminal style window with the selected code to painlessly share code snippets in a nice looking format
  - can predefine settings to be used, but also contains a sidebar to set them on the fly
#### ✓✓ motions category
  - primitive components that have animations added to each
#### ✓✓ build package.json
  - takes contents from package.dev.jsonc, formats the file and removes comments then overwrites package.json
  - to use add item `"type": "command",` and `"command": "ocrmnavigator.formatPackgeJson"`
#### ✓✓ the ability to set arguemnts for items, command, powershell and bash commands
  - [ ] `{ "label": "Open Settings", "type": "command", "path": "workbench.action.openSettings", "args": ["editor.fontSize"] }`
#### ✓✓ createFolderSmartIndexNamed  with named Exports
#### ✓✓ before initializing tthe config files, they are formatted, removing comments and trailing commas
#### ✓✓ create registry w/ named exports
#### ✓✓ each config item can now take the value tooltipText, that will be displayed in the items tooltip
#### ✓✓ icons reference list in devstack qp
  - [ ] whenever an item is clicked, copies it into your clipboard and exits the menu
#### ✓✓ devstack cmds/functions ref in devstack qp
  - [ ] whenever an item is clicked, copies it into your clipboard and exits the menu
#### ✓✓ terminal redesign
  - [ ] need to go through whole extension to make sure its using the new class
- [ ] added file back to main add button in title pane
- [ ] added snippets back, whenever item is clicked copying into clipboard 
- [ ] number of `modular` styled functions created
- [ ] created new marketplace rest api request to send vsix packages
- [ ] need to create section devoted discussing devstack commands and the amount of freedom and capapbilties users now have 
  - [ ] discuss orders 1-6
  - [ ] and other functions like it, and see if we cant break them down for users to use
- [ ] need to add to do, notes, reminders to readme, if not already
- [ ] new item types
  - [ ] settingsToggle - current settings value will be listed in the tooltip
  - [ ] tasks - triggers a task defined within tasks.json
  - [ ] apiCall - define items as api calls that you can trigger whenever needed
- so far testing has proven successs zero issues and meets expectations of what I wanted out of it
  - the new terminal system "persists" even after instance restarts where as whenever a command is executed through devstack, it will continue using the same powershell instance that was used prior to restarting instead of creating a new termninal window each cmd execution
  - adding to that, it acts, looks and feels like a shell should, there is no garbage text needed in order to complete some hack to achieve some functionality
  - the shell remains open and usable to the end user as if it was all one cohesive system that was built together, and depending on the type command triggered, each command awaits for the one prior to finish before executing it self
  - there are still a couple of terminals i need to clean up and get rid, but there were over 100 of them, so unless you use the notes portion of the extension you wont see it
#### ✓✓ Snippets - auto generated snippets items
- snippets are now eligible to be assigned to global vscode instance as well as individual workspaces
- just like npm scripts and tasks, this will also now be auto generated meanwhile keeping the same funcationality as before, so vscodes functionality of inline editor snippet insertion, still works as well as the context snippets accessible via quickpick in the editors context menu 
- the tooltips now feature a "view" of the snippets body allowing you to view the entire snippet before copying to clipboard
- same as before whenver clicked it places the body into your clipboard
- whatever snippets you set to workspace it will save to you active instances workspace, if using the ui to create / edit snippets
- as like before your free to edit the config files as you see fit
- the snippets system follows the exact steps that the file system does and stores in the same places
- so remember don't edit the snippets.json file contained within the extensions global folder, edit the global-snippets.json and its project specific configs
- can add folders or snippets to root level snippets folder
  - items inherit folders global value unless placed in the root snippets folder, in which any item within that folder can have either global set to true or false
#### ✓✓ open route in browser
  - fixed index and splat issues
#### ✓✓ icons
  - created quick pick menu that inserts icon at cursor and import statement at the top of the file

- [x] add global settings file opener in quick pick
- [x] need to add md pre-processor to readme
- [x] convert node .js scripts over to extension functions allowing other workspaces the same functionality

- [ ] TO-DO
  - [x] when logging in if the user is different then the current user in indexed reset all datqa
  - [x] changed createNote in configureAction to return note instead of redirect
  - [x] if (isTrashed) { return json({success: false, message: 'Note is in trash'}) }
  - [x] merge with devstack
  - [x] implement a queue system for rapid line item pushes. instead of cancelling subsequent operations, enqueue each push request and process them sequentially in FIFO order, with each waiting for the previous operation to complete before executing
  - [x] need to fix context menu for notes
- [x] create add items functions for apiCall
- [x] create add items functions for settingsToggle
- [x] recreate add cmdChain
- [ ] recreate add concurrent, 
- [ ] recreate add chain implementing a intellisense system to help with creating the new item type
- [ ] recreate add layout
- [x] need to create add items functions for search
- [x] need to test BE concurrent function
- [x] need to test BE sequential function
- [x] add new tools to drop down and devstack quickpick
- [x] need to create a section on how to benefit from the local / vs production database env toggle
- [x] create new move item
- [ ] new json/c formatter
<!-- #endregion in readme -->

