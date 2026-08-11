### <img src="https://media2.giphy.com/media/QssGEmpkyEOhBCb7e1/giphy.gif?cid=ecf05e47a0n3gi1bfqntqmob8g9aid1oyj2wr3ds3mg700bl&rid=giphy.gif" width="25"  style="vertical-align: middle; margin-bottom: 4px;"> **UPDATES**

To save on time, and due to the crazy amount of updates this extension receives, a more relaxed format will be used in place of the industry norm. 

> [!NOTE]
>
> DAMN, today... was just, in terms of the perfect code flowing from the tips of my fingers, placing it in the editor, today was one of those great days where nothing went wrong, everything worked perfectly the first shot with no errors or any issue you could think of, did not exist in my universe. The amount of work I was able to do, I wish every day was like this. 
>
> But as I'm still going at it I wanted to mark some of it down now before I forget because, there really is just that much code to go over.
>
> THEMES: the fuckers got another update, a couple actually. While the themes looked phenomaal before, I had noticed after creating one for my personal use and starting from scratch, there were a lot more color customizations that I could have added. Adding to what are some great themes, going that extra mile with the more finer details being added. Along with adding more colors to tokens and speaking of tokens... that god damn "base" variants color scheme... I cannot find the default color values listed anywhere and ended up having to go through a color per color basis, with a color picker and manually get each color. Even after that was done, some colors... I just didn't like... still don't to be honest. Like right now I've lost some syntax highlighting in markdown files and this entire section is green... it annoys and bugs the hell out of me, so much so that I will be dropping everything and going back to that, yet again. Like microsft why can't you just provide... just a basic decent, not too descriptive, docuemntation...
>
> MOVING FEATURES: I cannot beleive I was able to get this all done in one day not to mention, everything else and still coding. But most of the status bar quick pick menus have been removed from the status bar. Essentially had to recreate each feature in its ENIRETY, with what started as a very simple idea of, can I move the placement of those features icons into the activity bar, since I literlly have 2-3 icons that currently reside on it. Even though, it was a lot of work in order to accomplish, I am so much happier with those features as I do not like quickpicks. And serving the features in the sidebar allows for it to be open as long as you want/need without getting in the way.
>
> REMOVING ASGARD, RECREATING IT WITHIN DEVSTACK INSTEAD: As I used the npm library more and more it just kept nagging at me with how slow it's performance was. Especially in comparison to when I run similar functionality through vscode. I tried several solutions in trying to gain more performance out of it, but the library is so small there really weren't many oppurtunities to begin with. and after mulling it over, it makes sense to just obsorb it into the extension because currently it is one more thing. And no it is not lost on me when saying something like that when it comes to this extension and the 175+ extensions worth of functions it has, but having that library just adds one more thing externally, so it just made sense from both points of views to re build it within vscode. In so doing, unintentionally, will completely remove the need of including git and its use in vscode while this is available. As it will do the same job faster, easier, and with a lot less headaches, or the potential for headaches.
>
> THEME BUILDER, COLORS NAMES AND COLORS HAVE BEEN UPDATED: The names before now were alll of the place due to building different themes at different times, naming each of them so far apart in terms of time and when I named them. Now each theme looks as if it was created by the same resource because personally when I looked at it, even though I did build them for vscode, it looked as if someone had just went around grabbing themes from here and there, and just sticking to whatever name it originally had lol
>
> THEME BUILDER, NEW MATHMATICAL PROCESS TO CREATE PERFECT THEMES: Oh, one thing I did forget to add, a new tool was added after I finished this so both you and I can benefit from the formulas that were used in this feature. If I remember correctly, all you have to provide are:
> background
> forground
> primary
> and primary foreground
>
> and using math with several formulas it outputs a cohesive picture perfect theme that features a variety of colors. The more colors you add, the more it takes in as if you were building it from scratch so as it doesn't force you to go down any one path or inhibit you in any way, but as a default those 4 values are all you need in order for it to output
> taiwlind v3
> taiwlind v4
> vscode color customization object for settings.json files 
> AND, the complete file in order to create a theme extension and publish it on the marketplace
>
> The way I came up with the formuals and such is, by first taking a perfectly colored and profesionally done theme... that was probably created by someone who has a university degree in some art form. Taking each of the elements and deriving the difference in values between one another... taking those values and using math with the rgb spectrum I was able to calculate for example, just by providing a bakground color it can produce the input color, card color, accent color, secondary color, border colors and so on without fail.
>
> TERMINAL NGINS QUEUE SYSTEM, THAT I THOUGHT WAS ALREADY IN PLACE: Thhis is the third god damn time, where I thought the extension had something only to find out for whatever reason... that it does not in fact fucking have it. The first being batch rename, I remember exactly what happened. Frustrated, I deleted the entire thing so I could start from scratch at the begining of a new day. Forgot to start it right away, but because at the time had an extension, that worked very similarily to how I wanted it to be in the extension, and even the trigger was placed... where I wanted mine to be. I seriously thought that extension was apart of mine and just used it and left the extensions function blank... for months lol. The problem is that, this extension is far too big. Anyways, I seriously thought the terminal ngin had a proper queue system, especially whenever I accidently click on too many items too fast... they all just execute, as if there was a queue system coded in haha. Now it actually has one.
>
> TERMINAL NGIN DEV SERVER BUG FIXED: There was a bug, certain cases when dev servers were already running. Whenever you triggered a new item from devstack, it wouldn't open a new terminal but just send the text through to that dev servers terminal, as if you accidently pasted a string in it. I was using regex before, I fucking hate regex, it so unreliable over time. In it's place, since we know exactly how dev servers will be triggered through the extension via the means of a programmed button, a more explicit check has been coded in. Removing the regex entirely, and just do a straight up string to string comparison with zero sanitization. Every single use case of a dev server, has been added. The only downside to this is, whenever you go to create your dev server config items, they need to be perfect. If this ends up being a challenge for you, thats ok I got you, as there has been for a long time now a extension function that dynamically obtains your currently used package manager, and uses the correct command in relation to the manager you are using. Forgot to note, the ngin powershell enviroment wasn't the only one to get the queue upgrade, but also the linux enviroment as well. Working entirely seperate from eachother, each hosting their own implementation of the queue system.
>
> FINISHED OFF SEVERAL MORE COMPLICATED UI COMPONENTS THAT HAVE BEEN A WIP: While, for the most part a lot of components don't really end up being difficult but one that has been a pain has been input group. Yes it is a simple component, well everyone elses input group is simple. While not only not increasing the amount of props needed to use but also removing a couple in comparison to the average counterpart. All the while offering it with a much more wider use case such as not only inputs but can also use text areas, in all the variants it also comes with from the library. While at the same time:
> - inline start
> - inline end
> - inset start
> - inset end
> - inset start 2 ( so placing another element beside the first which makes the input or text area increase its padding left value, so you could have a button and a text value placed before the cursor in the input )
> - inset end 2
> - inset top left
> - inset top left 2
> - inset top right
> - inset top right 2
> - inset bottom
> - inset top
> - inset bottom left
> - inset bottom left 2
> - inset bottom right
> - inset bottom right 2
>
> Essentially covering, absolutely every single user case... you could imagine. ALL the while, no matter which one you end up going with the input or text area will not just take in one of the placements values in order to provide padding automatically based on each elements placement, but taking in ALL the elements alignments so that it works cohesively no matter where or what you place, whatever it is that you end up placing in it. Covering every single possibility across input AND textareas ( not to mention, allowing the use for not just buttons, but text and custom elements too ) is already a harder task than what the usual library has to put up with when creating this component. BUT, to do so in such a fashion that it doesn't add any new props but taking it further I have even removed multiple props in comparison to the average libraries implementation. In some cases it takes several++ less props then some input groups I've come aacross. Because, if I wanted to create a horrible component, but still have this level of alignemnts, I could very easily add 10-20 props needed in order to use it. Which is what a lot of devs end up doing because they do not see the value of having perfectly crafted ux's when it comes to using... any one thing.
>
> BROKKR MENU:
>
> UPDATED BROKKR VIEWER, NOW WITH MORE FUNCTIONALITY AND PROBABLY REPLACING SNAPSHOT NGIN:
>
> THEME BUILDER, VSCODE INTERFACE ADDED FOR LIVE PREVIEW:
>
> THEME BUILDER, SEMANTIC COLOR CUSTOMIZING WITH LIVE PREVIEW:
>
> THEME BUILDER, NEW INTELLIGENT NGIN CREATING BOTH DARK AND LIGHT THEMES BY MATHMATICALLY DETERMING THE PROPERLY COLOR VALUES IN RELATION TO ONE ANOTHER:
>
> STATE STORE, RECREATING THE LIBRARIES MANAGEMENT LIBRARY ( OR FEATURE WOULD BE MORE APPROPRAITE ) TO BE USED IN NON REACT APPS:
>
> DEVSTACKS CORE CONFIG INITIALIZATION LOGIC:
>
> MERGING BIFROST:
>
> PROGMATIC PAUSE TO WAIT FOR USER INPUT THROUGH THE TERMINAL NGIN
>



> A bug that was just discovered with the terminal ngin where after a random amount of time dev server commands would kill all currently open terminals instead of running the command. This happened randomly as the terminals weren't properly being disposed of. Meanwhile, though dev commands were killing terminals regular commands worked just fine. The bug has since been fixed and should no longer be a problem moving forward.
>
> UPDATE: this fix introduced a new bug where the dev server check was taking in all commands instead of just dev server commands. The logic has since been replaced with much more explicit checks by first determining if the triggered command contains an x path argument that determines which cwd to execute the command in, then checks if the triggered command is a dev server commmand, if none of those parameters are met, it just executes the command like it normally would. 
>
> Current to do list:
> - [ ] Atlas v2
> - [ ] concurrent v2 - 
> - [ ] resource, hardware and process montiors and information
> - [ ] snapshot ngin
> - [ ] auto port ngin
> - [ ] changelog ngin
> - [ ] faker ngin
> - [ ] artifact cache mgr
> - [ ] remote resource mgmnt
> - [ ] dev archive
> - [ ] schema visualizer
> - [ ] github tag navigator
> - [x] application layer data store - will be housed in the ui library ( currently in testing )
> - [x] bifrost ( currently in testing ) - think of remix stacks but platform agnostic. Which not only will there be opinionated platforms to install and use, "plugins" that are used in order to make each implementation opinionated, these too will also be shareable and used within other "stacks". For example, say you install a "stack" that has a couple of features but still needs a couple of others to get it where you need it to be for your use case. Shared plugins that will comprise of file scaffolding, required libraries, configs and more can be added to a stack in order to get the most out of it.
> - [x] rate limiter
> - [x] batching
> - [x] queue
> - [x] throttle
> - [x] github wrapper ( currently in testing ) the idea behind this is that it will only take one command to do any one thing, inplace of the 3-5 it currently takes to do anything while at the same time replacing github naming conventions that hold zero meaning, with names that even if a person first starting to code, would understand. Also having certain commands do more, for example create-project not only sets up your local repo but also creates a number of other files depending where your project currently sits when executing the command among other things
>
> Recently added but were never listed above:
> - product icons - icons search found in devstack menu now has all the available product icons
> - file icons
> - themes
>
> Midgardr to do list: 
> - [x] table 
> - [ ] event calendar
> - [ ] messenger
> - [ ] appointment scheduler
> - [ ] category X - while a lot of components have already been built, there are still a few that need to be created and or tested. This category holds a lot of promise with it being a new way to create react components by offering DOM variantions in addition to CSS variants
> - [ ] rich text editor - this will not be a wrapper but a scratch build rich text editor
> - [ ] editor  
> - [ ] prompt compiler 
>