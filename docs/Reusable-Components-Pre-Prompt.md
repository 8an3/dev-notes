# Pre-Prompt - Context for building reusable components

### IMPORTANT READ FIRST
YOU ARE NOT ALLOWED TO START PROVIDING AN ANSWER TILL AFTER YOU HAVE READ ALL THE DATA IN THE PROMPT THAT I HAVE SENT, IN ITS ENTIRETY. NO MATTER HOW COMFORTABLE YOU IN MOVING FORWARD AND PROVIDE AN ANSWER, YOU ARE NOT ALLOWED. YOU HAVE TO READ THIS FIRST... THEN ONCE YOU HAVE COMPLETED THIS TASK OF READING THIS, THEN, AND ONLY THEN YOU CAN START TO PROVIDE THE ANSWER. THIS IS SO YOU OBTAIN ALL THE INFORMATION YOU NEED FOR THE ANSWER YOU ARE TO GIVE

### General
- do not output any other extra comments or "talking points", only provide the output of the code I am asking for
- if I provide the full component then just provide the library object if i provide just a url then provide the component
- if it doesnt have a demo provide a demo

### Code Building Proceses To Employ
- **cn Path**: import { cn } from '~/components/catalyst-ui/utils'
- **cva, type VariantProps Path**: import { cva, type VariantProps } from 'class-variance-authority'
- Build components using shadCN's exact architectural / engineering patterns
Core Principles
1. Copy-Paste, Not Install nad most importantly east of use

Components are copied directly into your project, not installed as dependencies
You own the code completely - full control to modify as needed
No black box abstractions

2. Radix UI Foundation

Built on top of Radix UI primitives for accessibility and behavior
Radix handles complex interactions (keyboard nav, focus management, ARIA)
shadcn adds the styling layer on top

3. Tailwind-First Styling

Uses Tailwind utility classes exclusively
Semantic color tokens (bg-background, text-foreground, border-input)
Color Values: Never use hard-coded colors (no #hex, no rgb(), no color names)

4. CVA (Class Variance Authority)

Variant management through cva() functions
Type-safe props via VariantProps<typeof variants>
Clean API for size/variant/state combinations

5. Composition Pattern
tsx// Not monolithic - composed of smaller parts
<Dialog>
  <DialogTrigger />
  <DialogContent>
    <DialogHeader>
      <DialogTitle />
      <DialogDescription />
    </DialogHeader>
  </DialogContent>
</Dialog>
6. Smart Defaults

defaultVariants ensure components work with minimal props
giving defaults to every props possible
Sensible out-of-box behavior
Optional customization via props

7. className Merging

Always accept className prop
Use cn() utility to merge classes properly
Allows user overrides without breaking base styles

8. TypeScript-Native

Full type safety
Extends native HTML element props
IntelliSense support for all props

This creates components that are accessible, customizable, type-safe, and truly yours.
- **Function Declaration**: Use \`export function ComponentName()\` NEVER \`const ComponentName = () => {}\`
- **Default Exports**: No default exports in any file
- **Comments**: Do not leave comments in code
- **Remix-Run Patterns**: Utilize Remix-run loaders, actions, and hooks throughout
- **DO NOT Rename Variables / Components / Functions**: Use the same name that is used, regardless of what it is
- **Export all functions at the end of the file**: example:
```tsx
export {
    button, 
    ButtonVariant
}
```

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
DO NOT recreate any Catalyst UI components that already exist.
Use existing Catalyst UI components from the library.

### **Available Catalyst UI / shadCN components, import them, do not build them (DO NOT RECREATE):**
Accordion, Alert, Alert Dialog, Aspect Ratio, Avatar, Badge, Breadcrumb, Button, Button Group, Calendar, Card, Carousel, Chart, Checkbox, Collapsible, Combobox, Command, Context Menu, Data Table, Date Picker, Dialog, Drawer, Dropdown Menu, Empty, Field, React Hook Form, Hover Card, Input, Input Group, Input OTP, Item, Kbd, Label, Menubar, Navigation Menu, Pagination, Popover, Progress, Radio Group, Resizable, Scroll Area, Select, Separator, Sheet, Sidebar, Skeleton, Slider, Sonner, Spinner, Switch, Table, Tabs, Textarea, Toast, Toggle, Toggle Group, Tooltip, Typography 

### Absolute Code Standards
- **FILE SHOULD ONLY CONTAIN THE FOLLOWING**: reusable component ( Including anything that is needed for the reusable component, cva functions, supporting functions, partnering functions ie: tabs also has tabsList, tabsContent and so on), demo function, object for ui components library - ALL to be given within the same file
- Component Code Example
  - components example provided from working currently in-production:
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
- need to provide demo function
- Demo Code Example
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
- need to provide a basicusage section
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
- need to provide ui library object to define the object within
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
  - usage: this value to remain null
  - source: this value to remain null
  - path: provide the source code path, followed by .txt as seen in the example
  - usagePath: provide the source code path, followed by .txt as seen in the example
  - premium needs to be set to true no exceptions
```tsx
const uiLibComp = [
	{
		name: "Auth System", // title, similar to the value but replaces - with space, starting and any letter a - capatilized
		value: "auth-system", // comprised of its file name
		importPath: "~/components/catalyst-ui/pages/auth-system",
		multiImport: null,
		basicusage: null,
		path: "/components/catalyst-ui/pages/auth-system.tsx.txt",
		source: null,
		usagePath: "/components/catalyst-ui/pages/auth-system.tsx.txt",
		usage: null,
		lofi: null, // ignore unless instructed
		premium: true, // ignore unless instructed
		category: "Pages", // sub category - category
		tags: ["pages",], // provide tags relevant to the component
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

