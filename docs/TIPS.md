# Tip, Tricks and Random

> In other words, things that could be relevant but doesn't really fit anywhere since they aren't actual features of the extension itself.

--- 


> [!TIP] 
> AUTO CLIPBOARD INSERTING: I just mentioned this elsewhere, but I thought I might as well include it here. All through the extension, there are a ton of time saving techniques while the majority are out of your control, in terms of really... ensuring that the process the user has to go through to do something, I make sure its tight. No time wasted. 
> 
> Speaking of which I'm just about to run a timed test against what a typcal user has to do from when they start a project, to the point where all set up is done and you can actually start coding. While I already know, my process is faster so its not a matter of who wins that race. There's just some bets as... how big the multiplier will end up being. One persons is guess is an x factor of 87 while another beleives it will be atleast 75. I tend to work a bit faster so my money is at 50+. The only issue with measuring this is that... when it comes to things like the tailwind.config.ts file... you can spend an hour, or two, or three or even more time on that one file alone before you can even start coding your project. Leaving those outliers out and instead finding an example online that I can use and paste into the project. I haven't done that in a LONG time, so it will be the same experience as say someone who may not entirely know what they are doing in that dept.
>
> ANYWAYS, one of the time saving methods you do have in your control is that wnenever a quick pick is presented to you, 9 times out of 10 it will feature ( typcally the first input, if it isn't the first there is a very good reason for it ) a function that automatically takes whatever it is you have in your clipboard and auto pastes it for you into the input. In every case that I can remember, as long as you have that required piece of information that would usually take a minute or two to type out... that process can be completed in under 5 secs, start to finish. Once you get used to what buttons need to be pressed at their step in the process. In some cases, I've been able to complete them in under a second.

--- 

> [!TIP] 
> The following settings cannot be active while using the layout engine. While it doesn't actually hurt anything the behaviours will be modified by these settings, ie the first setting will automatically close any and all files not yet pinned essentially undoing any file opening events done by the engine.
> - `workbench.editor.enablePreview` - will auto close files
> - `workbench.editor.limit.enabled` - will auto close files

--- 


> [!TIP] 
> Additional Resources
> - [VS Code Settings Reference](https://code.visualstudio.com/docs/getstarted/settings)
> - [VS Code API Documentation](https://code.visualstudio.com/api)
> - [Workspace Configuration](https://code.visualstudio.com/docs/editor/workspaces)

--- 


> [!TIP]
> ADD CURSORS TO END OF LINE
> - shortcut - `Add cursors to line ends`: `ctrl + g`
>   - this was created out of frustration and necessity, this is EXTREMELY useful when editing... honestly, more than one line. With this shortcut, I can within seconds modify json objs or files, 10 of thousands of lines long. I also have some wizardy for when the data you need to modify, is just as much in total lines, BUT because of the format you can't use this trick, I have it somewhere so when I find it I'll be sure to add it. What it does, using regex you search for a sepcfic string that will get your cursor on each line of the 10,000 lines allowing you to move with the arrow keys in order to move to where you need to edit.

--- 


> [!TIP]
> MINIMAP: RELATIVE LINE VALUES
> - `"editor.lineNumbers": "relative",`
>   - Changing line numbers to relative, I didn't even know this could be done, till I was manually checking every single value for the layout engine. I wish I had this sooner. Honestly, static line numbers are so useless in comparison, ie say your creating a select and you have to manually transfer over the data from another list, counting or calculating the math on how many lines there are, to ensure your data pastes over the way you want to... I'm so happy I never have to do that again. But that event, while it only takes a min, or two, or three depending on how fast I'm going and whether or not I make a mistake. Over the course of a year, it adds up to a lot of time wasted. I seriously never used the line numbers as a refrence at all, in comparison to now. Not only getting that same value that I had to calculate before, to taking a second because you just look at the number. It also offers a VERY quick sanity check, ensuring that you are moving the same number of lines from one place to another. Or when ever you have an ai format or do something with more than 200 lines of code, they tend to drop a lot of your code... just because. This serves as a very quick way to catch them when they do.

--- 


> [!TIP]
> MINIMAP: PLACEMENT AND SIZE
> This one, while it was one of the more weirder things I tried, and it took a while to get used. Now that I'm used to, I will never go back to the default configuration
> - "editor.minimap.enabled": true,
> - "editor.minimap.maxColumn": 50,
> - "editor.minimap.showRegionSectionHeaders": true,
> - "editor.minimap.showMarkSectionHeaders": false,
> - "editor.minimap.autohide": "mouseover",
> - "editor.minimap.showSlider": "mouseover",
> - "editor.minimap.side": "left",
> - "editor.minimap.size": "fill",
> - "editor.minimap.renderCharacters": false,
> Yes, chaning the mini map to the left side of the editor and it will take you a WHILE to get used to this, I won't lie. But what you get in return? Whenever your coding in the editor and your mouse is left there as you type, it is more often than not closer to the left side than the right. Making it a lot less of a journey in terms of how far your cursor how to go in order to reach. The second benefit is that, in this configuration the middle of the screen now has two sliders, right beside eachother that control both files. As you can see I decresed the side of my minimap dramatically as the default, just takes up to much realestate and is far too distracting. The above settings leaves you no distractions, and now that I'm thinking about it, now that the config is burned more into muscle memory now, I will be decreasing the size further hopefully to the point where it is almost the width of a scroll bar. Anyways, have two scroll bars where your two editors meet, means you can very quickly navigate both files at once without moving your mouse very far if at all

--- 


> [!TIP]
> SEARCH EDITOR
> - the new search editor, be sure to check that out and use, because it has a killer ux... omg... I pretty much carbon copied vscodes search editor in terms of looks but... each result will disaply ( my config anyways ) 4 of the previous lines and 9 of the lines following the result. With this feature you will be able to click ON THE SEARCH RESULT and remotely edit that file, for when you search something and instead of using find and replace all and you only need to edit that one item. This will save so much time. This pretty much removes the worst part of vscodes search in the explorer pane, coupled with some features vscode does not have.

--- 


> [!TIP]
> MIDDLE MOUSE CLICK -> ENTER
> - shortcut - `middle mouse button / scroll wheel` -> `enter`
> - shortcut - `left click scroll wheel` -> `scroll up`
> - shortcut - `right click scroll wheel` -> `scroll down`
>   - I made this change today, and I fucking love it and I can't beleive I didn't think of this before. But mouse buttons, vscode doesn't let you do anything with them. I noticed a conflict with one command in the project so I was going to start changing the naming convention from `ocrmnavigator.gitadd` -> `ocrmnavigator.git.add`, but doing this over and over and over again using the find and replace. It's a fucking pain because while copy paste is on one side of the keyboard, you need to hit enter as it is just the way you should do that process instead of dragging the mouse over to confirm, but that causes you to flail your arm around for whatever amount of time. Today just thought of it out of no where and tried it, as middle mouse click does nothing really, programming it as `enter` this was the fastest find all and replacing I have ever done. As it was copy, paste, click on replace all, immediately without moving any body part clicking middle mouse click as I start to move it back to the next value I need to copy. After some use, swapping from application to application was a bit of a pain, but I didn't have any profiles set up, and luckily enough the software I have hot swaps through all my profiles automatically based on your focused app. 
>   - The other weird thing I did, and I'll admit I love it so much more then the regular scrolling with the wheel,  the wheel actuator JUST broke on my mouse, but even when I replace it I won't go back to scrolling like that again. programming the left and right movements of the scroll wheel itself, if you have a regular office mouse, you won't be able to do this. If you want to try it, I would highly recommend it, as you are no longer actively hammering the wheel forward or backwards. Now it's just a passive event of click and hold. It is so much better it kinda blows my mind, that I have not seen a single person do that for scrolling in its place



---

> [!TIP] 
> One thing I have been using, more and more. Is chromes, google lens... I think it is called. So whenever the need comes up that, you wish you could just place an dimensions worth of text, instead of having to retype it all out again. It's a pretty good for an ocr. The only issue with it really, is the fact that whatever text you want to place into your clipboard... has text or image or pdf or whatever was it is being delivered, it has to be within the confines of google chrome because of the sandboxed enviroment
>
> Kinda of a pain, but once you get used to that process... it does get quick. Well and depending on how fast you are with shortcuts and what not, it could almost be as quick as if it were in vscode. 
>
> Personally, windows key + shit + s, triggers the snippet tool. If you do not have windows power toys yet, go get it. You will use it so much as a dev, it doesn't even cost money its free from microsoft.
>
> Now this opens your snippet tool, capture the area you would like to get the text from. Save it to your desktop.
>
> Open file explorer, if your like me and have desktop disabled for files, folders and everything else. Open the image in google chrome.
>
> Finally, in the settings drop down meny, trigger google lens.
>
> Now I am aware of the ocr tool that comes with power toys. Yes it is quicker to use, I can't deny that aspect of it since its one shortcut, windows key + shift + t, I find that it doesn't translate the text that well. To the point that, despite my preferred method... taking longer but not by much tbh literally once you get fast at it, maybe a couple of seconds. With power toys, I'm sitting there fixing text for quite a while, 10, 20 maybe even 30 minutes because it doesn't do that great of a job. Where as gooogle lens... Is far better, and it's more of a review of what you got than an editing session.
>
> I have thought about adding this to the extension. The only reason I haven', I don't know enough about it yet and I do have some concerns. Because in order for a feature to be added it cannot in any way have any background processes running, which I have heard those types of program typically do. Maybe it is just the way people write them, probably, I don't know at this point. Once I get there, and have the time to research it... it it conforms to the guidelines and requirements for devstack... 100% it will be added.




