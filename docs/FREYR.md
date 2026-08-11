# FREYR

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;">  VANILLA TAILWIND

Tailwind as a portable CSS primitive that you can instantiate anywhere a JS runtime exists.

Remix routes, Express servers, inline HTML templates, any environment where you just need CSS output without caring about how it got there. This opens it up to a much wider scope — static site generators, email templates, server-rendered apps that don't want the Tailwind toolchain as a dependency, lightweight microservices that spit out HTML, even just rapid prototyping where spinning up a full Tailwind config is overkill.

> [!NOTE] 
>
> I'm apparently a glutton for pain... As I was coding this into one of my own features, I just started getting paranoid that... maybe the implementation was missing a few outliers I'm using or would want... Before now I will admit, it was a bit hacky as the majority of it was written hastily but it worked and at the time, I did not think this would get the amount of use it would or will be getting since I had thought it was only going to be used for a single use case... sigh... SO, as you know, I'm not one that typcailly shrugs and says good enough and moves on. It has been entirely re-written, covering, I beleive 95% of tailwind but instead of manually typing or copying data into the function, I have reacreated each section using functions and math to ensure that nothing is missed. 
> 
> In addition to that, there are more than several areas that go above and beyond what tailwind does out of the box for example expanding on animations.
>
> Also added the entire color wheel for all color utillities.
>
> ... sigh, in addition to that, this is gonna suck for me... but be fucking great for literally everyone else. If you have already used the tailwind preset ngin, you already know just how easy it is to set up and just how far and wide its abilities go in terms of total configurations that can be achveived, currently I think the preset ngin is at 40,060 configurable options... this too... is going to be in the implementation with a couple of additions since the scope is outside of tailwind and react. This is gonna suck, lol but it takes it from 40,060... without a calculator, 120,180 configurable options.
>
> SOO, despite looking slightly different n terms of its code, it will work virtually exactly the same to maintain consistency despite working in an entire different enviroment, just set the specified values and off you go!
>
> Customizing this time around I did make it easier to accomplish while at the same time, by coding it in such a way where... the second you look at it, it makes sense. and its clear as to what you need to do depending on how deep down you want to go into the rabbit hole of custumization. 
>
> All in all, despite this now being a recreated variant of the preset ngin... I honestly think this version is even more powerful as you are not bound by a react app in order to use it. You do NOT need taiiwind, or postcss or any of the other configuration hoops you need to expertly acrobat your ass through in order for it to work.
>
> USAGE: 
> 
> 1. Triggering the function will create a file with the ngin in it, in your workspace root
> 2. either leave it where it is to use, or move it to a more appropriate spot based on your apps file configuration
> 3. call the class in your web pages html style section
> 4. not required as the ngin contains default values for each of the configurable options, but you are free to set them to whatever value you desire
>
> And that is it my friend. No required accompanying libraries, and / or their required json config files. No required libraries to install. TO MAKE IT EVEN BETTER, just to use it with its defaults, is literlly 2 steps that a person on their very first day of coding could accomplish. Could it really be that simple?! Yes... yes it can tailwind.
>
> It's already done and finished... but I'm coming back to it. I did in fact not bring over the little box "ui" where it has the descriptions and is where you change the values that are set into the ngin to configure... but I think I will also bring that over. After working with it a little... it is FAR easier for someone to look at that "UI" container, quickly discern what it is they need to do along with digesting the provided information, because the class... is anything but small. Even though I coded it in a way that everything that you would be changing is placed first in the class, categorized by region wrappers... the difference in not just usability but it does offer a much better ux... like it actually does since you have all the configurable options and what each option can contain and what it does, is just right there and you never even have to enter the actual codes functions in order to configure it... it cannot get any easier than this within the context and its confines that it is in. So because of that, that "UI" will be implemented but expanded upon since this ngin version does contain more options to configure.

#### Usage Exmaples

- If using in a webview or within a function that create the pages html
```html
<style>
  ${new VanillaTailwind().VT()}
</style>
```

- Or server side in something like a Remix/Express route:
```jsx
const vt = new VanillaTailwind()
const css = vt.VT()

export const loader = () => new Response(css, {
  headers: { 'Content-Type': 'text/css' }
})

// OR 

const vt = new VanillaTailwind()
vt.THEME = 'Deep-Void'
vt.PRESET = 'MODERN'
vt.FONT = 'Geist'
vt.MODE = 'dark'
vt.ENVIROMENT = 'OTHER'

const css = vt.VT()

export const loader = () => new Response(css, {
  headers: { 'Content-Type': 'text/css' }
})
```

- Or inline it directly into your HTML template:

```jsx
const html = `
<!DOCTYPE html>
<html>
  <head>
    <style>${css}</style>
  </head>
  <body>...</body>
</html>
`
```

To ensure that you are not reintializing the class and the css every single page render, for example my current use case comprises of a vscode extension that uses webviews. I declared the class in my activate function, and pass the css string into any function that requires its use, essentially unlocking tailwind css across an entire app that does not have it or react installed.

```tsx
const vt = new VanillaTailwind()
const cachedCSS = vt.VT()

...OnboardingCommands(ctx.context, cachedCSS),
...FreyrCommands(ctx.context, cachedCSS),

```

To keep file size down and without the use of a compiler for this feature, here is a breakdown of exactly what is not covered in this feature that you would need to code in your css manually. the tldr is this feature covers 90-95% of tailwinds features but covering 99% of what is commonly used from the library.

While using, there has only been a single case now where I needed to manually include some css, didn't "need" it but wanted it as it was something to the effect of px-[223px] otherwise it covers everything that we typically use.

## Responsive Prefixes

Tailwind's JIT generates responsive variants on demand for **every** utility class. VanillaTailwind includes static responsive prefixes (`sm:`, `md:`, `lg:`, `xl:`, `2xl:`) for the most commonly used utilities:

- Display (`flex`, `grid`, `block`, `hidden`, etc.)
- Flex & Grid (`flex-col`, `flex-row`, `grid-cols-*`, `col-span-*`, etc.)
- Spacing (`p-*`, `m-*`, `gap-*`)
- Sizing (`w-*`, `h-*`)
- Positioning (`relative`, `absolute`, `top-*`, etc.)
- Alignment (`items-*`, `justify-*`)

**Not covered responsively:** color utilities, typography scale, border utilities, shadows, opacity, transforms, and any other utility not in the list above. For those you will need to write your own `@media` query manually.

## State Variants

Tailwind generates state variants on demand for every utility. VanillaTailwind includes static state variants (`hover:`, `focus:`, `active:`, `disabled:`, `checked:`, etc.) scoped to the most commonly needed utilities — primarily colors, opacity, shadows, transforms, display, and cursor.

**Not covered as state variants:** the full spacing scale, the full sizing scale, typography utilities, border radius, and any utility not in the pre-built state variant list. For those write CSS directly.

**Supported states:** `hover`, `focus`, `focus-within`, `focus-visible`, `active`, `visited`, `disabled`, `checked`, `required`, `invalid`, `valid`, `placeholder-shown`, `read-only`, `first`, `last`, `odd`, `even`, `first-of-type`, `last-of-type`, `only-child`, `empty`, `not-disabled`

**Supported group/peer variants:** `group-hover:`, `peer-checked:`, `peer-focus:`, `peer-disabled:`, `peer-placeholder-shown:`

## Dark Mode Variant

Tailwind supports `dark:` as a variant on any utility. VanillaTailwind includes `dark:` variants scoped to the same pre-built utility list as state variants above. Dark mode theming itself is handled at the `:root` / `.dark` CSS variable level — which means in practice you rarely need `dark:` prefixed classes at all since colors reference CSS variables that swap automatically.

## Arbitrary Values

Tailwind supports fully arbitrary values on any utility at build time, e.g. `w-[437px]`, `text-[#ff6600]`, `mt-[13px]`. VanillaTailwind covers arbitrary px values across common ranges:

- Sizing: `0–800px` in steps of 4, plus common breakpoint values up to `1920px`
- Spacing: `0–200px` every 1px, `204–400px` every 4px
- Font size, border width, border radius, blur, rotation, scale, duration, grid columns

## Variant Stacking

Tailwind supports stacking variants, e.g. `sm:hover:bg-primary`, `dark:focus:border-ring`, `group-hover:md:flex`. VanillaTailwind does not support stacked variants. Each variant prefix works independently only.

## JIT-Only Features

The following Tailwind v3 features require the JIT compiler and are not available in VanillaTailwind:

- `aria-*` variants (`aria-expanded:`, `aria-selected:`, etc.)
- `data-*` variants (`data-[state=open]:`, etc.)
- `supports-*` variants
- `has-*` variants
- `before:` / `after:` pseudo-element variants
- `selection:` variant
- `file:` variant (file input button styling)
- `marker:` variant
- `placeholder:` variant (as a prefix — `placeholder-*` color utilities are included)
- `nth-*` variants
- Fully dynamic arbitrary variants

---

## What Is Not Different

Everything else matches Tailwind v3 exactly — every utility class name, every value, every color, every spacing step, every sizing keyword, flexbox, grid, typography, borders, shadows, filters, transitions, animations, transforms, and all extended utilities. If a class exists in Tailwind v3 docs and is not listed above as a limitation, it exists in VanillaTailwind with the same name and behavior.

Due to the inclusion of the "UI" within the file, this concludes the docs for this feature because any and all information required to use the feature will be at the top of the file, other than the actual documentation to using tailind class names. At this time refer to [tailwinds site](https://tailwindcss.com/docs/aspect-ratio) because I just simply do not have the time to basically re-create what is already covered on their site.


Forgot to mention this, but radix-ui's use of 'data-' in its components and others is covered for in the css so that if you were to include any of its components, you will be fine doing so. It goes the same for shadcn components, apart from the ones that need react obviously.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Color Wheel

Using the color way more than I thought I ever would, I have started to annoyed with the fact that I have to leave VSCode to use it. So... were solving that problem.

There will be 2 versions made, the first being your typical color wheel, but more compacted and displaying the colors vertically. The same design thats on the components site because due to its compact styling, it very neatly fits ona single web page without scrolling.

The second version is ripping apart my color wheel picker, essentially its a different take on a color picker. For a lot of use cases, color pickers just suck. A while back I created a popover that contained the entire color wheel with some nice animations, and whenever you hovered over an of the colors it would display the name and the current color number you were hovering that when clicked on copies the color into the state.

Because it has to fit in a popover without looking stupid, this version is extremely compact, but actually looks... really nice, more than most full page colors wheels that I've seen anyways. Because of just how compact it is, it will fit really nicely in the sidebar with room to spare, for the following feature.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Color Picker

> If this does not prove... just how devoted I am to the end user experience and the processes that are needed to be carried out by the user in order for the end user to do whatever it is that you built for them and the processes needed in order to accomplish whatever the mouse maze you set up for them... I do not know what would demonstrate it more. Day... 3, I've lost count on how many different ways I have tried to make this happen. What exactly am I trying to accomplish?
>
> Press the eye dropper button, in vscode.
>
> Which activates the eye dropper (that is not in vscode due to the sandbox your a jailed in...)
>
> Click on a color, anywhere on your screen 
>
> It then places that color in your clipboard based on whatever format you had selected and thats it, and there will be a shortcut that triggers this as well. 
>
> The issues... the sandboxes... they're every where. If this were anyone else, they would have gotten to the third attempt and be like... looks like the user is going to have this feature... only within the confines of vscode... and call it a day. Which is exactly what I do not want. As I too am going to be using this. Are there eye droppers out there yes... but they all fail horribly at some point in this process but all of them atleast... accomplish one of these steps. A lot of them, tbh... that's as far as it goes haha. 99% of them fail when it comes to capturing the color and what happens next, and this is where you can tell where someone put the time in to ensure that the process is as smooth as possible and and does not inhibit the users actions or process in any form. Because once you capture that color, you should be able to quickly paste it, trigger the shortcut and your back at capturing the next color. If a color picker makes it to the end of the list, this is where they fail.
>
> SO it should just be trigger, capture, paste... trigger, capture, paste... trigger, capture, paste... its a simple fucking tool with a really simple fucking process, but it shows that the second theres friction people just shrug and go... meh its good enough.
>
> IT IS EXACTLY, this type of thinking... that decimates end user effeciency, because while that person shrugged it off... so did the next 10... and now it starts to compound. At the end of the year, your wasting... not days, not weeks... months... actually wasting months of end users time. Now lets compound that again for every single employee in the company. It's not about doing it right, its not even about the ux really... if you do not do this, the cascading effect is so monumental it quickly enters the realm of what you think is actually impossible. I have crunched these numbers so many times, because of exactly that. Thinking I did the math wrong, or I added an extra 0 or two somewhere. Only to find out after the 115 recalculation... no, thats the number. In reality, in this day and age of technology... this is probably one of the biggest contributing factors to underpaid employement, businiess bankruptcy, and so much more. The only reason I say probably, is because I haven't done the math on the other contributing factors to the extent that I have with this. And if you think I'm crazy, thats fine... That just tells me, you have not yet done the math.

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> VSCODE & TAILWIND STYLING

- [Themes](#themes)
- [VSCode & Tailwind Theme Builder](#vscode--tailwind-theme-builder)
- [Blacked Out](#blacked-out)
- [Blued Out](#blued-out)
- [Window Differentiator](#window-differentiator)
- [Reset - Window Differentiator](#reset---window-differentiator)


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Themes

> [!NOTE] 
>
> Whether you opt in to choosing a registered theme or providing your own custom theme through workbench.colorCustomizations, these are now set in the workspace settings.json file. Where as previously everything was set at the global level, which allows for even further customization in terms of a globally set theme and themes set with a workspace context. 
> 
> This has been mentioned previously but will mention it again here incase you missed it, along with workbench.colorCustomizations the following values are only set at a workspace level, workbench.iconTheme ( registered file icon theme packs ), workbench.colorTheme ( registered theme packs ), workbench.productIconTheme ( registered product icon theme packs ). The only way this would necessitate a change is if these three values, or any value on its own, can only be set a global level.
>
> Another recent change that has been put in place whenever you install the extension or open a new workspace, settings like registered theme, font, font size, minimap, breadcrumbs, and other "more frequrently toggled" items will transfer over and be placed into the new layout config object placed within the workspace config. As each new workspace you open the workspace config will come pre configured with a layout object to make the process easier of creating a workspace context layouts while at the same time keeping your beloved themes and fonts intact and carry them over for you.
>
> This won't effect new users or users opening new workspaces, but if your workspace currently does not have a layout it previously just returned the function... unintentionally crashing out all the features loading in after it. Instead if this were to happen, where it doesn't scan a config object in either the workspace or global config it will create a empty layout object to "build" the layout from, which obviously won't build anything as it contains nothing, but will stop the function from crashing out features loading after it.


Didn't realize it was this many, but 38 comprehensive dark themes have been registered and can be activated via the file context menu under themes found within the preferences submenu.

Currently there are no light themes registered, but I may add 38 light counter parts in the future as I'm unsure if they are even worth the time considering that devs typcically favour the dark flavour. 

However, each of the themes includes token colors. After creating them all I had found out there are also tokens for semantic highlighting and others... Well that's annoying. I fucking hate when resources talk about a subject but leave large portions of data out. 

No matter, each theme will cover the following sections as I now have to go back through all 40 of them to include them:

* languages: js, jsx, ts, tsx, python, html, css, json but where applicable file extensions were left out so as to cover all file types instead
* semantic highlighting rules 
* specfic token types to emphasize function variables, keywords, etc

The new count being 40 due to adding two more of my personal themes. These themes are a lot different in my opinion than the typical theme found in among the marketplace listings and convey a lot more "professional" looking UI than your typical "professional" theme due to the fact that all random over overstated colors that are typcaily sprinkled around virtually every single theme, have been removed or left out. 

For example blued-out features a dark blue theme throughout with borders consisting of a blue tinted grey. The text colors also go against the norms, where all text in the ui aside from the text found in the editors is muted-foreground, while the editors receive the foreground counter-part. Thus the end result, is a theme in which it has very little distractions in terms of different parts of the ui always trying to grab your attention. If this theming style appeals to you I highly suggest adding the following values to your global settings files:

- "git.diffEditor.renderGutterMenu": false,
- "git.decorations.enabled": false,
- "scm.diffDecorationsGutterAction": "none",
- "scm.diffDecorations": "none"

These settings remove all the dabs of color ( or I would label it as unicorn puke ) that github places in among the different parts of the ui including tabs, explorer pane, gutter, etc. 

The end result is a nice user interface that gives off the least amount of light while not sacrificing anything where it is important. If you suffer from headaches, eye pain, or get exhausted whenever you use a computer for long periods of times, than this theme, along with blacked-out, are two you should most definitely try out. Personally, I never suffered from the mentioned issues but I had noticed I was able to work a lot longer then I could typically, hours and hours longer. After using the two themes for over a year, I've noticed I'm now getting effected by those issues, since these themes have such an understateted tone to them ( or overall light exposure being blasted at you via your monitor ) in comparison to the average user interface. To the point that I can no longer use the average work station anymore. So, if they have made me accustemed to receiving less light exposure, then they will most definitely help you with those issues as well.

If you want to take it a step farther and you use minimaps like myself, than I would also suggest trying this minimap configuration:

- "editor.minimap.maxColumn": 50,
- "editor.minimap.showRegionSectionHeaders": true,
- "editor.minimap.showMarkSectionHeaders": false,
- "editor.minimap.autohide": "mouseover",
- "editor.minimap.showSlider": "mouseover",
- "editor.minimap.side": "left",
- "editor.minimap.size": "fill",
- "editor.minimap.renderCharacters": false,

The end result places the mini map on the left side with a smaller width than what is set by default with the rendered minimap text hidden from view unless hovered over. Whenever the minimap is not in use, the editor just has a slightly fatter gutter that now acts as a quick way to navigate files due to the fill value making it less of a scrolling type feature and more like a function that quickly lets you navigate the file in its entirety. I'll admit, if you do not already use the minimap on the left side, it will take some time getting used to but when you think about it you will see the benefits make it worth it for the following reasons: 

- your cursor is typically placed more to the left of the editor than the right, making it less of a journey to reach the minimap 
- whenever you have multiple editors up, for example using one file for reference ( the right editor ) while coding in another ( the left editor ). Makes it so that the coding editors scroll bar and the references minimap are literally right beside eachother and with ease can navigate the two files by using both
- there are more but I'd rather not convey more of the anal-retentive nerd image I seem to paint myself with

Blacked-out was made with the same design ideas as blued-out.

> [!NOTE]
>
> FEB 7, 2026: As I was waiting for some things to load I added... And for some reason I can't remember the total, and I'm not going back to count again... Lets just agree to agree that the new total count is between 50-55. Doesn't matter at this point really what the total is now because before adding these it was already a rediculous amount in comparison to the marketplace average... of 1 per extension. Noticed there were some gaps missing in comparison to whats available on the color wheel, and had some time to kill so I added a 80's miami theme as well. lol, its god awful but who knows, maybe someone out there may love it since its so loud. I can tell you one thing, it would def stop me in my tracks if I were walking by your station and saw that out of the corner of my eye and say, "what the f...", so if that's what your going for, than this is the theme for you.
>
> FEB 8, 2026: An update... to the previous update, lol. 
> There are now 140+ total themes to choose from. This total comes from 70 themes that all contian themed color tokens and semantic color tokens. Personally, I don't like the themed syntax highlighting but I know there are people out there that will go nuts for it, sitting there frantically clapping their hands together the first time they lay eyes on it. At the same time I know there are people, like myself, who do not want that. 
> 
> FEB 10, 2026: For each of the provided themes there is a "base" variant, that uses vscodes default dark syntax highlighting in place of the themed version because I was quite jealouse due to the themes turning out... way better than expected and not being able to use any of theme. The moment I tried coding with any one of theme since I tried multiple themes to find a syntax hightlight theme I could live with but trying each of them, I was like, "NOOPPEE". I'm pretty sure somewhere above I said this feature would get even more rediculous compared to the competing marketplace offerings, well I told ya so. Who knows there may be one out there, but the themes I've seen and installed... for some reason I've not once seen a theme that offered both a syntax theme and a default version of it without it. It's weird, as I continue to code I find a lot of features that I would consider to be the industry norm / default way of doing things, only to find out that even paid options don't even offer the same feature parity.
>
> FEB 11, 2026: As I was building my own theme completely from scratch I have noticed, I wasn't including as many items to each theme as I could have. This update... will take me a while since each theme will be almost tripling in size. Theres nothing wrong with the current themes, they're fucking great. It just bugs me knowing that, I could easily do better, albeit taking a while to complete. Not only will each theme look great given its base colors that are already set out in each theme, but every single theme will have the same level of depth with attention to detail.
>
> And I'll admit, I'm trying to cheat as much as I can by getting ai engines to help with this task but due to the size of the themes, they are becoming quite token heavy and can only complete a couple at a time, while I also manually edit them as well. Speaking of which, just burned through another quota and have to wait another 3 or so hours before receiving help again with this task, fuck I'm not even half way through, sigh that sucks, lol
>
> 



## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Blacked Out

Ultra-dark theme preset for VSCode with deep black backgrounds and optimized contrast.

**Access:** Settings Dropdown → Select option

**What It Does:**
- Applies ultra-dark theme configuration
- Sets theme for active workspace
- Optimized for reduced eye strain
- Perfect for dark environment coding

![Settings](https://raw.githubusercontent.com/8an3/midgardr-notes/main/config/settings.jpg)

---
## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Blued Out

Dark blue theme preset combining deep blacks with subtle blue accents.

**Access:** Settings Dropdown → Select option

**What It Does:**
- Applies dark blue theme configuration
- Sets theme for active workspace
- Blue-tinted dark interface
- Alternative to pure black themes

![Settings](https://raw.githubusercontent.com/8an3/midgardr-notes/main/config/settings.jpg)

---

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Window Differentiator

Color-code multiple VSCode windows to easily distinguish between different projects.

**Access:** Settings Dropdown → Select option

**Features:**
- Assign unique colors to each VSCode window
- 20+ color variants available
- Different color applied each time triggered
- Perfect for managing multiple projects
- Quick visual identification

![Settings](https://raw.githubusercontent.com/8an3/midgardr-notes/main/config/settings.jpg)

---

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Reset - Window Differentiator



Restore default VSCode window colors and remove custom window differentiation.

**Access:** Settings Dropdown → Select option

**What It Does:**
- Removes custom window colors
- Restores default VSCode appearance
- Resets all window color assignments

![Settings](https://raw.githubusercontent.com/8an3/midgardr-notes/main/config/settings.jpg)


---

[🡄 Return](https://github.com/8an3/DevStack)


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Product Icons

This now grants the ability to change product icons, file icons and themes on a workspace context level. 

### Manually
Currently, you can do this manually as it is already coded into the ngin.

You can now set a registered product icon theme explicitly through the following setting:

```json
{
  "productIconTheme": "baldr-icons",
}
```

Placement is at the root level of the args object alongside customizeLayout and others.


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> File Icons

### Manually
Currently, you can do this manually as it is already coded into the ngin.

You can now set a registered file icon theme explicitly through the following setting:

```json
{
  "fileIconTheme": "baldr-icons",
}
```

Placement is at the root level of the args object alongside customizeLayout and others.

