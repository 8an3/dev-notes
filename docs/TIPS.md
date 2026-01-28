# Tip, Tricks and Random

> In other words, things that could be relevant but doesn't really fit anywhere since they aren't actual features of the extension itself.


> [!TIP] 
> The following settings cannot be active while using the layout engine. While it doesn't actually hurt anything the behaviours will be modified by these settings, ie the first setting will automatically close any and all files not yet pinned essentially undoing any file opening events done by the engine.
> - `workbench.editor.enablePreview` - will auto close files
> - `workbench.editor.limit.enabled` - will auto close files


> [!TIP] 
> Additional Resources
> - [VS Code Settings Reference](https://code.visualstudio.com/docs/getstarted/settings)
> - [VS Code API Documentation](https://code.visualstudio.com/api)
> - [Workspace Configuration](https://code.visualstudio.com/docs/editor/workspaces)

> [!TIP]
> Due to the nature of this feature, coupled with the fact it gets pretty deep in how far it goes and pretty nerdy. If you reading this now, whether you like it or not, your obviously more of a power user than the average. These will just be random bits of information that I use to help in all manner of things, and will be given in no real order. Whenever they come to mind, I'll come back and continue to add them as there is a lot of them, I can never just sit there and remember them all.
>
> - shortcut - `Add cursors to line ends`: `ctrl + g`
>   - this was created out of frustration and necessity, this is EXTREMELY useful when editing... honestly, more than one line. With this shortcut, I can within seconds modify json objs or files, 10 of thousands of lines long. I also have some wizardy for when the data you need to modify, is just as much in total lines, BUT because of the format you can't use this trick, I have it somewhere so when I find it I'll be sure to add it. What it does, using regex you search for a sepcfic string that will get your cursor on each line of the 10,000 lines allowing you to move with the arrow keys in order to move to where you need to edit.
> 
> - `"editor.lineNumbers": "relative",`
>   - Changing line numbers to relative, I didn't even know this could be done, till I was manually checking every single value for the layout engine. I wish I had this sooner. Honestly, static line numbers are so useless in comparison, ie say your creating a select and you have to manually transfer over the data from another list, counting or calculating the math on how many lines there are, to ensure your data pastes over the way you want to... I'm so happy I never have to do that again. But that event, while it only takes a min, or two, or three depending on how fast I'm going and whether or not I make a mistake. Over the course of a year, it adds up to a lot of time wasted. I seriously never used the line numbers as a refrence at all, in comparison to now. Not only getting that same value that I had to calculate before, to taking a second because you just look at the number. It also offers a VERY quick sanity check, in so many differnt forms. Copying over dating? Check the number when you copy it, when you paste make sure its the same number, you have an ai prompt droning away making lists for you, before now I had to manually check every fucking line, but now... when I grab the data, make a mental note on total lines, once I get the ai's result, paste it in to the file, even today it happened over a dozen times, I HAD to go back and be tell the ai "listen here fucker stop deleting line items", and then the next prompt had the correct amount of lines. The amount of times, because I did not catch it right away, to THEN have to back and check line by line to see what I'm missing, you get the point.
> 
> - the new search editor, be sure to check that tout and use, because it has a killer ux... omg... I pretty much carbon copied vscodes search editor in terms of looks but... each result will disaply ( my config anyways ) 4 of the previous lines and 9 of the lines following the result. With this feature you will be able to click ON THE SEARCH RESULT and remotely edit that file, for when you search something and instead of using find and replace all and you only need to edit that one item. This will save so much time. This pretty much removes the worst part of vscodes search in the explorer pane, coupled with some features vscode does not have.
> 
> - shortcut - `middle mouse button / scroll wheel` -> `enter`
> - shortcut - `left click scroll wheel` -> `scroll up`
> - shortcut - `right click scroll wheel` -> `scroll down`
>   - I made this change today, and I fucking love it and I can't beleive I didn't think of this before. But mouse buttons, vscode doesn't let you do anything with them. I noticed a conflict with one command in the project so I was going to start changing the naming convention from `ocrmnavigator.gitadd` -> `ocrmnavigator.git.add`, but doing this over and over and over again using the find and replace. It's a fucking pain because while copy paste is on one side of the keyboard, you need to hit enter as it is just the way you should do that process instead of dragging the mouse over to confirm, but that causes you to flail your arm around for whatever amount of time. Today just thought of it out of no where and tried it, as middle mouse click does nothing really, programming it as `enter` this was the fastest find all and replacing I have ever done. As it was copy, paste, click on replace all, immediately without moving any body part clicking middle mouse click as I start to move it back to the next value I need to copy. After some use, swapping from application to application was a bit of a pain, but I didn't have any profiles set up, and luckily enough the software I have hot swaps through all my profiles automatically based on your focused app. 
>   - The other weird thing I did, and I'll admit I love it so much more then the regular scrolling with the wheel,  the wheel actuator JUST broke on my mouse, but even when I replace it I won't go back to scrolling like that again. programming the left and right movements of the scroll wheel itself, if you have a regular office mouse, you won't be able to do this. If you want to try it, I would highly recommend it, as you are no longer actively hammering the wheel forward or backwards. Now it's just a passive event of click and hold. It is so much better it kinda blows my mind, that I have not seen a single person do that for scrolling in its place
> 