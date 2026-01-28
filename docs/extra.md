## The ".env" Context Swapper (envProfile)

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



## Pro7 Archiver
Secure sensitive files in password-protected archives before pushing to GitHub, ensuring safe version control for proprietary code.



### VSCode Icons

Visual reference for all available VSCode icons and their identifiers.

**Access:** DevStack Quick Pick menu in status bar

**Features:**
- Browse complete icon library
- Search by name or category
- Quick copy icon identifiers
- Visual preview of all icons
- Integration with custom commands

**Usage:** Perfect for customizing your extension commands, status bar items, and UI elements with the right visual indicators.

**Note:** Regularly updated to include new VSCode icon additions and improvements.


---

[🡄 Return](https://github.com/8an3/DevStack)
