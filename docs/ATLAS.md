# ATLAS

> [!NOTE]
> The new layout system is already underway, starting with focusing on the UI and how each level feels along with adjusting which level should control what exactly. No idea how I'll go about the back end of things yet, but we'll get there and figure it out. 
>
> Want to say this here in case you don't make it to the end, IF you haven't tried it yet... try this layout engine. I now have a config or more for every workspace... and it has been such a better experience than I first thought this feature would have as far as overall impact to the user experience within vscode. Even though an update is coming, who knows when it will done enough to use which is why I'm still suggesting, try this out seriously if I had to choose 5 features for someone to try out with this extension... this would be number 1 or number 2.
>
> In case you didn't read the notes below, some things that I did come across but still have to dive into further to see if they are viable paths to edit. A while back I tried adding a feature to the extension where it blocks... ALL toast notifications. Using insiders, they're plentiful and annoying and to make matters worse there seems to be a ton of devs that love recommending things that also pop up and ya... hit a dead end with it before, but it seems like this could be something that might get done.
> Don't read into this too much, but I did see some icons values... who knows, maybe even add custom icons to vscode?! That would be nice. And not just in the file tree.
> Even after finding that security threat in vscode and before even talking to microsoft I had decided NOT to move forward with it because of that... after all that, they never even responded, figures. Despite that I still don't want to use the workaround that I had found, primarily due to, exposing how its done and even though microsoft doesn't care I'd rather just keep that under wraps instead of advertising it to everyone. With saving that, I did see some values that might actually get the end result that I was going for... so, atleast the idea isn't completely dead yet, because weirdly this one feature excites me most currently. I don't know why, maybe it's because I had to deal with performance issues a lot, I was running a lot although I wasn't running a lot in vscode itself which was the main culprit but still.
> I don't know how but, I do really want some sort of stale data / garbage collector since going through those values... I saw A LOT of old data, that hasn't been used in years just sitting there. I'll try to calculate just how much storage that's actually taking up, because if it isn't enough to warrant going through the trouble, then theres no point.
> OH, almost forgot, once sauron is up and working I will be working on setting up the profile contexts up next in regards to layouts, and probably even for the rest of the extension. 

> [!NOTE]
> Levels 1, 2 and 3 will be getting more options to configure. Currently I have only coded in my own settings into Saurons tab, and it is astromically funny just how big of a difference there is between them. But after seeing it come together in the ui, it's going to be easy enough to know that no one should have any issue having the config they want as each part has descriptions and what not. 
>
> The new atlas layout system will come out in 2 versions, one after another. The first will be virtually how it is now but in ui form. Since there are a lot of moving parts I want to make sure the ui works before even moving on to the more complex settings that will be available in level 4, which means if you don't plan on using that level, you will be able to work with the new system rather quickly. With the new system being so simple the only documentation there will be is just an overview of each of the levels, and that's it really. as it's pretty self explanatory. At which point I will start working on the last tab, which might be over and done with quickly or... it will take some time with trying to figure out what everything does. A lot of that extra time will depend on new the systems being introduced to handle the new features, if any.


## Layout Configuration Guide
More of an overview of what to expect, than an actual guide since it's extremely straight forward, except maybe one part which I will go over.

### Casual
- Layout name
- Icon - allowing you to set that layouts icon to be displayed in the sidebar
- Pre-configured theme dropdown - that will provide a selection of pre configured themes that I have registered with the extension
- UI Elements - this being one of the sections that was added on you can control: 
  - Primary sidebar
  - Secondary sidebar
  - Activity bar
  - Status bar
  - Panel Visibility
  - Panel alignment
  - Mode
- One auto run terminal command that executes once the workspace initializes
- file inputs so as to set a file for a 2 col editor group, you may only place one file in each of the 2 columns that are avaialable at this level
- checkbox to set the layout to deafult

### Intermediate
In addition to the above:
- Custom theme colors - instead of going with one of the many pre configured themes you may set your own color scheme. By shrinking down the amount of values needed to be placed in the custom section, this allows for you to create a nice cohesive theme across the entire UI with very little effort. Saving you tons of time in the process compared to the default process of completing this task. The following colors will be avaialbe for you to customize:
  - Background
  - Muted Background
  - Foreground
  - muted foreground
  - border
  - primary
  - primary foreground
- Instead of one file per col, you may select as many files as you wish and organize them per col
### Power User
In addition to the above:
- Plex vs Default Layout: Editor Grid
- Plex vs Default Layout: Terminal Grid

You may choose to stick with the default columns layout, but customizing the amount to whatever you wish it to be and allowing you to assign as many files to each.
If you prefer the linux `plex` style layout configuration, you may choose the amount of cols and rows to be used for both terminals and editor groups.

Just like you can with editors, you may choose to add as many config items to any terminal group you may wish, each item adds a new tab within that terminal group.

### Sauron
In addition to the above:
This one has changed the most... weirdly, due to the overall length I have had to modify it by adding in a second sidebar to the right, and a search bar when dealing with settings values.
The sidebar contains the following: 
- Theme, as you can now edit every single color value via a color picker or input to paste in your value
- Auto run - you may place as many config items as you wish here, selectable via a drop down that scans your current config and populating the options with them
- Auto close - same as above but runs when you go to close the workspace, you may also override the execution of these commands by double clicking the windows close button
- Git - has a value to place the desired branch you would like whenever you trigger that layout, as well as on open and on close values to place git related commands
- Configuration settings - I have no hardcoded a single setting, opting out for the lazy mans version by dynamically generating this list via your vscode instance and populating the list with all the commands available to you at the time of creating or editing that current config
- .vscdb settings - this is where the `hidden` or whatever you want to call them, settings will be that we cannot modify anywhere else but here
- Editor grid - same as last group
- Terminal Grid - same as last group
- and this isn't all the items just yet, below you will find documentation on how to use the remaining items.

#### Icons
This feature won't be available till the first round of the feature has been completed, so if you can't save a layout or if `vsicons-custom-icons` doesn't exist don't bother trying to use this.
This will only be available to the Sauron level due to the fact that, you will HAVE to be navigating and placing items in the global user folder. So if your not comfortable enough to use the UI at this level, just come back to this later when you are.

The main portion of code isn't even done yet, and I'm doing thngs like this already, anyways... You now have access to not only place your own custom icons to be used within the virtual file system in place of the current vscode icons that are avilable. I will also be setting up a number of icons to be used as well, specficially just colored variants of the defaults to help seperate items from one another, rather than one giant long white blob.

##### Naming Convention
To use this feature name your icon with a unique and relevant name for example, I would highly suggest naming your icon something along the lines of:
- `colored-settings-item-type-skyler.svg`

being very specific about what it is, if you can add `blue-` or whatever color it may be at the beginning increasing the odds of securing a unique name instead of experiencing a naming collision. Then I followed it up with my name, to add an even higher probability of success. 

I'm assuming since you are in this level, you won't naming it something like `icon.svg`... please don't do that. If you do, don't bother complaining to me about it, lol. 

##### Folder Path For Storing Your Icon
Take your cool svg and place it in this folder:
- `C:\Users\<your_user>\AppData\Roaming\<Code Folder>\User\vsicons-custom-icons\`

`Code Folder` being:
- `Code` if you have the standard vscode edition
- `Code - Insiders` if you have the bleeding edge edition

##### Using Your New Custom Icon
Once you have placed the icon into the folder, you may now call on it whenever you create a new item, edit an item through the UI, or when editing your config manually. Using the same name I used earlier I would reference it by:
- `colored-settings-item-type-skyler`

After placing the icon into the folder, you will have to restart your instance in order for vscode to register the new icon.

##### Provided Custom Icons
As mentioned earlier I will also be placing custom icons in addition to the above feature which will be discoverable via the vscode icons quick pick, I'll place them at the top of the list.

> [!NOTE]
> I think I touched on the notion of getting the use of custom icons in other places, other than just the extensions file tree... as of right now there doesn't seem to be a way in which I can expose other avenues to everyone. Doesn't mean it can't be done, if it can be done... I just haven't found out how yet.


#### Ignore All Notifications / Toasts ( WIP )
#### Workspace Extensions Context ( WIP )
#### Profile Context ( WIP )

<br /><br />

## Notes for future features... 

> [!NOTE] 
> In this section I will be leaving myself notes that I do not want to forget because I think I stumbled on exactly what I wanted... from the begining. If you aren't into reverse engineering things and diving into something that has zero documentation, or just don't get enjoy getting to the level NERDNESS, that this is going to get into. I would suggest skipping this part entirely as you will probably find 100% of this boring among other things. 
> If your the NERD among geeks, your more than welcome to read on, with saying that these will be structured as notes, not actual documentation even though this topic will probably get documented more here... then anywhere else. I will start off by quickly going over what it is that I found, because I totally found it by accident, and if it wasn't for actually making this layout engine ( most people dont ), I would have saw that data in the file and just immediatly closed it. LUCKILY, I saw some values... that I fucking wanted to modify, lol. 
> features 
> - global context: `AppData\Roaming\Code - Insiders\User\globalStorage\state.vscdb` 
> - profile context: `AppData\Roaming\Code - Insiders\User\profiles\55de5399\globalStorage\state.vscdb`
> - workspace context
> - stale / garbage cleaner
> - level of user access
>   - Level 1: Muggles (basic UI/theme)
>   - Level 2: Casual nerds (colors by zone)
>   - Level 3: Power users (full theme control)
>   - Level 4: SAURON MODE (raw database access)
> - Profile Comparator
> - ignore all toasts ( the dream is alive again )
> - custom icons usable through the vscode ui??? maybe....
> - workspace context extension toggle ( another dream has come back from the grave, i seriously did NOT see this one coming )
>
>
> Literally resorting to read the hex dump at first, and quickly saw some values that... up till now and seeing this, there is no other way in either editing or even just viewing the value thats held in a state context and because of that, there is a ton of the ui... you can't modify and if you can modify... you cannot do so in a reliable manner without those values. The COOL thing that is making me love what I'm seeing so far... is accessing that profile scope and from a cursor glance... its the context state... extension state... literally everything that I have been wanting access to since I really start to dig deep into this feature. 
> - so were are going to have a global config
> - workspace config
> - and hopefully... even a profile config... Which I have never even heard in any form in any extension offering configurations in any sense on a profile to profile basis. Not on the level this is going to get into fuck ya.
>
> - DUE TO THE LEVEL OF JUST HOW COMPLICATED THIS WIL GET... need to rethink the dx/ux, in its current state... im not even happy with where it is despite being so simple to do. 
> - We are going to have to offer a webview, similar to odin... but taking it further where there will be a drop down so we can select level of "nerdness", and having the default ui be on a level that all muggles would appreciate and can easily glide through and setting up their own config, while the select offering 3-4 levels of nerdness all the way to the level of manipulation that would even quench Saurons thirst for it, meaning... lets fucking expose everything... in which case, I would not only make the user create their own back up before any changes could be done... but also doing that for the user adding a third layer of backup
> - the other levels only allowing modifaction of a pre determined set of items
>   1. first being basic ui and theme on a per workspace, profile and global context... we should even have the theme builder incorporated and avialable through vscodes editor... taking it a step even further
>     - first tab font, theme, preset just like how it is in the tailwind.config ngin
>     - then offering deeper levels of customization going deeper with each tab as 95% would be happy with the first tab anyways with it have 18,000 configurations
>     - then basic ui manipulation with just eiditng editors groups on a per column basis, allowing them to open and pin files and over state such as zen mode and thats it
>   2. allowing the choice of choosing colors for the ui 
>     - offer them in zones only, sidebar editors secondary sidebar
>     - in terms of text foreground and muted foregroud only
>     - borders does all border colors
>   3. going deper
>     - in terms of theme, now grating access to coloring the context menus, gutters, panel, tabs, and icon color
>   4. offering a dx unparallel in terms of total customization... but making it on level that would be such a stark contrast to the headache that is vscodes implementation, its almost on the same pain levels as getting kicked in the nuts
>
> in terms of ui... dropdowns or toggles for everything except the items that NEED inputs but only granting access to those inputs to the 2 nerdiest classes... everyones else gets pre defined values that will suck to code.. BUT to amek it a better user experince...  i think thats the way to go... just switchs and dropdowns.... ya...
> examples of accessible values: 
> - Comments.hidden [{"id":"workbench.panel.comments","isHidden":false}]
> - sync.productQuality insider
> - views.customizations 
> OH AHH OHH 
> - workbench.activityBar.location default
> - workbench.auxiliaryBar.empty false 
> - workbench.sideBar.size 433
> - workbench.auxiliaryBar.size 310
> - workbench.panel.size 262
> - extensions.dismissedNotifications []
> - iconThemeData we need to check this one out a bit more... can we add custom icons straight into vscode.... shit maybe
> - notifications.doNotDisturbMode false remember blocking all toasts..... 
> - terminal.history.entries.commands literlly 100's of cmmands of history
> - vscode.git  "git.repositoryCache": 
> - vscode.github-github vscode username
>
> 
- workbench.panel.markers.hidden
```json
[
  {
    "id": "workbench.panel.markers.view",
    "isHidden": false,
    "order": 2
  },
  {
    "id": "terminal",
    "isHidden": false
  },
  {
    "id": "workbench.panel.repl.view",
    "isHidden": false
  }
]
```
- terminal.hidden
```json
[
  {
    "id": "terminal",
    "isHidden": false
  },
  {
    "id": "workbench.panel.repl.view",
    "isHidden": false
  }
]
```
- extensionsEnablement/malicious atelast my extension isnt on that list lol
```json
[
  {
    "id": "heartacker.git-graph-ai"
  },
  {
    "id": "Med-H.git-graph-revamped"
  },
  {
    "id": "betterthanalltime.calva-vscode"
  },
  {
    "id": "priskinski.Theme-AgolaDark-remake"
  },
  {
    "id": "priskinski.Theme-Amy-remake"
  },
  {
    "id": "priskinski.Theme-Amber-remake"
  },
  {
    "id": "priskinski.Theme-AllHallowsEve-remake"
  },
  {
    "id": "priskinski.Theme-Afterglow-remake"
  },
  {
    "id": "yfdyh000.aar-vsc-test"
  },
  {
    "id": "mercerllc.mercer-onboarding-helper"
  },
  {
    "id": "esonhugh.weaponized"
  },
  {
    "id": "luater.luatide"
  },
  {
    "id": "JosephDembele95.email-grabber"
  },
  {
    "id": "RabobankAI.rabobank-code-assistant"
  },
  {
    "id": "blackforest.blackforest-1234"
  },
  {
    "id": "prettierteam.prettier"
  },
  {
    "id": "evaera-rbx.vscode-rojo-rbx"
  },
  {
    "id": "discord-inc.discord-rich-presence-rpc"
  },
  {
    "id": "MarkH.chatgpt-autocoder-vscode"
  },
  {
    "id": "MarkH.claude-autocoder-vscode"
  },
  {
    "id": "MarkH.discord-rich-presence-vs"
  },
  {
    "id": "MarkH.golang-compiler-vscode"
  },
  {
    "id": "MarkH.html-obfuscator-vscode"
  },
  {
    "id": "MarkH.python-obfuscator-vscode"
  },
  {
    "id": "MarkH.rust-compiler-vs"
  },
  {
    "id": "VSCodeDeveloper.sobidity-compiler"
  },
  {
    "id": "visualstuiocode.emmet"
  },
  {
    "id": "joaomoreno.banana"
  },
  {
    "id": "JacobeanResearchandDevelopmentLLC.vscode-scxml-preview"
  },
  {
    "id": "joaquin6.package-watch"
  },
  {
    "id": "KazuoCode.gthubsum"
  },
  {
    "id": "MaxGotovkin.tslens"
  },
  {
    "id": "stephen-riley.regexworkbench"
  },
  {
    "id": "guozebin.api-generator-plugin"
  },
  {
    "id": "code-tester.code-tester"
  },
  {
    "id": "viralvaghela.darkcbtheme"
  },
  {
    "id": "viralvaghela.normalnameimgtest"
  },
  {
    "id": "k3s0externobyes.k3s0externobyes"
  },
  {
    "id": "testUseracc1111.python-vscode"
  },
  {
    "id": "NealKornet.theme-darcula-dark"
  },
  {
    "id": "FlydCode.codelinter"
  },
  {
    "id": "FlydCode.codewithfriends"
  },
  {
    "id": "benawad.vsinder"
  },
  {
    "id": "BXDS-DLP.BXDS-DLP"
  },
  {
    "id": "kyntrack.log-matrix"
  },
  {
    "id": "kyntrack.track-vscode"
  },
  {
    "id": "gitkraken-dev.gitlens-pro"
  },
  {
    "id": "Glenn-marks1990.live-sass-compiler"
  },
  {
    "id": "platformio-dev.platform-io"
  },
  {
    "id": "syj-first-extension.code-whisperer"
  },
  {
    "id": "darcula-theme.darcula-official"
  },
  {
    "id": "sopspub.org"
  },
  {
    "id": "darcula-theme2.darcula-official2"
  },
  {
    "id": "vivo-ai-code.vivo-ai-code-vscode"
  },
  {
    "id": "Ericsson123.DarkThemed"
  },
  {
    "id": "A-M.idxmlfun930470"
  },
  {
    "id": "A-M.angelica-color-theme"
  },
  {
    "id": "A-M.idmarkdownfun930470"
  },
  {
    "id": "A-M.idjsonfun930470"
  },
  {
    "id": "A-M.idsqlfun930470"
  },
  {
    "id": "A-M.idhtmlfun930470"
  },
  {
    "id": "A-M.idyamlfun930470"
  },
  {
    "id": "A-M.idgroovyfun930470"
  },
  {
    "id": "A-M.idobjectivea2cfun930470"
  },
  {
    "id": "A-M.idcssfun930470"
  },
  {
    "id": "A-M.idca17fun930470"
  },
  {
    "id": "A-M.idgradlefun930470"
  },
  {
    "id": "A-M.idphpfun930470"
  },
  {
    "id": "A-M.idpythonfun930470"
  },
  {
    "id": "A-M.idjavascriptfun930470"
  },
  {
    "id": "A-M.idjavafun930470"
  },
  {
    "id": "A-M.idmatlabfun930470"
  },
  {
    "id": "A-M.idca24a24fun930470"
  },
  {
    "id": "A-M.iddartfun930470"
  },
  {
    "id": "A-M.idbasicfun930470"
  },
  {
    "id": "A-M.idshellfun930470"
  },
  {
    "id": "A-M.idkotlinfun930470"
  },
  {
    "id": "A-M.idvba1netfun930470"
  },
  {
    "id": "A-M.idcfun930470"
  },
  {
    "id": "A-M.idrustfun930470"
  },
  {
    "id": "A-M.idrubyfun930470"
  },
  {
    "id": "A-M.idswiftfun930470"
  },
  {
    "id": "A-M.idscalafun930470"
  },
  {
    "id": "A-M.idperlfun930470"
  },
  {
    "id": "A-M.idspellfun930470"
  },
  {
    "id": "A-M.idhaskellfun930470"
  },
  {
    "id": "A-M.idpascalfun930470"
  },
  {
    "id": "A-M.idrfun930470"
  },
  {
    "id": "A-M.idtypescriptfun930470"
  },
  {
    "id": "A-M.idfortranfun930470"
  },
  {
    "id": "A-M.idgofun930470"
  },
  {
    "id": "A-M.idluafun930470"
  },
  {
    "id": "A-M.idactionscriptfun930470"
  },
  {
    "id": "A-M.idtclfun930470"
  },
  {
    "id": "A-M.idclojurefun930470"
  },
  {
    "id": "A-M.idvhdlfun930470"
  },
  {
    "id": "A-M.idbashfun930470"
  },
  {
    "id": "A-M.idfa17fun930470"
  },
  {
    "id": "A-M.idcythonfun930470"
  },
  {
    "id": "A-M.idlispfun930470"
  },
  {
    "id": "A-M.iddockerfun930470"
  },
  {
    "id": "A-M.idcobolfun930470"
  },
  {
    "id": "A-M.iddelphifun930470"
  },
  {
    "id": "A-M.idjupiterfun930470"
  },
  {
    "id": "A-M.idnodefun930470"
  },
  {
    "id": "A-M.idgeminifun930470"
  },
  {
    "id": "A-M.idschemefun930470"
  },
  {
    "id": "A-M.idandroidfun930470"
  },
  {
    "id": "A-M.idawsfun930470"
  },
  {
    "id": "A-M.idjupyterfun930470"
  },
  {
    "id": "A-M.idmachinea31learningfun930470"
  },
  {
    "id": "A-M.idadafun930470"
  },
  {
    "id": "A-M.idassemblyfun930470"
  },
  {
    "id": "A-M.iderlangfun930470"
  },
  {
    "id": "A-M.idsasfun930470"
  },
  {
    "id": "A-M.idfirebasefun930470"
  },
  {
    "id": "A-M.idamazonfun930470"
  },
  {
    "id": "A-M.idnotebookfun930470"
  },
  {
    "id": "A-M.idchatgptfun930470"
  },
  {
    "id": "A-M.idnpmfun930470"
  },
  {
    "id": "A-M.idopenclfun930470"
  },
  {
    "id": "A-M.idrpgfun930470"
  },
  {
    "id": "A-M.idsolidityfun930470"
  },
  {
    "id": "A-M.idgithubfun930470"
  },
  {
    "id": "A-M.idaifun930470"
  },
  {
    "id": "A-M.idyarnfun930470"
  },
  {
    "id": "A-M.idawkfun930470"
  },
  {
    "id": "A-M.idmlfun930470"
  },
  {
    "id": "A-M.idelixirfun930470"
  },
  {
    "id": "A-M.idmyfun930470"
  },
  {
    "id": "A-M.idgooglefun930470"
  },
  {
    "id": "A-M.idapifun930470"
  },
  {
    "id": "A-M.iddatafun930470"
  },
  {
    "id": "A-M.iduifun930470"
  },
  {
    "id": "A-M.idrestfun930470"
  },
  {
    "id": "A-M.idiconfun930470"
  },
  {
    "id": "A-M.idgitfun930470"
  },
  {
    "id": "A-M.ideslintfun930470"
  },
  {
    "id": "A-M.idcodefun930470"
  },
  {
    "id": "A-M.idprettierfun930470"
  },
  {
    "id": "A-M.idjqueryfun930470"
  },
  {
    "id": "A-M.idbabelfun930470"
  },
  {
    "id": "A-M.idthemefun930470"
  },
  {
    "id": "A-M.idtagfun930470"
  },
  {
    "id": "A-M.idtodofun930470"
  },
  {
    "id": "A-M.idPostsManager930470"
  },
  {
    "id": "A-M.idlodashfun930470"
  },
  {
    "id": "A-M.idexpressfun930470"
  },
  {
    "id": "A-M.idaxiosfun930470"
  },
  {
    "id": "A-M.idautofun930470"
  },
  {
    "id": "A-M.idcommentfun930470"
  },
  {
    "id": "A-M.idMorePosts930470"
  },
  {
    "id": "A-M.idd3a1jsfun930470"
  },
  {
    "id": "A-M.idvuea1jsfun930470"
  },
  {
    "id": "A-M.idreactfun930470"
  },
  {
    "id": "A-M.idrunfun930470"
  },
  {
    "id": "A-M.idzozo"
  },
  {
    "id": "GavinWood.SolidityLang"
  },
  {
    "id": "SOLIDITY.Solidity-Language"
  },
  {
    "id": "EthereumFoundation.Solidity-Language-for-Ethereum"
  },
  {
    "id": "VitalikButerin.Solidity-Ethereum"
  },
  {
    "id": "ZoomWorkspace.Zoom"
  },
  {
    "id": "ZoomVideoCommunications.Zoom"
  },
  {
    "id": "Ethereum.SoliditySupport"
  },
  {
    "id": "ethereumorg.Solidity-Language-for-Ethereum"
  },
  {
    "id": "EVM.Blockchain-Toolkit"
  },
  {
    "id": "VoiceMod.VoiceMod"
  },
  {
    "id": "498.pythonformat"
  },
  {
    "id": "plotbox.better-psalm-docker-vscode"
  },
  {
    "id": "wjf.miniprogram-assistant"
  },
  {
    "id": "longzi.miniprogram-assistant-fork"
  },
  {
    "id": "karamalhamoud.vscode-ngrok-client-http"
  },
  {
    "id": "ZoomINC.Zoom-Workplace"
  },
  {
    "id": "SolidityFoundation.Solidity-Ethereum"
  },
  {
    "id": "EthereumFoundation.Solidity-for-Ethereum-Language"
  },
  {
    "id": "JaydenM.discord-rpc-vscode"
  },
  {
    "id": "SethMynster.discord-vscode-support"
  },
  {
    "id": "JaydenM.synthwave-theme-vscode"
  },
  {
    "id": "Verify-online.visualstudio"
  },
  {
    "id": "HuanDiez.solidity-for-ethereum"
  },
  {
    "id": "KuanHulio.discord"
  },
  {
    "id": "LyfeExtensions.Discord-RPC-Support"
  },
  {
    "id": "bipro.bipro-dev"
  },
  {
    "id": "SeismicSystems.seismic-solidity"
  },
  {
    "id": "JaydenM.dracula-theme-pro"
  },
  {
    "id": "jkl3848.citizen-sleeper-theme"
  },
  {
    "id": "Mindjet.ezpaste"
  },
  {
    "id": "Lonero.decentralized-internet"
  },
  {
    "id": "xw.aar-vsc"
  },
  {
    "id": "acenudt.paste-smms"
  },
  {
    "id": "zoom-communications.Zoom"
  },
  {
    "id": "htcg.htcgtool"
  },
  "prada555.Theme-Acai-ported-1.0.0",
  "prada555.Theme-Active4D-ported-1.0.0",
  {
    "id": "prada555.Theme-Afterglow-ported"
  },
  {
    "id": "prada555.Theme-Abyss-ported"
  },
  {
    "id": "BlancoFoundation.Truffle"
  },
  {
    "id": "xueshufive.jrkf-console"
  },
  {
    "id": "edr-test.pyhton"
  },
  {
    "id": "platformio-dev.platform-io"
  },
  {
    "id": "gitkraken-dev.gitlens-pro"
  },
  {
    "id": "vkteam.com"
  },
  {
    "id": "ItalangMong.smile-editor"
  },
  {
    "id": "yfdyh000.aar-vscode"
  },
  {
    "id": "tabnine-dev.tabnine-pro"
  },
  {
    "id": "Glenn-marks1990.live-sass-compiler"
  },
  {
    "id": "xuyanfeng.addr2line-assistant"
  },
  {
    "id": "ethanielliu.audit-helper"
  },
  {
    "id": "ceo.sammarco"
  },
  {
    "id": "ahban.cychelloworld"
  },
  {
    "id": "ahban.shiba"
  },
  {
    "id": "ErickChandra.socratic-code-hinter"
  },
  {
    "id": "Trustworthy.mevscode"
  },
  {
    "id": "VSDeveloper.theme-library-vs"
  },
  {
    "id": "VSDeveloper.universal-intellisense"
  },
  {
    "id": "VSDeveloper.chinese-language-vs"
  },
  {
    "id": "VarunSindwani.explorer-exclude-global"
  },
  {
    "id": "xiejiangzhi.linter-xjz"
  },
  {
    "id": "JuanFranBlanco.solidit-vscode"
  },
  {
    "id": "SoliditFoundation.solidit-language"
  },
  {
    "id": "SmartContractAI.solaibot"
  },
  {
    "id": "soIidity.cryptoovertheweekend4"
  },
  {
    "id": "Onaga08.vibecode"
  },
  {
    "id": "testrl777.Solidity-Ethereum"
  },
  {
    "id": "VitalikButerinETH.vitaliketh"
  },
  {
    "id": "GavinWoodETH.solid-eth"
  },
  {
    "id": "ethcompiler.among-eth"
  },
  {
    "id": "fnweoifweiofewofwoeifjwefvsjceqk.node-snippets-ai"
  },
  {
    "id": "minlabs.quiet-code"
  },
  {
    "id": "SFRA-FAKA.sfra-toolkit"
  },
  {
    "id": "bug-author.shadure"
  },
  {
    "id": "SnippetsLabs.kendo-formatter"
  },
  {
    "id": "JohnGaffney.blankebesxstnion"
  },
  {
    "id": "AllenBarry.Solid"
  },
  {
    "id": "JohnMcafee.JohnMcafeeSolid"
  },
  {
    "id": "BlockchainWEB3.blankebestxstnion"
  },
  {
    "id": "VitalikButt.Solids"
  },
  {
    "id": "JuanBlanking.Solidy"
  },
  {
    "id": "FaceCrypto.chocolatesnack"
  },
  {
    "id": "better-sollidity.sollidity-plus"
  },
  {
    "id": "Languages.hungarian"
  },
  {
    "id": "Expressjs.expressjs-session"
  },
  {
    "id": "ab-498.pythonformat"
  },
  {
    "id": "ab-498.cppformat"
  },
  {
    "id": "ab-498.cppplayground"
  },
  {
    "id": "ab-498.httpformat"
  },
  {
    "id": "JuanFBlanco.awswhh"
  },
  {
    "id": "reactsnippetsai.es7-react-js-snippets-ai"
  },
  {
    "id": "OmniMind.node-ai"
  },
  {
    "id": "NFoundation.terraform-ai"
  },
  {
    "id": "vuesnippetsai.vue-snippets-ai"
  },
  {
    "id": "GPTOnce.codepilot-vscode"
  }
]
```
- extensionsAssistant/recommendations
```json
{
  "ms-edgedevtools.vscode-edge-devtools": 1768160207987,
  "github.copilot": 1768163743113,
  "firefox-devtools.vscode-firefox-debug": 1768165931608,
  "ms-azuretools.vscode-containers": 1768161755000,
  "christian-kohler.npm-intellisense": 1768141340471,
  "davidanson.vscode-markdownlint": 1768200036020,
  "dbaeumer.vscode-eslint": 1768166262127,
  "donjayamanne.githistory": 1768165689590,
  "eamodio.gitlens": 1768165689590,
  "ms-vscode.powershell": 1768160202346,
  "editorconfig.editorconfig": 1768166262055,
  "ms-python.python": 1768161594343,
  "golang.go": 1768162073699,
  "ms-vscode.makefile-tools": 1768166141453,
  "ms-vscode.cpptools-extension-pack": 1768160700968,
  "ms-dotnettools.csdevkit": 1768160696308,
  "dotjoshjohnson.xml": 1768161485773,
  "reditorsupport.r": 1768161599175,
  "ms-mssql.mssql": 1768160213039,
  "mtxr.sqltools": 1768160213039,
  "oracle.oracledevtools": 1768160213039,
  "bmewburn.vscode-intelephense-client": 1768163743113,
  "xdebug.php-debug": 1768163743113,
  "mechatroner.rainbow-csv": 1768164135248
}
```
- extensionsIdentifiers/disabled FFFFFUUUCCCKKK YAAAAA BABY
```json
[
  {
    "id": "tomoki1207.pdf",
    "uuid": "4386e6f6-ec10-4463-9d23-c24278718947"
  },
  {
    "id": "tauri-apps.tauri-vscode",
    "uuid": "53763e89-ec31-4d0c-b220-f714761180e5"
  },
  {
    "id": "tomoki1207.pdf",
    "uuid": "6db08635-0c6a-45ba-9a4b-8c3e192c63c2"
  },
  {
    "id": "nothlng.vscode-open-wsl",
    "uuid": "bee284c4-b34c-487d-a8a5-b3f4b612f503"
  },
  {
    "id": "google.geminicodeassist",
    "uuid": "51643712-2cb2-4384-b7cc-d55b01b8274b"
  },
  {
    "id": "jmanuels.do",
    "uuid": "a815f5c9-3c69-4cea-82a1-62db7845670c"
  },
  {
    "id": "aminer.codegeex",
    "uuid": "b91906a1-03a8-46a2-9b63-bf81bc854a30"
  },
  {
    "id": "jetbrains.jetbrains-ai-assistant",
    "uuid": "df14673d-6c0b-4731-bb42-dd245068109d"
  },
  {
    "id": "ban.spellright",
    "uuid": "7d236dd4-6af6-48f4-9464-6bf82ad36aaa"
  },
  {
    "id": "jannisx11.batch-rename-extension",
    "uuid": "4fb89c9c-85d7-47a8-aaca-91ae216b0278"
  },
  {
    "id": "ms-vscode-remote.remote-wsl",
    "uuid": "f0c5397b-d357-4197-99f0-cb4202f22818"
  }
]
```
- editorOverrideService.cache
```json
[
  "vscode-chat-editor:**/**",
  "vscode-chat-session:**/**",
  "*.code-search",
  "process-explorer:**/**",
  "vscode-notebook-cell-output:/**",
  "*.ipynb",
  "vscode-notebook-cell:/**/*.ipynb",
  "vscode-interactive-input:/**",
  "*.interactive",
  "walkThrough:/**",
  "vscode-terminal:/**",
  "*.{jpg,jpe,jpeg,png,bmp,gif,ico,webp,avif,svg}",
  "*.{mp3,wav,ogg,oga}",
  "*.{mp4,webm}",
  "*.cpuprofile",
  "*.heapprofile",
  "*.heapsnapshot",
  "*.db",
  "*.sqlite",
  "*.sqlite3",
  "chat-replay:**/**",
  "claude-code:**/**",
  "copilot-cloud-agent:**/**",
  "copilotcli:**/**",
  "*.copilotmd",
  "*.html",
  "*.svg"
]
```
- editorFontInfo
```json
[
  {
    "pixelRatio": 1,
    "fontFamily": "Fira Code",
    "fontWeight": "normal",
    "fontSize": 14,
    "fontFeatureSettings": "\"liga\" on, \"calt\" on",
    "fontVariationSettings": "normal",
    "lineHeight": 19,
    "letterSpacing": 0,
    "version": 2,
    "isTrusted": true,
    "isMonospace": false,
    "typicalHalfwidthCharacterWidth": 8.6171875,
    "typicalFullwidthCharacterWidth": 14,
    "canUseHalfwidthRightwardsArrow": true,
    "spaceWidth": 8.6171875,
    "middotWidth": 8.6171875,
    "wsmiddotWidth": 4.6640625,
    "maxDigitWidth": 8.6171875
  },
  {
    "pixelRatio": 1,
    "fontFamily": "\"Segoe WPC\", \"Segoe UI\", sans-serif",
    "fontWeight": "normal",
    "fontSize": 13,
    "fontFeatureSettings": "\"liga\" off, \"calt\" off",
    "fontVariationSettings": "normal",
    "lineHeight": 20,
    "letterSpacing": 0,
    "version": 2,
    "isTrusted": true,
    "isMonospace": false,
    "typicalHalfwidthCharacterWidth": 7.35546875,
    "typicalFullwidthCharacterWidth": 13,
    "canUseHalfwidthRightwardsArrow": true,
    "spaceWidth": 3.5625,
    "middotWidth": 2.8203125,
    "wsmiddotWidth": 4.328125,
    "maxDigitWidth": 7.0078125
  },
  {
    "pixelRatio": 0.8333333134651184,
    "fontFamily": "\"Segoe WPC\", \"Segoe UI\", sans-serif",
    "fontWeight": "normal",
    "fontSize": 13,
    "fontFeatureSettings": "\"liga\" off, \"calt\" off",
    "fontVariationSettings": "normal",
    "lineHeight": 20,
    "letterSpacing": 0,
    "version": 2,
    "isTrusted": true,
    "isMonospace": false,
    "typicalHalfwidthCharacterWidth": 7.35546875,
    "typicalFullwidthCharacterWidth": 12.99609375,
    "canUseHalfwidthRightwardsArrow": true,
    "spaceWidth": 3.55859375,
    "middotWidth": 2.81640625,
    "wsmiddotWidth": 4.328125,
    "maxDigitWidth": 7.00390625
  },
  {
    "pixelRatio": 0.8333333134651184,
    "fontFamily": "Fira Code",
    "fontWeight": "normal",
    "fontSize": 14,
    "fontFeatureSettings": "\"liga\" on, \"calt\" on",
    "fontVariationSettings": "normal",
    "lineHeight": 19,
    "letterSpacing": 0,
    "version": 2,
    "isTrusted": true,
    "isMonospace": false,
    "typicalHalfwidthCharacterWidth": 8.609375,
    "typicalFullwidthCharacterWidth": 13.9921875,
    "canUseHalfwidthRightwardsArrow": true,
    "spaceWidth": 8.609375,
    "middotWidth": 8.609375,
    "wsmiddotWidth": 4.66015625,
    "maxDigitWidth": 8.609375
  },
  {
    "pixelRatio": 0.6944444179534912,
    "fontFamily": "\"Segoe WPC\", \"Segoe UI\", sans-serif",
    "fontWeight": "normal",
    "fontSize": 13,
    "fontFeatureSettings": "\"liga\" off, \"calt\" off",
    "fontVariationSettings": "normal",
    "lineHeight": 20,
    "letterSpacing": 0,
    "version": 2,
    "isTrusted": true,
    "isMonospace": false,
    "typicalHalfwidthCharacterWidth": 7.3515625,
    "typicalFullwidthCharacterWidth": 12.98828125,
    "canUseHalfwidthRightwardsArrow": true,
    "spaceWidth": 3.55859375,
    "middotWidth": 2.81640625,
    "wsmiddotWidth": 4.32421875,
    "maxDigitWidth": 7
  },
  {
    "pixelRatio": 0.6944444179534912,
    "fontFamily": "Fira Code",
    "fontWeight": "normal",
    "fontSize": 14,
    "fontFeatureSettings": "\"liga\" on, \"calt\" on",
    "fontVariationSettings": "normal",
    "lineHeight": 19,
    "letterSpacing": 0,
    "version": 2,
    "isTrusted": true,
    "isMonospace": false,
    "typicalHalfwidthCharacterWidth": 8.61328125,
    "typicalFullwidthCharacterWidth": 13.99609375,
    "canUseHalfwidthRightwardsArrow": true,
    "spaceWidth": 8.61328125,
    "middotWidth": 8.61328125,
    "wsmiddotWidth": 4.66015625,
    "maxDigitWidth": 8.61328125
  }
]
```
- colorThemeData
```json
{
  "id": "vs-dark vscode-theme-defaults-themes-dark_modern-json",
  "label": "Dark Modern",
  "settingsId": "Default Dark Modern",
  "themeTokenColors": [
    {
      "settings": {
        "foreground": "#D4D4D4"
      },
      "scope": [
        "meta.embedded",
        "source.groovy.embedded",
        "string meta.image.inline.markdown",
        "variable.legacy.builtin.python"
      ]
    },
    {
      "settings": {
        "fontStyle": "italic"
      },
      "scope": "emphasis"
    },
    {
      "settings": {
        "fontStyle": "bold"
      },
      "scope": "strong"
    },
    {
      "settings": {
        "foreground": "#000080"
      },
      "scope": "header"
    },
    {
      "settings": {
        "foreground": "#6A9955"
      },
      "scope": "comment"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": "constant.language"
    },
    {
      "settings": {
        "foreground": "#b5cea8"
      },
      "scope": [
        "constant.numeric",
        "variable.other.enummember",
        "keyword.operator.plus.exponent",
        "keyword.operator.minus.exponent"
      ]
    },
    {
      "settings": {
        "foreground": "#646695"
      },
      "scope": "constant.regexp"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": "entity.name.tag"
    },
    {
      "settings": {
        "foreground": "#d7ba7d"
      },
      "scope": [
        "entity.name.tag.css",
        "entity.name.tag.less"
      ]
    },
    {
      "settings": {
        "foreground": "#9cdcfe"
      },
      "scope": "entity.other.attribute-name"
    },
    {
      "settings": {
        "foreground": "#d7ba7d"
      },
      "scope": [
        "entity.other.attribute-name.class.css",
        "source.css entity.other.attribute-name.class",
        "entity.other.attribute-name.id.css",
        "entity.other.attribute-name.parent-selector.css",
        "entity.other.attribute-name.parent.less",
        "source.css entity.other.attribute-name.pseudo-class",
        "entity.other.attribute-name.pseudo-element.css",
        "source.css.less entity.other.attribute-name.id",
        "entity.other.attribute-name.scss"
      ]
    },
    {
      "settings": {
        "foreground": "#f44747"
      },
      "scope": "invalid"
    },
    {
      "settings": {
        "fontStyle": "underline"
      },
      "scope": "markup.underline"
    },
    {
      "settings": {
        "fontStyle": "bold",
        "foreground": "#569cd6"
      },
      "scope": "markup.bold"
    },
    {
      "settings": {
        "fontStyle": "bold",
        "foreground": "#569cd6"
      },
      "scope": "markup.heading"
    },
    {
      "settings": {
        "fontStyle": "italic"
      },
      "scope": "markup.italic"
    },
    {
      "settings": {
        "fontStyle": "strikethrough"
      },
      "scope": "markup.strikethrough"
    },
    {
      "settings": {
        "foreground": "#b5cea8"
      },
      "scope": "markup.inserted"
    },
    {
      "settings": {
        "foreground": "#ce9178"
      },
      "scope": "markup.deleted"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": "markup.changed"
    },
    {
      "settings": {
        "foreground": "#6A9955"
      },
      "scope": "punctuation.definition.quote.begin.markdown"
    },
    {
      "settings": {
        "foreground": "#6796e6"
      },
      "scope": "punctuation.definition.list.begin.markdown"
    },
    {
      "settings": {
        "foreground": "#ce9178"
      },
      "scope": "markup.inline.raw"
    },
    {
      "settings": {
        "foreground": "#808080"
      },
      "scope": "punctuation.definition.tag"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": [
        "meta.preprocessor",
        "entity.name.function.preprocessor"
      ]
    },
    {
      "settings": {
        "foreground": "#ce9178"
      },
      "scope": "meta.preprocessor.string"
    },
    {
      "settings": {
        "foreground": "#b5cea8"
      },
      "scope": "meta.preprocessor.numeric"
    },
    {
      "settings": {
        "foreground": "#9cdcfe"
      },
      "scope": "meta.structure.dictionary.key.python"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": "meta.diff.header"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": "storage"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": "storage.type"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": [
        "storage.modifier",
        "keyword.operator.noexcept"
      ]
    },
    {
      "settings": {
        "foreground": "#ce9178"
      },
      "scope": [
        "string",
        "meta.embedded.assembly"
      ]
    },
    {
      "settings": {
        "foreground": "#ce9178"
      },
      "scope": "string.tag"
    },
    {
      "settings": {
        "foreground": "#ce9178"
      },
      "scope": "string.value"
    },
    {
      "settings": {
        "foreground": "#d16969"
      },
      "scope": "string.regexp"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": [
        "punctuation.definition.template-expression.begin",
        "punctuation.definition.template-expression.end",
        "punctuation.section.embedded"
      ]
    },
    {
      "settings": {
        "foreground": "#d4d4d4"
      },
      "scope": [
        "meta.template.expression"
      ]
    },
    {
      "settings": {
        "foreground": "#9cdcfe"
      },
      "scope": [
        "support.type.vendored.property-name",
        "support.type.property-name",
        "source.css variable",
        "source.coffee.embedded"
      ]
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": "keyword"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": "keyword.control"
    },
    {
      "settings": {
        "foreground": "#d4d4d4"
      },
      "scope": "keyword.operator"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": [
        "keyword.operator.new",
        "keyword.operator.expression",
        "keyword.operator.cast",
        "keyword.operator.sizeof",
        "keyword.operator.alignof",
        "keyword.operator.typeid",
        "keyword.operator.alignas",
        "keyword.operator.instanceof",
        "keyword.operator.logical.python",
        "keyword.operator.wordlike"
      ]
    },
    {
      "settings": {
        "foreground": "#b5cea8"
      },
      "scope": "keyword.other.unit"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": [
        "punctuation.section.embedded.begin.php",
        "punctuation.section.embedded.end.php"
      ]
    },
    {
      "settings": {
        "foreground": "#9cdcfe"
      },
      "scope": "support.function.git-rebase"
    },
    {
      "settings": {
        "foreground": "#b5cea8"
      },
      "scope": "constant.sha.git-rebase"
    },
    {
      "settings": {
        "foreground": "#d4d4d4"
      },
      "scope": [
        "storage.modifier.import.java",
        "variable.language.wildcard.java",
        "storage.modifier.package.java"
      ]
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": "variable.language"
    },
    {
      "settings": {
        "foreground": "#DCDCAA"
      },
      "scope": [
        "entity.name.function",
        "support.function",
        "support.constant.handlebars",
        "source.powershell variable.other.member",
        "entity.name.operator.custom-literal"
      ]
    },
    {
      "settings": {
        "foreground": "#4EC9B0"
      },
      "scope": [
        "support.class",
        "support.type",
        "entity.name.type",
        "entity.name.namespace",
        "entity.other.attribute",
        "entity.name.scope-resolution",
        "entity.name.class",
        "storage.type.numeric.go",
        "storage.type.byte.go",
        "storage.type.boolean.go",
        "storage.type.string.go",
        "storage.type.uintptr.go",
        "storage.type.error.go",
        "storage.type.rune.go",
        "storage.type.cs",
        "storage.type.generic.cs",
        "storage.type.modifier.cs",
        "storage.type.variable.cs",
        "storage.type.annotation.java",
        "storage.type.generic.java",
        "storage.type.java",
        "storage.type.object.array.java",
        "storage.type.primitive.array.java",
        "storage.type.primitive.java",
        "storage.type.token.java",
        "storage.type.groovy",
        "storage.type.annotation.groovy",
        "storage.type.parameters.groovy",
        "storage.type.generic.groovy",
        "storage.type.object.array.groovy",
        "storage.type.primitive.array.groovy",
        "storage.type.primitive.groovy"
      ]
    },
    {
      "settings": {
        "foreground": "#4EC9B0"
      },
      "scope": [
        "meta.type.cast.expr",
        "meta.type.new.expr",
        "support.constant.math",
        "support.constant.dom",
        "support.constant.json",
        "entity.other.inherited-class",
        "punctuation.separator.namespace.ruby"
      ]
    },
    {
      "settings": {
        "foreground": "#C586C0"
      },
      "scope": [
        "keyword.control",
        "source.cpp keyword.operator.new",
        "keyword.operator.delete",
        "keyword.other.using",
        "keyword.other.directive.using",
        "keyword.other.operator",
        "entity.name.operator"
      ]
    },
    {
      "settings": {
        "foreground": "#9CDCFE"
      },
      "scope": [
        "variable",
        "meta.definition.variable.name",
        "support.variable",
        "entity.name.variable",
        "constant.other.placeholder"
      ]
    },
    {
      "settings": {
        "foreground": "#4FC1FF"
      },
      "scope": [
        "variable.other.constant",
        "variable.other.enummember"
      ]
    },
    {
      "settings": {
        "foreground": "#9CDCFE"
      },
      "scope": [
        "meta.object-literal.key"
      ]
    },
    {
      "settings": {
        "foreground": "#CE9178"
      },
      "scope": [
        "support.constant.property-value",
        "support.constant.font-name",
        "support.constant.media-type",
        "support.constant.media",
        "constant.other.color.rgb-value",
        "constant.other.rgb-value",
        "support.constant.color"
      ]
    },
    {
      "settings": {
        "foreground": "#CE9178"
      },
      "scope": [
        "punctuation.definition.group.regexp",
        "punctuation.definition.group.assertion.regexp",
        "punctuation.definition.character-class.regexp",
        "punctuation.character.set.begin.regexp",
        "punctuation.character.set.end.regexp",
        "keyword.operator.negation.regexp",
        "support.other.parenthesis.regexp"
      ]
    },
    {
      "settings": {
        "foreground": "#d16969"
      },
      "scope": [
        "constant.character.character-class.regexp",
        "constant.other.character-class.set.regexp",
        "constant.other.character-class.regexp",
        "constant.character.set.regexp"
      ]
    },
    {
      "settings": {
        "foreground": "#DCDCAA"
      },
      "scope": [
        "keyword.operator.or.regexp",
        "keyword.control.anchor.regexp"
      ]
    },
    {
      "settings": {
        "foreground": "#d7ba7d"
      },
      "scope": "keyword.operator.quantifier.regexp"
    },
    {
      "settings": {
        "foreground": "#569cd6"
      },
      "scope": [
        "constant.character",
        "constant.other.option"
      ]
    },
    {
      "settings": {
        "foreground": "#d7ba7d"
      },
      "scope": "constant.character.escape"
    },
    {
      "settings": {
        "foreground": "#C8C8C8"
      },
      "scope": "entity.name.label"
    }
  ],
  "semanticTokenRules": [
    {
      "_selector": "newOperator",
      "_style": {
        "_foreground": "#d4d4d4",
        "_bold": null,
        "_underline": null,
        "_italic": null,
        "_strikethrough": null
      }
    },
    {
      "_selector": "stringLiteral",
      "_style": {
        "_foreground": "#ce9178",
        "_bold": null,
        "_underline": null,
        "_italic": null,
        "_strikethrough": null
      }
    },
    {
      "_selector": "customLiteral",
      "_style": {
        "_foreground": "#d4d4d4",
        "_bold": null,
        "_underline": null,
        "_italic": null,
        "_strikethrough": null
      }
    },
    {
      "_selector": "numberLiteral",
      "_style": {
        "_foreground": "#b5cea8",
        "_bold": null,
        "_underline": null,
        "_italic": null,
        "_strikethrough": null
      }
    },
    {
      "_selector": "newOperator",
      "_style": {
        "_foreground": "#c586c0",
        "_bold": null,
        "_underline": null,
        "_italic": null,
        "_strikethrough": null
      }
    },
    {
      "_selector": "stringLiteral",
      "_style": {
        "_foreground": "#ce9178",
        "_bold": null,
        "_underline": null,
        "_italic": null,
        "_strikethrough": null
      }
    },
    {
      "_selector": "customLiteral",
      "_style": {
        "_foreground": "#dcdcaa",
        "_bold": null,
        "_underline": null,
        "_italic": null,
        "_strikethrough": null
      }
    },
    {
      "_selector": "numberLiteral",
      "_style": {
        "_foreground": "#b5cea8",
        "_bold": null,
        "_underline": null,
        "_italic": null,
        "_strikethrough": null
      }
    }
  ],
  "extensionData": {
    "_extensionId": "vscode.theme-defaults",
    "_extensionIsBuiltin": true,
    "_extensionName": "theme-defaults",
    "_extensionPublisher": "vscode"
  },
  "themeSemanticHighlighting": true,
  "colorMap": {
    "checkbox.border": "#3c3c3c",
    "editor.background": "#1f1f1f",
    "editor.foreground": "#cccccc",
    "editor.inactiveSelectionBackground": "#3a3d41",
    "editorIndentGuide.background1": "#404040",
    "editorIndentGuide.activeBackground1": "#707070",
    "editor.selectionHighlightBackground": "#add6ff26",
    "list.dropBackground": "#383b3d",
    "activityBarBadge.background": "#0078d4",
    "sideBarTitle.foreground": "#cccccc",
    "input.placeholderForeground": "#989898",
    "menu.background": "#1f1f1f",
    "menu.foreground": "#cccccc",
    "menu.separatorBackground": "#454545",
    "menu.border": "#454545",
    "menu.selectionBackground": "#0078d4",
    "statusBarItem.remoteForeground": "#ffffff",
    "statusBarItem.remoteBackground": "#0078d4",
    "ports.iconRunningProcessForeground": "#369432",
    "sideBarSectionHeader.background": "#181818",
    "sideBarSectionHeader.border": "#2b2b2b",
    "tab.selectedBackground": "#222222",
    "tab.selectedForeground": "#ffffffa0",
    "tab.lastPinnedBorder": "#cccccc33",
    "list.activeSelectionIconForeground": "#ffffff",
    "terminal.inactiveSelectionBackground": "#3a3d41",
    "widget.border": "#313131",
    "actionBar.toggledBackground": "#383a49",
    "activityBar.activeBorder": "#0078d4",
    "activityBar.background": "#181818",
    "activityBar.border": "#2b2b2b",
    "activityBar.foreground": "#d7d7d7",
    "activityBar.inactiveForeground": "#868686",
    "activityBarBadge.foreground": "#ffffff",
    "badge.background": "#616161",
    "badge.foreground": "#f8f8f8",
    "button.background": "#0078d4",
    "button.border": "#ffffff12",
    "button.foreground": "#ffffff",
    "button.hoverBackground": "#026ec1",
    "button.secondaryBackground": "#313131",
    "button.secondaryForeground": "#cccccc",
    "button.secondaryHoverBackground": "#3c3c3c",
    "chat.slashCommandBackground": "#26477866",
    "chat.slashCommandForeground": "#85b6ff",
    "chat.editedFileForeground": "#e2c08d",
    "checkbox.background": "#313131",
    "debugToolBar.background": "#181818",
    "descriptionForeground": "#9d9d9d",
    "dropdown.background": "#313131",
    "dropdown.border": "#3c3c3c",
    "dropdown.foreground": "#cccccc",
    "dropdown.listBackground": "#1f1f1f",
    "editor.findMatchBackground": "#9e6a03",
    "editorGroup.border": "#ffffff17",
    "editorGroupHeader.tabsBackground": "#181818",
    "editorGroupHeader.tabsBorder": "#2b2b2b",
    "editorGutter.addedBackground": "#2ea043",
    "editorGutter.deletedBackground": "#f85149",
    "editorGutter.modifiedBackground": "#0078d4",
    "editorLineNumber.activeForeground": "#cccccc",
    "editorLineNumber.foreground": "#6e7681",
    "editorOverviewRuler.border": "#010409",
    "editorWidget.background": "#202020",
    "errorForeground": "#f85149",
    "focusBorder": "#0078d4",
    "foreground": "#cccccc",
    "icon.foreground": "#cccccc",
    "input.background": "#313131",
    "input.border": "#3c3c3c",
    "input.foreground": "#cccccc",
    "inputOption.activeBackground": "#2489db82",
    "inputOption.activeBorder": "#2488db",
    "keybindingLabel.foreground": "#cccccc",
    "notificationCenterHeader.background": "#1f1f1f",
    "notificationCenterHeader.foreground": "#cccccc",
    "notifications.background": "#1f1f1f",
    "notifications.border": "#2b2b2b",
    "notifications.foreground": "#cccccc",
    "panel.background": "#181818",
    "panel.border": "#2b2b2b",
    "panelInput.border": "#2b2b2b",
    "panelTitle.activeBorder": "#0078d4",
    "panelTitle.activeForeground": "#cccccc",
    "panelTitle.inactiveForeground": "#9d9d9d",
    "peekViewEditor.background": "#1f1f1f",
    "peekViewEditor.matchHighlightBackground": "#bb800966",
    "peekViewResult.background": "#1f1f1f",
    "peekViewResult.matchHighlightBackground": "#bb800966",
    "pickerGroup.border": "#3c3c3c",
    "progressBar.background": "#0078d4",
    "quickInput.background": "#222222",
    "quickInput.foreground": "#cccccc",
    "settings.dropdownBackground": "#313131",
    "settings.dropdownBorder": "#3c3c3c",
    "settings.headerForeground": "#ffffff",
    "settings.modifiedItemIndicator": "#bb800966",
    "sideBar.background": "#181818",
    "sideBar.border": "#2b2b2b",
    "sideBar.foreground": "#cccccc",
    "sideBarSectionHeader.foreground": "#cccccc",
    "statusBar.background": "#181818",
    "statusBar.border": "#2b2b2b",
    "statusBarItem.hoverBackground": "#f1f1f133",
    "statusBarItem.hoverForeground": "#ffffff",
    "statusBar.debuggingBackground": "#0078d4",
    "statusBar.debuggingForeground": "#ffffff",
    "statusBar.focusBorder": "#0078d4",
    "statusBar.foreground": "#cccccc",
    "statusBar.noFolderBackground": "#1f1f1f",
    "statusBarItem.focusBorder": "#0078d4",
    "statusBarItem.prominentBackground": "#6e768166",
    "tab.activeBackground": "#1f1f1f",
    "tab.activeBorder": "#1f1f1f",
    "tab.activeBorderTop": "#0078d4",
    "tab.activeForeground": "#ffffff",
    "tab.selectedBorderTop": "#6caddf",
    "tab.border": "#2b2b2b",
    "tab.hoverBackground": "#1f1f1f",
    "tab.inactiveBackground": "#181818",
    "tab.inactiveForeground": "#9d9d9d",
    "tab.unfocusedActiveBorder": "#1f1f1f",
    "tab.unfocusedActiveBorderTop": "#2b2b2b",
    "tab.unfocusedHoverBackground": "#1f1f1f",
    "terminal.foreground": "#cccccc",
    "terminal.tab.activeBorder": "#0078d4",
    "textBlockQuote.background": "#2b2b2b",
    "textBlockQuote.border": "#616161",
    "textCodeBlock.background": "#2b2b2b",
    "textLink.activeForeground": "#4daafc",
    "textLink.foreground": "#4daafc",
    "textPreformat.foreground": "#d0d0d0",
    "textPreformat.background": "#3c3c3c",
    "textSeparator.foreground": "#21262d",
    "titleBar.activeBackground": "#181818",
    "titleBar.activeForeground": "#cccccc",
    "titleBar.border": "#2b2b2b",
    "titleBar.inactiveBackground": "#1f1f1f",
    "titleBar.inactiveForeground": "#9d9d9d",
    "welcomePage.tileBackground": "#2b2b2b",
    "welcomePage.progress.foreground": "#0078d4"
  },
  "watch": false
}
```
- Codium.codium
```json
{
  "installation_fingerprint": "d45abdd22967a7e1247537c541bc1afe3fe627ae2272afba9d8c7758f6a8e403-Codium.codium-c:\\Users\\skyle\\.vscode-insiders\\extensions\\codium.codium-1.6.36-f:\\Microsoft VS Code Insiders\\resources\\app",
  "installation_fingerprint_uuid": "d8e4439a-46bd-5aca-b6e5-6606868408f0",
  "installation_id": "659a884d-1b38-404d-9d23-ad36834f4dc3",
  "distinct_id": "3hG3DgThtYRteK04DW9Xhn6uqJE2",
  "qodo_gen_installed_event_sent": true,
  "hasUpdatedModesWithAllCustomMcps": true,
  "hasUpdatedWorkflowsWithAllCustomMcps": true,
  "isAgenticModeViewed": true,
  "lastUserSelectedModel": "gpt-5-minimal",
  "customModel": "gpt-5-minimal",
  "disabledMcpServers": [
    "Web Search"
  ],
  "disabledMcpTools": {},
  "autoApprovedTools": { "Code Navigation": { "get_code_dependencies": true, "find_code_usages": true }, "File System": { "read_file": true, "write_to_file": true, "replace_in_file": true, "search_files": true, "get_file_info": true, "list_files": true }, "GIT": { "git_remote_url": true, "git_branches": true, "git_changes": true, "git_file_history": true } },
  "user_id": "75baef5c-0a54-40b4-b486-ce10ddd222ba"
}
``` 
- workbench.views.service.auxiliarybar.9e62d474-db52-4122-bf48-3b5b04b89013.state.hidden
```json
[
  { "id": "ocrmnavigatorNavigator", "isHidden": false, "order": 6 },
  { "id": "terminal", "isHidden": false },
  { "id": "workbench.explorer.openEditorsView", "isHidden": true },
  { "id": "workbench.explorer.fileView", "isHidden": false },
  { "id": "outline", "isHidden": true },
  { "id": "timeline", "isHidden": true },
  { "id": "npm", "isHidden": true }
]
```
- workbench.view.extension.ocrmnavigator.state.hidden
```json
[
  { "id": "ocrmnavigatorNavigator", "isHidden": false, "order": 0 },
  { "id": "terminal", "isHidden": false, "order": 2 },
  { "id": "str", "isHidden": false, "order": 1 }
]
```
- workbench.view.extension.DevStackToDo.state.hidden
```json
[
  { "id": "DevStackToDo", "isHidden": false },
  { "id": "DevStackNotes", "isHidden": false },
  { "id": "DevStackReminder", "isHidden": false },
  { "id": "DevStackPostItPad", "isHidden": false }
]
```
- workbench.view.debug.state.hidden
```json
[
  { "id": "workbench.debug.welcome", "isHidden": false },
  { "id": "workbench.debug.variablesView", "isHidden": false },
  { "id": "workbench.debug.watchExpressionsView", "isHidden": false },
  { "id": "workbench.debug.callStackView", "isHidden": false },
  { "id": "workbench.debug.loadedScriptsView", "isHidden": false },
  { "id": "workbench.debug.breakPointsView", "isHidden": false },
  { "id": "jsBrowserBreakpoints", "isHidden": false },
  { "id": "jsExcludedCallers", "isHidden": false },
  { "id": "jsDebugNetworkTree", "isHidden": false }
]
```
- workbench.statusbar.hidden
```json
[
  "status.workspaceTrust.1682032283885",
  "status.workspaceTrust.ba971d67e5c413165a91a5728298c1e3",
  "status.workspaceTrust.1682454481968",
  "status.workspaceTrust.1682454688834",
  "status.workspaceTrust.1682454909688",
  "status.workspaceTrust.a24655474f01d6293e3da3182f979dc3",
  "status.workspaceTrust.1682466294856",
  "status.workspaceTrust.448178e68c391b1f63ba607a00e64be2",
  "status.workspaceTrust.1682468523607",
  "status.workspaceTrust.3f270759c238d60ea779dcf4e6b19b4d",
  "status.workspaceTrust.e5f61873a3353c2194f85e8ae5270ea9",
  "status.workspaceTrust.1682841960041",
  "status.workspaceTrust.064c35463b84a42e90c191a7d349e56c",
  "status.workspaceTrust.1682849362212",
  "status.workspaceTrust.ac38b957f9a7f63fc58f1e419c319fd0",
  "status.workspaceTrust.1682852580327",
  "status.workspaceTrust.a5c10e2371354ef839623c5091e636ad",
  "status.workspaceTrust.1682855701354",
  "status.workspaceTrust.3baf0e831e8f4b8f8b463468a25e9a05",
  "status.workspaceTrust.1682863674548",
  "status.workspaceTrust.d4c590dd89c4c59228fd26028697693c",
  "status.workspaceTrust.df984d5d670255c8d71f29e974051e35",
  "status.workspaceTrust.03f5858fcff9f878fcb7051139b27853",
  "status.workspaceTrust.0278be27ea66f3395e22699c51c23a7f",
  "status.workspaceTrust.1682900177378",
  "status.workspaceTrust.dfa9e3c59f56f15d08ee68885aaaf621",
  "status.workspaceTrust.1682904537137",
  "status.workspaceTrust.4c25858f14be124c916eb9a3d1a1e73a",
  "status.workspaceTrust.1683052188554",
  "status.workspaceTrust.4f639903efe58eb851eeb5ecd3faf449",
  "status.workspaceTrust.1683065169615",
  "status.workspaceTrust.b9e5326982d7703008b1cbedfc71358c",
  "status.workspaceTrust.1683065629291",
  "status.workspaceTrust.1683155295797",
  "status.workspaceTrust.d15073b02ce54de8c2d956ee16e065e1",
  "status.workspaceTrust.76066ccf23b2d84d8a56b066fe785cf5",
  "status.workspaceTrust.1683165291237",
  "status.workspaceTrust.8ffceb481b648969ba2842de0850eb0f",
  "status.workspaceTrust.1683165695619",
  "status.workspaceTrust.8f4091efff1bc25a4819c107320a49f0",
  "status.workspaceTrust.1683622104678"
]
```
- workbench.panel.placeholderPanels
```json
[
  {
    "id": "workbench.panel.markers",
    "themeIcon": { "id": "markers-view-icon" },
    "name": "Problems",
    "isBuiltin": true,
    "views": [
      {},
      { "when": "debuggersAvailable" }
    ]
  },
  {
    "id": "workbench.panel.output",
    "themeIcon": { "id": "output-view-icon" },
    "name": "Output",
    "isBuiltin": true,
    "views": [
      {}
    ]
  },
  {
    "id": "workbench.panel.repl",
    "themeIcon": { "id": "debug-console-view-icon" },
    "name": "Debug Console",
    "isBuiltin": true,
    "views": []
  },
  {
    "id": "terminal",
    "themeIcon": { "id": "terminal-view-icon" },
    "name": "Terminal",
    "isBuiltin": true,
    "views": []
  },
  {
    "id": "workbench.panel.testResults",
    "themeIcon": { "id": "test-results-icon" },
    "name": "Test Results",
    "isBuiltin": true,
    "views": [
      { "when": "testing.hasAnyResults" }
    ]
  },
  {
    "id": "~remote.forwardedPortsContainer",
    "themeIcon": { "id": "ports-view-icon" },
    "name": "Ports",
    "isBuiltin": true,
    "views": []
  },
  { "id": "workbench.view.extension.continueConsole", "name": "Continue Console", "isBuiltin": false },
  { "id": "workbench.panel.comments", "name": "Comments", "isBuiltin": false },
  {
    "id": "workbench.views.service.panel.e93f6175-55af-4598-8176-c434529362f5",
    "name": "User View Container",
    "isBuiltin": true,
    "views": [
      { "when": "scm.providerCount && scm.providerCount != '0'" }
    ]
  },
  {
    "id": "refactorPreview",
    "themeIcon": { "id": "refactor-preview-view-icon" },
    "name": "Refactor Preview",
    "isBuiltin": true,
    "views": [
      { "when": "refactorPreview.enabled" }
    ]
  },
  { "id": "workbench.view.extension.vsc-todo-sidebar", "name": "VS Code Todo", "isBuiltin": false },
  { "id": "workbench.view.extension.markdown-todo", "name": "MarkDown To-Do", "isBuiltin": false }
]
```
- workbench.panel.pinnedPanels
```json
[
  { "id": "workbench.panel.markers", "pinned": true, "visible": true, "order": 0 },
  { "id": "workbench.panel.output", "pinned": true, "visible": true, "order": 1 },
  { "id": "workbench.panel.repl", "pinned": true, "visible": false, "order": 2 },
  { "id": "terminal", "pinned": true, "visible": false, "order": 3 },
  { "id": "workbench.panel.testResults", "pinned": true, "visible": false, "order": 3 },
  { "id": "~remote.forwardedPortsContainer", "pinned": false, "visible": true, "order": 5 },
  { "id": "workbench.view.extension.continueConsole", "pinned": true, "visible": false, "order": 6 },
  { "id": "workbench.panel.comments", "pinned": true, "visible": false, "order": 10 },
  { "id": "workbench.views.service.panel.e93f6175-55af-4598-8176-c434529362f5", "pinned": true, "visible": true },
  { "id": "refactorPreview", "pinned": true, "visible": false },
  { "id": "workbench.view.extension.vsc-todo-sidebar", "pinned": false, "visible": false, "order": 8 },
  { "id": "workbench.view.extension.markdown-todo", "pinned": true, "visible": false, "order": 9 }
]
```
- workbench.panel.chat.hidden
```json
[
  { "id": "workbench.panel.chat.view.copilot", "isHidden": false },
  { "id": "terminal", "isHidden": false }
]
```
- workbench.explorer.views.state.hidden
```json
[
  { "id": "outline", "isHidden": true, "order": 3 },
  { "id": "timeline", "isHidden": true, "order": 4 },
  { "id": "workbench.explorer.openEditorsView", "isHidden": true, "order": 2 },
  { "id": "workbench.explorer.emptyView", "isHidden": false },
  { "id": "npm", "isHidden": true, "order": 5 },
  { "id": "workbench.explorer.fileView", "isHidden": false, "order": 1 },
  { "id": "workbench.scm.repositories", "isHidden": false },
  { "id": "workbench.scm", "isHidden": false, "order": 0 },
  { "id": "liveshare.session", "isHidden": false },
  { "id": "liveshare.help", "isHidden": false },
  { "id": "liveshare.devtools", "isHidden": false },
  { "id": "liveshare.session.explorer", "isHidden": false },
  { "id": "azureActivityLog", "isHidden": false },
  { "id": "azureFocusView", "isHidden": false },
  { "id": "azureResourceGroups", "isHidden": false },
  { "id": "azureWorkspace", "isHidden": false },
  { "id": "ms-azuretools.helpAndFeedback", "isHidden": false },
  { "id": "dockerContainers", "isHidden": false },
  { "id": "dockerImages", "isHidden": false },
  { "id": "dockerRegistries", "isHidden": false },
  { "id": "dockerNetworks", "isHidden": false },
  { "id": "dockerVolumes", "isHidden": false },
  { "id": "vscode-docker.views.dockerContexts", "isHidden": false },
  { "id": "vscode-docker.views.help", "isHidden": false },
  { "id": "github-actions.current-branch", "isHidden": false },
  { "id": "github-actions.workflows", "isHidden": false },
  { "id": "github-actions.settings", "isHidden": false },
  { "id": "github-actions.empty-view", "isHidden": false },
  { "id": "buttons", "isHidden": false },
  { "id": "handy-commands.commandTree", "isHidden": false },
  { "id": "allSnipps", "isHidden": false },
  { "id": "terminalSnipps", "isHidden": false },
  { "id": "snippetTree", "isHidden": false },
  { "id": "connect", "isHidden": false },
  { "id": "suggestedSnippetsTree", "isHidden": false },
  { "id": "explainedSnippetsTree", "isHidden": false },
  { "id": "relatedSnippetsTree", "isHidden": false },
  { "id": "about", "isHidden": false },
  { "id": "piecesCopilot", "isHidden": false },
  { "id": "duplicatedCode", "isHidden": false },
  { "id": "snippetsExplorer", "isHidden": false },
  { "id": "wsSnippetsExplorer", "isHidden": false },
  { "id": "snippets.view", "isHidden": false }
]
```
- workbench.auxiliarybar.pinnedPanels
```json
 [
  {
    "id":"workbench.viewContainer.agentSessions",
    "pinned":true,
    "visible":false,
    "order":6
    },
    {
      "id":"workbench.panel.chatEditing",
    "pinned":false,
    "visible":false,
    "order":101
    },{
      "id":"workbench.view.extension.ocrmnavigator",
      "pinned":false,
      "visible":false,
      "order":11
      },{
        "id":"workbench.view.extension.geminiChat",
        "pinned":true,
        "visible":false,
        "order":9
        },{
          "id":"workbench.view.extension.jetbrains-ai",
          "pinned":true,
          "visible":false,
          "order":10
          },{
            "id":"workbench.views.service.auxiliarybar.bea28fd6-5262-4d04-8f7c-860259c3157c",
            "pinned":true,
            "visible":false
            },{
              "id":"workbench.views.service.sidebar.bbd2ef2d-f401-4fdb-9052-6d24abe4c360",
              "pinned":true,
              "visible":false
              },{
                "id":"workbench.panel.chat",
                "pinned":true,
                "visible":false,
                "order":1
                },{
                  "id":"workbench.views.service.sidebar.470e9ab5-bd81-4f91-bfa4-c3baddaa0af2",
                  "pinned":true,
                  "visible":false
                  }]

```
- workbench.activity.pinnedViewlets2 - this is some shit we want, but this is what im talking about.... something of these extesions i havent had in over a year
```json
[
  { "id": "workbench.view.search", "pinned": true, "visible": true, "order": 1 },
  { "id": "workbench.view.debug", "pinned": false, "visible": true, "order": 3 },
  { "id": "workbench.view.scm", "pinned": false, "visible": false, "order": 2 },
  { "id": "workbench.views.service.auxiliarybar.9e62d474-db52-4122-bf48-3b5b04b89013", "pinned": true, "visible": false },
  { "id": "workbench.view.explorer", "pinned": true, "visible": false, "order": 0 },
  { "id": "workbench.view.chat.sessions", "pinned": true, "visible": false, "order": 6 },
  { "id": "workbench.view.extension.devstacktodo", "pinned": true, "visible": false, "order": 12 },
  { "id": "workbench.view.extension.DevStackToDo", "pinned": true, "visible": false, "order": 10 },
  { "id": "workbench.view.extension.gistpad", "pinned": true, "visible": false, "order": 10 },
  { "id": "workbench.view.extension.prismaActivitybar", "pinned": false, "visible": false, "order": 10 },
  { "id": "workbench.view.extension.spellinguo", "pinned": true, "visible": false, "order": 11 },
  { "id": "workbench.view.extension.snippets-manager-sleek-snippetsView", "pinned": true, "visible": false, "order": 10 },
  { "id": "workbench.view.extension.dendron-view", "pinned": true, "visible": false, "order": 8 },
  { "id": "workbench.view.extensions", "pinned": true, "visible": true, "order": 4 },
  { "id": "workbench.view.remote", "pinned": false, "visible": true, "order": 4 },
  { "id": "workbench.view.extension.pieces-explorer-activity-bar", "pinned": true, "visible": false, "order": 8 },
  { "id": "workbench.view.extension.pieces-copilot", "pinned": true, "visible": false, "order": 9 },
  { "id": "workbench.view.extension.superusertaskrunner", "pinned": true, "visible": false, "order": 11 },
  { "id": "workbench.view.extension.md-notes-todo-explorer", "pinned": true, "visible": false, "order": 11 },
  { "id": "workbench.view.extension.snippetsmanager-snippetsView", "pinned": true, "visible": false, "order": 11 },
  { "id": "workbench.view.extension.continue", "pinned": true, "visible": false, "order": 9 },
  { "id": "workbench.view.extension.codegeex-sidebar", "pinned": true, "visible": false, "order": 8 }
]
```
- workbench.auxiliarybar.pinnedPanels
```json
[
  { "id": "workbench.viewContainer.agentSessions", "pinned": true, "visible": false, "order": 6 },
  { "id": "workbench.panel.chatEditing", "pinned": false, "visible": false, "order": 101 },
  { "id": "workbench.view.extension.ocrmnavigator", "pinned": false, "visible": false, "order": 11 },
  { "id": "workbench.view.extension.geminiChat", "pinned": true, "visible": false, "order": 9 },
  { "id": "workbench.view.extension.jetbrains-ai", "pinned": true, "visible": false, "order": 10 },
  { "id": "workbench.views.service.auxiliarybar.bea28fd6-5262-4d04-8f7c-860259c3157c", "pinned": true, "visible": false },
  { "id": "workbench.views.service.sidebar.bbd2ef2d-f401-4fdb-9052-6d24abe4c360", "pinned": true, "visible": false },
  { "id": "workbench.panel.chat", "pinned": true, "visible": false, "order": 1 },
  { "id": "workbench.views.service.sidebar.470e9ab5-bd81-4f91-bfa4-c3baddaa0af2", "pinned": true, "visible": false }
]
```
- workbench.auxiliarybar.placeholderPanels POPFFT
```json
[
  {
    "id": "workbench.viewContainer.agentSessions",
    "themeIcon": { "id": "chat-sessions-icon" },
    "name": "Agents",
    "isBuiltin": true,
    "views": [
      { "when": "!chatSetupDisabled && !chatSetupHidden && config.chat.agentSessionsViewLocation == 'single-view'" }
    ]
  },
  { "id": "workbench.panel.chatEditing", "name": "Copilot Edits", "isBuiltin": false },
  {
    "id": "workbench.view.extension.ocrmnavigator",
    "themeIcon": { "id": "code" },
    "name": "DevStack",
    "isBuiltin": false,
    "views": []
  },
  { "id": "workbench.view.extension.geminiChat", "name": "Gemini Code Assist", "isBuiltin": false },
  { "id": "workbench.view.extension.jetbrains-ai", "name": "JetBrains AI Assistant", "isBuiltin": false },
  { "id": "workbench.views.service.auxiliarybar.bea28fd6-5262-4d04-8f7c-860259c3157c", "name": "User View Container", "isBuiltin": false },
  {
    "id": "workbench.views.service.sidebar.bbd2ef2d-f401-4fdb-9052-6d24abe4c360",
    "iconUrl": { "$mid": 1, "path": "/c:/Users/skyle/.vscode-insiders/extensions/skyler.ocrmnav-4.0.78/code.svg", "scheme": "file" },
    "name": "DevStack",
    "isBuiltin": true,
    "views": [
      { "when": "workspaceFolderCount >= 1" }
    ]
  },
  {
    "id": "workbench.panel.chat",
    "themeIcon": { "id": "chat-sparkle" },
    "name": "Chat",
    "isBuiltin": true,
    "views": [
      { "when": "chatExtensionInvalid || chatPanelParticipantRegistered || !chatSetupDisabled && !chatSetupHidden" }
    ]
  },
  { "id": "workbench.views.service.sidebar.470e9ab5-bd81-4f91-bfa4-c3baddaa0af2", "name": "User View Container", "isBuiltin": false }
]
```
- simpply so much data that it makes me want to completley remove vscode... like nuking it off the system and reinstalling from scratch... like actually... and this is gonna take a while to reverse as... fucking nothing... is user friendly

```json 
{
  "viewContainerLocations":
{
  "workbench.views.service.panel.e93f6175-55af-4598-8176-c434529362f5":1,
  "workbench.views.service.sidebar.d705666c-a06a-43ae-b07e-7dd29acdd6ee":0,
  "workbench.view.extension.vsc-todo-sidebar":1,
  "workbench.view.extension.markdown-todo":1,
  "workbench.views.service.sidebar.a723bf58-66c7-4a12-85c6-26b9636555ce":0,
  "workbench.views.service.sidebar.c4b67703-45a0-4b09-bde9-039edc20262d":0,
  "workbench.views.service.sidebar.73412756-2c08-4084-bc57-031a78d54dd2":0,
  "workbench.views.service.sidebar.470e9ab5-bd81-4f91-bfa4-c3baddaa0af2":2,
  "workbench.view.extension.ocrmnavigator":2,
  "workbench.views.service.sidebar.3264ea6a-e0b9-4b2c-a0c7-4f09350e8fb0":0,
  "workbench.views.service.auxiliarybar.9e62d474-db52-4122-bf48-3b5b04b89013":0,
  "workbench.view.extension.geminiChat":2,
  "workbench.view.extension.jetbrains-ai":2,
  "workbench.views.service.auxiliarybar.bea28fd6-5262-4d04-8f7c-860259c3157c":2,
  "workbench.views.service.sidebar.bbd2ef2d-f401-4fdb-9052-6d24abe4c360":2
  },
"viewLocations":{
  "workbench.panel.repl.view":"workbench.panel.markers",
  "workbench.scm.repositories":"workbench.views.service.panel.e93f6175-55af-4598-8176-c434529362f5",
  "workbench.scm":"workbench.views.service.sidebar.d705666c-a06a-43ae-b07e-7dd29acdd6ee",
  "snippets-manager-sleek-snippetsView-WorkspaceSnippetsExplorerView":"workbench.view.explorer",
  "snippets-manager-sleek-snippetsView-ExtensionSnippetsExplorerView":"workbench.view.explorer",
  "cevsCore":"workbench.views.service.sidebar.a723bf58-66c7-4a12-85c6-26b9636555ce",
  "to-do-explorer":"workbench.views.service.sidebar.c4b67703-45a0-4b09-bde9-039edc20262d",
  "snippets-manager-sleek-snippetsView-UserSnippetsExplorerView":"workbench.views.service.sidebar.73412756-2c08-4084-bc57-031a78d54dd2",
  "opinionatedCrmNavigator":"workbench.views.service.sidebar.470e9ab5-bd81-4f91-bfa4-c3baddaa0af2",
  "workbench.view.search":"workbench.views.service.sidebar.3264ea6a-e0b9-4b2c-a0c7-4f09350e8fb0",
 } }
```
---

[🡄 Return](https://github.com/8an3/DevStack)





# 
