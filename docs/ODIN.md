# ODIN

Odin, as its now called, got a bit of a re work and with it came some features I've never heard of from a search feature. From the beginning I've wanted to create this using custom editor, couldn't get it working at the time, moved forward with a webivew... which i hate. When I was looking at adding a couple of features, I said fuck it lets try again, and was successful.

Along with that, some cool features were added:

### Regex

Yes, vscodes native search does have the ability to use regex but it could be... just a bit better. 

This being one of those things that... unless your 10-20 years in, probably don't know how to code and even if you have dabbled in the arts that is regex, probably don't know how powerful or useful it actually can be. For me anyways, I had this sweet list of regex strings I had saved that allowed me to do all sorts of things, that saved... an INCREDIBLE amount of time in comparison as to when I didn't have them. I can't remember if it was due to my computer giving out or a drive, but they were lost. Adding to the injury, since I did have all those sites bookmarked where I got those strings, ALL but one... are now offline. If I could expresss the eye roll or the sigh in the magnitude when it happened as I was finding this out through a text doc, I would. 

Instead of leaving you completely in the darkness, now whenever regex is enabled a new input row will appear containing a dropdown and couple inputs and buttons. The dropdown provides a list of pre-made regex strings to use, once one is selected it will populate that string into one of the inputs, while the second input will be used in conjuction with the first, lastly the buttons that appear will help in implementing the desired effect.

For example, one that I find is incredibly useful, but can never remember the actual string `Place Cursor At All Occurrences`. Whenever you have a json file that needs a change done on one of the values that is 20,000 objects long, this would absolutely suck... manually editing. Instead, choose this option and in the second input type out the string of the value you would like the cursor placed. Once you hit, I think its complete... it will be obvious once your using, it will then place 20,000 cursors in that json file so you can edit all 20,000 objects... as if it were one. Almost forgot, the dropdown that populates when you enable regex, does contain an option for custom so you can use it just like you would vscodes implementation.

### config.odin

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
> I deleted this part because I wanted to start from scratch in terms of the docs.
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

### Fuzzy searching

Using fuse.js, there is a button in the search input to enable fuzzy searching. My only advice when using this, unless you rreeaaallllyy need to... I highly recommend filing out the exlude/include field. Searching already is resource heavy and so is fuzzy searching, combining the two unless you fill out the exclude/include field... you will hear your fans ramp up. I haven't tried this yet, as I'm currently packaging the extension up as I write this. If this does become a problem, I will look into writing a custom search engine because I do want this feature but I'll only view it as a problem if there are issues when using this feature, with the exclude/include fields filled out.

### Remote editing

The regex feature as its implemented is cool, the config is cool but personally... I think this is, if ever you could express how nerdy I am this would be it, cool as fuck.

By setting the context lines before and after, expanding your field of view into each file your search result resides in. Instead of just, showing you what is there. Each search result will be a text area allowing you to edit that file as if you were currently in it. Meaning 10 search results come up because your searching for naming colisions, you can't use find all and replace as that wouldn't solve the issue. Instead you can manually adjust each name and click on save all once you are done which pushes the changes to the effected files.

Or what if you just need to edit one file, instead of navigating to the file and line number... just make your change right there in the editor, negating the chore of opening and closing of files.

I've already used this a couple of times, not only does it save time from having to navigate to the file and then double clicking on the search result again to bring you to the actual line number that you need to get to. It also saves time having to manually close each tab that you opened in order to make those changes. VSCode employees, if your reading this... whoever would be the one that could implement this into your app... please go show them this, as this one feature will make me forever use my implementation over yours.

### Layout

This one will be unintuitive at first but it will make sense once you use it. 

The layout in terms of inputs... has been completely reversed. This is due to the fact that whenever you use more than just the search field, the search input is typically used last. Now when you start at the include field, pressing enter will move the cursor into the next input field, exlude, once done or if you would like to leave it empty, pressing enter again puts you into the search field. As the replace field is primarily used once you have already found what you need, this is still placed in the accordian styled input row.

