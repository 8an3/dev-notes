# MIÐGARÐR SDk

## [VS Code Integration Features](#vs-code-integration-features)
- [Smart Prop Autocomplete](#smart-prop-autocomplete)
- [Signature Help](#signature-help)
- [Hover Documentation](#hover-documentation)
- [Auto Import](#auto-import)
- [Go To Definition](#go-to-definition)
- [Missing Import Warnings](#missing-import-warnings)
- [In Editor Comp Autocomplete](#in-editor-comp-autocomplete)
- [Developer Experience Achievements](#developer-experience-achievements)


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Editor Context Insert

Inserts selected component at cursor via the editor context menu. Menu options will be based upon current subscription status.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Quick Pick Insert

Copies the selected component into your clipboard via the quick pick menu located in the status bar. Menu options will be based upon current subscription status.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Automated Installation



## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Smart Prop Autocomplete

Pressing ctrl & spacebar while your cursor is inside the quotations of any props value will bring up an intellisense dropdown with the available prop values that can be assigned.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Signature Help

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Hover Documentation

Whenever hovering over a components name a hovercard will appear with its relevant documentation, removing the need to ever visit the site. The card will contain the following:
- name
- cateogry
- import statement
- basic usage example
- usage example
- props
- link to the components url to quickly navigate straight to the page instead having to make us, open a browser, go to the landing page.... ya no
- if the component is a primitive or uses any primitive, links will be provided to radix ui's site
- dependencies
- features list 
- tags list

Personally, it really bothers me when a library uses a component to build off of... and not provide the apis to use the thing. To make matters WORSE, I've noticed libraries aren't even providing links... the components documentation page, lets just build something, ship it... and if the user needs something... fuck it they can figure it out right?

With so much on my plate, I too have forgotten to include it, but I won't just be including the links, personally that alone I think is absurd. I understand, devs are used to a shitty fucking user experience... and don't expect one because it's just that bad.

Instead each component that uses any one of the primitives, there will be a second props table added displaying all the props values for that primitive straight from the radix ui, or whoever the provider is. 

Thus truly ensuring that you do not need to minimize or open another window while coding as all the information, components and everything else you need, is already here.





## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Auto Import

To auto import the component right click the components name where ever it may be used within the editor, select `Add Import` in the editor context menu. 

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Go To Definition

Using cmd & ctrl & clicking the components name will bring up the source codes file in a, sheet style dropdown? I don't what what you call this really, any how, it allows you to view the source code file without navigating to it, while at the same time double clicking anywhere inside the "dropdown sheet" will navigate you to the source code file itself.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> In Editor Comp Autocomplete

Whenever you start to code a component `<`, pressing ctrl & spacebar will bring up the intellisense dropdown containing every single component currently available in the library, all 2500+.
