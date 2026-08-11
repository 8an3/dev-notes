

<p style="text-align: center;">
  <img style="display: block; margin: 0 auto;" src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/odin.png" />
</p>

<p align="center"><h1 align="center">DevStack</h1></p>
<p align="center"><em>The Extension That Fixed VSCode</em></p>



> [!IMPORTANT]
>
> Any time you see a feature mentioning finding it among the status bar menus, this has recently been changed as all status bar menus have been moved into the activity bar. If it is not apparent as to which activity bar view it currently resides in, then it will be covered under the devstack menu sidebar. As this has been the single point of focus when consolidating and exposing all of vscodes features as well as hosting as a menu system for this extensions features.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Quick Setup (2 minutes)
   
### Step 1 Restart VS Code
After installation, restart VS Code to apply layout configurations.
   
### Step 2 Clean Up Activity Bar
Right-click the Activity Bar and uncheck these default items:
   - Explorer ( currently still under developement, so for the mean time you can keep this here )
   - Search
   - Source Control
   - Run and Debug
   - Extensions
   
### Step 3 You're Done!
All features are still available - just in better places.

***In terms of removing the extensions icon, there is no replacement for this exactly. The only reason I have removed it personally is due to the fact that whenever I have a situation where an extension could help me with coding, instead of searching the marketplace for a solution, I simply just build it myself. So for this item, you may leave in the activity bar if you would like.***

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Setup

This extension has become so large and massive, I would have never guessed it would be where it is today, or where it will get to tomorrow. 

I have tried to make the onboarding experience as best as I can, and only falling short in a couple of areas due to vscodes restrictions, for example I have included a base layout configuration that is included with the workspace config. This allows for a much easier process for you to set up workspace context layouts. If you do not wish to use this feature, just remove the layout config item from your workspace config. 

Even though, the experience and UI will change for you, I have coded it so that items like your desired registered theme, font size, word wrapping, breadcrumbs, and more will carry over into the layout config item that gets generated for each workspace you create. Which means, yes a lot will change, but not for configurations you love and enjoy that do not need be overwritten. If you have already installed the extension, but not yet restarted your instance the layout config has already been created for you and I would ask for you at this time, to restart the vscode instance.

If your worried about loosing your place here, as soon as you restart the intance there is an oboarding page that will pop up when your vscode instance loads up that can be toggled off or even kept on if you desire.

Once loaded back into vscode, you will see there is a lot going on in a lot of different places. The UI as a whole, but to make the experience better I will go over a couple of changes that need to be done manually to finalize the process.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> The Activity Bar

Situated to the left of the window ( depending on your settings but this is the default location ), currently this will have exploded with new items for you and need to remove the default vscode features. We are just removing the icons, not the actual feature so in the case that you actually would rather use the vscode variant, your more than welcome to remove the extensions icon and replace with vscodes. Or in the case of developing new features, if something were to break later down the road, for example a new feature was added to the search but happened to break other features, till it is fixed you can easily swap out search engines.

This process is very simple despite the amount of new items you have, as all you need to do is toggle off every single vscode feature making it so the only remaining items are provided from this extension. 

Before moving on, yes there are a couple of features you will notice that aren't among the icons in the activity bar. Do not worry, trust me, they have actually been replaced but just reside else where while at the same time offering a better ux than the default.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Default Configs

When you first install the extension, you will have a choice of selecting configs consisting of examples and configs consisting of a single folder.

If this is your first time using the extension I suggest the option containing examples as if gives a wide range of what can be accomplished with all the many different config types that include:
- examples of each config item
- examples showacase extended use of its config item type
- how to include env variables with config items
- how to create and use hidden item types
- and much more...

Even if you do not plan on editing the config itself, and only use the ui elements to add, edit or remove items. They will still provide value on what exactly you can include with each config item.

The workspace default config, while limited in terms of examples provided it does come with a layout config item to allow for a much easier and faster workspace context layout configuration. Which we will expand upon later on in the docs.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> To Get The Most Out Of This Extension

Or in other terms, hit the ground running. The best way to go over the documentation is to go over the terminal ngin and its config items, and the layout ngin.

The config items that are used in devstacks sidebar are still by far the most powerfull feature that can be found in the extension. But its power is built over time as you build your config, as config items are built as you need them when coding. 

Where as, that layout ngin is just one config item and you get immediate gratification of an entire new vscode expereience that can't get from any other extension, seriously.

Then using the rest the features as you would vscodes features, they are there waiting to be used and will be available to you when the need arises. At that time, come back to the docs and refer to its section learn about it. 

Currently the docs sit over 72+ files and that isn't even including the long list of features I had put off on documenting or forgot to come back to. So this list will grow and it would be stupid for someone to sit there and read all of the docs in one setting. 

This strategy not only gives you that wow factor, or instant gratification of, "shit this extension is cool". While it also sets you perfectly down the correct path in getting the most out of the config items.

<!-- #region --->

> [!TIP]
>
> I mentioned this in the readme, but lets talk about your VSCodes performance and if you opt in to taking the suggestions laid out, I promise you this will be the single most largest improvement to your applications performance you have ever seen. As I had noticed that, even till today, these changes were and are still the biggest gains I have ever gotten when optimizing the application for performance.
>
> These will include features that I know there will be people that just... cannot live without them. Which is why this is being presented as a tip and a suggested path to take instead of just doing it for you as that would be too obnoxious for me to do.
>
> Lets take care of the most hungry, memory starving glutton that plagues every vscode users experience... GitHub.
>
> Yes, I know... Literally everyone uses it to the point that it was integrated into vscode as a default feature. But, lets be real... You do not need the functionality it offers, no one does. It sits there constantly taking up a lot of your systems performance, for what? A notification in the activity bar telling you how many files are dirty in comparison to your repo? I disabled it over 6 months ago, not only have I NOT missed it, I haven't... even really thought about it. Which is GREAT, because that means it offered nothing of value I couldn't live without. 
>
> Before we move on to the how, lets go over the why because I know even after reading the previous paragraph that some of you will be sitting there, but I need it for this or that. To be honest, you don't to the point that, for anyone who doesn't want to remove this feature from the activity bar, do this instead. 
> 
> Remove it just for the next 7 days, thats it. As long as your coding during those 7 days, that's all I ask. At the end, put it back on. I garauntee, most if not all who try this, you won't even think about it on the 7th day to put back on your activity. A lot of you, it might be 2-3 weeks before you realize that you had already finished the 7 days weeks ago. In terms of why you NEED to get rid of it and what I have done to ensure that you no longer need it.
>
> As you code, every single key stroke you make... github reacts, and then does all sorts of manner of things behind the scenes without you even knowing. Not to mention, while it may seem effecient with smaller projects, I garauntee you its anything but. Why do you need to index 1000's of files, that I have't opened in weeks. 
>
> If you work in larger projects, the second you disable github... it will feel like you can finally breath again since the elephant that was sitting on your chest was finally was shoved off. That's the way it felt for me. As that one settting turned a slugish vscode instance, into a snappy and responsive editor again. Making me disable it in every workspace, without looking back.
>
> If you want to get into the really nerdy details and go down the rabbit hole to learn more. I just recovered a vscode extension architecture breakdown that covers vscode and the technical side of why it does what it does. It also goes into the industry wide beleif of why and how to fix the performance issues. 
>
> The replacement is a github CLI wrapper that was designed in such a way that whenever you push to your remote, it will not fail. In addition to that, the naming convention has been swapped out to replace the confusing names with ones that already hold meaning to people and even someone in their first week, can guess as to what it means just from the name alone. Not only making it easier to identify, but each menu option that is available contains a hover card with all of its documentation relevant to that menu option. Making it so you do not need to open documentation or navigate several layers of a website in order to either find out what it does or how to use it. Finally, every single github process that typically needs anywhere from 4-12 commands or clicks has been brought down to one. 
>
> Labeled HEIMDALLR that has the valknut icon, or in other words the same icon that is used as the red section indicator in all the markdown docs.
>
> Upon opening that sidebar you will be greeted with a file tree view containing 4 folders:
> - BIFROST - The platform agnostic installer that uses a lot of the same functions HEIMDALLR has, which you will see why shortly
> - BALDR Icons - triggering that file item activates the installation process for that react icon library. 
> - MIDGARDR SDK UI Components CLI Tool... but instead of using the cli, you have nice and easy items to click on in place of typing out terminal commands that require you to go to the docs every time you need to use it
> - last but not least, HEIMDALLR
> 
> Within the heimdallr folder, there are a number of subfolders that breakdown into each of the naming conventions used accompanied with the terminolgy that you already know in order to make the switch as effortless and easy as possible.
>
> > Each name that was chosen was carefully looked at, compared, broken down to ensure that each of the names hold not only a previously indoctirned meaning that defines that work for each person... but ensuring that each endocturned meaning is relevant to its coresponding functionality. Which means, someone in the first week of coding can actually succesufully guess what each name represents.
>
> - project - is your local repo so anytime project is referenced its refering to the local representation of your remote repo
> - source - refers to your remote, as it is the source of your project
> - timeline - is your branch, timeline was chosen because whether you are new or not timeline immediatly tells someone that it can be temparay, can be deleted or can become the final project 
> - version - replacing tags, this name immediatly conveys a versioning system where as tags... simply does not
>
> You will quickly notice that it covers all of the processes you are used to, and more such as:
> - Upload + where it not only pushes your local to your remote, but at the same time upgrades the project patch by one, ++ upgrades the minor and finally +++ upgrades the major
> - download file, now this is a feature you probably not even have thought about in the past while at the same time, doesn't make sense NOT to have it. Why can't I download a single file from a repo without having to go to github? Currently, you have to visit the site, navigate to the repo, go through the file explorer and navigate to the desired page. Once there, you have a choice of viewing the raw or download the file. Literally just upgraded to improve the UX even more. On triggering this menu option, it will ask you a series of questions while also providing folder contents so that you don't have to leave vscode to download a file from not only from the current repo your working in, but any of your repos in addition downloading files from any public repo.
> - download folder, while the previous is available, albeit not offering the option in a user friendly manner. This is not an option anywhere, which is weird. Follows the same step by step process as the previous
> - archive, a host of functions for anyone working with vscode extensions and even an option if you would like to include your projects secrets with your github pushes
> - publish, whether you would like to progmatically publish your npm package with a single click, if you have a .vsix to update that needs to be sent or instead of using vsce there is a custom variant to use instead
>
> As you can tell, all the bases have been covered when it comes to dealing with github and even goes beyond with offering features that you cannot find anywhere else. 
>
> But this tool goes beyond what was covered so far, as each process does even more at the same time for example creating a new local project:
> First starts by prompt for the following:
> - project name
> - project description to be included in your package.json
> - which package manager you would like to use
> - which license you would like to have included in your project, from the get go
> - its not updated in the docs, but I have since added a changelog and readme template wizard as well
> - asks if you woud like to install the icons library once your new project has intialized
> - also asks about the ui components library ( which also installs and configures tailwind for you )
> - finishing off with asking if you would like to have the installation process done for you
>
> Once it has the needed values it goes on to do the following for you:
> - create the new project folder for you
> - cd into the project 
> - create readme
> - license
> - package.json
> - .env and .dev.env ( more on that later )
> - .gitignore, with a base config to ensure that you never include the neccesities any push to your remote moving forward
> - instailize github project locally
> - creates the remote repo
> - adds, commits and all other manner of commands to finalzie the creation of your new remote repo 
> - creates asgard.config with the provided values for future use
> - installs all libraries ( if you prompted yes ) 
> - installs baldr icons ( if you prompted yes )
> - installs tailwind, postcss and configures the required files ( if you prompted yeds to the ui library ) 
> 
> in addition to the above, depending on the selected optoin when it came to the ui library, different tailwind.config.js are available, such as the tailwind config preset ngin. Allows you to control not only your apps theme, with 75+ themes to choose from, but also providing 110+ fonts and finally allowing you to customize the apps presets which controls the overall look and feel of your entire app by changing the padding, margins, borders and more across your entire application
>
> The tailwind config preset ngin is a must have for everyone, while yes there are 40,060+ configurations through this one file, but more importantly it takes your most complicated config file that you need to configure, turning it into the easiest. How? To configure the ngin, there is a section at the top of the file that describes the three values you can configure, lists what values you have to choose from and it does all this without you have to make a single change to actual code used to make this file happen. Making it so, someone in their first week of coding can not only install tailwind but have it configured as if they've been on the job for 5-10 years. Meanwhile, for those of you who want different theme or style options. It was built in a way that makes customizing it, very simple and easy to accomplish.
>
> While creating a project through githubs mandated processes you start off with an empty project, leaving a lot more steps for you to do. Meanwhile, in comparison you now have a great jumping off point to just include the desired platform. Speaking of which, found in the same sidebar but moving up one folder and opening bifrost, you are now presented with a generous list of platforms to choose from. Choosing any of the options found in this folder will start off by installing your desired platform followed by all the other steps we just went over. 
>
> Which means, no matter what react based application you want to build, it will be a complete breeze to set up. 
>
> Personally, when I first started coding I would have to go to the platforms site, copy the command to install or start the install process. Need tailwind so lets now go over to that site, navigating all the different menus on which platform I was using and so on. Search for an icon library, making sure I think I like the library before then grabbing its command to install. Then heading over to a components library... depending on which one you use, this part of the process itself could either be a complete drag of a chore to do or not as bad but still have to go through the motions with including it in your app. At this point you still don't have a github repo set up. 
>
> I'll admit it will feel weird at first, but you will get used to it pretty quickly, as I don't even have source control on my activity bar anymore.
>
> Once you have removed github from your activity bar here are the following settings to place in either your workspace or global settings.json file
>
> - "git.autoRepositoryDetection": false, // Scans your entire workspace for any folders containing a .git directory
> - "git.detectSubmodules": false, // Scans your project for Git submodules and treats them as separate repositories
> - "git.autofetch": false, // Periodically and silently contacts your remote server (e.g., GitHub) to check for new commits
> - "git.autorefresh": false, // Automatically updates the Source Control panel when you change a file on disk
> - "git.diffEditor.renderGutterMenu": false,
> - "git.decorations.enabled": false,
> - "explorer.decorations.colors": false,
>
> For now that is all you really need to change, if you want to take it farther or if you work in larger projects I'll quickly go over some more settings in the accordian below.
>
> Cheers
>


<details>
<summary>More settings.json configurations to gain back performace</summary>

> [!TIP]
>
> If your aren't used to navigating to the 2 places that the settings files are placed, instead of navigating the maze of file explorers, a cheat is already in place for you to take advantage of. In the sidebar, open the devstack menu, you will be presented with a long list of buttons to click. Each section is categorically organized, VSCode Config folder, by deafult, should already be expanded granting viewable access to both available options for workspace and the more annoying sibling to navigate to, your global setttings file. I suggest using the global settings file, as there are a surprising amount of settings that can only be set in the global file. Basically the workspace file is for a custom theme, and any workspace specific settings, otherwise using the global over the workspace is more advantageous in the long run.
>
> Whichever one you decide to go with, I suggest creating a copy somewhere. It's a good habit to back up and settings files your about to edit, that way if something were to happen that you do not like, it is a very easy fix since all you need to do is paste back in the orginial contents.
> 
> Whenever you start this process, the name of the game is 'What can I live without?'. 
>
> AI's right now are still coming out like crazy, but they tank your performance HARD. With saying that, you can still enjoy the use the ai engines give while at the same time keeping your performance. This can be achieved by making the ai engine reactive instead of pro active. No matter which engine you have installed they will all have the following settings except for gemini where that one will yolo mode which I do mention below. 
> - whatever you do, do not enable yolo mode, that is just irresponsible on the devs behalf
> - code generation pane view enabled - nope, don't need that
> - enable the use of .gitignore so that you can configure what it can and can't scan - yes enable this, as simply just enabling this will lock it out of node_modules at the very least
> - display inline context hint - no
> - enable telemtry - no, so much so you shouldn't enable this across the board for any extension
> - inline suggestions: enable auto - no thank you, we do not need a perverted ai micro managing every key stroke we make
> - local codebase awarenesss - sigh, no
> - outlines: automatic outline generation - no, lol
> - inline suggestions: next edit predictions - if you want to yolo your performance right into the dumpster fire that will become your workstation, this is something you would want. That must be a new setting, I was joking do not enable this
>
> If you use co-pilot specifically, this one setting does the same as above.
> - "github.copilot.enable": { "*": false },
>
> Next on the chopping block are your watchers: ( depending on the platform you typically code with, these will change )

```json
{
    // stops vscode from watching the files contained within this object
    "files.watcherExclude": {
        ".vscode/ocrmnavigator/odin/version/**": true,
        "**/.git/objects/**": true,
        "**/.git/subtree-cache/**": true,
        "**/node_modules/**": true,
        "**/dist/**": true,
        "**/build/**": true,
        "**/.vscode/**": true,
        "**/coverage/**": true,
        "**/.cache/**": true
    },
    // this object removes the files from view within your explorer, this one being more stylistic in nature
    "files.exclude": {},
    // this one also increases performance, but when using the search as it default by not scanning these folders whenever you start a new search
    "search.exclude": {
        ".vscode/ocrmnavigator/odin/version/**": true,
        "**/.git/objects/**": true,
        "**/.git/subtree-cache/**": true,
        "**/node_modules/**": true,
        "**/dist/**": true,
        "**/build/**": true,
        "**/.vscode/**": true,
        "**/coverage/**": true,
        "**/.cache/**": true
    },
}
```

> [!TIP]
>
> There are a couple of approachs that you can take from here on out, the first being apply all the settings which will remove everything all at once. The second option slowely adding them one or two at a time to see exactly what it does before moving forward. 
>
> If you are someone who knows that you CANNOT live without a lot of features, go with the second option. If you are unsure or know you CAM live without a lot of them, go with the first. That way no matter which option go with, it will be the fastest option to take based on your prefrences.
>
> But so far we have:
> - taken care of github
> - optimized vscode with scanning certain folders ( and you can expand on items like too, same goes for search exclude. )
> - optimized your search engine
> - editing your ai engines from being pro-active to react in nature
>
> This alone, should net HUGE gains in performance but it shouldn't end here as there are a couple more settings we can take care of. When I say a couple, there is a lot since vscode isn't shipped with this in mind. 
> 
> At any time if I leave out an explanation thinking that it is obvious as to the nature of what that setting controls when I shouldn't have made that assumption, as I have been working with these a lot. Just take the setting, place it in the file and when you hover over it there will be a hover card that pops up and explains the setting. Along with that, if there is a setting that is not a boolean, there typically tends to be more than 2 choices that vary the results of that setting. In order for you to see exactly what values can be applied, place your cursor inbetween your double quotes and press ctrl + spacebar, and a dropdown menu will appear. The only times this or the hover card will NOT show up, is if that setting is no longer available in your version, I mention this because I only use vscode insiders. While 99% to 100% of the following options will also be available to you there may be one that isnt.
>
>    

```json
{
    "eslint.run": "onSave", 
    "eslint.format.enable": false,
    "typescript.tsserver.experimental.enableProjectDiagnostics": false,
    "typescript.tsserver.log": "off",
    "update.showReleaseNotes": false,
    "update.enableWindowsBackgroundUpdates": false,
    "editor.selectionHighlight": true,
    "problems.decorations.enabled": false,
    "css.validate": false,
    "diffEditor.codeLens": false,
    "debug.openDebug": "neverOpen",
    "debug.toolBarLocation": "hidden",
    "debug.showInStatusBar": "never",
    "editor.inlineSuggest.enabled": false,
    "workbench.editor.enablePreviewFromQuickOpen": false,
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
    "editor.codeLens": false,
    "editor.lightbulb.enabled": "onCode",
    "merge-conflict.codeLens.enabled": false,
    "multiDiffEditor.experimental.enabled": false,
    "jsonc.validate.enable": true,
    "json.validate.enable": true,
    "prettier.enable": true,
    "markdown.validate.enable": false,
    "extensions.ignoreRecommendations": true,
    "html.validate.scripts": false,
    "markdown.server.log": "off",
    "editor.minimap.enabled": true,
    "breadcrumbs.enabled": false,
    "workbench.commandPalette.history": 30,
    "scm.diffDecorationsGutterAction": "none",
    "scm.diffDecorations": "none",
    "workbench.remoteIndicator.showExtensionRecommendations": false,
    "window.restoreWindows": "one",
    "workbench.editor.decorations.colors": false,
    "js/ts.updateImportsOnFileMove.enabled": "always",
    "js/ts.validate.enabled": true,
    "search.useIgnoreFiles": true,
}
```

> Any time you see a setting that I have enabled, feel free to disable. Most of the time depending on which file I'm in, I tend to toggle a lot of settings. For example I have some json files, that if I were to open without disabling the validation and error checking, I kid you not, my entire vscode instance just freezes and locks up for more than 5-10 as it scans the entire file sometimes even crashing it entirely.

    

</details>

<!-- #endregion --->


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Closing Notes

I'm aware that being so upfront about the extension and exactly how it will effect your coding enviroment will turn some people away because of how large of a change it is. Which is fine, this extension will not be for everyone. 

But for anyone who does try it out, I hope you enjoy the new experience as I have, so much so I no longer even thinking about trying to find a new platform. 

