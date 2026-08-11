# VÖLUNDR 

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Format JSON

Avialable to trigger via the second registered json formatter or by using 'ocrmnavigator.format.json.file' in a bifrost config item, featuring the following formatting options:
- any object within the array that does not contain children will be converted from multi line to single line
- removes all trailing commas that are followed by a closing bracket
- adds trailing commas to any object that is not followed by a closing bracket
- removes all inline comments
- removes all block comments

For some reason I just couldn't get the inline conversion to work right before but now it finally it works flawlessly as I hate how much space multiline objects waste, and personally I find it way easier to not only read by following inline objects instead of objects that take up the massive amount of space they typically do


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Organize Objects by Value Property

- triggered via the editors context menu contained in the root level
- once triggered it will take each arrays objects and sort each of them by the value property contained within each object, alphatically

> [!NOTE]
> The following sections were lost during the last documentation overhaul. Be that as it may till they can be created again, here is a placeholder since each feature is obvious to what it does, you only really need to know how to trigger it.
> 
> Each of the following features can be found in the editors context menu, either in the root level or contained within the formatters sub menu, except for one 'json validator' which is found among [midgardr's tool set](https://catalyst-software.vercel.app/asgard/midgardr/home/JSON-Formatter-and-Validator).

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Remove Trailing Commas

Remove trailing commas from JSON and JavaScript objects.

**Access:** Right-click → Formatters → Select option

**Features:**
- Cleans JSON files
- Cleans JavaScript objects
- Ensures code compatibility
- One-click cleanup

![Formatters](https://raw.githubusercontent.com/8an3/midgardr-notes/main/config/formatters.jpg)


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Inline Imports

Convert multi-line imports to single-line format.

**Access:** Right-click → Format document with → Select option

**Features:**
- Transforms multi-line imports into single-line format
- Automatically converts `@` to `~` in import paths
- Clean, consistent import statements

[Video Demo](https://youtu.be/YV9dIXP1ob4)




## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  JSON File Formatting and Validation

I haven't had much luck with formatters in the past tbh, but I have been using this foramtter for a while now without issue. I will revisit the formatter configurator at some point to re create the underlying functionality of it as it is not in the best condition currently. At that time, I will make the json/jsonc formatter configurable as it is not in its current state. As I'm assuming not many people will enjoy the current settings that it was coded with as it turns multi line objects into single line. For some reason I seem to be one of a few who opt for this configuration. IF you are one of those few, enjoy! 

This is now available to be configured as a default formatter for the json and jsonc file type with vscode.

Format JSON/JSONC files and toggle error checking.

**Available Commands:**

**Formatting:**
- `ocrmnavigator.formatCurrentJsonFile` - Format Current JSON File (converts multiline to inline)
- `ocrmnavigator.formatPackgeDevJson` - Format package.dev.json
- `ocrmnavigator.formatGlobalNavigatorConfigJson` - Format Global Navigator Config JSON

**Validation Toggle:**
- `ocrmnavigator.performanceSwitch.json.validate.toggle` - Toggle JSON error checking
- `ocrmnavigator.performanceSwitch.jsonc.validate.toggle` - Toggle JSONC error checking

**Usage:** Create DevStack item with type `command` using these command IDs, or access via DevStack Quick Pick


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Remove All Comments

Strip all comments from the current file.

**Access:** Right-click → Formatters → Select option or Command Palette

**Features:**
- Removes all comment types
- Works with multiple languages
- Clean code output
- Preserves code functionality

![Formatters](https://raw.githubusercontent.com/8an3/midgardr-notes/main/config/formatters.jpg)

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Remove console.log

Remove console.log statements from files, folders, or entire workspace.

**From File:**
- **Access:** Right-click → Formatters → Select option or Command Palette
- Removes all console.log statements from current file

**From Folder:**
- **Access:** Right-click folder → Formatters → Select option
- Removes all console.log statements from all files in selected folder

**From Workspace:**
- **Access:** Command Palette → Select remove console.log from workspace
- Removes all console.log statements from entire workspace

![Formatters](https://raw.githubusercontent.com/8an3/midgardr-notes/main/config/formatters.jpg)

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  Remove Unused Imports

Detect and remove import statements that are not used in the file.

**Access:** Right-click → Formatters → Select option or Command Palette

**Features:**
- Automatic detection of unused imports
- Clean up import statements
- Improved code readability
- Reduces bundle size

![Formatters](https://raw.githubusercontent.com/8an3/midgardr-notes/main/config/formatters.jpg)


