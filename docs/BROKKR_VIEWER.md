# BROKKR
## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> BROKKR Viewer

> [!IMPORTANT]
>
> Brokkr ngin now tracks ALL UI states that are changed while using the ngin.
>
> If you would like a reliable user experience of changing layouts, use the newly created customize layout feature that you can find in the viewer in place of vscodes customize layout. It works and looks EXACTLY the same as vscodes implementation, the only difference being is that each change commited to the UI is tracked and will be used with customizing ui elements. This is due to the fact that some ui elements and their current state, cannot be accessed progmatically by extension authors.

> [!NOTE]
>
> The config viewer / editor has turned out far better than I thought it would.
>
> It was created as a means to quickly edit items within your config. At first only taking care of few things, but now other than actual custom settings values, it now takes care of everything. 
>
> For example, with the UI library and this vscode extension, my focus changes a lot from file to file. Especially in the vscode extesion, it a tad annoying since the "dev server" equivlant for testing the changes you made to the extensions code... is horribly unreliable at this extension size. To the point now, whenever a change is made and I need to review it in order to make final changes. Instead of using the server through f5, I'm doing a complete re-compiling of the extensions code, archiving it, installing and then restarting then entire instance. There will be times that I'll do this once every min and a half to 2 mins. 
>
> Thus depsite the layout engine... making life so much easier. It was the lil edits to it that I needed but because everything is changing so fast, they have to be quick. With these requirements, deleteing files in your editor groups, virtually instant with very little steps in the process to complete. Currently I can't think of a faster process or one that contains less steps to complete to add files to any one of your editor groups. 
>
> As your working in the file, to quickly add it, copy the relative path so that it is in your clipboard. Click add file, and it will take your clipboard contents and place it into the input for you. For editor group one its just 2 enter button presses and your done. Once you get quick at it, it is less than 1 or 2 seconds.
>
> That speed wouldn't be possible with a regular file picker.
>
> But that one piece of information, is really the only "hidden" thing about this, and because if you have the need to use this, then you alrady know everything you need to in order to use this. 
>
> The only thing I can MAYBE add to these docs is, if you haven't figured this out yet because you were afraid to click on things. Clicking on an item within the menu opens a quick pick asking if you would like to delete that item from the config. And again to add anything, just click on one of the add options. It's designed like all other others that have similar functionality, and now that you know about the auto clipboard insert... this is used EVERYWHERE. From snippets, to adding a config items. Anytime I can get away with or when it makes sense to add it, its added 100% of the time. 
>
> And because this tool is so much easier to use this time around, I guess that concludes the docs.