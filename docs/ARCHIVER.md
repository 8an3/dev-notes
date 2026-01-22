## VSIX Archiver

The status quo is to use vsce, but I experienced an edge case in which I could not push my extension, despite there being nothing wrong with it. As I naturally do when something gives me issues, I just rebuild it myself. Not just reminding me how much I have microsfts docs, but I was shocked by the end result.

The custom alternative is not just faster, a lot faster, but it's also a LOT less restrictive. Which makes me question, why is vsce in terms of being strict with its requirements going so well and beyond what is actually required by microsoft in order publish an extension in terms of the actual archive. Because honestly... that is all it is... just an unprotected archive that you can technically... just use 7zip to archive your extension... then change the file extension to .vsce, lol. I change microsofts extensions alll the time in order to get them working without some specialize product. There really isn't much in terms of requirements when it comes to this process.

Requirements for the custom archiver are: 
- readme.md
- changelog.md
- ... it's been a while since I wrote it and only having to write it again due to migrating everthing over to the new docs it seems I lost the previous version... Just pulling the code up to read.
- package.json
  - publish name in the package.json
  - name of extension ie
  - "name": "ocrmnav",
  - "publisher": "skyler",
Last one is not a requirement but you can include a .vscodeignore file in your workspace root that will take the parameters set forth and be sure so as to not archive them with your extension.
IF you use pro7... place *.pro7 in vscode ignore are you will get an email from their security team since pro7 is a password protected archive.

The output is slightly different from vsce with, publisher-projectname.vsce

Personally, I've never went back to vsce not just because it's faster, despite being more thant 4x faster at time even more. But the restrictions is enough to deter me away from vsce. For example, using vsce you cannot have any svg's in your readme. This has no such restriction. You will find a list of other restrictions that vsce has, that this does not so it just depends on how you want to build your readme's and what you would like to use in them, as I have in the past been stuck with just svgs and before this just had to suck it up and not include them.






## VSIX Publisher



## Pro7

# Publish from existing VSIX
vsce publish --packagePath ./my-extension.vsix

# With PAT token inline (if not logged in)
vsce publish --packagePath ./my-extension.vsix --pat YOUR_PAT_TOKEN

# Package only (what you're doing now)
vsce package

# Package AND publish in one go
vsce publish

vsce publish --packagePath path/to/your-extension-1.0.1.vsix