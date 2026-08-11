# Archiving 

## Table of Contents
- [Custom VSIX Archiver](#custom-vsix-archiver)
  - [Why a Custom Archiver?](#why-a-custom-archiver)
  - [Requirements](#requirements)
  - [Key Features & Benefits](#key-features--benefits)
  - [File Structure & Output](#file-structure--output)
  - [Restrictions Comparison](#restrictions-comparison)
- [VSIX Publisher](#vsix-publisher)
- [Pro7](#pro7)
- [VSIX Publishing Commands](#vsix-publishing-commands)
  - [Publish from Existing VSIX](#publish-from-existing-vsix)
  - [Package Commands](#package-commands)

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Custom VSIX Archiver

Alternative VSIX packaging solution as an alternative to vsce.

**Access:** DevStack Quick Pick → Custom VSIX Packager

**Features:**
- Smaller file sizes compared to vsce
- Custom ignore patterns
- Structure visualization
- More resilient build process
 
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

> [!NOTE]
> FUCK you vsce... omg, I understand my most recent bug is probably to be categorized as a 0.01% chance in happening... but fucking still. This is why I try to code things with a little restrictions as possible, because the moment you start adding restrictinos to things that don't REALLY need to be there, shit like this happens. This has been the most rediculously tedious exercise I have ever done. Having to coordinate, 4 different sources in order for the vsix package to come out correctly... like c'mon. Having to configure each in such a way that, packages, modules, files and all manner of others, are either included or not depending on which stage in the archiving process it is in... like what the fuck. Such a stupid experience that was to the point that the custom vsix archiver will be getting an update. Not to make it more restrictive... but actually the opposite to  make it even more open because right now it is going off of .vscodeignore and such... fuck that, I'm never putting myself through that again.
>
> So instead of making you put yoursaelf through that headache inducing activity, there is going to be ONE config file... that's it. You can either white list or black list, your choice. So you can make sure files and or folders are included in with your vsix archive. NOW, this does not include the modifcation of the compilation process. This just effects the archiving process, even before this last bug I've had issues in the past with vsce not including what I explicitly tell it to... I don't even know why it didn't either. BUT, this last bug ended up being so bad and taking so much time, I will never use vsce again once the extension is back up and running, to the point that I will ensure I have an insurance policy to never use it again by creating a standalone node .js file that replicates the process so in case it is down for me... I stil do not have to use vsce, which I'll include... somewhere I don't know where but ya.
>
> The update hasn't happened yet, but as soon as the extenion is good to go I'll add this.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Custom .vsix publisher

**Access:** HEIMDALLR sidebar → HEIMDALLR → publish → authorized || unauthorized → push .vsix via vsce

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Custom .vsix & ovsx publisher

**Access:** HEIMDALLR sidebar → HEIMDALLR → publish → authorized || unauthorized → push .vsix via vsce & ovsx

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Pro7 Archiver

Secure sensitive files in password-protected archives before pushing to GitHub, ensuring safe version control for proprietary code.

**Access:** HEIMDALLR sidebar → HEIMDALLR → archive → pro7 archiver

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> The ".env" Context Swapper (envProfile)

- Manual .env editing is a nightmare because one typo breaks the whole app.
- The Pain: Opening .env, commenting out 10 lines of "Prod" vars, uncommenting 10 lines of "Dev" vars, and repeating this for every microservice.
- The Fix: Create a type that swaps entire sets of variables.
- How it works: 
  - two .env files one labeled `.env` and the other `.hermes` 
  - two values each in the `.hermes` file to differiantiate the two they will be in the following format
    - `LOCAL_enviroment='development'`
    - `REMOTE_enviroment='production'`
    - `LOCAL_DATABASE_URL="postgres://postgres:owner@localhost:5432/server"`
    - `REMOTE_DATABASE_URL="postgresql://owner:server@server/db?sslmode=require"`
    - `LOCAL_SESSION_SECRET='local-secret'`
    - `REMOTE_SESSION_SECRET='remote-session-secret'`
    - `LOCAL_PADDLE_CLIENT_TOKEN="api-token"`
    - `REMOTE_PADDLE_CLIENT_TOKEN="api-token"`
    - `LOCAL_PADDLE_SERVER_TOKEN="api-token"`
    - `REMOTE_PADDLE_SERVER_TOKEN="api-token"`
  - if either value is missing in the `.hermes.` file still invlude it in `.env`but the variable is set to empty ie:
    - `DATABASE_URL=""`
  - in a quickpick tha tis already built i will provide two buttons one `Set Local .env Var's` and `Set Remote .env Var's`
  - no matter what the current state is, it will always grab the the corresponding values of which is triggered and set them in .env so as to never error out





