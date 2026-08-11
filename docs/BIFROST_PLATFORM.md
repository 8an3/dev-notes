

# BIFRÖST

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  BIFRÖST: Platform Asgnostic Installer - Projects

> [!NOTE]
> Before this update, this feature was already farther ahead and better at what it does than any other like it. With this update though, this really takes the entire platform eco-system and brings it all together. Now at 92+ different platforms taking this feature into the realm of redicoulosness in terms of what else is in this space as it is already hard enough to find a tool akin to this, but even when you do they typically focus on one area and thats it. Meanwhile, again not abiding by industry norms and flipping off conformity, this shows what can be done as far as providing a lot better user experience, despite there being 57 different apps that this can now create.
> 
> If I were to read this, and knowing what else is out there... I don't think I would beleive it. Which makes this yet another feature that seems to good to be true. Inactuality, this was honestly not that bad of an addition because of how it was originally coded since I'm adding this while I'm dealing with diagnosing a bug else where in the extension that is just taking a long time to get to the bottom of.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Create Wizard 


Clicking any one option starts the process to create your new app with the desired platform. You can either complete the step by step wizard or install via a pre-confgured config. 

![Z](https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/projects.jpg)


No matter how you enter the creating process, it will be split up into two seperate parts.
1. the first being the prompting process where it will present a series of prompts for you to answer in order to configure the application.
2. the build/install part will trigger a entirely different seperate function. Meaning that, if something happens during this stage of the process, you will be completly fine since the first step has already concluded and your new config file is already written so that if you cancel this step, or your computer freezes or crahes or you have a power outage. You can just start the install via config wizard and off to the races you go.

The wizard will prompt you on the following ( but will vary based on platform ):

 

### 1. `projectDir`
**Purpose:** Resolve or prompt the user for the root directory where the new project will be created.

- If `npd` is passed, it is used directly.
- Otherwise, the user is prompted to select or enter a directory path.
- **Exits early** if no path is provided.

---

### 2. `projectName`
**Purpose:** Prompt the user to enter a valid project name.

- The name is validated (e.g. no illegal characters, not empty).
- **Exits early** if the name is invalid or dismissed.

---

### 3. `projectDesc`
**Purpose:** Prompt the user to enter an optional project description.

- Maps to the `description` field in `config.asgard`.
- No early exit — description is optional.

---

### 4. `projectPlatform`
**Purpose:** Prompt the user to select a platform and template.

**Returns:** `{ selectedPlatform, template }`

Supported platforms include:
#### Platforms


- React Router
- Vue
- Nuxt
- Vite + React
- Next.js
- Svelte Kit
- Astro
- Solid Start
- Qwik
- CRA - Create React App
- Analog.js
- TanStack Start
- Gatsby
- Gridsome
- VSCode Extension
- Monorepos
    - tcreate-turbo
    - tNx Workspace
    - tpnpm workspace
- Browser Extensions
    - tChrome Extension
    - tFirefox Extension
    - tPlasmo
- Desktop
    - tTauri
    - tElectron
    - tNeutralinojs
    - tWails
- Mobile
    - tCapacitor
    - tExpo / React Native
- Backend / API
    - tHono
    - tFastify
    - tElysiaJS
    - ttRPC Standalone
    - tNestJS
    - tAdonisJS
    - tNitro
- Cloud / Serverless
    - tloudflare Workers
    - tAWS CDK App
    - tSST
- CLI Tools
    - tOclif
    - tCliffy
- Library / Package
    - tsup Library
    - Vite Library Mode
- Developer Tools
    - Raycast Extension
    - Obsidian Plugin
    - Figma Plugin
    - Grafana Plugin
    - Neovim Plugin
    - JetBrains Plugin
- Shopify
    - Shopify App
    - Shopify App (Remix)
    - Shopify Theme
    - Shopify Functions
- WordPress
    - WordPress Plugin
    - WordPress Theme
- Remix-Run
    - cloudflare
    - cloudflare-workers
    - express
    - remix
    - remix-javascript
    - spa
    - cloudflare-pages - Classic Compiler
    - cloudflare-workers - Classic Compiler
    - deno - Classic Compiler
    - express - Classic Compiler
    - fly - Classic Compiler
    - remix - Classic Compiler
    - remix-javascript - Classic Compiler
- react-router
    - default
    - default-ts
    - basic
    - basic-ts
    - cloudflare-d1
    - cloudflare-pages
    - express
    - node

- **Exits early** if either `selectedPlatform` or `template` is not selected.

---

### 5. `projectPkgMgr`
**Purpose:** Prompt the user to select a package manager.

Options typically include: `npm`, `yarn`, `pnpm`, `bun`

- Maps to the `packageManager` field.
- **Exits early** if dismissed.

---

### 6. `projectRepo`
**Purpose:** Prompt the user to enter a repository name.

- Maps to the `repo` field.
- **Exits early** if dismissed.

---

### 7. `projectOwner`
**Purpose:** Prompt the user to enter the repository owner (GitHub username or org).

- Maps to the `owner` field.
- **Exits early** if dismissed.

---

### 8. `projectBranch`
**Purpose:** Prompt the user to specify the default Git branch name.

- Maps to the `branch` field (e.g. `main`, `master`).
- **Exits early** if dismissed.

---

### 9. `projectPrivate`
**Purpose:** Prompt the user to choose whether the repository should be private.

- Returns `"true"` or `"false"` as a string.
- Maps to `private: boolean` in config.
- **Exits early** if dismissed.

---

### 10. `projectLicense`
**Purpose:** Prompt the user to select a license for the project.

- Maps to the `license` field.
- No early exit — optional.

---

### 11. `projectReadme`
**Purpose:** Prompt the user to select a README template.

- Maps to `readmeTemplate`. Defaults to `"none"` if not selected.
- No early exit — optional.

---

### 12. `projecChangelog`
**Purpose:** Prompt the user to select a CHANGELOG template.

- Maps to the `changelogTemplate` field.
- No early exit — optional.

---

### 13. `projectAutoPushRepo`
**Purpose:** Ask the user whether to automatically push to the remote repository after initialization.

- Returns `"true"` or `"false"` as a string.
- Maps to `autoPushRepo: boolean`.
- No early exit — optional.

---

### 14. `projectBaldr`
**Purpose:** Ask the user whether to enable Baldr integration.

- Returns `"true"` or `"false"` as a string.
- Maps to `baldr: boolean`.
- No early exit.

---

### 15. `projectMidgardr`
**Purpose:** Ask the user whether to enable Midgardr and which level/mode to install.

|  Value | Effect on Config |
|---|---|
| `"none"` | `hashImports: false`, `presetNgin: "none"` |
| `"full-w-ngin"` | `presetNgin: "ngin"` |
| `"full-install"` | `presetNgin: "basic"` |
| `"select-components"` | `presetNgin: "basic"` |
| `"configure-tailwind-postcss"` | `presetNgin: "basic"` |
| `"comps-and-libs"` | `presetNgin: "basic"` |

- Maps to `midgardr: boolean`, `midgardrLevel`, `hashImports`, and `presetNgin`.
- No early exit.

---

### 16. `projectPostCss`
**Purpose:** Ask the user whether to include PostCSS configuration.

- Returns `"true"` or `"false"`.
- Maps to `postcss: boolean`.
- No early exit.

---

### 17. `projectTailwind`
**Purpose:** Ask the user whether to include Tailwind CSS.

- Returns `"true"` or `"false"`.
- Maps to `tailwind: boolean`.
- No early exit.

---
### 18. `projectPresetNgin`
**Purpose:** Ask the user to select a preset engine configuration.

- Maps to `presetNgin`. Can be `"ngin"`, `"basic"`, or `"none"`.
- This value is also derived from `whichMidgardr` — the higher-priority value wins via the ternary resolution in config assembly.
- No early exit.

---

### 19. `projectInstallPostInit`
**Purpose:** Ask the user whether to run install automatically after project initialization.

- **Only prompted when `createConfig === false`.**
- When `createConfig === true`, this is hardcoded to `"false"` and the prompt is skipped.
- Returns `"true"` or `"false"`.
- Maps to `installPostInit: boolean`.

---

### Platform-Specific Prompts (Conditional)

Triggered only when the selected platform matches. Each returns a `platformConfig` object merged into the config, based on the selected platform.

 
---

### Post-Prompt Derived Fields

These are not user-prompted — they are resolved automatically after all prompts complete.

| Field | Source |
|---|---|
| `tags` | Derived via `detectTagsFromStack(template)` |
| `version` | Read from `package.json` if it exists, otherwise `"0.0.1"` |
| `sourceDirectory` | `"src"` for frontend platforms, `"app"` for all others |
| `theme` | Hardcoded `"blue"` |
| `preset` | Hardcoded `"MODERN"` |
| `font` | Hardcoded `"Geist"` |
| `mode` | Hardcoded `"dark"` |
| `hashImports` | `false` if `whichMidgardr === "none"`, otherwise `true` |
| `ensureBaseGitignore` | Always `true` |
| `updatedAt` | `new Date().toISOString()` at time of creation |

---

### Output

On completion, the config is written to:

```
{projectPath}/config.asgard
```

As a formatted JSON file. If `createConfig === true`, execution stops here. Otherwise, `installViaConfig(projectPath)` is invoked to proceed with installation.


I ALMOST forgot about this, the only reason deployment is NOT among the items you see to get automated in this process is because while, yes there are a ton of options out there. IMO, there is really only one worth using due to its UX/DX, which is vercel. They already have automatic deployment available, you just have to... "assign" it, is the best word I can use that describes their process. Because there is no configuring with them which is great. Simply you log in, click create deployment, click on the repo you would like to deploy and click start or finish or whatever it is. That is it. Everytime you push your repo from here on out, it updates your deployment.

THE ONLY reason its not programed into this process is becase you have to pay for the account in order to access their api. You want me to collect all the users, funnel them to you... and pay to do that? C'mon... Theres a reason 99% of the platforms, DON'T do that. Honestly, that is my only grip with them. Due to my experience with them, along with all the others I have tried, I will never use another provider as long as they are in business, at this point in time.

One note on the configuring part, I dont know if its still like this as I have not checked on this for a while. Vercels turbo repo auto deployment does take some configuration when I used it, but they may have changed by now. 


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  BIFRÖST: Platform Asgnostic Installer - Platforms

You can skip a couple of steps by selecting one of the options that was listed above from the platforms section

![Z](https://raw.githubusercontent.com/8an3/midgardr-notes/main/ui/platforms.jpg)

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  BIFRÖST: Platform Installer - MONOREPO

> [!NOTE]
> Haha, omg... funny story, I know there is a place somewhere in the docs where I had said the first app I had made was a vscode command short cut extension. The first UNSUCCESSFUL attempt was actually trying to recreate turbo repo. 
>
> Theyre docs, garaunteed have changed since, weren't the best back then. At the time, it wasn't properly documented on how to completly set up a turborepo app with deploying to vercel, which both are built by vercel. When I finally had figured out how to do that all on my own, it was became apparent very quickly that what turbo repo actually did, and what I wanted... were 2 totally different things. 
> 
> At the time I was working on a large app, so large that remix-run... was so slow at creating dev servers it became a huge pain. SO, what did I want? I wanted to take a monorepo configured application where the crm I was building, instead of having one monolithic application to work on all the time, I wanted to split it up. Sales would be one section, administration another, bdc another, service center, and on and on. Each app being their own remix run application for not only quicker dev times, but it makes it a lot easier to work with smaller chunks rather than one huge app among other reasons. The components like the crms navbar and sidebars and such would be "packages" that would be shared among the different apps. 
> 
> Turbo repo... does not do this. What it does, is create a entirely new deployemnt for each app within the mono repo as if the mono repo never existed, for good reason which you will see why in a second.
> 
> If you have ever worked with remix-run before, your reading that saying to yourself... "good fucking luck with that pal!" lol, I would also say that if I knew what I knew today. I wouldn't have even attempted that, if I knew what I knew today.
>
> Remix-runs build process, is... difficult on a good day, we'll leave it at that. There is not a single mention, on the internet where this has ever been done before, the task of taking 2 or more completely seperate remix wep apps, have the build process build them as if they were one single application. With the end result being the sales, service, parts, administartion, etc depts would be available at a single url.
> 
> This took me a while, and I ended up finishing the vscode command extension before I finished this. BUT... I did get it to work, and actually a lot of the things I wanted out of that very first library.. went into devstack. Now this feature, is not currently in bifrost... yet. 
>
> I say yet because, that crm is done and built. It can be shipped, and it is actaully the best crm on the market by about 10-12 years IF, and thats a huge if, competing offerings would take notice of it right away. Have all the meetings that are necessary to then put it on their devs schedule. Because it would take an entire scratch build, from everyone in the industry, in order to match what I've done. 
>
> My skill since completing that app... has massively increased. So much so, as much as it will fucking suck... I'm going to rebuild it. I already have new protocols written for it and everything. Which means... I want this feature I made a reality about a year ago... to come back from the dead.
>


Monorepo support in Bifröst is configured manually via `config.asgard`. There is no prompt-driven flow for this feature — the monorepo is defined entirely upfront in the config before installation begins.

---

### How It Works

When `installViaConfig` detects a `monorepo` array in your `config.asgard`, it carries out the following in sequence:

1. Creates the monorepo root with a `package.json`, workspaces file, `.env`, and all base files required to bootstrap the monorepo.
2. Loops through each workspace, creates its directory, then iterates through each app defined within it.
3. For each app, runs the **exact same build process** Bifröst runs for any standalone project — full install, config resolution, platform setup, and all.
4. On completion, outputs a JSON file containing the full command set for your Devstack config.

---

### Config Structure

The `monorepo` field is an array where each entry is a fully-specified project config — identical in shape to the root-level config. Each entry represents one application within the monorepo.

```jsonc
{
  "name": "my-monorepo",
  "platform": "pnpmworkspace",
  // ... root config fields ...

  "monorepo": [
    {
      "name": "sales",
      "description": "Sales department app",
      "platform": "vite-react",
      "template": "...",
      "tags": [],
      "postInstall": [],
      "plugins": [],
      "platformConfig": {},
      "repo": "my-monorepo",
      "owner": "your-github-username",
      "branch": "main",
      "private": true,
      "version": "0.0.1",
      "packageManager": "pnpm",
      "baldr": false,
      "midgardr": false,
      "midgardrLevel": "none",
      "postcss": false,
      "tailwind": true,
      "theme": "blue",
      "preset": "MODERN",
      "font": "Geist",
      "mode": "dark",
      "presetNgin": "none",
      "license": "MIT",
      "readmeTemplate": "none",
      "changelogTemplate": "none",
      "hashImports": false,
      "path": "/path/to/monorepo/apps/sales",
      "sourceDirectory": "src",
      "autoPushRepo": false,
      "installPostInit": false,
      "ensureBaseGitignore": true,
      "updatedAt": "2025-01-01T00:00:00.000Z"
    },
    {
      "name": "admin",
      "description": "Administration department app",
      "platform": "vite-react",
      "template": "...",
      "tags": [],
      "postInstall": [],
      "plugins": [],
      "platformConfig": {},
      "repo": "my-monorepo",
      "owner": "your-github-username",
      "branch": "main",
      "private": true,
      "version": "0.0.1",
      "packageManager": "pnpm",
      "baldr": false,
      "midgardr": false,
      "midgardrLevel": "none",
      "postcss": false,
      "tailwind": true,
      "theme": "blue",
      "preset": "MODERN",
      "font": "Geist",
      "mode": "dark",
      "presetNgin": "none",
      "license": "MIT",
      "readmeTemplate": "none",
      "changelogTemplate": "none",
      "hashImports": false,
      "path": "/path/to/monorepo/apps/admin",
      "sourceDirectory": "src",
      "autoPushRepo": false,
      "installPostInit": false,
      "ensureBaseGitignore": true,
      "updatedAt": "2025-01-01T00:00:00.000Z"
    }
  ]
}
```

Each entry in the `monorepo` array supports the full config schema — every field available to a standalone project is available per-app in the monorepo.

---

### Config Fields Reference

Every entry in the `monorepo` array shares the same schema as the root config. For full field definitions see the [config.asgard field reference](./CONFIG.md).

| Field | Type | Description |
|---|---|---|
| `name` | `string` | App name |
| `description` | `string` | App description |
| `platform` | `string` | Platform key (e.g. `vite-react`, `nestjs`) |
| `template` | `string` | Template identifier for the selected platform |
| `tags` | `string[]` | Auto-detected tags from the stack |
| `postInstall` | `array` | Commands to run after install |
| `plugins` | `array` | Plugins to apply during install |
| `platformConfig` | `object` | Platform-specific configuration |
| `repo` | `string` | Repository name |
| `owner` | `string` | GitHub username or organization |
| `branch` | `string` | Default Git branch |
| `private` | `boolean` | Whether the repo is private |
| `version` | `string` | Starting version, defaults to `0.0.1` |
| `packageManager` | `string` | `npm` \| `yarn` \| `pnpm` \| `bun` |
| `baldr` | `boolean` | Enable Baldr integration |
| `midgardr` | `boolean` | Enable Midgardr integration |
| `midgardrLevel` | `string` | Midgardr install level |
| `postcss` | `boolean` | Include PostCSS |
| `tailwind` | `boolean` | Include Tailwind CSS |
| `theme` | `string` | UI theme |
| `preset` | `string` | Preset mode |
| `font` | `string` | Default font |
| `mode` | `string` | `dark` \| `light` |
| `presetNgin` | `string` | `"ngin"` \| `"basic"` \| `"none"` |
| `license` | `string` | License identifier |
| `readmeTemplate` | `string` | README template or `"none"` |
| `changelogTemplate` | `string` | CHANGELOG template |
| `hashImports` | `boolean` | Derived from `midgardrLevel` |
| `path` | `string` | Absolute path to this app within the monorepo |
| `sourceDirectory` | `string` | `"src"` for frontend platforms, `"app"` for all others |
| `autoPushRepo` | `boolean` | Auto-push to remote on init |
| `installPostInit` | `boolean` | Run install automatically after init |
| `ensureBaseGitignore` | `boolean` | Always `true` |
| `updatedAt` | `string` | ISO timestamp |

---

### Generated Devstack Commands

After the full monorepo build completes, Bifröst outputs a JSON file containing a Devstack-ready command set for every app. Each app receives the following commands in both a scoped (`app`) and global (`all`) variant:

- `dev` — start the dev server
- `build` — run the build
- `install` — install dependencies
- `clean` — remove `node_modules`, `dist`, `public/build`, lock files
- `run-build` — clean + install + build chained
- `prisma:reset` — reset the Prisma database
- `prisma:studio` — open Prisma Studio
- `github:sync` — sync with the remote repository

The `all` variants are designed so that regardless of your current working directory within the monorepo, every command executes correctly and the terminal returns to the path it was invoked from on completion.

> **Note:** The generated JSON is not automatically merged into your Devstack config. Copy the relevant commands from the output file into your config manually. This is intentional — the volume of commands generated for larger monorepos makes automatic injection impractical without review first.



> [!NOTE]
> That's what it does now... soon it will do what I outlined earlier. Taking 2+ remix run applications and when it is done it will be as if you had made a singular application that runs on one url, deployment... or how ever you want to split the hair.
>
> As cool as that is, the time savings... compared to other monorepos will be an exact match to how much bifrost outpaces every other platform installer, but compounded by the amount of apps you want in your monorepo. Don't beleive me? Think about it, a monorepo is literlly just a collection of applications where each application is it's own entirely built app. So if your already saving 45 minutes to 3 hours on one app... what if your monorepo has 3, or 4, 7 applications even? The first monorepo I built? Days... multiple days, just to get to the point where I could start coding. With this addition to bifrost? at MOST, 15 minutes. That's me being really conservative, I would still be comfortable putting money on it finishing... 6, 7, or 8 minutes, meaning I'm confident that it will finish in that time frame.
>
> In addition to that, there will be pre-made packages available straight from the installer as well. Want tailwind in your mono repo?... done, shadcn? done.


### Coming Soon

- Pre-made shared packages available directly from the installer (Tailwind, shadcn/ui, and more) configured automatically across all apps in the monorepo.
- Unified single-URL deployment for multiple Remix applications within a monorepo — running and deploying as a single application rather than isolated deployments per app.


### Why It Matters

#### Time Savings

Bifröst already eliminates 45 minutes to 3 hours of setup time on a standalone project. In a monorepo, that savings doesn't add — it multiplies. Every app in your monorepo runs through the exact same build process Bifröst uses for any standalone project. That means a 7-app monorepo that would take multiple days to bootstrap manually is done in under 10 minutes. The gap between Bifröst and every other monorepo setup doesn't grow linearly with the number of apps — it compounds with each one.

#### Consistency

The more underappreciated benefit is consistency. In a manually bootstrapped monorepo, no two apps are ever set up the same way. By app 3 or app 7, something has been skipped, something was done differently, someone was in a hurry. That drift is invisible at first and becomes significant technical debt fast.

Because every app in a Bifröst monorepo runs through the same installation process with the same standards, every app comes out identical in structure and configuration regardless of how many are in the repo. There is no drift. There is no "we set this one up differently." That consistency is what makes a large monorepo actually maintainable long term — and it is something no amount of documentation or team discipline can reliably replicate when bootstrapping manually. At this point in time, there is not a single other monorepo platform that offers this level of consistency.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  BIFRÖST: Platform Installer - Heimdallr Integration

With Heimdallr being merged into the same library/module/extension, instead of being created into seperate libraries we get to enjoy benefits that heimdallr offers.

Intergrated into each installation process, your project can create and auto push the first push for you so that when your installation process has completed you not only already have a repo set up for you but it also already contains your base appplication. 

All of the extra benefits without click a single button or entering a single terminal command.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  BIFRÖST: Plugins

Plugin installer / wizard for bifrost projects.

## Installing A Plugin

### `List available plugins to install` 

Running the following command will start plugin installation process:

sidebar -> heimdallr -> plugins -> install plugin from registry

The installer will then obtain the list of available plugins to choose from the @a5gard/bifrost-plugin repo (owner `8an3`) from the file labeled `registry.bifrost`

### Direct Installation

or you may use the supplied method 

```bash
bunx @a5gard/bifrost-plugin otp-auth-plugin
```

Which will immediatly start the installation process, after scanning your projects config.bifrost to see if the platforms match for compatibility to ensure you are installing the correct plugin.

## `Plugin wizard`
### Creating your own plugin

Running the following command will start the create plugin wizard:

sidebar -> heimdallr -> plugins -> Create Wizard

Where it will then inquirer:
- name of plugin ( req )
- platform ( req )
- description ( req )
- tags you would like to have associated with your plugin
- will ask if you would like to supply the req. libraries now
  - a placeholder will display the format to input the library names but will go as follows @remix-run/react, remix-auth, react
- auto push / create github repo

It will then create:
- create `files/` folder
- run `npm init`
- push to github
- create a readme containing a plugin guide and links to the site in order to submit your new plugin and discover others
- create `plugin.bifrost` configuration file, filing in all the fields that it had gotten from you during the setup process
  - name
  - description
  - platform
  - tags, if you completed this step
  - libraries, if you completed this step
  - github

Plugins are to be made with their own repo so as it can host all the required files for the plugin. 
The repo is required to include a json config file labeled `plugin.bifrost` and a folder labeled `files` where it will host all the required files.
When installing a plugin it will prompt the user to either confirm the default supplied file location or the use can also edit the location to suite their use cases needs.

### plugin.bifrost

```json
{
  "name": "otp-auth-plugin",
  "description": "A custom one time password auth plugin for the remix platform",
  "platform": "remix",
  "github": "8an3/otp-auth-plugin",
  "tags": ["remix-run", "auth", "one-time-password"],
  "libraries": ["remix-auth-totp","remix-auth","@catalystsoftware/icons","@prisma/client","resend"],
  "files": [
        {
        "name": "email.tsx",
        "location": "app/components/catalyst-ui/utils/email.tsx"
        },
        {
        "name": "client-auth.tsx",
        "location": "app/components/catalyst-ui/utils/client-auth.tsx"
        },
        {
        "name": "auth-session.ts",
        "location": "app/components/catalyst-ui/utils/auth-session.ts"
        },
        {
        "name": "prisma.ts",
        "location": "app/components/catalyst-ui/utils/prisma.ts"
        },
        {
        "name": "login.tsx",
        "location": "app/routes/auth/login.tsx"
        },
        {
        "name": "lougout.tsx",
        "location": "app/routes/auth/lougout.tsx"
        },
        {
        "name": "signup.tsx",
        "location": "app/routes/auth/signup.tsx"
        },
        {
        "name": "magic-link.tsx",
        "location": "app/routes/auth/magic-link.tsx"
        },
             {
        "name": "verify.tsx",
        "location": "app/routes/auth/verify.tsx"
        },
    ],
    "configs":[]
}
```

## `Submit Plugin`

Running the following command will start the submission process without the need of interactive mode:

sidebar -> heimdallr -> plugins -> submit to registry

Selecting this option will automate the submission process for you, adding your plugin to the libraries registry. Allowing you to share you plugin with others that will also be posted on the site to allow users to find it more easily. 


## Searching / Posting Templates and Plugins

Shortly a site will be available for use where you can search for templates and plugins.

Feature two tabs, both tabs will host a filtering section located to the left of the pages content and a search bar located at the top of each tabs section. Allowing you to filter by platform, tags, etc meanwhile the search bar will allow you to search for individual templates or plugins for you to use.

### Templates

Each template result will display:
- name
- description
- platform
- command line to install the template
- tags
- any plugins that are to be included with the templates installation 

### Plugins

Each plugin result will display
- name
- description
- platform
- command line to install the plugin
- tags
- required libraries
- required files

### Submitting

Whether its a template or plugin, you will have the ability to submit your own to be included with its respective registry, this step is not required or needed but will help in its overall discoverability.
All you have to do in order to submit is supply your templates or plugins config file once you start the submission process. The pages nav bar will host a `submit` button in order to start the process.

Upon submission the website will automatically update the relevant registry file and push the update to github to ensure the process is automated.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  BIFRÖST-PLUGINS 

