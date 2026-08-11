# HEIMDALLR

Simply put, replaces githubs naming convention with names that hold meaning to them, in addition to, each github command sequence has been replace with a single command, ie: In order to create a project, not only is it 5 or 6 commands long but it even takes 2 seperate clis in order to accomplish, meanwhile 'asgard create-project' not only does the same thing but more.

> [!NOTE]
> I won't lie, I had my reservations about how great and reliable this was going to be. Mainly because, I've already built github into systems, and I knew going into it this time just how much of a temper github could have.
>
> My last implementation... flawless, as it uses github as a source of truth, doesnt even have a local to back up off of in the case it errors out... because it doesn't no matter how you treat it. If we take out the sign in process from our point of view or context, so that we are just left with day to day use. You honestly couldn't even tell it was using github as a database, essentially that's what it's doing. Not a single error in 9 months or so, no failed pushes, NO ERROR OF ANY KIND. Theres no pushing, pulling, checkouts, NOTHING, there is no markings or indicators of github. WHICH IS GREAT, kind of embarressing for githubs dev team though.
>
> This time around, using a completely different implementation. There is not a single piece of code that you could look at and say, that was copied over.
>
> Were about the 2 weekish point of testing, even going so far as completely removing the default github sidebar and all of its functionality, because we don't need it... hopefully. This time, you know its github, kinda, because... it was built with a different idea and goal in mind. 
> 
> Actually, I'll take that back... because it doesn't feel like I'm using github. BUT, taking another path of extremes... its fucking redicously awesome at what it does and in terms of just how much of it too, since the sheer size is mind boggling. Yet... still no errors, meanwhile the entire naming convention was swapped. 
> 
> In addition to, replacing every single process github has... all of them, fucking right in the garbage. The end result of that was no matter the process, it had to be a single click, period. No fucking 5-15 step cli and browser navigations and all the other crap. 
> 
> Meanwhile we are maxing out to the extreme on just how much we can get a way with for each process. SO, for the user... it is an easy surface area to learn, despite it actually being a more complicated tool and offering way more functionality, cutting the time to compentency... DRAMATICALLY. Not to mention, all the time gained back that github wastes.
>
> Both implementations... are used through vscode. Which makes it even more embarrassing, while yes... this is the actual redesign github needs, 100%, and I have no problem admitting to saying that even if it was at a github conference and I was speaking at the front of the room. 
> 
> But its a better ux, that is more reliable, while it accomplishing more tasks... vscodes github implementation was done BY GITHUB devs so it could be offered as a default feature when shipped. EVEN just using their ui... it errors out, lol and all your doing is clicking buttons. Which means you are using the tailored step by step process, designed by github. 
>
> To say that I'm happy with the end result would be an understatement, and if any github devs read this... EVEN THOUGH I already know a redesign would NEVER happen. Maybe if github survives another 100 years and the entire management team is no longer there... MAYBE, then it will change. But hey who knows, send it up the chain internally... hell might actually freeze over, we truly never know.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Overview

This library is for you if one of the following is true:
1. finds github too complicated
2. hates memorizing or having to look up commands whenever you go to use git/github
3. can't remember the exact commands or flags needed to run git commands
4. no longer wants to use git but doesn't want to actually use another platform for whatever reason
5. new to development
6. tired of git/github
7. would like a resource that handles more than just github
8. and the list goes on...

While this resource works with more than just github as I have merged my other libraries in with this one, instead of have 9 resources which is dumb...

This resource is for anyone who has to continue using github but doesn't actually want to use it, or if your new to development. 

If your new to development, I urge you to use this library as it will save you from many headaches and time wasting excercises of dealing with github. It's a great platform and a great idea, they just really missed the mark when it comes to implementation and user experience. This is due to the fact that their naming conventions hold no meaning behind them for new people coming into the industry and the required commands to do anything you need to do... simply put, make no sense unless you either created the platform yourself or were one of the unlucky devs, like me, who had to bash their head against the wall in order to learn the platform.

For experienced devs, simply put, this will not only save you time but also save you from having to continue memorizing everything which will decrease the cognitive load of whenever you have to deal with github, which we use every day.

Either way as you can tell from the toc, the naming convention set forth by github has been replaced with a naming convention that not only makes sense but will actually hold meaning to you whether this is your first day or 10th year.

If this is your 10th year, the following breakdown will provide the conversions on the naming convention:
- project - is your local repo so anything project is referenced its refering to the local representation of your remote repo
- source - refers to remote, as it is the source of your project
- timeline - is your branch, timeline was chosen because whether you are new or not timeline immediatly tells someone that it can be temparay, can be deleted or can become the final project 
- version - replacing tags, this name immediatly conveys a versioning system where as tags... simply does not

To help with chaotic nature that is github and remove the fear of pushing or pulling of any one thing, a system has been put in place to ease and remove these burdens. If your new and have never used github, just skip this part as you do not need to know about this since the fear I'm talking about only plagues people who have used github.

The system that has been put in place is a custom sync sequence that happens before a lot of commands are actually executed, thus removing the pop up prompts like rejected push and other similar prompts telling you that your push or sync has failed. For example, whenever you use upload-project, aka git add *, git commit.. and so on, before running the actual push commands it will first pull/fetch/rebase, merge it with your local, and finally push the local to your repo. This ensures that before any action is taken, whatever branch your currently on, is always up to date so as you will never experience a conflit in refs or heads. If your skeptical about never to experience this again, I don't blame you but to ease this concern in one of my other projects I have an extension that contains a notes and to do app. Simple in nature I know but it uses github as a source of truth, which to be honest I have never seen another dev do before. The notes and to do files are accessible in every single workspace and I can have 4 workspaces open and use the extension in each of them whether or not their are dirty or clean notes in any number of them. This was made 9-10 months ago and not once have I ever had a rejected push. This project will receive the same treatment.

The reason I can ensure this, is because I too will be using this resource and do you think that I... want to deal with this crap day in and day out? No... lol, I do not. But before you ask, yes I'm making this entirely for myself and making public so I can access it everywhere. The only reason for the docs is because... I tend to build larger than normal resources, so large that at times I need to refer to my own documentation in order to remember how to use it, seriously. My vscode extension contains 175+ worth of extensions features and functionality. Currently I have 9 npm libraries, and right before creating this github wrapper I was looking at it and said to myself, "this is stupid, why am I creating so many?" and those libraries will be merged with this one. In addition to that, any other idea or need that comes up will also be added to this library. The only reason why I make the docs so descriptive as I don't need this much information in order to remember how to use it is because even in my last career I always went out of my way to help my colleagues and since I'm already making the documentation I might as well make it right so that anyone else can use it too.

The only libraries I plan on keeping up are the ones that have seen a lot of use considering, I have never told anyone about any of them, otherwise they will be removed once they have been merged



> [!NOTE] 
> Flags are not required and when left out it will prompt for the required information

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> create-project

### With no arguments

```sh
asgard new-project
**```
****
If you use the above command a series of prompts will be provided inquiring:
1. project name
2. which package manager you would like to use
3. license you would like to use
4. confirmation to pre install icons library
5. confirmation to pre install components library

Silently it will:
- create the new project folder
- cd into the project folder
- create readme.md
- create license.md
- create package.json
- create .env and .dev.env
- create .gitignore
- initialize github project
- create github repo
- push project to the new repo
- creates asgard.config with the provided values to be used later**

Proving just how much easier life will become when using this resource, as this now perfectly sets you up to dive into whatever project you were planning on creating.

### With arguments

```sh
asgard new-project project-name
```

replacing project-name with whatever you would like to call your project, doing this skips the prompt process with a set of defaults:
- icons: false
- ui components: false
- license: MIT
- branch: main
- package manger: pnpm

This command will follow the same processs as the previous.

### With config

```sh
asgard new-project
```

You may provide your own config with whatever values you would like by first creating the projects folder and then creating the config file 'config.asgard' and running the above command.

### Fallbacks

If you have never used github before or using it for the first time on this station there are a few command that will ensure that you have the required values in order to run everything and if you don't currently have them it will start off by asking you to provide username/owner, email and github token. This will trigger before running the following commands:

- create-project
- download-file
- download-folder
- download-source


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> delete-project

New: Removes saved temporary work that you previously set aside. Think of it like deleting a bookmark of your work in progress.

Exp: Removes a stash entry

```sh
asgard delete-project
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> load-project

New: Brings back work you temporarily set aside. Imagine you put some papers in a drawer to work on something else - this takes those papers back out and puts them on your desk.

Exp: Restores and removes a stash entry (pop operation)

```sh
asgard load-project
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> save-project

New: Packages up all your current changes, labels them with a note, and sends them to GitHub. It's like saving your video game progress to the cloud.

Exp: Stages all changes, commits with message, and pushes to remote

```sh
asgard save-project
asgard save-project -m "added login page"
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> upload-project

New: Makes sure your local work matches what's on GitHub, then sends your changes up. Prevents conflicts by always checking first.

Exp: Syncs local with remote then pushes

```sh
asgard upload-project
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> upload-project

New: Sends your changes to GitHub and automatically updates your project's version number by one tiny step (like going from 1.0.5 to 1.0.6). Use this for small bug fixes.

Exp: Sync, bump patch version, commit, tag, push with tags

```sh
asgard upload-project+
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> upload-project++

New: Sends your changes to GitHub and updates your version number for a new feature (like going from 1.2.0 to 1.3.0). Use this when you add something new but don't break existing features.

Exp: Sync, bump minor version, commit, tag, push with tags

```sh
asgard upload-project++
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> upload-project+++

New: Sends your changes to GitHub and updates your version number for major changes (like going from 2.0.0 to 3.0.0). Use this when you make big changes that might break things for people using your code.

Exp: Sync, bump major version, commit, tag, push with tags

```sh
asgard upload-project+++
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> delete-source

New: Removes a connection between your local project and a copy stored somewhere online. Like unlinking your phone from a cloud backup.

Exp: Removes a remote reference

```sh
asgard delete-source
asgard delete-source -n 'backup'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> download-source

New: Makes a complete copy of someone's project from GitHub onto your computer. Like downloading a complete folder from Google Drive.

Exp: Clones a repository to local machine

```sh
asgard download-source
asgard download-source owner/repo
asgard download-source -u 'https://github.com/owner/repo'
asgard download-source -o 'owner' -r 'repo' -d 'my-folder'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> set-source

New: Changes where your project sends and receives updates from. Like changing which cloud storage account your files sync with.

Exp: Updates remote URL

```sh
asgard set-source -u 'https://github.com/newowner/repo.git'
asgard set-source -r 'main' -u 'https://github.com/newowner/repo.git'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> sync-source

New: Downloads any new changes from GitHub and uploads your changes. Makes sure everyone is working with the same files.

Exp: Fetch, pull with rebase, auto-commit if needed, push

```sh
asgard sync-source
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> create-timeline

New: Creates a separate workspace where you can experiment without affecting your main work. Like making a copy of your essay to try different edits.

Exp: Creates and checks out new branch after syncing

```sh
asgard create-timeline
asgard create-timeline -n 'dark-mode-feature'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> combine-timelines

New: Takes work from one experimental workspace and merges it into your current workspace. Both workspaces still exist after. Like copying chapters from one document into another.

Exp: Merges another branch into current branch

```sh
asgard combine-timelines
asgard combine-timelines -b 'dark-mode-feature'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> delete-timeline

New: Permanently deletes an experimental workspace. Use this when you're done with it or don't need it anymore.

Exp: Deletes a local branch

```sh
asgard delete-timeline
asgard delete-timeline -b 'old-experiment'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> replace-timeline

New: Combines an experimental workspace into your main workspace, then deletes the experimental one. Use this when your experiment is successful and you want to make it permanent.

Exp: Merges branch into main and deletes source branch

```sh
asgard replace-timeline
asgard replace-timeline -b 'finished-feature'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> switch-timeline

New: Moves you from one workspace to another. Like switching between different tabs in your browser - all your work is still there, you're just looking at a different one.

Exp: Checks out different branch after syncing

```sh
asgard switch-timeline
asgard switch-timeline -b 'dark-mode-feature'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> view-timeline

New: Shows you all the different workspaces you have in your project and which one you're currently in.

Exp: Lists all local branches

```sh
asgard view-timeline
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> restore-version

New: Rewinds your entire project back to how it looked at a specific point in the past. Like using "undo" but for your whole project. WARNING: This erases everything after that point.

Exp: Hard reset to specific commit

```sh
asgard restore-version
asgard restore-version -h 'abc1234'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> delete-version

New: Removes a label you previously put on a specific version of your project. The actual version is still in your history, you're just removing the bookmark.

Exp: Deletes a git tag

```sh
asgard delete-version
asgard delete-version -t 'v1.0.0'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> view-versions

New: Shows all the labeled versions of your project. These are like bookmarks showing important moments in your project's history.

Exp: Lists all git tags

```sh
asgard view-versions
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> download-file

New: Downloads just one specific file from someone's GitHub project instead of the whole thing. Like downloading a single photo from someone's album instead of the entire album.

Exp: Downloads single file from repository

```sh
asgard download-file
asgard download-file owner/repo src/index.js
asgard download-file -u 'https://github.com/owner/repo/blob/main/src/index.js'
asgard download-file -o 'owner' -r 'repo' -p 'src/index.js' -b 'main'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> download-folder

New: Downloads just one folder from someone's GitHub project instead of everything. Like downloading one folder from Dropbox instead of their entire account.

Exp: Downloads specific folder from repository using sparse checkout or raw HTTP

```sh
asgard download-folder
asgard download-folder owner/repo src/components
asgard download-folder -u 'https://github.com/owner/repo/tree/main/src/components'
asgard download-folder -o 'owner' -r 'repo' -p 'src/components' -b 'main'
asgard download-folder --raw -u 'https://github.com/owner/repo/tree/main/src/components'
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> view-timeline

New: Shows you all the different workspaces you have in your project and which one you're currently in.
Exp: Lists all local branches

```sh
asgard view-timeline
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> view-versions

New: Shows all the labeled versions of your project. These are like bookmarks showing important moments in your project's history.
Exp: Lists all git tags

```sh
asgard view-versions
```


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> publish-project

New: Takes your existing project folder and creates a GitHub repo for it, then sends everything up. Like taking a project you've been working on locally and finally backing it up to the cloud.

Exp: Creates GitHub repository for existing local project, initializes git if needed, creates missing files (README, CHANGELOG, LICENSE, config.asgard), and pushes everything

```sh
asgard publish-project
```
 