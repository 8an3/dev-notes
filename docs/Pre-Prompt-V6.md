# Catalyst Pre-Prompt v5.0 - Overview / Breakdown of capabilities
1. Output consistency - across engines, sessions, users
    - example: creating a components library, ensuring all reuseable components are built employing the same build process, across sessions, instances and even engines
2. Reproducibility - same input = same output, always
3. Context persistence - state that carries across sessions
    - example: no matter which instance, session or engine it will always have the data it needs at all times, as if it were just one continuous instance
4. Cumulative knowledge / Gain experience
   - example: ai engines now have the ability to recall and use functions it exported in previously created files, which now opens the door for much, much larger projects 
   - example 2: the ability call previously created variables that consist in any manner allowing it to resuse the same data structures it created for other parts of the application
5. Enterprise scalability - McDonald's-level consistency at any scale
6. Debug AI Outputs - gives user the ability to view whenever a engine makes a assumption regading a decision it needed to make to provide the answer. Till now, you couldn't tell what the ai was doing exactly, never mind whenever it had to assume some information in order to provide that output. When an assumption is wrong in one instance, it will continue to make that same assumption, that the user doesn't even know its making, thus get frustrated with the engine making the same mistake, all the while not even telling the user... anything to this regard leaving the user perplexed on why something didn't work
7. In-Real Time Patch Fixes
8. Unlocked Abilities
9. One single pre-prompt at the start of an instance, will dictate the ais behaviour for the remainder of that instance. This has been a benifit that was evident through testing. Thus saving the user on its overall instance quota and providing a more effecient workspace while working on a single "problem" or "function" within an app
10. ui is made to make the process as easy as possible no matter the skill or experience level
    - easy as click what you want
    - add ai instructions on what you want it to help create
    - copy
    - paste into prompt

## V5 Patch list
- claude has a bug where it clear some or all of its value  in the ui. mainly in the code review area forget the name but it has something to move data around and he bugs out... what could we say to him in the pre prompt that would refrain him from using this function 

# Catalyst Pre-Prompt v5.0

## DEFAULT SECTION ( TO BE USED WITH ALL DEFAULTS)

### IMPORTANT READ FIRST
YOU ARE NOT ALLOWED TO START PROVIDING AN ANSWER TILL AFTER YOU HAVE READ ALL THE DATA IN THE PROMPT THAT I HAVE SENT, IN ITS ENTIRETY. NO MATTER HOW COMFORTABLE YOU IN MOVING FORWARD AND PROVIDE AN ANSWER, YOU ARE NOT ALLOWED. YOU HAVE TO READ THIS FIRST... THEN ONCE YOU HAVE COMPLETED THIS TASK OF READING THIS, THEN, AND ONLY THEN YOU CAN START TO PROVIDE THE ANSWER. THIS IS SO YOU OBTAIN ALL THE INFORMATION YOU NEED FOR THE ANSWER YOU ARE TO GIVE

### General
- do not output any other extra comments or "talking points", only provide the output of the code I am asking for 
  
### Platform & Technology Stack
- **Framework**: Remix Run v2 (use loaders, actions, and Remix hooks)
- **Styling**: Tailwind CSS v3 (semantic classes ONLY: bg-background, text-foreground, border-border, etc.)
- **Component Library**: shadCN Components
- **Icons**: lucide-react
- **Tailwind.css Path**: ~/styles/tailwind.css
- **json import Path**: @remix-run/node
- **Primsa Path**: ~/modules/libs/prisma
- **Utilities Path**: ~/components/catalyst-ui/utils
- **Components Path**: ~/components/catalyst-ui/components
  - Correct: 'import { Button } from "~/components/catalyst-ui"'
  - Wrong: 'import { Button } from "~/components/catalyst-ui"'
- **cn Path**: import { cn } from '~/components/catalyst-ui/utils'
- **cva, type VariantProps Path**: import { cva, type VariantProps } from 'class-variance-authority'

### Absolute Code Standards
- **Function Declaration**: Use \`export function ComponentName()\` NEVER \`const ComponentName = () => {}\`
- **Default Exports**: No default exports in any file
- **Comments**: Do not leave comments in code
- **Color Values**: Never use hard-coded colors (no #hex, no rgb(), no color names)
- **Remix Patterns**: Utilize Remix loaders, actions, and hooks throughout
- **DO NOT Rename Variables / Components / Functions**: Use the same name that I use, regardless of what it is

### Critical Functional Requirements
All interactive features MUST be fully functional and working:
- Search inputs must actually search/filter data
- Filter controls must actually filter results
- Sort buttons must actually sort data
- Loading states must represent real async operations
- No placeholder functionality
- No dummy/mock implementations
- If a component has interactive elements, those elements MUST work in the context they are used.
- No "TODO" or "implement this later" code
- Form submissions must handle data
- Buttons must have real onClick handlers with logic
  - unless the button is used within remix's Form or fetcher.Form component
  - if those features are not used, then the following form example must be used along side any other functionality that needs to be triggered when that form is submitted, this format  your more than welcome to create a function before the return statment to define this  
```tsx
const fetcher = useFetcher()
const formData = new FormData();
formData.append("id", item.id);
formData.append("intent", "deleteProgress");
fetcher.submit(formData, { method: "post" });
```

### Catalyst UI / shadCN Component Usage (READ CAREFULLY)
DO NOT recreate any shadCN components that already exist.
Use existing shadCN components from the library.

### **Available Catalyst UI / shadCN components, import them, do not build them (DO NOT RECREATE):**
Accordion, Alert, Alert Dialog, Aspect Ratio, Avatar, Badge, Breadcrumb, Button, Button Group, Calendar, Card, Carousel, Chart, Checkbox, Collapsible, Combobox, Command, Context Menu, Data Table, Date Picker, Dialog, Drawer, Dropdown Menu, Empty, Field, React Hook Form, Hover Card, Input, Input Group, Input OTP, Item, Kbd, Label, Menubar, Navigation Menu, Pagination, Popover, Progress, Radio Group, Resizable, Scroll Area, Select, Separator, Sheet, Sidebar, Skeleton, Slider, Sonner, Spinner, Switch, Table, Tabs, Textarea, Toast, Toggle, Toggle Group, Tooltip, Typography 

## REMIX-RUN ROUTE SECTION ( TEMPLATE )
- **Action**: if it needs one:
```jsx
export async function action({ request }: ActionFunction) {
    const d = Object.fromEntries(await request.formData());
    const intent = d.intent
    if (intent === 'submitContactUs') {
            await prisma.contactUs.create({
                data: {
                    name: d.name,
                    email: d.email,
                    message: d.message,
                }
            })
        return json({ success: true})
    }
    return json({ success: false})
}
```

- if we need to use an action that intakes data from a form this is how it will be done:
```jsx
const d = Object.fromEntries(await request.formData());
```
- a page is allowed to have more than one form action, each form action needs to include an intent
    - the intent value will be accesssible in the action via:
```jsx
const intent = d.intent
```
- **form values**:  will be accesssible in the following formatted examples:
  - d.name
  - d.email
  - d.message
- **each forms intent**: will be encased in a if statement that will end with:
  - return json({ success: true, })
  - the true statement to be followed by any other values needed to be pushed back to the page through the use of a fetcher
- **User variable**: to be used within every action / loader:
```jsx
import path: import { optionalAuth } from "~/routes/userAuth"
// when calling and setting the user value: 
const { user } = await optionalAuth(request);
```

- **Loader**: if it has one, requires the following as a minimum to be loaded into the default function:
```tsx
const { user } = await optionalAuth(request);
return json({ user })
```

- **Meta**: required in route files:
```jsx
export const meta: MetaFunction = () => {return [{ title: "Catalyst Software" }, { name: "description", content: "Catalyst Software" }]};
```

- **links: LinksFunction**: required in route files:
```jsx
import ZapSVG from '~/components/images/icon.svg'
export const links: LinksFunction = () => [{ rel: "icon", type: "image/svg", href: ZapSVG }];
```

## REUSABLE COMPONENTS SECTION ( TEMPLATE )
- **Function Declaration2**: Use \`const ComponentName = () => {}\` NEVER \`export function ComponentName()\`
- **Default Exports**: No default exports in any file
- **Comments**: Do not leave comments in code
- **Color Values**: Never use hard-coded colors (no #hex, no rgb(), no color names)
- **Remix Patterns**: Utilize Remix loaders, actions, and hooks throughout
- **DO NOT Rename Variables / Components / Functions**: Use the same name that is used, regardless of what it is
- **Export all functions at the end of the file**: example:
```jsx
export {
    button, 
    ButtonVariant
}
```
- **All interactive features MUST be fully functional and working**: for example:
  - Search inputs must actually search/filter data
  - Filter controls must actually filter results
  - Sort buttons must actually sort data
  - Loading states must represent real async operations
  - No placeholder functionality
  - No dummy/mock implementations
  - If a component has interactive elements, those elements MUST work in the context they are used.
  - No "TODO" or "implement this later" code
  - Form submissions must handle data
  - Buttons must have real onClick handlers with logic
    - unless the button is used within remix's Form or fetcher.Form component
    - if those features are not used, then the following form example must be used along side any other functionality that needs to be triggered when that form is submitted, this format  your more than welcome to create a function before the return statment to define this  
```tsx
const fetcher = useFetcher()
const formData = new FormData();
formData.append("id", item.id);
formData.append("intent", "deleteProgress");
fetcher.submit(formData, { method: "post" });
```
- **Mimic Building Technique**: Build components using shadCN's exact architectural patterns
- **Props Default Values**: All props must have sensible default values to minimize end-user configuration, so we need to provide defaults
- **DO NOT JUST FOR THE SAKE CREATE PROPS**: Only create props when needed, do not create a long laundry list of made up on the spot props
  - NOTE: these are examples and does not by any means put any resrictions when providing a default value to a prop, the idea and reasoning behind is to take away as many steps from the user in order to implement something, allowing the user to implement easier. less errors in implementing due to not providing the props they needed to, mastery of learning to use the component in its basic form, thus allow the user to learn more components in a short window of time. For example:
    - variant: default, outline, ghost, destructive
    - size: sm, md, lg
    - align: left, center, right
    - color: primary, destgructive, warning, success, failure, 
    - disabled: true: false
    - value
    - text
    - subText
    - state
    - label
    - direction
    - title
    - desc ( other name used: desciption )
- **Support variants**: via props when multiple styles are applicable
- **Always accept and merge className**: prop for style overrides
  - for merging styles, use cn as it safely solves virtually all issus when not using cn
  - example useage:
    1. \`className={cn(buttonVariants({ variant, size, className, align }))}\`
    2. \`className={cn("absolute left-0 block transition-all duration-300 ease-in-out rounded-full", "bg-current")}\`
    3. \`className={cn("absolute left-0 block transition-all duration-300 ease-in-out rounded-full",\`
          \`if page.view === true ? "bg-background" : "bg-desctrucive" ,    \`  
          \`"bg-current"\`
       \`)}\`
- **Support children prop**: when content should be customizable
- **Props interface**: should extend appropriate React HTML attributes
- **Use TypeScript interfaces**
- **FILE SHOULD ONLY CONTAIN THE FOLLOWING**: reusable component ( Including anything that is needed for the reusable component, cva functions, supporting functions, partnering functions ie: tabs also has tabsList, tabsContent and so on), demo function, object for ui components library - ALL to be given within the same file
- **REQUIRED Demo Function**: Demo Code Example
    - naming convention component name follow by Demo like seen in the exmaple
    - 2 examples MAX, no more - no less, unless instructed other wise 
    - the only exception, are reusable components that have variants coded into the component 
      - example:
        - toast - has 45 variants in total and we need to display them
        - which means, a component that has 0 variants the max is 2, you are not allowed to just write code in the demo creating random variants that do nothing other then to waste time and resources... as it does not show, or display the real usage of the code it self in the first place
  ```tsx
  export function ToggleButtonDemo() {
  	const [boldActive, setBoldActive] = useState(false)
  	const [italicActive, setItalicActive] = useState(false)

  	return (
  		<div className="space-y-8 p-6 max-w-2xl mx-auto">
  			<div>
  				<h2 className="text-2xl font-bold mb-4">Basic Toggle Buttons</h2>
  				<div className="flex gap-2 flex-wrap">
  					<ToggleButton
  						checked={boldActive}
  						onChange={setBoldActive}
  						icon={<Bold className="h-4 w-4" />}
  					/>
  					<ToggleButton
  						checked={italicActive}
  						onChange={setItalicActive}
  						icon={<Italic className="h-4 w-4" />}
  					/>
  				</div>
  			</div>
  		</div>
  	)
  }
  ```
- **REQUIRED basicusage section WITHIN UI LIBRARY OBJECT**:
- basicusage Code Example 1 
  - for componets that have a lot of elements that need to be used with in order for it to work
  - for example: 
    - tabs, contextMenu, dropdownMenu, etc
  - will consist of one example only in its most basic form to use the component
```tsx
		basicusage: \`
<Tabs defaultValue="tab1" className="">
  <TabsList>
    <TabsTrigger value="tab1">Account</TabsTrigger>
    <TabsTrigger value="tab2">Password</TabsTrigger>
  </TabsList>
  <TabsContent value="tab1">Make</TabsContent>
  <TabsContent value="tab2">Change</TabsContent>
</Tabs>\`,
```
- basicusage Code Example 2
  - for components that have less elements that need to be used with in order for it to work, 
  - for example: 
    - button, input, buttonlinkstyled, etc
  - will consist of two examples
    - the first being used with 0 props
    - the second being used with all available props, using its default as the value to be provided
```tsx
		basicusage: \`
<ButtonLinkStyled>
	Content
</ButtonLinkStyled>

<ButtonLinkStyled primary  
	to="/"
	variant="outline"
	align="middle"
	size="sm"
	prefetch="intent"
	className=""
	loadingText="Navigating..."
>
	Content
</ButtonLinkStyled>\`,
```
- **REQUIRED props section WITHIN UI LIBRARY OBJECT**: Props Value Example
  - each component has props that need to be seen by the user so each component needs to receive this within the ui libraries object in the follow format
```tsx
const props = {
    props: {
        "Button": [
				{ name: "className", type: "string", default: "null" },
				{ name: "size", type: "sm | md | lg | xl", default: "md" },
			],
        "ButtonLink": [
				{ name: "className", type: "string", default: "null" },
				{ name: "size", type: "sm | md | lg | xl", default: "md" },
			],
		},
}
```
- **REQUIRED ui library object**: to define the object within
- Object For UI Components Library
  - importPath:
    - base to be used in every value ~/components/catalyst-ui 
    - next value consists of the category name
    - next value consists of the sub-category name, if it resides in one
    - file name derived fom the function name, capitals are lower case and a - place infront of them except for the first letter
  - multiImport: if the component contains multiple exports that are used for the function itself
      - example component, tabs
      - format, a comma seperated list contained in double quotes: "Tabs, TabsContent, TabsList, TabsTrigger",
      - null if component does not have multiple exports
  - basicusage: example provided previously
    - only reason for it to remain null, if the code escapes via the use a back ticks and \${ } ie a dollar sign, followed by a open curly bracket
      - if thats the case, provide the source code path, followed by .txt as seen in the example in the usagePath value
  - usage: example provided previously
    - only reason for it to remain null, if the code escapes via the use a back ticks and \${ } ie a dollar sign, followed by a open curly bracket
      - if thats the case, provide the source code path, followed by .txt as seen in the example in the usagePath value
  - source: this value to remain null
  - path: provide the source code path, followed by .txt as seen in the example
```tsx
const uiLibComp = [
	{
		name: "Auth System", // title, similar to the value but replaces - with space, starting and any letter a - capatilized
		value: "auth-system", // comprised of its file name
		importPath: "~/components/catalyst-ui/components/utility/auth-system",
		multiImport: null,
		basicusage: null,
		path: "/components/catalyst-ui/components/utility/auth-system.tsx.txt",
		source: null,
		usagePath: "/components/catalyst-ui/components/utility/auth-system.tsx.txt",
		usage: null,
		lofi: null, // ignore unless instructed
		premium: true, // ignore unless instructed
		category: "UI - Components", // sub category - category
		tags: ["ui", "components", "interactive"], // provide tags relevant to the component
		features: ["Responsive", "TypeScript", "Accessible"], // provide feature values relevant to the component
		dependencies: ["lucide-react", "react"], // list all dependencies
		demo: [<AuthSystemDemo />], // placing the demo as a function, IN THE FORMAT THAT YOU SEE HERE
		props: {
			"Button": [
				{ name: "className", type: "string", default: "null" },
				{ name: "size", type: "sm | md | lg | xl", default: "md" },
			],
			"ButtonLink": [
				{ name: "className", type: "string", default: "null" },
				{ name: "size", type: "sm | md | lg | xl", default: "md" },
			],
		},
		desc: null, // ignore unless instructed
		status: null, // ignore unless instructed
		lastUpdated: null, // ignore unless instructed
	},

];
```
- **Component Code Example**: components example provided from working currently in-production:
```tsx
import React from 'react'
import { cva, type VariantProps } from 'class-variance-authority'
import { cn } from '~/components/catalyst-ui/utils'
import { Slot } from "@radix-ui/react-slot"

const buttonVariants = cva(
  "inline-flex items-center justify-center gap-2 whitespace-nowrap rounded-md text-sm font-medium transition-all disabled:pointer-events-none disabled:opacity-50 [&_svg]:pointer-events-none [&_svg:not([class*='size-'])]:size-4 shrink-0 [&_svg]:shrink-0 outline-none focus-visible:border-ring focus-visible:ring-ring/50 focus-visible:ring-[3px] aria-invalid:ring-destructive/20 dark:aria-invalid:ring-destructive/40 aria-invalid:border-destructive",
  {
    variants: {
      variant: {
        default:
          "bg-primary text-primary-foreground shadow-xs hover:bg-primary/90",
        destructive:
          "bg-destructive text-white shadow-xs hover:bg-destructive/90 focus-visible:ring-destructive/20 dark:focus-visible:ring-destructive/40 dark:bg-destructive/60",
        outline:
          "border bg-background shadow-xs hover:bg-accent hover:text-accent-foreground dark:bg-input/30 dark:border-input dark:hover:bg-input/50",
        secondary:
          "bg-secondary text-secondary-foreground shadow-xs hover:bg-secondary/80",
        ghost:
          "hover:bg-accent hover:text-accent-foreground dark:hover:bg-accent/50",
        link: "text-primary underline-offset-4 hover:underline",
      },
      size: {
        default: "h-9 px-4 py-2 has-[>svg]:px-3",
        sm: "h-8 rounded-md gap-1.5 px-3 has-[>svg]:px-2.5",
        lg: "h-10 rounded-md px-6 has-[>svg]:px-4",
        icon: "size-9",
      },
      align: {
        left: "justify-start text-left",
        middle: "justify-center text-center",
        right: "justify-end text-right",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
      align: "middle",
    },
  }
)

function Button({
  className,
  variant,
  size,
  align,
  asChild = false,
  ...props
}: React.ComponentProps<"button"> &
  VariantProps<typeof buttonVariants> & {
    asChild?: boolean
  }) {
  const Comp = asChild ? Slot : "button"
  return (
    <Comp
      data-slot="button"
      className={cn(buttonVariants({ variant, size, className, align }))}
      {...props}
    />
  )
}

export {  Button, buttonVariants }
```
- **Lo-Fi Code Example**: 
  - naming convention
    - name of function it is representing
    - followed by LoFi
  - building techniques / guidelines to following when creating lo-fi's
    - use atom, it adheres to tailwind theme class variables making it useable in any project no matter the theme difference
    - for that reason do not hard code color values
    - over size of the lo-fi must remain on the smaller side and these are displayed in stuch a context
    - if a list of lo-fi's are provided to build when given instruction
      - each lo-fi must be contain with in its own file
      - due to every lofi having its own file, whatever imports it uses need to be included for example: atom like you see below
```tsx
import { Atom } from "~/components/catalyst-ui/lo-fi/utils/atom"

export function ButtonLoFi() {
  return (
    <div className="flex flex-wrap gap-2">
      <Atom shade="300" className="h-6 w-24 rounded-full" />
      <Atom shade="500" className="h-6 w-20 rounded-full" />
      <Atom shade="200" className="h-6 w-16 rounded-full" />
    </div>
  )
}

```

## TEMPLATE SECTION ( TEMPLATE )
- **Import Tailwind**: via:
  - \`{ rel: "stylesheet", href: tailwind }\`
  - \`import tailwind from '~/styles/tailwind.css'\`

```jsx
import tailwind from '~/styles/tailwind.css'

export const links: LinksFunction = () => [
  { rel: "icon", type: "image/svg", href: ZapSVG },
  { rel: "stylesheet", href: tailwind }
];
```

- **Action**: if it needs one:
```jsx
export async function action({ request }: ActionFunction) {
    const d = Object.fromEntries(await request.formData());
    const intent = d.intent
    if (intent === 'submitContactUs') {
            await prisma.contactUs.create({
                data: {
                    name: d.name,
                    email: d.email,
                    message: d.message,
                }
            })
        return json({ success: true})
    }
    return json({ success: false})
}
```
- if we need to use an action that intakes data from a form this is how it will be done:
```jsx
const d = Object.fromEntries(await request.formData());
```
- a page is allowed to have more than one form action, each form action needs to include an intent
    - the intent value will be accesssible in the action via:
```jsx
const intent = d.intent
```
- **form values**:  will be accesssible in the following formatted examples:
  - d.name
  - d.email
  - d.message
- **each forms intent**: will be encased in a if statement that will end with:
  - return json({ success: true, })
  - the true statement to be followed by any other values needed to be pushed back to the page through the use of a fetcher
- **User variable**: to be used within every action / loader:
```jsx
import path: import { optionalAuth } from "~/routes/userAuth"
// when calling and setting the user value: 
const { user } = await optionalAuth(request);
```

- **Loader**: if it has one, requires the following as a minimum to be loaded into the default function:
```tsx
const { user } = await optionalAuth(request);
return json({ user })
```

- **Meta**: required in route files:
```jsx
export const meta: MetaFunction = () => {return [{ title: "Catalyst Software" }, { name: "description", content: "Catalyst Software" }]};
```

- **links: LinksFunction**: required in route files:
```jsx
import ZapSVG from '~/components/images/icon.svg'
export const links: LinksFunction = () => [{ rel: "icon", type: "image/svg", href: ZapSVG }];
```

- **REQUIRED ui library object**: to define the object within UI Components Library
  - importPath:
    - base to be used in every value ~/components/catalyst-ui 
    - next value consists of the category name
    - next value consists of the sub-category name, if it resides in one
    - file name derived fom the function name, capitals are lower case and a - place infront of them except for the first letter
  - multiImport: if the component contains multiple exports that are used for the function itself
      - example component, tabs
      - format, a comma seperated list contained in double quotes: "Tabs, TabsContent, TabsList, TabsTrigger",
      - null if component does not have multiple exports
  - basicusage: example provided previously
    - only reason for it to remain null, if the code escapes via the use a back ticks and \${ } ie a dollar sign, followed by a open curly bracket
      - if thats the case, provide the source code path, followed by .txt as seen in the example in the usagePath value
  - usage: example provided previously
    - only reason for it to remain null, if the code escapes via the use a back ticks and \${ } ie a dollar sign, followed by a open curly bracket
      - if thats the case, provide the source code path, followed by .txt as seen in the example in the usagePath value
  - source: this value to remain null
  - path: provide the source code path, followed by .txt as seen in the example
```jsx
const uiLibComp = [
	{
		name: "Auth System", // title, similar to the value but replaces - with space, starting and any letter a - capatilized
		value: "auth-system", // comprised of its file name
		importPath: "~/components/catalyst-ui/components/utility/auth-system",
		multiImport: null,
		basicusage: null,
		path: "/components/catalyst-ui/components/utility/auth-system.tsx.txt",
		source: null,
		usagePath: "/components/catalyst-ui/components/utility/auth-system.tsx.txt",
		usage: null,
		lofi: null, // ignore unless instructed
		premium: true, // ignore unless instructed
		category: "UI - Components", // sub category - category
		tags: ["ui", "components", "interactive"], // provide tags relevant to the component
		features: ["Responsive", "TypeScript", "Accessible"], // provide feature values relevant to the component
		dependencies: ["lucide-react", "react"], // list all dependencies
		demo: [<AuthSystemDemo />], // placing the demo as a function, IN THE FORMAT THAT YOU SEE HERE
		props: {
			"Button": [
				{ name: "className", type: "string", default: "null" },
				{ name: "size", type: "sm | md | lg | xl", default: "md" },
			],
			"ButtonLink": [
				{ name: "className", type: "string", default: "null" },
				{ name: "size", type: "sm | md | lg | xl", default: "md" },
			],
		},
		desc: null, // ignore unless instructed
		status: null, // ignore unless instructed
		lastUpdated: null, // ignore unless instructed
	},

];
```

## ERRORS, IMPORTS AND PLUS SECTION ( TEMPLATE )
- Focus ONLY on actual compilation/runtime errors - ignore style suggestions
- also disregard any "small" errors that would not stop complilation/runtime of the application
- Provide specific, actionable fix suggestions
- Explain WHY the error occurs and HOW your solution addresses it
- If there are multiple possible fixes, rank them by likelihood of success
- Be concise but thorough
- if the import error is related to a catalyst-ui library component, 99% of the time the component can be imported by "~/components/catalyst-ui"
- if instructed to auto fix errors, if the error has multiple solutions rank the solutions first and choose the most likely one
- if instructed to auto fix errors, in ai chat keep a record of everything that was done, incase one of the fixes was not successful that way you can provide the user with a report of what was done for them to review and fix

### Critical Functional Requirements
- **All interactive features MUST be fully functional and working**: for example:
  - Search inputs must actually search/filter data
  - Filter controls must actually filter results
  - Sort buttons must actually sort data
  - Loading states must represent real async operations
  - No placeholder functionality
  - No dummy/mock implementations
  - If a component has interactive elements, those elements MUST work in the context they are used.
  - No "TODO" or "implement this later" code
  - Form submissions must handle data
  - Buttons must have real onClick handlers with logic
    - unless the button is used within remix's Form or fetcher.Form component
    - if those features are not used, then the following form example must be used along side any other functionality that needs to be triggered when that form is submitted, this format  your more than welcome to create a function before the return statment to define this  
```jsx
const fetcher = useFetcher()
const formData = new FormData();
formData.append("id", item.id);
formData.append("intent", "deleteProgress");
fetcher.submit(formData, { method: "post" });
```

### Scope Adherence
- Only do what is explicitly asked
- Do not refactor, reorganize, or "improve" code unless specifically requested
- Changing variable names ≠ permission to restructure logic
- Follow the existing pattern/structure exactly

### Continuous Growth and Experience
- Once you have finished and provided the result, I need you to provide the information needed for the next 2 sections, thus giving you access to functions and variables you created no matter what instance it was created in, the two sections are labeled "Available Functions / Components" and "Available Variables"
- format: 
  - function name 
  - location to call function
  - description of what the function has the ability to do, what values will it export to be used where the user uses it. Basically anything you need to know how, what, why, when and where
- example:
  - Button
    - ~/components/catalyst-ui/components
    - a reusable component that can be used within forms

### Array/Object Structure Preservation  
- If data is provided as separate arrays, keep them separate
- If items are listed individually, keep them individual
- Do not consolidate, merge, or deduplicate without explicit instruction

## VSCODE EXTENSION ( TEMPLATE )
### Platform & Technology Stack
- **ANY VALUE OVERRIDES ANY PREVIOUS MENTION OF THAT SAME VALUE**
- **Framework**: VSCode Extension
- **Builder**: Webpack
- **Command Naming Convention**: \`ocrmnavigator.name\` for commands and package.json
 
### Current Dependencies to work with 
- "@babel/types": "^7.24.0",
- "@svgr/webpack": "^8.1.0",
- "@types/cors": "^2.8.19",
- "@types/glob": "^8.0.0",
- "@types/mocha": "^10.0.0",
- "@types/node": "^18.0.0",
- "@types/uuid": "^10.0.0",
- "@types/vscode": "^1.98.0",
- "@vscode/test-cli": "^0.0.10",
- "glob": "^10.0.0",
- "mocha": "^10.0.0",
- "npm-run-all": "^4.1.5",
- "ts-loader": "^9.5.2",
- "tsx": "^3.12.7",
- "typescript": "^5.9.2",
- "url-loader": "^4.1.1",
- "webpack": "^5.98.0",
- "webpack-cli": "^6.0.1",
- "webpack-node-externals": "^3.0.0"

### Absolute Code Standards
- **Command Registration**: Place a comma at the end of each register command instead of semicolon:
  ```typescript
  vscode.commands.registerCommand("ocrmnavigator.openPrePrompt", async () => {
    await vscode.env.openExternal(vscode.Uri.parse(\`\${DEVSTACK_URL}/Catalyst/Pre-Prompt/dashboard\`));
  }),
  ```
- **Helper Functions**: All helper functions will be placed in separate files. When providing code, keep this in mind so you can export the functions and import them into the \`extension.ts\` file
- **Extension.ts File**: When providing code for the \`extension.ts\` file, only provide the register command code. Don't bother coding anything else as I already have it
- **Comments**: Do not leave comments in code unless specifically requested
- **Error Handling**: Include proper error handling for all async operations and VSCode API calls
- **Type Safety**: Use proper TypeScript types, avoid \`any\` unless absolutely necessary

### VSCode Extension Best Practices
- Use VSCode API methods correctly (commands, workspace, window, etc.)
- Properly dispose of resources in the \`deactivate()\` function
- Register all commands in the \`activate()\` function
- Use \`context.subscriptions.push()\` for all disposables
- Follow VSCode extension guidelines for user notifications (info, warning, error)

### File Organization
- **extension.ts**: Command registrations only
- **helpers/**: All helper functions and utilities
- **types/**: Type definitions and interfaces
- **constants/**: Constants and configuration values

### Command Registration Pattern
```typescript
context.subscriptions.push(
  vscode.commands.registerCommand("ocrmnavigator.commandName", async () => {
    // Command logic here
  }));
```

### Output Expectations
- Provide only the requested code
- Include proper imports at the top of files
- Ensure all code is production-ready
- No placeholder or TODO comments
- All functions must be fully implemented

## COMMON NON-DEAFULT SECTION ( NOT A TEMPLATE )

### Scope Adherence
- Only do what is explicitly asked
- Do not refactor, reorganize, or "improve" code unless specifically requested
- Changing variable names ≠ permission to restructure logic
- Follow the existing pattern/structure exactly

### Decision Transparency ( Debug whatever decision it made to produce the wrong result, typically due to an assumption it made )
- When information is ambiguous or missing, explicitly state: "ASSUMPTION: [what I'm assuming] - confirm if correct"
- Before making structural changes, list what I'm inferring vs what was explicitly stated
- If consolidating/simplifying code, ask first rather than assume it's wanted
- When multiple interpretations exist, present options instead of choosing one silently

### Continuous Growth and Experience
- Once you have finished and provided the result, I need you to provide the information needed for the next 2 sections, thus giving you access to functions and variables you created no matter what instance it was created in, the two sections are labeled "Available Functions / Components" and "Available Variables"
- format: 
  - function name 
  - location to call function
  - description of what the function has the ability to do, what values will it export to be used where the user uses it. Basically anything you need to know how, what, why, when and where
- example:
  - Button
    - ~/components/catalyst-ui/components
    - a reusable component that can be used within forms

### Available Functions / Components

### Available Variables

### Patch Fixes

### Variable/Object Naming
- When asked to rename variables/objects, ONLY change the names
- Do not restructure, reformat, or reorganize the data
- Maintain exact same structure, just different identifiers

### Array/Object Structure Preservation  
- If data is provided as separate arrays, keep them separate
- If items are listed individually, keep them individual
- Do not consolidate, merge, or deduplicate without explicit instruction

### Template Compliance
- When a template/example is provided, match its structure exactly
- Same nesting depth, same property names, same data organization
- "Use this format" means replicate the structure, not interpret the intent

### Import Statement Accuracy
- Double-check all import paths match the provided structure
- Never assume a component location - use the exact path given
- If unsure about an import, use the pattern shown in other imports

### Form/State Management
- When localStorage is mentioned, actually implement localStorage (read AND write)
- When fetcher is mentioned, use fetcher.submit() not form submission
- When activeItems/activeCards is the state name, use that exact name everywhere

### Type Consistency
- If database returns Json type, parse it consistently everywhere it's used
- Cast types once at the data boundary, not scattered throughout
- If a variable is string[], don't treat it as string in some places
  
### Context Retention & State Tracking
- Before writing code, mentally inventory: what functions exist, what variables are in scope, what the current schema actually is
- Reference previous code in the conversation to verify what's already been established
- Maintain awareness of the full codebase context, not just the current file
- If uncertain about what exists, ask rather than assume

### Pattern Consistency Enforcement
- Identify the specific implementation patterns in use (Remix loader/action structure, fetcher vs form submission, naming conventions)
- Once a pattern is identified, apply it everywhere without deviation
- One file's pattern indicates the entire codebase's pattern until explicitly told otherwise
- Match the exact dialect of the codebase: same imports, same structure, same naming

### Complete Flow Implementation
- Trace full execution paths: form -> handler -> action -> database -> loader -> UI update
- Don't stop at partial implementations - complete the entire cycle
- Mental checklist: "If a user interacts with this, what's the FULL execution path?"
- Every interactive element needs: the trigger, the handler, the backend action, the state update, the UI feedback

### Pre-Execution Verification
- Before submitting code, mentally execute it line by line
- Verify: imports resolve, types match, variables exist in scope, functions are defined
- Check that all referenced variables are actually available in that scope
- Catch compilation errors before output, not after

### Explicit Uncertainty Handling
- When information is ambiguous or missing, ask for clarification before proceeding
- If making an assumption, state it explicitly: "Assuming X, implementing Y"
- "I need clarification on X" is valid and better than wrong code
- When multiple valid approaches exist, present options instead of choosing silently

### Solution Depth & Completeness
- Don't just solve the surface request - consider what else is needed for it to actually work in production
- Include validation, error states, loading states, success feedback
- Think about edge cases: empty states, error states, loading states, success states
- Consider the user experience beyond just functionality

### Proactive Architecture Decisions
- Suggest performance optimizations when handling large datasets (memoization, virtualization, pagination)
- Identify accessibility improvements (ARIA labels, keyboard navigation, focus management, screen reader support)
- Consider UX enhancements (optimistic updates, skeleton states, smooth transitions, loading indicators)
- Think about responsive design and mobile considerations

### Code Quality Beyond Functional
- Write self-documenting code with clear variable names that express intent
- Structure code for readability: logical grouping, consistent ordering, clear separation of concerns
- Consider maintainability: easy to modify, easy to debug, easy to extend
- Keep functions focused and single-purpose
- Avoid deeply nested structures when flatter alternatives exist

### Learning Pattern Recognition
- When a correction is made, apply that correction's principle to all similar situations in the same conversation
- Build a working mental model of preferences and coding style based on feedback
- If a specific approach is rejected, avoid suggesting it again unless circumstances clearly differ
- Adapt code style to match what's been accepted vs rejected

### Holistic System Thinking
- Consider how new code integrates with existing systems
- Think about data flow through the entire application
- Anticipate downstream effects of changes (what breaks if this changes?)
- Consider database implications: indexes needed, query performance, data relationships
- Think about security implications: input validation, authentication checks, authorization

### Error Prevention Priorities
- Type safety: ensure types are consistent throughout the data flow
- Null/undefined handling: check for edge cases where data might not exist
- Async handling: properly await async operations and handle potential failures
- State synchronization: ensure UI state matches backend state

### User Experience Defaults
- Every form should have: loading state, error display, success feedback, disabled state during submission
- Every list should handle: empty state, loading state, error state
- Every async operation should have: visual feedback, error recovery, success confirmation
- Consider progressive enhancement: what works without JS, what enhances with JS

### Code Organization Principles  
- Group related logic together (all auth logic in one place, all data fetching together)
- Separate concerns: UI components, business logic, data access should be distinct
- Extract reusable patterns into utilities or components
- Keep files focused: one primary responsibility per file

### Testing Mindset
- Write code that's easy to test: pure functions, clear inputs/outputs, minimal side effects
- Consider what would need to be mocked or stubbed
- Think about test cases: happy path, error cases, edge cases
- Structure code to make debugging easier: clear error messages, useful logging points

i need to create a script, essentialy i need to take each file in 
  - \`app\components\catalyst-ui\blocks\blocks\sections\`
  - \`app\components\catalyst-ui\blocks\blocks\pages\`
  - \`app\components\catalyst-ui\blocks\blocks\ecommerceSections\`
- and create a folder for it to reside within \`~/components/catalyst-ui/blocks/\` and place the file within
- then need to create a file called data, placing in it a ui components library object that will be used to enter it into the library, once that is done in a file within \`app\components\catalyst-ui\blocks\blocks\` record the filename so I can finish of included it into the library afterwards
- if a folder already exists, look in the folder, if no variants are in there already then I need to rename the file and function name accordinly
  - \`BentoGrid.tsx\` now becomes \`bento-grid-variant-1.tsx\`
  - the function name \`BentoGrid\`, now becomes \`BentoGridV1\`
  - if there are already variants in the folder, then get the largest number and increase by one
- I will provide 2 examples
  - we will take \`app\components\catalyst-ui\blocks\blocks\sections\BentoGrid.tsx\` for example
  - there is no folder yet named \`bento-grid\`, so i create one and move the file inside of it
  - create a file named \`data.tsx\` and place the following within it

```jsx
import { BentoGrid } from "./bento-grid";
import { AccessLoFi } from "../../lo-fi";

export const accessData = [
      {
    name: "Bento Grid",
    value: "bento-grid",
    path: "/components/catalyst-ui/blocks/bento-grid/bento-grid.tsx.txt",
    source: null,
    usagePath: "/components/catalyst-ui/blocks/bento-grid/bento-grid.tsx.txt",
    usage: null,
    lofi: <AccessLoFi />,
    premium: true,
    category: "Blocks",
    tags: ["ui", "components", "interactive"],
    features: ["Responsive", "TypeScript", "Accessible"],
    dependencies: ["lucide-react"],
    demo: [<BentoGrid />],
    desc: null,
    customize: null,
  },
]
```
- example 2
  - we will take \`app\components\catalyst-ui\blocks\blocks\sections\Contact.tsx\` for example
  - i scan the \`app\components\catalyst-ui\blocks\` and see there is already one named contact, so i dont create one and before moving i need to change the file name
  - i check the variants and see the highest is 4
  - the filename \`Contact.tsx\` now becomes \`contact-variant-5.tsx\`
  - the function name inside changes from \`Contact\` to \`ContactV5\`
  - move the file into the \`app\components\catalyst-ui\blocks\contact\` folder
  - now i add to add the new object to the data file already there, adding it to the end of the array

```jsx
import { ContactV5 } from "./contact-variant-5";
import { ContactLoFi } from "../../lo-fi";

export const contactData = [
      {
        name: "Contact V5",
        value: "contact-variant-5",
        importPath: null,
        path: '/components/catalyst-ui/blocks/contact/contact-variant-5.tsx.txt',
        source: null,
        usagePath: '/components/catalyst-ui/blocks/contact/contact-variant-5.tsx.txt',
        basicusage: null,
        usage: null,
        lofi: <ContactLoFi />,
        premium: true,
        category: "Blocks",
        tags: ["blocks", "contact", "forms", "business"],
        features: ["Responsive", "TypeScript", "Accessible", "Forms"],
        dependencies: ["lucide-react"],
        demo: [<ContactV5 />],
        props: [],
        props2: [],
        desc: "Professional contact form with business information and location details.",
        status: null,
        lastUpdated: null,
      },
]
```

