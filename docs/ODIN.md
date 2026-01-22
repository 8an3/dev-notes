# ODIN

## Search Editor
Odin, as its now called, got a bit of a re work and with it came some features I've never heard of from a search feature. From the beginning I've wanted to create this using custom editor, couldn't get it working at the time, moved forward with a webivew... which i hate. When I was looking at adding a couple of features, I said fuck it lets try again, and was successful.

Along with that, some cool features were added:

### Remote editing

The regex feature as its implemented is cool, the config is cool but personally... I think this is, if ever you could express how nerdy I am this would be it, cool as fuck.

By setting the context lines before and after, expanding your field of view into each file your search result resides in. Instead of just, showing you what is there. Each search result will be a text area allowing you to edit that file as if you were currently in it. Meaning 10 search results come up because your searching for naming colisions, you can't use find all and replace as that wouldn't solve the issue. Instead you can manually adjust each name and click on save all once you are done which pushes the changes to the effected files.

Or what if you just need to edit one file, instead of navigating to the file and line number... just make your change right there in the editor, negating the chore of opening and closing of files.

I've already used this a couple of times, not only does it save time from having to navigate to the file and then double clicking on the search result again to bring you to the actual line number that you need to get to. It also saves time having to manually close each tab that you opened in order to make those changes. VSCode employees, if your reading this... whoever would be the one that could implement this into your app... please go show them this, as this one feature will make me forever use my implementation over yours.

### config.odin

Before getting into the thick of it, basically there are three ways in going about your use of this in terms of the config:
1. Do nothing. Defaulting to always starting with the same values each time, just like vscode does. That way, if your the type of user that doesn't want to touch anything, just use it, and come and go as you please... you're covered.
2. For the ones that want to take it a step further, and would like to customize it only so far, so that you only wish to customize the settings through vscode or the extension. Essentially, setting up your own default values that you would start with each time. Great, set your settings and your covered. Either hit ctrl and comma, taking you to the settings screen and search for ocrmnav.
3. For the next group, you want the same but to also continue down that path, taking it further and have the config update as you use it. For example, before long you notice that you use files to include more often than not, well with this value set to true when you enable files to include, close the editor and to come back 5 minutes later, it will still in fact be enabled and ready for you the next time you come to it.
4. The last group, maybe you need to take things a step further and not only want all the above but also you want to pre-configure on a search by search basis and have different configurations set up for different use cases... primed and ready to go. Great you can do just that. saving the config with the .odin file extension will do just that. Couple with the virtual file system, you can create file items in the explorer pane, setting your .odin file as a line item to be click on. Once clicked, that config file will be used when opening the search editor allowing you to customize on a input field and button basis, having everything tuned the way you need it to be for the project your working on or whatever the case may be.

When re-creating the search using vscodes custom editor... seeing how they are built gave me an idea. Why couldn't I configure how each button or input starts when the editor opens? Turns out you can, lol. At the same time, created in a way that any file with the extension as .odin will open as the search editor. Taking advantage of the core extension that is already in place, you now have a item type of 'search' on jacked up configurable steroids by creating your own config, then creating an item type of file, it will open the .odin and because of how the extension and feature is configured it will immediatly open that file type with the search editor and take advantage of whatever pre configured config you have set up. How much of the search editor can we configure? Everything... 

```json
{
  "query": "",
  "replace": "",
  "includePattern": "",
  "excludePattern": "",
  "useRegex": false,
  "caseSensitive": false,
  "matchWholeWord": false,
  "useFuzzy": false,
  "searchInOpenEditorsOnly": false,
  "useExcludeSettings": false,
  "includeEnabled": false,
  "excludeEnabled": false,
  "searchScope": "workspace",
  "searchParams": {},
  "results": [],
  "savedPatterns": {
    "include": [
      { id: 1, value: "project-config.json, global-navigator-config.json, f:/DevStack/*," },
      { id: 2, value: "**/*" },
      { id: 4, value: "package.dev.jsonc, package.json" },
      { id: 5, value: "F:\\playground\\app\\components\\catalyst-ui\\blocks\\*" },
      { id: 6, value: "F:\\playground\\app\\components\\catalyst-ui\\" }
      { id: 7, value: "F:\\playground\\app\\components\\catalyst-ui\\data\\*" }
    ],
    "exclude": [
      { id: 1, value: "*.js, *.d.ts, *.map, *.cjs,  *.mjs, *.d.cts, *.mts, node_modules/*," }
    ]
  },
  "searchHistory": []
}
```

As you may have noticed everything configurable, so if you consistently have a search that you are doing at work instead of manually doing it each time, you can just click a line item in the extension instead and because of it being an editor instead of using vscodes search in the explorer pane... you can open 5 at once if you wanted. From a performance point, if you do... do that, just be sure your filing out the exclude portion. 

**You cannot save your custom config as 'config.odin' as it checks the file name and determines what to do at that point**

> [!NOTE]
> config.odin, is in addition to the already in place extension settings that you can set for odin. These settings set the default behaviors when you open search, where as creating new config .odin file enables a case by case configuration. This allows the power users to do as they wish while at the same time giving the simplicity everyone else needs, due to the fact that you don't even need to set any of the settings in order for it to work and can still leverage the powers that this has over the default implementation that is vscodes explorer pane search.

```json
{
    "ocrmnavigator.odin.contextLinesBefore": { "type": "number", "default": 4, "description": "Number of lines to show before each search match" },
    "ocrmnavigator.odin.contextLinesAfter": { "type": "number", "default": 10, "description": "Number of lines to show after each search match" },
    "ocrmnavigator.odin.query": { "type": "string", "default": "", "description": "Set default query string that would be used when editor opens" },
    "ocrmnavigator.odin.replace": { "type": "string", "default": "", "description": "Set default replace string that would be used when editor opens" },
    "ocrmnavigator.odin.includePattern": { "type": "string", "default": "", "description": "Set default includePattern string that would be used when editor opens" },
    "ocrmnavigator.odin.excludePattern": { "type": "string", "default": "", "description": "Set default excludePattern string that would be used when editor opens" },
    "ocrmnavigator.odin.useRegex": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.caseSensitive": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.matchWholeWord": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.useFuzzy": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.searchInOpenEditorsOnly": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.useExcludeSettings": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.includeEnabled": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.excludeEnabled": { "type": "boolean", "default": false, "description": "Enables or disables useRegex when editor opens" },
    "ocrmnavigator.odin.searchScope": {
          "type": "string",
          "default": "workspace",
          "enum": [
            "workspace",
            "openFiles",
            "currentFile",
            "gitChanges",
            "off"
          ],
          "description": "Set default search context value"
        },
}
```


### Regex

Yes, vscodes native search does have the ability to use regex but it could be... just a bit better. 

This being one of those things that... unless your 10-20 years in, probably don't know how to code and even if you have dabbled in the arts that is regex, probably don't know how powerful or useful it actually can be. For me anyways, I had this sweet list of regex strings I had saved that allowed me to do all sorts of things, that saved... an INCREDIBLE amount of time in comparison as to when I didn't have them. I can't remember if it was due to my computer giving out or a drive, but they were lost. Adding to the injury, since I did have all those sites bookmarked where I got those strings, ALL but one... are now offline. If I could expresss the eye roll or the sigh in the magnitude when it happened as I was finding this out through a text doc, I would. 

Instead of leaving you completely in the darkness, now whenever regex is enabled a new input row will appear containing a dropdown and couple inputs and buttons. The dropdown provides a list of pre-made regex strings to use, once one is selected it will populate that string into one of the inputs, while the second input will be used in conjuction with the first, lastly the buttons that appear will help in implementing the desired effect.

For example, one that I find is incredibly useful, but can never remember the actual string `Place Cursor At All Occurrences`. Whenever you have a json file that needs a change done on one of the values that is 20,000 objects long, this would absolutely suck... manually editing. Instead, choose this option and in the second input type out the string of the value you would like the cursor placed. Once you hit, I think its complete... it will be obvious once your using, it will then place 20,000 cursors in that json file so you can edit all 20,000 objects... as if it were one. Almost forgot, the dropdown that populates when you enable regex, does contain an option for custom so you can use it just like you would vscodes implementation.


### Fuzzy searching

Using fuse.js, there is a button in the search input to enable fuzzy searching. My only advice when using this, unless you rreeaaallllyy need to... I highly recommend filing out the exlude/include field. Searching already is resource heavy and so is fuzzy searching, combining the two unless you fill out the exclude/include field... you will hear your fans ramp up. I haven't tried this yet, as I'm currently packaging the extension up as I write this. If this does become a problem, I will look into writing a custom search engine because I do want this feature but I'll only view it as a problem if there are issues when using this feature, with the exclude/include fields filled out.


### Layout

This one will be unintuitive at first but it will make sense once you use it. 

The layout in terms of inputs... has been completely reversed. This is due to the fact that whenever you use more than just the search field, the search input is typically used last. Now when you start at the include field, pressing enter will move the cursor into the next input field, exlude, once done or if you would like to leave it empty, pressing enter again puts you into the search field. As the replace field is primarily used once you have already found what you need, this is still placed in the accordian styled input row.


## GitHub Tag Navigator

Github does a lot of things right but... it also gets a lot of things wrong. Relevant use case: When your searching for a section of code within a file, without knowing exactly with version it was in. It's great that you can version the hell out of a project but when it comes to this specific use case, its a pain to incrementally navigate tags/version in your project. This specializes in that, for now anyways. I know there are a lot of areas on their site that need improvements, but instead of going off the deep end and going after all of them right away. For the mean time this will just specialize in tag navigation.

Built using vscodes custom editor, enabling us to open as many editors we wish to.

Accessible via devstack quick pick.

## Dependency "Deep Link" (packageSearch)

Quick access to library documentation and entry points directly from imports.

**Access:** Hover over imports in your code

**Features:**
- Clickable links for package.json
- Clickable links for README.md
- Direct access to package entry point
- No more scrolling through node_modules in sidebar
- Instant documentation access

**Usage:** Hover over any import statement to reveal clickable links to package documentation and code.

## File Line Jumper

Create clickable file links with specific line numbers.

**Access:** Use `// @dev path:line` syntax in comments

**Syntax:** `// @dev path/to/file.tsx:lineNumber`

**Example:** `// @dev app/components/catalyst-ui/primitives/table.tsx:6`

**Features:**
- Creates clickable links in any file
- Opens files at specific line numbers
- Works before and after return statements
- Quick navigation to exact code locations

[Video Demo](https://youtu.be/xR1osGkuNCA)
![File Line Jumper](https://raw.githubusercontent.com/8an3/dev-notes/main/ui/vfs/file-linking.jpg?raw=true)

## File Search Jumper

Create search-based file links that navigate to the first instance of a search term.

**Access:** Use `// @devsearch path:term` syntax in comments

**Syntax:** `// @devsearch path/to/file.tsx:SearchTerm`

**Example:** `// @devsearch app/components/catalyst-ui/data/table-data.tsx:Table`

**Features:**
- Creates links that search for specific terms
- Navigates to first instance of search term
- Useful for finding component definitions
- Quick code exploration

[Video Demo](https://youtu.be/Otd3jWfSf4M)
![File Search Jumper](https://raw.githubusercontent.com/8an3/dev-notes/main/ui/vfs/file-searching.jpg?raw=true)