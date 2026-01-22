# GINNUNGAGAP

Personally, I hate limitations, which is one of the reasons you rarely see any put in place in this extension. Don't ask how, since I currently do not have the slightest clue on how to pull this off yet but I will. I wanted to create something that remix used to have, because I do not think this feature will be seen again even if remix does release their next version. 

Remix stacks was a great idea allowing users to, very quickly and painlessly, create opionated versions of a platform that came pre installed with a great many of features. If you don't know what I'm talking about, remix had a feature in which when you were first creating the base of a new project, you had the option to reference a stack in the actual terminal command. While behind the scenes it was basically just another means of git clone, it allowed the user to start off with an opionated version of remix which included pre configured auth, tailwind, schemas, use of different databases, docker and so much more. All the user had to do was, `npx create-remix custom-stack` or something akin to that. Which from a ux perspective was a really nice feature.

Other platforms have tried to replicate this, but have come short in terms of execution. I don't want to see this idea die with a project, because it was exectued in a great way but I want to expand on it where they should/could have.

One such area is plugins. This will be made in a way, even when creating your "stack" as it were, so that you can not only just post the finished stack for people to use, but also be able to share the features in which that stack hosts. For example, a stack that features a pre configured auth system, already complete with login / logout pages, schema and more. It would be great... if that creator could also post the plug in that could be used with other stacks. This one feature would be able to take a already customized stack and any user would then be able to inject a great many of other features that are needed for that project. Taking something that could take weeks or more, into... less than 30 minutes.

I also want to make finding each project/plugin a lot easier. It will host not only a search bar to quickly find what your looking for but also filters in order to browse the available items with ease. 

Architecture Templates, pre-configured platform scaffolding think of it as, incorporating remix-stacks into devstack, but less restrictive all the while having more features, making it even more powerful, saving even more time
- auto:
    - install
    - git initalize and first push
    - schafold prisma with seed and schema
    - set up auth and auth routes
    - pre-configured tooling (eslint, prettier, tsconfig)
    - create common files (.gitignore, .env.example, README template)
    - package libraires and configs into groups, so can be used across several platforms
    - create / overwrite files, folders taking a template project and making it even more custom
    - tsconfig.json (your preferred settings)
    - .eslintrc (your rules)
    - .prettierrc (your formatting)
    - jest.config.js (your test setup)
    - docker-compose.yml (your local stack)
    - Create .gitignore from template
    - Set up branches (main, develop)
    - changelog
    - .env templates per project type
    - Common variables already filled
    - Docker Stack Initialization 
    - Postgres + pgAdmin
    - Redis
    - MongoDB + Mongo Express
    - Your common service stack
    - CI/CD Pipeline Templates
    - API Route Boilerplate
    - Create CRUD endpoints
    - Error handling wrapper
    - select readme.md template to be used
    - Webpack config for your setup
    - Vite config
    - Rollup config
    - Monorepo Setup
    - and more

Unfortuantly due to the nature of this extension, this will have to be its own npx product. In terms of how you will use it:

From the terminal:
- `npx create-devstack project-name`
- it will then ask:
  - which packge manager you would like to use
  - if you would like to install everything for you
  - if you would like to have it set up git and execute the first push
  - in order to take advantage of plugins it with either ask you to type in the plugins or provide a list for you to select which ever ones you would like to install

Obviously I would rather present a list of plugins instead of typing it in. The issues I see with this would be, what if that plugin list grows too much and secondly due to the overall idea of being agnostic in terms of platform how will the user know which ones they can or cannot use. One solution I can think of right off the bat:
- the list that would be generated would be filtered by platform and only presenting the plugins that are categorized to be used for that platform
- having a seperate npx command that can be used once the project is already present on the users computer that would be executed inside that workspace.... this option would also be a great thing to include either way

The last option coupled with `npx create-devstack` in which it would present the user a list of available options in addition to `npx create-devstack project-name` would offer the best ux. Which could be accomplished with two api's one that presents the avaialable projects to use, and one taking in a platform param and with that param it filters the plugins before sending the list back to the user to choose from. ie: `npx devstack-plugin` behind the scenes the script will scan for platform send the http request to the api and respond with the list.