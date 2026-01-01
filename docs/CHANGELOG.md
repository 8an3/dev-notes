### <img src="https://media2.giphy.com/media/QssGEmpkyEOhBCb7e1/giphy.gif?cid=ecf05e47a0n3gi1bfqntqmob8g9aid1oyj2wr3ds3mg700bl&rid=giphy.gif" width="25"  style="vertical-align: middle; margin-bottom: 4px;"> **UPDATES**

<!-- #region ✓ in readme -->

To save on time, and due to the crazy amount of updates this extension receives, a more relaxed format will be used in place of the industry norm. It will be more of a revolving door of updates then just a continous changelog text wall, that will only feature the most recent 10 changes. But at the bottom of the doc will host a table featuring all features checked off with the following 2 boxes, readme docs written for that feature and tested. Tested meaning, has gone through enough testing for me to no longer think or worry about whether something in that feature is currently not working. Every single feature already goes through initial testing before its even made available.



> [!IMPORTANT] 
> LAYOUT ENGINE CONFIG HAS BEEN UPDATED!
> If you have already started using the layout engine, you will have to update your config as most of it will not work.
>
> This was due to several settings being horribly unreliable. Without the access to vscodes context, theres no way to 100% garuarantee a value. Instead of guessing the value, or following the foot steps of others where in they create their own context in which if they are wrong in guessing what the current state is, that invalid state will follow for the rest of the vscode instance.
>
> The best path forward, that I can currently see, assumming a baseline state but not to record that state so as to allow you to use vscode ux features such as the customize layout option available on the menubar and others reasons.
>
> It's not all bad news, if anything the changes made have actually provided you the even more freedom in terms of the config. Each object that contains key:value pairs are placed as a whole into the settings.json file, meaning your more then free to treat the sections performance and workspace as more organizational objects and you are free to place whatever settings you desire in either object. Customize layout is now a requirement, whenever your creating or modifying your configs be sure to copy that over from the provided example in the docs.

<!-- #endregion ✓✓ in readme and tested -->

<!-- #region ✓ in readme -->

<details closed><summary  style="font-size: 1.2em;">The ".env" Context Swapper (envProfile)</summary>

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

</details>

<!-- #endregion ✓ in readme -->
<!-- #region ✓ in readme -->
<details closed><summary  style="font-size: 1.2em;">✓ VSCode commands has been rebuilt</summary>

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


</details>

<!-- #endregion ✓ in readme -->
#### Intelligent JSON Schema Support

#### item type `settings`

#### item type `label`

#### snapshot engine

#### persistant bookmarks
<!-- #region ✓ in readme -->
<details closed><summary  style="font-size: 1.2em;">Search Editor</summary>
It is modeled after vscodes search editor, exactly, so it will feel and operate in the same fashion. As for added features:
- Opens a search editor with template for search params
- Executes search showing 5 lines before/after each match
- Full find/replace functionality (replace single or replace all)
- there will be four inputs using codelense to create them within an text editor, exactly the way vscode created
  - for exmaple, you search for xyz, 50 results pop up
  - but you don't want to change all 50 results, just one
  - instead of navigating to that file, which would be double clicking the search result, to navigate to that line OR searching in THAT file for the line you need to get to 
  - you will be able to make the changes from the search editor itself, making changes remotely and it will edit the relevant file in question
- Changes are tracked automatically
- When you save (Ctrl+S), all your edits get applied back to the original files
- Double-click navigation to jump to the actual file
- File type filters
- toggable fuse.js search capabilties, disaplyed as a button inside the first input along with regex, case match and amtch whole word
- toggles based in the first input for:
  - Regex (already there conceptually)
  - Case sensitive
  - Match whole word
  - Fuzzy search
- toggles based in the files to include input for:
  - search in open editors only
- toggles based in the files to exclude input for:
  - use exclude settings and ignore files

</details>

<!-- #endregion ✓ in readme -->
#### VSCode Extension Configuration Testing Suite
<!-- #region ✓ in readme -->
<details closed><summary  style="font-size: 1.2em;">DevStack Commands</summary>
suprisingly I had the first collision take place just recently, due to adding notes and to do into the extension. Obviously hosting it own functions where I didn't need to worry about that, but when brought over it created an issue for the already in place github features, which prompted a change in how devstack commands will be made moving forward. The change offers enough of a benefit in warranting the change made through the extension. Not just for you, but also myself, in where each command will instantly tell us where the command originated from and allows for a far more simpler naming convention for example:
- `ext.gitHubPushCommand` → `ext.git.push`

I wish I would have thought of this earlier due to just how much better that is, because it not only makes it simpler to debug and code, but in terms of your benefit, a lot easier to guess if you know the extension has it. Adding to that, discovery of commands for users also becomes a lot easier, as the dynamic lists that produce the commands for you to view will now categorize them in a much cleaner format.

ONTOP, of that change and doing the house work of starting that conversion. I have found areas in which to continue adding commands for users using the modular format, unlocking even more functions that you can program into your configs. Before this chore is done I imagine there will be a lot more prouced because of it.

Just to name a few, these are some of the git commands available in which all, aside for a couple, are modular leaving you to your own devices and creating whatever executions you would like:

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
- ocrmnavigator.git.removeUnusedImports
- ocrmnavigator.git.showQuickPick
- ocrmnavigator.git.autoCommitPush
- ocrmnavigator.git.autoCommitPushUpgrade
- ocrmnavigator.git.G4PUBNPM
- ocrmnavigator.git.dbAllLocal
- ocrmnavigator.git.dbAllRemote
- ocrmnavigator.git.dbReset
- ocrmnavigator.git.databasepushtorepo
- ocrmnavigator.git.dbSeed
- ocrmnavigator.git.dbGen
- ocrmnavigator.git.dbStudio
- ocrmnavigator.project.clean
- ocrmnavigator.project.DukeNUKEM
- ocrmnavigator.project.i
- ocrmnavigator.project.build
- ocrmnavigator.vscode.REXT
- ocrmnavigator.vscode.RTS
- ocrmnavigator.vscode.RWINDOW
- ocrmnavigator.vscode.DEVTOOLS
- ocrmnavigator.git.showFullToken

Only downside is, if you have already built config items consisting of commands from devstack, then you will 100% have to update them. This was a necessary change, and I would rather do this now rather than when there is another 1500 commands available. Sooner or later this would have had to be taken care of, but atleast with this new format it makes everything even more simple. I just wish I could change the first part, the only reason I am not is because it would truly break every current users... everything. Settings that they already have in place, configs, and so on. And creating the housework of recreating and reconfiguring everything that they already in have place.
</details>

<!-- #endregion ✓ in readme -->
<!-- #region ✓ in readme -->
<details closed><summary  style="font-size: 1.2em;">Monaco update two - catalyst editor</summary>

the added updates continues to push it farther and farther away from its original idea of just a markdown editor
- there have been... 30+ additions to the drop down menus
- the issue with saving settings to local storage has been fixed
- any adjustable setting that was not already added to the list to be saved locally, now is
- due to using monaco editors in more than one place a centralized 'editor' and renderer was made replacing the code in each implementation
- rename tabs, while it said you could do it, couldnt really. now whenever you trigger the function to rename tabs, the actual tab it self with feature an input for you to make the edit
- there was about... I want to say 50-70+ additions to the reference table found in the right sidebar not to mention adjustments to others
- the languages list now features its respective icon to find the language you are looking for a lot easier


</details>

<!-- #endregion ✓ in readme -->
<!-- #region ✓ in readme -->
<details closed><summary  style="font-size: 1.2em;">Snippets</summary>

I really need to atleast add something to this doc whenever I do something, I just dont have the time. 
The last two days alone, have been NOTHING but typing documentation... I guess thats what I get when creating a ridiculously stupid extension such as this. 

Just added two more items to the tldr, sitting there looking at it... its rediculous. I don't get how there aren't better solutions out there, and makes me shake my head.

how is it that a sales person of all professions in which the typical sales person couldn't any less tech orientated, who never even finished highschool and not receiving a single credit in one, not going to college or uni, and started coding one tool for the sole reason to help decrease the amount of time wasted during my day-to-day sales processes. 
 
Blows my mind on a couple of levels, not trying to blow up my own ego because I wish I never had to create this extension and everything in it. just from the viewpoint of the workload... this is so much fucking work and while its cool to see that list there, and how it continues to grow, I wish there were just better tools available so I didn't have to do this for myself. 

And if I were actually doing this for you the user instead of just me, there would be EVEN more work involved in terms of overall testing of each feature, docs, ux and ui design that list goes on. So thinking of it that way I'm happy I never decided to just focus on the user, as selfish as that may seem, but it also proves how far that is from the truth of the matter or else I wouldnt be sharing this in the first place. I'm sorry i know I'm just ranting, because I just submitted a report that would remove a feature from this extension that would benefit, and I kid you not, every single vscode user


Anyways, snippets has almost... actually no... every piece of code referencing snippets in any form has been either deleting and recreated or updated.

- in terms of the file tree you now have:
  - auto generated items based on your snippets content
  - contextually organize snippets on a workspace by workspace basis if you want, or leave me globally accessible
  - the snippt item in the config, you can now view its entire body through the tool tip even before clicking it
- due to the changes with context and others, the .snippets file has been replaced with a config, completely changing the format meanwhile still providing access to vscodes native snippet editor inline insertion
- the editor has also changed but only in terms of backend functionality
- its not active yet, but you will also be able to save sets of snippets as "profiles" through the web ui in the case to allow for greater organization for downloading and distributing said snippets 
- snippets will also be remotely accessible, meaning if you would like access to your personal snippets at work, EVEN THOUGH you are using your work email in your vscode instance, you can log in  via your personal account as there will be a github oauth authentication also getting added because of this, and download your personal snippets to your work computer

in short, a lot of updates because I know I'm missing a couple. Making this in terms of feature parity, greater than any enterprise and paid solutions found elsewhere. While before, it was still a better tool in terms of ux than any other, it didn't have the features to make it best in class like it does now. When you think about it, is pretty rediculous considering, this is just one small feature among the collosal list featured in the toc
</details>

<!-- #endregion ✓ in readme -->
<!-- #region ✓ in readme -->
 

#### 

#### 


####
## testing and readme breakdown

| Feature                        | readme writtenm        | tested |
| ------------------------------ | ---------------------- | ------ |
| The "Global Search Shortcut" (savedSearch)    | ✗       | ✗     |
| Dependency "Deep Link" (packageSearch)        | ✓       | ✗     |
| The "Zombie Process Killer" (portReaper)      | ✓       | ✗     |
| The ".env" Context Swapper (envProfile)       | ✓       | ✗     |
| Intelligent JSON Schema Support               | ✗       | ✗     |
| VSCode Extension Configuration Testing Suite  | ✓ ish   | ✗     |
| VSCode commands has been rebuilt              | ✓       | ✓     |
| Concurrent and VFS base code   | ✓                      | ✓     |
| File Link Jumper               | ✓                      | ✓     |
| monaco editer updates          | ✓                      | ✗     |
| readme generator               | ✓                      | ✗     |
| encoders                       | ✓                      | ✗     |
| To do, Notes, Reminders        | ✗                      | ✗     |
| item type `settings`           | ✓                      | ✓     |
| item type `layout`             | ✓                      | ✗     |
| item type `label`              | ✓                      | ✓     |
| snapshot engine                | ✓                      | ✗     |
| persistant bookmarks           | ✗                      | ✗     |
| Search Editor                  | ✓ ish                  | ✗     |
| DevStack Commands              | ✗                      | ✗     |
| Snippets                       | ✗                      | ✗     |


<!-- #### To do, Notes, Reminders
  - merged into devstack
  - added post it notes section


#### The "Global Search Shortcut" (savedSearch)
- The Pain: You find yourself searching for the same things over and over: TODO:, console.log(, FIXME:, or a specific @deprecated tag. VSCode's search doesn't "save" these queries well.
- The Fix: A searchPreset type.
- How it works: You define a label ("Find all Logs") and a regex. Clicking it instantly triggers the workbench.extensions.search ( or global search sidebar if workbench.extensions.search does not take in a arg) with that regex pre-filled and executed. 
- obj example - `{ "label": "console.log(", "path": "regex pattern to find console.log(", "type": "search", "icon": "search" },
-->