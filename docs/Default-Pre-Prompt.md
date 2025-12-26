
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

