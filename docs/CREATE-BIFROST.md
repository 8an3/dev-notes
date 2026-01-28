# BIFROST

> [!IMPORTANT]
> Currently in alpha testing...

Currently in testing, but after its creation it looks as if it will accomplish exactly what I was going for when I first thought of this idea, which was:
- a resource that caters to more than just a single platform
- create a plugin system in which any project can install and use, obviously as long as its platform compatible
- a search and discover system where you can find templates and plugins by either filtering results or search for individual plugins

Obviously no platform is going to advertise the use of a competing platform, and currently there is no resource like this. Along with the fact that, there is also nothing of its kind like a plugin system, in which it takes care of the installation process for you. Hoping that this fills those gaps, and creates a great community resource. 

The idea originally stemed from using remix-stacks, in which it was a great system that was implemented with its ease of use to very quickly install a opinionated platforms template. But I wanted to take the idea further, and implemented with a better ux. In the end, two seperate npm libraries were created
- `create-bifrost`
- `bifrost-plugin`

The first devoted to templates while the later caters to plugins once a templates installation process has already completed. Both feature interactive and with options modes.

To make the process easy for creators a simple config file is all that is needed to submit and be listed for use.

```json
{
  "name": "My Stack",
  "description": "A custom template for X platform",
  "platform": "remix",
  "github": "owner/repo",
  "tags": ["react", "typescript", "tailwind"],
  "postInstall": ["setup", "db:generate"],
  "plugins": ["owner/plugin1", "owner/plugin2"]
}
```

As you can see, it leverages systems already in place by taking advantage of npm scripts. Allowing creators, without any extra hassle, include custom post install processes to take place during the installation process. 

All the while taking advantage of the newly created plugin system. Where you can keep your original project clean by creating plugins and referencing them instead of including them within that specific template. Ultimately allowing for a quicker creation process, all the while allowing you to create multiple templates using the same "base" project. 

For example, you could create a foundational project using 'react-router', leaving it devoid of any additional libraries and or file scaffolding. Instead creating "plugins" that will be used in its place, that install the required libraries, files and configurations once the original template has finished initializing.

To create a plugin, for exmaple a one time password auth system that includes all the required files such as login, logout, etc. Can easily be done by including all the required files contained in a folder labeled `files` and creating the plugins config file labeled `plugin.bifrost` containing the following:

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

You may or may not include a readme, depending on the degree of difficulty your plugin is, but all that is required is the config file and the folder containing all required files.

All that is required to list the plugin or template, is to submit the config file on the site.

By utilizing already in place systems in addition to the plugins, I'm hoping it not only fills in the gaps but at the same time giving a great ux. Below you overview the libraries readme's.



# create-bifrost

Platform-agnostic project creator with extensible template system inspired by Remix Stacks.

## Features

- 🌈 **Platform Agnostic**: Works with any framework (Remix, Next.js, Vite, etc.)
- 📦 **Multiple Package Managers**: Support for npm, pnpm, yarn, and bun
- 🎯 **Git-based Stacks**: Use any GitHub repository as a template
- 🚀 **Interactive CLI**: Guided setup with smart prompts
- ⚡ **Fast Setup**: Clone, configure, and install in seconds
- 🔄 **Auto Git Push**: Optionally push initial commit to GitHub

## Usage

### Interactive Mode

```bash
bunx create-bifrost
```

In interactive mode, the following prompts will display:
- What would you like to name your new project?
- Which platform would you like to use?
- Which package manager do you prefer?
- Would you like to have the install command run once the project has initialized?
- Would you like to auto create and push the first commit to GitHub?

### With Options

```bash
bunx create-bifrost my-app --template owner/repo --pkg-mgr bun
```

### Full Example

```bash
bunx create-bifrost my-app -s remix-run/indie-template -p bun
```

### Platform Templates

```bash
bunx create-bifrost my-app --list-templates
```

## Options

| Flag | Alias | Description |
|------|-------|-------------|
| `--template` | `-s` | Stack to use (format: owner/repo) |
| `--pkg-mgr` | `-p` | Package manager (npm, pnpm, yarn, bun) |
| `--no-install` | | Skip dependency installation |
| `--help` | `-h` | Show help |
| `--version` | `-V` | Show version |

## Creating Your Own Template

Any GitHub repository can be used as a template. To make this process easier whenenver you create a project based off of a platforms base installer, a config file will be created for you in order to create and post your own template. If you want to create your own template based off of another, the original templates config will already be located within the root folder. All you have to do is edit the config in order meet your newly created projects use case needs.

```bash
bunx create-bifrost my-app --template name/repo
```

### Stack Configuration (Optional)

Add a `config.bifrost` to your repository root for enhanced functionality:

```json
{
  "name": "My Stack",
  "description": "A custom template for X platform",
  "platform": "remix",
  "github": "owner/repo",
  "tags": ["react", "typescript", "tailwind"],
  "postInstall": ["setup", "db:generate"],
  "plugins": ["owner/plugin1", "owner/plugin2"]
}
```

## Installing A Plugin

Once your project has completed its installation process, you may now cd into the newly created directory and run

```bash
bunx bifrost-plugin
```

Entering interactive mode it will then obtain the list of available plugins to choose from the bifrost-plugin repo (owner `8an3`) from the file labeled `registry.bifrost`

or you may use the supplied method 

```bash
bunx bifrost-plugin otp-auth-plugin
```

Which will immediatly start the installation process, after scanning your projects config.bifrost to see if the platforms match for compatibility to ensure you are installing the correct plugin.

## Creating your own plugin

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
    "configs":[
        {
            "targetFile": "prisma/schema.prisma",
            "configSource": "prisma-schema.txt",
            "insertType": "append" // or "replace", "merge"?
        }
    ]
}
```

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
