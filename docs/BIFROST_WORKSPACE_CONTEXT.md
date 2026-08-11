# BIFRÖST


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Workspace Context
 
![Z](https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/devstack.jpg)

Create configurations that work across workspaces or stay project-specific. 
1. To take advantage of this feature you must create or set a folder to global: true at the root level
2. any item placed inside the global folders will now be available to use in any workspace

How to create global folders
1. create a folder via the plus icon in the devstack panes title bar, and follow the steps
2. if you are comfortable editing configs, within the devstack quickpick menu located on the status bar select `GBL DevStack Config`, opening your global config. Despite already being in your global config you still need to set the folders global value to true. Now you can also set items themselves at the root too if you wish. If you want to have zero folders and all items, you can do that too but I would highly recommend using folders from the start. 

### Config Strategies
In the beginning, you may only want a dozen or so items available in the pane so that they are readily available. As time goes on though, this list WILL increase over time I promise you that, my global config alone is 325+ items currently. 
That does not include my workspace config, OR any of the auto generated items that get added onto the config dynamically. You can do as you wish, that's why I made the extension in a way where there is virtually no limitations put onto you in any shape or form. 
BUT if you want to save time in the long run, seriously... use LOTS of folders, haha, or else you will end up what I did, every month or couple of weeks reorganizing it because with all the added extra items it gets too disorganized.

From a strategic view point, you don't have to have all of the items that will get the most use at the top, as you can set folders to be expanded or collapsed when you open vscode. Currently my set up is as follows:

1. main - set to collapsed this contains all the powershell items to quickly open projects I code in, with personal projects in a subfolder within main to divide them
2. cmds - set to expanded as default, within this folder there are 10 or so commands folldowed by 4 folders that contain more commands that are less used...ish, i say ish because the first folder I'm always opening but is too large to keep open all the time in order to quickly access everything else, as it contains not only fold items, but also toggle folds as well, instead of unfolding all i can quickly swap back and forth from toggling just 2, or 3 and so on
3. updaters - set to collapsed, containing all items related to github, building, etc
4. settings - everything after this is set to collapsed
5. files - taking advantage of relative paths, setting items like readme.me package.json, seed.ts and so on, grants you quick access to those files no matter the workspace you are in, saving you from having to create items for those files... in every workspace config
6. prompts - i use "prompt"... a lot, as my personal project pertaining to that still cannot be published I resort to using it manually still, this allows me quick access to it due to having a script that updates these items automatically at build to to ensure no matter what edits i make to my prompts, my config is always up to date
7. other - contains url items and other misc items that dont get much use
 
everything after this is workspace related, al-in-all I have 31 folders and ever since I started using the label item, I haven't had the itch to re-organize in... a long time actually.

```json
[
    { "label": "★ ━━━━ ☆ ━━━━ PROJECT ━━━━ ☆ ━━━━ ★", "type": "label", "icon": "chrome-minimize" },
    { "label": "★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆ ━━━━ ★ ━━━━ ☆",  "type": "label", "icon": "chrome-minimize" },
]
```
I've played around with a TON of different label styles, landing on this being the one I hated the least amount. I don't love it, but it works as vscode doesn't seem to like a lot of the inputs I was using. Check the label section, as I will include a ton of special chars to try.

#### Key Features
- Split configuration between global and workspace settings
- Configure folders as globally available or workspace-specific
- Support for hybrid configurations and per-project customization


