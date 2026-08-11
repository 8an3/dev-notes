# BIFRÖST

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Terminal and Multi Kernel Ngin

The terminal ngin is where all of the features sends it code to execute in a temrinal enviroment or the triggering of any of the config item types. 

It pulls its weight in so many areas, and even working in ways that were some unforeseen benefits. It not only ensures for a much more effecient coding enviroment as it reuses the same terminal window whenever a command is executed, but it also automatically takes care of the chore of having to take care of dev servers. As the ngin sends a ctrl + c command to the currently open dev server, closes it, then opens a new terminal to run the dev server command. 

This is just one of the many benefits it provides, and honestly it's because of the ngin that this extension is where it's at today due to being such a an asset within the codebase.

This extension started out life as a vscode command short cut creator, where using a file tree in the sidebar to allow the creation of as many commands as I needed at less than an arms length away. 

It is because of how much better and surprisingly more reliable my extension was at providing that solution in comparison to at the time current marketplace offerings that, the next time a extension just really got on my nerves it gave me the confidence to try again. And again, and again... 100+ times later is how we arrive where we are today.

This section is not required by any means, but if you want to get the absolute most out of your config and the items you place within. It will be a benefit in knowing how it works. Because out of all the features in this extension, the config and the sidebar that uses it... is still by far the most power part of this extension. Any part that is required or important, was pulled out of this doc and placed in the same file as the overview of the config items.

With saying that, it takes a while to truly see not just the over amount of use you could get from it but also at just how capable it is. This is due to the fact that your config, builds over time. Slowely, but surely it ends up being this amazing tool... that you probably won't be able to live without ever again. And to prove the point of its perceived value being built over time, look at the layout ngin in comparison. You make one config object, and bam your done. Your ENTIRE vscode experience changes... from the second you save that layout config in your workspace folder. Each and every single time you open vscode, it provides that perceived value over and over and over again. 

I'm not trying to downplay by any means, as it is probably my second favorite feature, but I hope the point comes across to you that while the layout ngin, gives amazing wow factor with zero work. The temrinal ngin and the config, is almost the exact opposite. 

While, its more of a slow burn, there is nothing else on the marketplace that can accomplish and do what it does. From one workspace, I can control... every single project, and its build, commits, pushing, version bumping, all the while there are some apps that require data from others. Making it so among all the commands being executed there is data being flown around to land where it needs to for the apps to update themselves all on their own, the ability to push to npm, github, vercel and all other manner of providers to push to from one workspace... with a single click that does 8 projects simultaneously. 

Never seen a ci/cd do that before, well I haven't. I can't imagine you couldn't do this on some of them, but... it definitely wouldn't be as easy to pull off... I can promise you that. 

There are a couple of features in this extension that... are so ahead of competing offerings that they would be a millennium falcon, where as the others would be a 2004 pt Cruiser. Not trying to boost my own ego, as I'm just trying to bring this point up without underselling it so much that, its true value doesn't even get noticed. I truly do not care who downloads this extension, because I have always built this for my use and my use only.

For example this extensions ability to work on a workspace context basis, while yes 100% there are other extensions that have tried their go at this. None of them come close to the fluid, reliable, cohesive functionality that this one does. To the point that, if I didn't tell you... you wouldn't know. As it doesn't error out, and loads into your vscode instance while combining global and workspace data together as one. Even if you let your kid on your computer who does something stupid, god knows what and the end result is 20-30 features firing off across 8 different workspaces, while your vscode instances will more than likely come to a grinding halt, the use of workspace contexts used for and by this extension in each workspace, will still be 100% working without a single issue. Even if you accidently open and or create 4, 5 or even 10 workspaces in a second. When the dust finally settles and your finally able to use your vscodes instances, it wouldn't even enter my mind to confirm the workspace config in the current instance before going to use any of its items. Each and every workspace will contain an editable config of the global context in addition to the workspace config. Giving you complete control over more app functions and features than vscode ever did. This part of the extension WILL NOT error and crash. I'm not that great of a dev, I just got really lucky.

One of the others is the terminal and multi kernel ngin. There is not a single... other example that comes close. Yes there are extensions that fire off vscode commands, or powershell commands. IF your lucky, you may find one that does powershell and bash. Even if you were to handicap this extension, and have a 1 on 1 comparison whhere it just compared this extensions powershell and bash terminal features against any other, this extensions use of them will still put it in a class all on its own. I won't go over all the resons right here, but [click here](#terminal-list) if you want to go over some of them that I outline later on.

There are several others, that I won't go over again, as the extensions tldr goes over the majority of them as I still have not gone through the extension in its entirety to see if anything else should be added to that list. Which, I am very strict with that list, by not only check each item on that list myself, but also verifying through 2 seperate ai ngins in order to compare features and data points to see if that feature should be on that list or not no matter which column it ends up under. Currently there is one other that is not featured in the tldr, but should be... Honestly... I don't even know what category to put this under, even after inquiring 4 different ai's in trying to find the answer.

This extension is something that people have tried to attempt, but never finished, and I wouldn't blame them. Currently, there is no category that this extension fits under... as one does not exist. The closest parallel is what VSCodium or Cursor did, except they forked the actual source. This extension achieves the same end result, a fundamentally different IDE experience, but entirely within the extension API, which is the constraint that makes it genuinely novel. As it provides an experience difference that you can only get by installing an entirely different software, without all the hassle. With a single click, its added to your vscode application and ready to go. Don't want it anymore, just disable or uninstall the extension. No bloated app installers, or ad infested .exes.

"Workbench Override Extension" — this is the most technically accurate VS Code-specific description, since workbench is literally what VS Code calls its UI shell layer, but a more befitting category title, taking into consideration other naming conventions used through the space, Workbench Distribution. It's precise, it uses VS Code's own vocabulary, and it draws a clear line between what this extension is and a regular extension or a full fork.

Anyways, welcome and I truly hope this extension helps you with your day to day as a dev and allows you to be a lot more efficient at the same time.








### Terminal Ngin

Most extensions spawn a new terminal instance every time you click a button, leading to a "terminal graveyard" by the end of the day. This extension uses a centralized Command Engine class to manage all terminal interactions through a single, intelligent interface.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> The Smart Queue System
When you trigger a command, the engine performs a real-time status check:
- Idle Terminal: If the terminal is open and free, the command executes immediately.
- Busy Terminal: If a process is already running, the engine queues your next command. It will fire automatically as soon as the current task finishes.
- User Flow: This allows you to click multiple menu items in succession and return to your code, knowing the engine will handle the execution sequence in the background.

I have to admit, while even documenting it, I had forgotten to finish it off due to the fact that with the way it's currently built it really worked well with await despite edge cases. So much so I geniunely thought, I had coded it. Earlier today as I was in that part of the code... I was staring at it wondering where the fuck the queue system went lol. 

The terminal ngin now actually features a queue system and it is clearly evident if you go smash a bunch of config items like a kid in an elevator. Previously, when I thought I had done it, we did not have the second concurrent instance that runs along side the powershell instance to allow two concurrent instances running on both windows and linux enviroments.

The linux counterpart now features a mirrored implmentation, so you can run dev servers, regular commands, smash a shit ton of config items all at once and both instances will act the exact same.

Speaking of such, the dev server bug seems to have been completely removed which is nice but on a more depressing note, I just finished coding all the merges that happened... It was only then did I think about, I wonder if I can progmatically trigger a "press enter to continue" screen through the terminal as users go through certain functionality. As i would have defiently have used it in the latest updates in several spots. After that addition, I truly do not know what else this ngin could get updated with at this point.

### Terminal List
1. env variables that get nabbed the second before the comand executes
2. 24 different config item types that get executed through a single end point
3. "enter to continue" sceens that get triggered progmatically
4. a real concurrent system, that can even be nested or also run its counterpart WITHIN the same sequence
5. concurrent system features a single parent instance that delegates all input to the child instances while the parent acts as the viewer by taking all children outputs, coloring them and piping them to one window
6. not to mention, doing the exact same thing with a bash terminal enviroemnt through wsl debian, AT THE SAME TIME
7. each command executed, re-uses the same terminal instance for every single command, instead of just creating a new one whenever the user triggers a command
8. to ensure dev servers are not only forgotten but are also given the ability to do what ever they want whenever they want. For exmaple whenever you trigger a dev server command, the ngin first picks it up from its scans to determine what your executing, it then takes that dev server command and checks it against all currently open terminals. If there is already a dev server running on that same port, it first sends ctrl + c to that instance, closes it, and then opens a new instance to execute the dev server again. MEANWHILE, if there are no other terminals running that dev server command, no matter what state all the instances are in it will open a new terminal for that dev server, in any amount that you trigger. The end result being a beautiful cohesive system, that would otherwise be chaotic and a pain having to manually do everything.
9. BTW, ^ is not only done in just the windows powershell enviroment, but also wsl debian
10. through the use of one of its args
11. chain sequence exection 
12. queue system, thats actually pretty robust... just smashed the same button over 100 times, we'll see how that goes but so far it's hammering one command as soon as the previous finishes
13. terminal ngin is also being used in and alongside other features like the layout ngin, allowing a customized grid or col layout and a workspace context basis, or even whenever you trigger a new layout
14. I know I'm missing some things...
15. Perfect surgical percision when it comes to executing, whatever you want... wherever you want and when that command finishes from executing something on an entirely different drive... your greeted with your terminal being, exactly where it was before you triggered that command. Have to admit this has come in handy with the bifrost merge.
16. Ya I'm missing some for sure, I know I didn't meantion the use of conditional command execution, but thats kinda covered under 24 differrent command types
17. dynamically setting and keeping track of ports it assigns through the use of ${PORT}, so whenever feature V gets assigned port V, every single time you go to restart that service the terminal ngin ensures that the same port is used for that service for the entirety of that vscode instance
18. I knew I was forgetting something and it seems like I have forgotten more than I thought I would as this line should be split up across 5-6, the automatic use of the terminal ngin through the use of the layout config and all the different capabilties and run times it has
19. technically, the extensions workspace context journal, because it is a undocumented config item type

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> The Smart Queue System - Show Queue Status & Skip Current Queue Item

More than once now, it has happened to me where I've queued a bunch of items but I accidently triggered one function I didn't want, instead of interrupting functions already in progress along with everything else you have queued, you can just skip the one item via the devstack menu 'skip terminal cmd'. Once triggered it will send a 'resolved' status to the terminal ngins promise so that it moves on to the next item within your queue and continue working.

In addition to that, there will also be a 'view current queue function' where it querys the queue within the terminel ngin for it to return the currently running command. Thus helping you make sure that it is the command you want to skip. 

> [!NOTE]
> Ahhh... fuck it. I want a media player ui panel that displays all currently active commands sitting in the queue as if it were a playlist where you can pause, stop, play the queue at will. 
> 
> Ontop of that, I want each of the items in the queue to act like... songs in a playlist. Move them up, or down, move to top of queue or bottom of the queue as well as completely removing them via context menu.
>
> ... Why not... As soon as I had finished putting together the skip and view... It just came to mind, I have no idea why though. In all my years of using a computer, I have never once seen any type of terminal have such functionality, whether it be linux, mac os or windows.. How the fuck am I going to pause the commands? lol, meh its a part of the details. Pausing would be nice though, especially in this type of enviroment where half way through a pnpm i or some other kinda resource heavy command, but as your still coding you need the resources for something else... instead of waiting or skipping it to come back to later... just pause the install process. I already know without looking this is not something... that currently exists in another extension... so I can't even cheat off of someone elses homework to learn how to do it...
>
> It will be a sidebar, btw. Split into two, one for powershell and one for debian, ya because I just NEEDED to make it harder for myself.




## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Self-Managing Dev Servers
The engine treats Dev Servers (persistent processes) differently than one-off scripts:
- Port Protection: If you trigger a dev server that is already running in an active terminal, the engine programmatically sends Ctrl+C to kill the old process before spawning the new one on the same port.
- Multi-Server Support: If you trigger a different dev server, the engine recognizes the port conflict isn't present and opens a dedicated terminal for that specific server.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> The "Unified Switch" Architecture
Architecturally, every item type in your config—regardless of complexity—is routed through a single execution function. This unified logic powers the extension’s most advanced features:
- Nested Execution: Because the engine uses a recursive switch, you can nest Chains inside Concurrent items.
- Hybrid Workflows: You can create a "Launch" command that fires three tasks concurrently, while one of those tasks is actually a sequential "Chain" of three other scripts.
- Efficiency: This streamlined code path means less overhead, fewer bugs, and a consistent behavior across all command types.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> The Unified Execution Engine
Historically, every command type had its own isolated function. The new architecture routes every single interaction through a Unified Switch. This is the "brain" of the extension that makes complex nesting possible.

By centralizing execution, the extension handles Chains (sequential) and Concurrent (parallel) tasks using the same core logic. This recursion is what allows for "absurd" configurations, like a concurrent block that triggers multiple independent chains.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Logic Preview (Simplified)
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

### Why this is a "Game Changer"
Because the engine is recursive (executeItem can call itself), the complexity you can achieve is limited only by your imagination.
- Sequential Chains: You can ensure that a "Test" command finishes successfully before the "Deploy" command even starts.
- Parallel Power: You can launch your frontend, backend, and database watcher simultaneously.
- Hybrid Nesting: You can create a Concurrent item where:
  - Task A starts immediately.
  - Task B is a Chain that runs a build script, then a cleanup script.
  - Task C starts a dev server (which the engine will smartly restart if it's already running).

This level of orchestration ensures that no matter how many tasks you trigger, the extension manages the terminal state, the sequence, and the resource overhead without you ever needing to intervene.

### The Power of Nested Logic
If you look closely at the engine's execution flow, you’ll notice a "weird" behavior that is actually its greatest strength: Recursive Nesting.

Because the engine routes every item through the same centralized logic, you can create hybrid configurations that mix sequential and parallel execution in ways standard extensions don't allow.

### A Developer’s Advantage
From a maintenance perspective, this "One Ring" function makes the extension incredibly lean:
- Centralized Logic: Every new item type added to the extension only needs to be defined in one place.
- Code Efficiency: We achieve massive functionality with a fraction of the code, leading to fewer bugs and a significantly smaller extension footprint.
- Infinite Flexibility: This isn't a locked-down UI; it's an execution engine. You aren't limited by how I think you should work, but by how you choose to nest your commands.

Bottom Line: By moving away from "one function per item" and toward a unified execution switch, the extension gains a level of "absurd" power and efficiency that makes it a true CI/CD-grade tool inside your editor.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Resources

- [Visual Guide](https://raw.githubusercontent.com/8an3/midgardr-notes/blob/main/vfs/SequentialExecution+.gif?raw=true)
- [Video Tutorial](https://youtu.be/NtnVq8CNJ7A)

<!-- 

First Ættr (Freyr's Ættr)

- ᚠ (Fehu) - Cattle, wealth, prosperity
- ᚢ (Uruz) - Aurochs, strength, vitality
- ᚦ (Thurisaz) - Thorn, giant, Thor's hammer, force
- ᚨ (Ansuz) - God, Odin, wisdom, communication
- ᚱ (Raidho) - Ride, journey, wheel, movement
- ᚲ (Kenaz) - Torch, knowledge, craft, transformation
- ᚷ (Gebo) - Gift, exchange, partnership
- ᚹ (Wunjo) - Joy, glory, perfection

Second Ættr (Heimdall's Ættr)

- ᚺ (Hagalaz) - Hail, disruption, transformation
- ᚾ (Nauthiz) - Need, necessity, constraint
- ᛁ (Isa) - Ice, stillness, stasis
- ᛃ (Jera) - Year, harvest, cycles, reward
- ᛇ (Eihwaz) - Yew tree, Yggdrasil, endurance
- ᛈ (Perthro) - Dice cup, mystery, fate, secrets
- ᛉ (Algiz) - Elk, protection, defense
- ᛊ (Sowilo) - Sun, success, wholeness, victory

Third Ættr (Tyr's Ættr)

- ᛏ (Tiwaz/Tyr) - Tyr, justice, honor, victory
- ᛒ (Berkano) - Birch, birth, growth, new beginnings
- ᛖ (Ehwaz) - Horse, partnership, movement, trust
- ᛗ (Mannaz) - Man, humanity, mind, memory
- ᛚ (Laguz) - Water, lake, flow, chaos, intuition
- ᛜ (Ingwaz) - Ing/Freyr, fertility, abundance, potential
- ᛞ (Dagaz) - Day, dawn, awakening, breakthrough
- ᛟ (Othala) - Inheritance, homeland, heritage, ancestral property


- Contained within the extension:
  - ᛒ BROKKR - layout ngin The dwarf craftsman who forged Mjölnir and other legendary items
  - ᛒ BIFRÖST - Terminal & Multi-Kernel Ngin
  - ᚨ ODIN - search editor 
  - ᚹ VALHALLA - data storage 
  - ᚱ RÚNAR - snippets
  - no name (Current: File Navigation System) World tree connecting all realms perfect for file/system navigation suggests "connecting everything"
  - ᚹ VÖLUNDR - 
  - ᚺ HUGINN & ᛗ MUNINN - Remix/Prisma utilities
  - ᛏ TYR - Port & Process/Errors
  - ᛜ FREYR - VS Code Styling/Theming
  - ᛊ SKÁLD - Catalyst Editor
  - ᚱ RATATOSKR - File Tree Builder/Visualization tool
  - ᚹ VIÐARR - Automation events
  - 𐌍 NEMESIS - Create Incoming Tunnel
  - 𐌇 HERACLES - Batch Rename
  - ☿ HERMÓÐR - API Secret Grabber
  - ᚺ HEIMDALLR - react preformance fucntions
  - ᚺ HÖFUÐ	- Intellisense Schema Ngin	
  - ᛊ SAGA - to dos notes and reminders
  - ᚷ GINNUNGAGAP - 
  - ᚢ URÐR - Snapshot Engine 
  - ᚹ VEÐRFÖLNIR - VSCInfo 


- App / projects created outside of the project
  - consumer apps
    - ᚹ VALHALLA - Realtor CRM 
    - SLEIPNIR - Automotive Dealer CRM
    - FREYR - Restaurant POS
    - TYR - Store POS
    - FORSETI - Lawyer CRM

  - dev apps
    - a5gard - npm org / A5GARD github org
    - ᛚ LOKI - AI
    - ᛒ BIFRÖST - Template installer/creator
    - ᛒ BIFRÖST-PLUGIN - Plugin installer/creator
    - ᛇ YGGDRASIL - Central CLI hub (connects all tools)
    - ᛗ MIÐGARÐR - formerly know as Catalyst UI & @a5gard/migardr-ui is a npm libarry that will now get cahnged
    - ᚦ THOR - CSS/tailwind
    - ᛒ BALDR - @catalystsoftware/icons
    - ᛗ MÍMIR - DevArchive?
    - ᚨ ODIN - IDE Editor
    - GULLVEIG - Auto Finance Calculator
    - ᛊ SKÁLD - Catalyst Editor & Rich Text Editor
    - ᚱ RÚNAR - Snippets
    - ☿ HERMÓÐR - Messenger 
    - ᛊ SAGA - Appointment Scheduler
    - ᚢ URÐR - Event Calendar
    - GRÍÐR - table, wrapper for tanstacks table

    AVAILABLE NAMES
    - ᚹ VÖLUNDR (Master smith/craftsman (Wayland the Smith)) for cleanup/refactoring/automation tools suggests "craftsmanship/maintenance"
    - ᚺ HUGINN
    - ᛗ MUNINN (Remix/Prisma utilities) Odin's ravens: Thought and Memory for framework utilities
    - ᛏ TYR (Current: Port & Process/Errors) God of law, justice, heroic glory for debugging/error handling suggests "order/resolution"
    - ᛜ FREYR (Current: VS Code Styling/Theming) For theming/beautification tools suggests "abundance/beauty"
    - ᛊ SKÁLD (Current: Catalyst Editor) Norse poets/storytellers for documentation/markdown/editing tools suggests "crafting stories/narratives"
    - ᛗ MÍMIR - DevArchive
    - ᚱ RATATOSKR - File Tree Builder/Visualization tool
    - ᛚ LOKI - AI
    - ᛁ ÍVALDI (The Master Forger) The Sons of Ívaldi were the dwarves who crafted the greatest treasures of the gods (Odin’s spear, Sif’s golden hair, Freyr’s ship). A UI library is essentially a collection of "master-crafted treasures" that other developers use to build their world. The Vibe: Industrial, precise, and foundational. 
    - ᚹ VIÐARR - Automation events
    - 𐌍 NEMESIS - Create Incoming Tunnel
    - 𐌇 HERACLES - Batch Rename
    - ☿ HERMÓÐR - API Secret Grabber
    - ᚺ HEIMDALLR - The Gatekeeper who controls who enters the bridge and when.
    - ᚺ HÖFUÐ	Intellisense Schema Ngin	Heimdallr's sword; represents the sharp, precise "edge" of your code intelligence.
    - ᛊ SAGA - Goddess who sits beside Odin and tells him stories Associated with history and remembering Perfect for notes that tell the "story" of your work Simple, memorable name
    - ᚷ GINNUNGAGAP- The primordial void where all potential exists Perfect: modules exist here before being "born" into projects - Rune: Gebo ᚷ gift/exchange
    - ᚢ URÐR for Snapshot Engine "That which has become" (one of the three Norns) She represents the PAST Norns control fate/destiny - snapshots control your project's fate Rollback = returning to the past Urðr governs
    - ᚹ VEÐRFÖLNIR for VSCInfo - Eagle atop Yggdrasil, sees EVERYTHING  oversight/monitoring from above viewing system continuously

DEV

AVAILABLE NORSE/MYTHOLOGICAL NAMES:
Major Gods/Figures:

SLEIPNIR (Odin's 8-legged horse)
FENRIR (The great wolf)
GERI & FREKI (Odin's wolves)
GUNGNIR (Odin's spear)
DRAUPNIR (Odin's ring)
MJÖLNIR (Thor's hammer)
SIF (Thor's wife, harvest goddess)
IDUNN (Youth goddess, keeper of apples)
BRAGI (Poetry god)
FORSETI (Justice god)
NJORD (Sea god)
ULLR (Archery/skiing god)
HODER (Blind god)
VALI (Avenger)
MAGNI (Thor's son - strength)
MODI (Thor's son - courage)
NANNA (Baldr's wife)
EIR (Healing goddess)
GEFION (Giver goddess)
VAR (Goddess of oaths)
VOR (Goddess of wisdom)
SYN (Guardian goddess)
HLIN (Protection goddess)
SNOTRA (Wisdom goddess)
GERSEMI (Freyja's daughter - precious)
HNOSS (Freyja's daughter - treasure)

Giants/Creatures:

HRUNGNIR (Stone giant)
JÖRMUNGANDR (World serpent)
NIDHOGG (Dragon gnawing roots)
RATATOSK (Already used)
HRAESVELGR (Eagle creating wind)
SKOLL (Wolf chasing sun)
HATI (Wolf chasing moon)
SURTR (Fire giant)
YMIR (Primordial giant)
THRYM (Frost giant king)
THIAZI (Storm giant)
GRENDEL (Monster)
FAFNIR (Dragon)
AUDUMBLA (Primordial cow)

Valkyries:

BRUNHILDE
SIGRUN
SVAFA
KARA
SKULD
GÖNDUL
HILDR
GEIRSKÖGUL
RANDGRID
RADGRID
REGINLEIF

Dwarves:

ANDVARI
BROKK
EITRI
DVALIN
ALFRIGG
BERLING
GRERR
SINDRI
DURIN

Other:

HEL (Death/underworld)
SIGYN (Loki's wife)
MODGUD (Bridge guardian)
HVERGELMIR (Source of rivers)
MUSPELHEIM (Fire realm)
NIFLHEIM (Ice realm)
ALFHEIM (Light elf realm)
SVARTALFHEIM (Dark elf realm)
JOTUNHEIM (Giant realm)
MIDGARD (Human realm)
ASGARD (God realm)
-->

<!-- 
## Complete Archaic Greek Alphabet Reference

- 𐌀 (Alpha) - A
- 𐌁 (Beta) - B
- 𐌂 (Gamma) - G
- 𐌃 (Delta) - D
- 𐌄 (Epsilon) - E
- 𐌅 (Digamma/Wau) - W/V
- 𐌆 (Zeta) - Z
- 𐌇 (Eta) - H/Ē
- 𐌈 (Theta) - Th
- 𐌉 (Iota) - I
- 𐌊 (Kappa) - K
- 𐌋 (Lambda) - L
- 𐌌 (Mu) - M
- 𐌍 (Nu) - N
- 𐌎 (Xi) - X
- 𐌏 (Omicron) - O
- 𐌐 (Pi) - P
- 𐌑 (San/Tsade) - Ts
- 𐌒 (Qoppa) - Q
- 𐌓 (Rho) - R
- 𐌔 (Sigma) - S
- 𐌕 (Tau) - T
- 𐌖 (Upsilon) - U/Y
- 𐌗 (Phi) - Ph
- 𐌘 (Chi) - Ch/Kh
- 𐌙 (Psi) - Ps
- 𐌚 (Omega) - Ō
- -->


