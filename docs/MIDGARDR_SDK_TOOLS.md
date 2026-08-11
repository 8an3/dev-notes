# MIÐGARÐR SDk


## [Tool Suite](#tool-suite)
- [Development Tools](#development-tools)
  - [VSCode Cmd Reference](#vscode-cmd-reference)
  - [Markdown Cheat Sheet](#markdown-cheat-sheet)
  - [IRIS: Color Tools](#iris-color-tools)
    - [IRIS: Color Converter](#iris-color-converter)
    - [IRIS: Color Wheel](#iris-color-wheel)
  - [React/Tailwind Sandbox](#react-tailwind-sandbox)
  - [Theme Builder](#theme-builder)
  - [Typography Tester](#typography-tester)
  - [Layout Generator](#layout-generator)
  - [X Tester](#x-tester)
  - [Components Reel](#components-reel)
  - [Tailwind Converter](#tailwind-converter)
  - [Animation Builder](#animation-builder)
  - [Responsive Design Helper](#responsive-design-helper)
  - [Code Carousel](#code-carousel)
  - [Sandbox](#sandbox)
  - [Icons](#icons)
  - [RÚNAR Editor](#rúnar-editor)
  - [Regex Tester](#regex-tester)
  - [JSON Formatter & Validator](#json-formatter--validator)
  - [API Response Mocker](#api-response-mocker)
  - [Lorem Ipsum Generator](#lorem-ipsum-generator)
  - [Cron Expression Builder](#cron-expression-builder)
  - [UUID Hash Generator](#uuid-hash-generator)
  - [Code Diff Viewer](#code-diff-viewer)
  - [Flexbox Sandbox](#flexbox-sandbox)
  - [Grid Sandbox](#grid-sandbox)
  - [QR Code Generator](#qr-code-generator)
  - [Responsive Preview](#responsive-preview)
  - [Accessibility Checker](#accessibility-checker)
  - [Animation Builder](#animation-builder-1)
  - [Chart Playground](#chart-playground)
  - [MD Badge Builder](#md-badge-builder)
  - [Spinner Generator](#spinner-generator)
  - [Terminal Menu Generator](#terminal-menu-generator)
- [ENCODER_DECODER_LAB](#encoder_decoder-lab)
  - [Image to Base64](#image-to-base64)
    - [PNG to Base64](#png-to-base64)
    - [JPG to Base64](#jpg-to-base64)
    - [WEBP to Base64](#webp-to-base64)
    - [PDF to Base64](#pdf-to-base64)
  - [Base64 to Image](#base64-to-image)
    - [Base64 to PNG](#base64-to-png)
    - [Base64 to JPG](#base64-to-jpg)
    - [Base64 to WEBP](#base64-to-webp)
    - [Base64 to PDF](#base64-to-pdf)
  - [Data Conversion](#data-conversion)
    - [CSV to JSON](#csv-to-json)
    - [Image to SVG](#image-to-svg)
      - [PNG to SVG](#png-to-svg)
      - [JPG to SVG](#jpg-to-svg)
      - [WEBP to SVG](#webp-to-svg)
    - [Media Conversion](#media-conversion)
      - [MP4 to MP3](#mp4-to-mp3)


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Mathmatical Color Converter

> [!NOTE]
>
> While I admit this being a bit more of an advanced tool, I promise that no matter what skill level you are currently at in terms of building themes or generating picture perfect UI color schemes, this will catapult your skill level far beyond what it should be. And I will go over this, as if you know nothing about colors... will barely even mention the proper terminology in order to explain everything.
> 
> Currently, I know enough about colors, color palletes, hues, shading and all other matters pertaining to colors, to know that... I fucking suck at making themes from scratch. At this knowledge level  I currently won't even waste my time trying because I know that there is an art to picking a color pallete that everyone will lov, but I did not attend art school although I am good at other things. 
>
> For example, math and science is every where and while art really... doesn't have anything to do those topics, maybe we can find some math in art. As I was staring at some one elses theme, I just kept asking myself, "How the fuck did they get that "input" color from that "background" color? Like what sliders or knobs do you need to use in order to achieve that end result?". Not even bothering with taking on that challenge, and attempting to achieve that same input color by playing with a bunch of color sliders. 
>
> Thankfully at this point I asked myself, "Is there a way to mathmatically calculate the difference between these two colors?" Again, thankfully when I took this question to an ai prompt... it didn't take long to convey what I wanted to get done.
>
> I'll be using a common libraries resource for this so as to make it a lot easier to provide the correct colors and a visual to go with the explanation if you need it. Go to [shadcn](https://ui.shadcn.com/)'s home page, to the right of the tabs there is a dropdown that allows you to select a theme, currently I'm on dark neutral.
>
> Click on the copy button beside the dropdown so you can open the color swatches that the theme is based off of, because when using a color picker with a live theme it's not always the most reliable  in extracting the exact color you want as it tends to change as you move the mouse around. To keep everyone on the same page, please use the background swatch found in the dialog that pops.
> 
> So using whatever color picker you have available to you, if you don't have one and are on windows pressing windows key + shift + c, will trigger a color picker if you have power toys installed ( a windows app ). If you don't have that installed ( or even if you do since this tool I'm about to go over is a lot better ), using microsfts store, download 'desktop color picker pro' its free and it features a cursor/picker with a zoomed in view so you can properly get the right color whenever you are trying to extract it from any ui. 
> 
> If you don't know what I'm talking about, install this tool and just going around your ui and look at different colored elements and you will see, for example blue text... isn't always exactly blue text, when you zoom in, it features different shades of blues, greens, whites, yellows and without that zoomed in view of what you are clicking on to extract the exact color you want... you could be sitting there for... 2, 4, sometimes even 10 minutes randomly click the same blue character... just to get the blue you see on the screen.
>
> With your color picker hover over background color swatch and you should get '#0A0A0A', and after checking the actual background it matches so this is perfect. Looking at the rest of the ui, you will notice that the inputs are not as dark, being slightly lighter in color, and active items even more so such as the radio group.
>
> While shadcn/vercel probably has a staff member or two who have art degrees, we're going to try to cheat our way to the top when it comes to creating picture perfect themes.
>
> Using your color picker hover over one of the inputs that does not change color... when you hover over it with the picker, and you should get a value of '#161616'
>
> Is there some possiblity of mathmatically determining how to achieve the same color difference between that background and input color, and then take any background color and find out what the correct color value should be used for its input? To expand on it even further, can we use that same formula/function and just slightly change the knob ( values ) in order to also determine what our active radio group colors should be? Well... apparently there is.
>
> I won't dive into the actual math, but now that you get the idea behind this in what this tool sets out to achieve, I can go over the converter.

The converter will contain 4 parts, parts 1 and 2 will work along side one another and parts 3 and 4 will work on their own.

The first section, will take in that background color in the first input and also take in that input color in the second input. When these two values are populated there will be a result that pops up that gives you the exact number you need in order to complete the next step.

Working on whatever theme you are, taking whatever color you need to start with, place it within the first input. The tool should already have the value derived from the previous step so it will automatically produce a color value that is mathmatically the same difference between itself and the color you just provided, as it is for the first two colors you provided. 

Now you aren't limited to just background and input colors, as you can use the same formula on a number of things in order to find the perfect color to use in combination with the first color. And since the first step, calculates what the actual difference is between the two, it doesn't matter how much of a difference there is.

The third section will contain an input and to the right of it you will be able to adjust the rgb value up or down to dynamically to achieve the same result that would be produced above, but allowing you to visually see a mathmatically correct color across its sliding values in comparison to sliding the color knob on a 16 different colored background.

The fourth section, while similar to the previous, uses a different formula that you can change the value of the given percentage in order to slide up and down that color range.

Depending on where, exactly the color is from in terms of the spectrum the mulitpler method gets messy with low color values, which is why I decided to include both of them.

Hopefully, I explained this in a way that anyone from any skill level can understand, even if you never created your own theme before. Personally, I wish I had a tool like this when I started playing around with themes. The hours I spent staring at other peoples themes just wondering how exactly they got the colors they did that were based off of the backgrounds and such and going so far as attempting to play with the hues and such to attempt in getting the same result... omg. This literlly takes a task that, without that degree, would take hours in order to properly get the perfect color to use and cutting it down to seconds. And yes, I know those art majors probably have some stupidly expensive art software where it does exactly the above for them too.

Personally, I will be taking these exact formulas and pumping them into my theme builder, which will enable me to... with very little inputs, create the perfect theme every time. This will be achieved by supplying a hex value and the mulipler value into a function, in order for it to calculate it on its own by setting the values once and letting it do the rest.

```jsx
export function getInputColorByOffset(hex: string, multi = 10) {
  // Remove # if present
  const cleanHex = hex.replace('#', '');
  
  // Parse RGB values
  const r = parseInt(cleanHex.substring(0, 2), 16);
  const g = parseInt(cleanHex.substring(2, 4), 16);
  const b = parseInt(cleanHex.substring(4, 6), 16);
  
  // Add "multi" to each channel, clamp to 255
  const newR = Math.min(r + Number(multi), 255);
  const newG = Math.min(g + Number(multi), 255);
  const newB = Math.min(b + Number(multi), 255);
  
  // Convert back to hex
  return '#' + 
    newR.toString(16).padStart(2, '0') +
    newG.toString(16).padStart(2, '0') +
    newB.toString(16).padStart(2, '0');
}

export function getInputColorByMultiplier(hex: string, multi = 1.83){
  // Remove # if present
  const cleanHex = hex.replace('#', '');
  
  // Parse RGB values
  const r = parseInt(cleanHex.substring(0, 2), 16);
  const g = parseInt(cleanHex.substring(2, 4), 16);
  const b = parseInt(cleanHex.substring(4, 6), 16);
  
  // Multiply by "multi", round, clamp to 255
  const newR = Math.min(Math.round(r * Number(multi)), 255);
  const newG = Math.min(Math.round(g * Number(multi)), 255);
  const newB = Math.min(Math.round(b * Number(multi)), 255);
  
  // Convert back to hex
  return '#' + 
    newR.toString(16).padStart(2, '0') +
    newG.toString(16).padStart(2, '0') +
    newB.toString(16).padStart(2, '0');
}
```

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> VSCode & Tailwind Theme Builder

Obviously I enjoy looking at a nice user interface, who doesn't? The real question is, who wants to build themes the way microsoft intended with vscode? Fucking nobody... My god, this is a prime example on how to not include a feature. Especially a feature that so many people would want to use at varying skill levels.

This being such a complicated task to complete it took me ages, just to work up the confidence to start editing that object in the settings.json file... let me re-phrase that, it took me ages just to learn on how to find out what values are needed to be modified in order to create a theme in the first place, unbelievable.

Seriously, the system that vscode created to edit the theme is simply, just garbage, but we have to endure it because... that's how you edit the theme. After creating... about the third theme I stopped creating them all together. Once I got good enough at coding, I created a tailwind theme builder that maps the same tailwind theme to all the elements found in vscodes UI. Making it so that creating a vscode theme, no longer sucks.

Now the theme builder is currently at it's umphteen revision, it does quite a lot more while solving some critical UX problems... that nobody even seems to be attempting to solve. 

Like color pickers? I know you, myself and every other dev has just lived with these things, but fuck do they suck when building a theme. Taking an exercise that, lets be honest, takes a while all on its own but then whenever you want to manually customize a color and use that color picker, your adding a unknown multiplier thats based on how perfect you want the theme to look and then again, multipling the time by the amount of custom colors you want to customize. Who wants to build themes like that? Again, fucking nobody. So along side every single color picker, just in case that one person out there that wants it, there is a new style of color picker that, tbh I've never seen created anywhere else in any context. Simply named, the color wheel picker. Instead of making you dial in each color with 6 different knobs, it just provides every option available on the color wheel. Whenever you hover over a color, a tooptip displays with the colors name and number value. It works so much better, here on out I will be droping the color picker all together and use the color wheel picker in its place, except for uses cases like this theme builder.

![Z](https://raw.githubusercontent.com/8an3/midgardr-notes/main/freyr/colorwheelpicker.png)

### Live Previews

The theme builder hosts a number of live previews so you can see exactly what your building as you build it, consisting of but not limited to:
- a webpage that features a host of components to ensure you know exactly the theme your building for your tailwind.css file
- a recreated vscode user interface that achieves the same as above
- lastly a specialized vscode interface that hosts a number of different files to view that you can change from switch tab to tab, just like you do in vscode. Each file features a different language so that you can preview token colors and semantic token colors that change how the syntax highlighting looks as you build on the fly. This is another feature, I have yet to see elsewhere

### Color Output Formats

Due to working in so many enviroments it obviously outputs in more formats than the current tailwind version, such as:
- tailwind v4
- tailwind v3
- settings.json ( so you can paste it straight into your file )
- while the last one doesn't exactly have a name per say, but it outputs the exact object you need in order to create your very own vscode theme extension. Actually... as it includes all the colors needed, all the values that are required, the token colors you have chosen along side the semantic token colors as well

### Intelligent Color Mapping

This one took a while to get right but when it was perfected... it really made the exercise of creating a vscode theme a breeze.

Whenever you select a preset theme configuration, or whenever you select a color to use in your tailwind theme it automatically applies the same colors to your vscode theme, token colors and semantic token colors. 

In the time it takes to create a tailwind theme, you now have two other output options that you can choose from for setting that same theme in vscode.

Not only does it provide the perfect vscode theme to quickly paste into your project, it also provides THEMED token colors its semantic counterpart. Thus taking a task that was usually only being done, by seasoned devs and opening it up to virtually... any skill level. Not to mention, drastically cutting down the required time in creating themes 100 fold.

MEANWHILE, the theme builder still lets you custmize each vscode color option whenever you go to individually custmize it. So if you hate the color of the border that used in your tailwind theme, no problem change it.

### Closing Notes

Obviously, I do not stick to industry norms when it comes to things and since I already have a vscode UI, why not squeeze more out of it. Ontop of visually see what colors do what and where, I've also added options to change several elements in the ui itself as well. For example, toggling breadcrumbs, minimap, and a long list of other UI manipulation features that are found in vscode.

The theme builder is up and does all the points listed above. Just don't mind the tailwind section as I use it to build more complicated than normal components by putting them through there paces over several examples. So if you see some components that are kind of messed up thats why but I hope the awesomeness of the theme builder as a whole makes you overlook that.

---

 



## React/Tailwind Sandbox




Live development environment for designing and testing React components with Tailwind CSS.

**Access:** Web GUI

**Features:**
- Monaco editor integration
- Hot reload for instant feedback
- Dynamic component dock
- Component library integration
- Export functionality
- Custom sandbox config files
- Real-time preview
- Isolated testing environment

**Perfect For:**
- Component prototyping
- Tailwind experimentation
- Quick UI testing
- Design iteration


## VSCode Commands Cheat Sheet

Comprehensive reference guide with 360+ commonly used VSCode commands.

**Access:** Reference menu

**Features:**
- Browse complete command list
- Search and filter by category
- Quick copy functionality
- Organized by command type

![VSCode Commands Reference](https://raw.githubusercontent.com/8an3/midgardr-notes/main/reference/vscode-cmds-reference.jpg?raw=true)

---


## Color Wheel

Advanced color picker with multiple format outputs, inspired by ShadCN design.

**Access:** Web GUI

**Features:**
- Interactive color selection
- Multiple format outputs (HEX, RGB, HSL)
- Copy to clipboard
- Real-time preview
- Color palette generation

![Color Wheel](https://raw.githubusercontent.com/8an3/midgardr-notes/main/shadcn/color-wheel.jpg?raw=true)

---


---

## Tailwind Converter

Convert Tailwind CSS classes between v3 and v4 with ease.

**Access:** Web GUI

**Features:**
- Bidirectional conversion (v3 ↔ v4)
- Bulk class conversion
- Syntax highlighting
- Copy converted output
- Migration assistance

![Tailwind Converter](https://raw.githubusercontent.com/8an3/midgardr-notes/main/tools/tailwind-converter.jpg)

---
