## Catalyst Pre-Prompt v2.0

### IMPORTANT READ FIRST
YOU ARE NOT ALLOWED TO START PROVIDING AN ANSWER TILL AFTER YOU HAVE READ ALL THE DATA IN THE PROMPT THAT I HAVE SENT, IN ITS ENTIRETY. NO MATTER HOW COMFORTABLE YOU IN MOVING FORWARD AND PROVIDE AN ANSWER, YOU ARE NOT ALLOWED. YOU HAVE TO READ THIS FIRST... THEN ONCE YOU HAVE COMPLETED THIS TASK OF READING THIS, THEN, AND ONLY THEN YOU CAN START TO PROVIDE THE ANSWER. THIS IS SO YOU OBTAIN ALL THE INFORMATION YOU NEED FOR THE ANSWER YOU ARE TO GIVE

### General
- do not output any other extra comments or "talking points", only provide the output of the code I am asking for
- if I provide the full component then just provide the library object if i provide just a url then provide the component
- if it doesnt have a demo provide a demo

### Platform & Technology Stack
- **Framework**: Remix Run v2 (use loaders, actions, and Remix hooks)
- **Styling**: Tailwind CSS v3 (semantic classes ONLY: bg-background, text-foreground, border-border, etc.)
- **Component Library**: shadCN UI
- **Icons**: lucide-react
- **Tailwind.css Path**: ~/styles/tailwind.css
- **json import Path**: @remix-run/node
- **Primsa Path**: ~/modules/libs/prisma
- **Utilities Path**: ~/components/catalyst-ui/utils
- **Components Path**: ~/components/catalyst-ui/components
  - Correct: \`import { Button } from "~/components/catalyst-ui"\`
  - Wrong: \`import { Button } from "~/components/catalyst-ui"\`

### Absolute Code Standards
- **Function Declaration**: Use \`export function ComponentName()\` NEVER \`const ComponentName = () => {}\`
- **Default Exports**: No default exports in any file
- **Comments**: Do not leave comments in code
- **Color Values**: Never use hard-coded colors (no #hex, no rgb(), no color names)
- **Remix Patterns**: Utilize Remix loaders, actions, and hooks throughout

### Code Building Proceses To Employ
- Build components using shadCN's exact architectural patterns
- All props must have sensible default values to minimize end-user configuration
- Support variants via props when multiple styles are applicable
- Always accept and merge className prop for style overrides
- Support children prop when content should be customizable
- Props interface should extend appropriate React HTML attributes

### Critical Functional Requirements
All interactive features MUST be fully functional and working:
- Search inputs must actually search/filter data
- Filter controls must actually filter results
- Sort buttons must actually sort data
- Form submissions must handle data
- Buttons must have real onClick handlers with logic
  - unless the button is used within remix's Form or fetcher.Form component
  - if those features are not used, then the following form example must be used along side any other functionality that needs to be triggered when that form is submitted, this format  your more than welcome to create a function before the return statment to define this
  
\`\`\`tsx
const fetcher = useFetcher()
const formData = new FormData();
formData.append("id", item.id);
formData.append("intent", "deleteProgress");
fetcher.submit(formData, { method: "post" });
\`\`\`

- Loading states must represent real async operations
- No placeholder functionality
- No dummy/mock implementations
- No "TODO" or "implement this later" code

If a component has interactive elements, those elements MUST work in the context they are used.

### shadCN Component Usage (READ CAREFULLY)
DO NOT recreate any shadCN components that already exist.
Use existing shadCN components from the library.

### **Available shadCN components, import them, do not build them (DO NOT RECREATE):**
Accordion, Alert, Alert Dialog, Aspect Ratio, Avatar, Badge, Breadcrumb, Button, Button Group, Calendar, Card, Carousel, Chart, Checkbox, Collapsible, Combobox, Command, Context Menu, Data Table, Date Picker, Dialog, Drawer, Dropdown Menu, Empty, Field, React Hook Form, Hover Card, Input, Input Group, Input OTP, Item, Kbd, Label, Menubar, Navigation Menu, Pagination, Popover, Progress, Radio Group, Resizable, Scroll Area, Select, Separator, Sheet, Sidebar, Skeleton, Slider, Sonner, Spinner, Switch, Table, Tabs, Textarea, Toast, Toggle, Toggle Group, Tooltip, Typography 

### Loader, if it has one, requires the following as a minimum to be loaded into the default function:
\`\`\`tsx
const { user } = await optionalAuth(request);
return json({ user })
\`\`\`

### Action, if it has one:
- if we need to use an action that intakes data from a form this is how it will be done:
  - const d = Object.fromEntries(await request.formData());
- a page is allowed to have more than one form action, each form action needs to include an intent
    - the intent value will be accesssible in the action via:
      - const intent = d.intent
- form values will be accesssible in the following formatted examples:
  - d.name
  - d.email
  - d.message
- each forms intent will be encased in a if statement that will end with:
  - return json({ success: true, })
  - the true statement to be folloed by any other values needed to be pushed back to the page through the use of a fetcher

### User variable, to be used within every action / loader:
- import path: import { optionalAuth } from "~/routes/userAuth"
- when calling and setting the user value:  const { user } = await optionalAuth(request);

### Meta, required in route files:
\`\`\`typescript
export const meta: MetaFunction = () => {return [{ title: "Catalyst Software" }, { name: "description", content: "Catalyst Software" }]};
\`\`\`

### links: LinksFunction, required in route files:
\`\`\`typescript
import ZapSVG from '~/components/images/icon.svg'
export const links: LinksFunction = () => [{ rel: "icon", type: "image/svg", href: ZapSVG }];
\`\`\`

# DEMO TEST

## Buttons
https://ui.shadcn.com/docs/components/button
https://primereact.org/button/
https://rsuitejs.com/components/button/
https://chakra-ui.com/docs/components/button
https://flowbite.com/docs/components/buttons/
https://mui.com/material-ui/react-button/
https://ant.design/components/button
https://react-bootstrap.github.io/docs/components/buttons
https://mantine.dev/core/button/
https://nextui.org/docs/components/button

## Badges
https://ui.shadcn.com/docs/components/badge
https://primereact.org/badge/
https://rsuitejs.com/components/badge/
https://chakra-ui.com/docs/components/badge
https://flowbite.com/docs/components/badge/
https://mui.com/material-ui/react-badge/
https://ant.design/components/badge
https://react-bootstrap.github.io/docs/components/badge
https://mantine.dev/core/badge/
https://nextui.org/docs/components/badge

## Avatars
https://ui.shadcn.com/docs/components/avatar
https://primereact.org/avatar/
https://rsuitejs.com/components/avatar/
https://chakra-ui.com/docs/components/avatar
https://flowbite.com/docs/components/avatar/
https://mui.com/material-ui/react-avatar/
https://ant.design/components/avatar
https://mantine.dev/core/avatar/
https://nextui.org/docs/components/avatar

## Alerts
https://ui.shadcn.com/docs/components/alert
https://primereact.org/message/
https://rsuitejs.com/components/message/
https://chakra-ui.com/docs/components/alert
https://flowbite.com/docs/components/alerts/
https://mui.com/material-ui/react-alert/
https://ant.design/components/alert
https://react-bootstrap.github.io/docs/components/alerts
https://mantine.dev/core/alert/
https://nextui.org/docs/components/snippet

## Inputs
https://ui.shadcn.com/docs/components/input
https://primereact.org/inputtext/
https://rsuitejs.com/components/input/
https://chakra-ui.com/docs/components/input
https://flowbite.com/docs/forms/input-field/
https://mui.com/material-ui/react-text-field/
https://ant.design/components/input
https://react-bootstrap.github.io/docs/forms/form-control
https://mantine.dev/core/input/
https://nextui.org/docs/components/input

## Checkboxes
https://ui.shadcn.com/docs/components/checkbox
https://primereact.org/checkbox/
https://rsuitejs.com/components/checkbox/
https://chakra-ui.com/docs/components/checkbox
https://flowbite.com/docs/forms/checkbox/
https://mui.com/material-ui/react-checkbox/
https://ant.design/components/checkbox
https://react-bootstrap.github.io/docs/forms/checks-radios
https://mantine.dev/core/checkbox/
https://nextui.org/docs/components/checkbox

## Switches/Toggles
https://ui.shadcn.com/docs/components/switch
https://primereact.org/togglebutton/
https://rsuitejs.com/components/toggle/
https://chakra-ui.com/docs/components/switch
https://flowbite.com/docs/forms/toggle/
https://mui.com/material-ui/react-switch/
https://ant.design/components/switch
https://mantine.dev/core/switch/
https://nextui.org/docs/components/switch

## Cards
https://ui.shadcn.com/docs/components/card
https://primereact.org/card/
https://rsuitejs.com/components/panel/
https://chakra-ui.com/docs/components/card
https://flowbite.com/docs/components/card/
https://mui.com/material-ui/react-card/
https://ant.design/components/card
https://react-bootstrap.github.io/docs/components/cards
https://mantine.dev/core/card/
https://nextui.org/docs/components/card

## Chips/Tags
https://primereact.org/chip/
https://rsuitejs.com/components/tag/
https://chakra-ui.com/docs/components/tag
https://mui.com/material-ui/react-chip/
https://ant.design/components/tag
https://mantine.dev/core/chip/
https://nextui.org/docs/components/chip

## Progress Bars
https://ui.shadcn.com/docs/components/progress
https://primereact.org/progressbar/
https://rsuitejs.com/components/progress/
https://chakra-ui.com/docs/components/progress
https://flowbite.com/docs/components/progress/
https://mui.com/material-ui/react-progress/
https://ant.design/components/progress
https://mantine.dev/core/progress/
https://nextui.org/docs/components/progress

## Spinners/Loaders
https://primereact.org/progressspinner/
https://rsuitejs.com/components/loader/
https://chakra-ui.com/docs/components/spinner
https://flowbite.com/docs/components/spinner/
https://mui.com/material-ui/react-progress/#circular
https://ant.design/components/spin
https://mantine.dev/core/loader/
https://nextui.org/docs/components/spinner

## Dividers
https://ui.shadcn.com/docs/components/separator
https://primereact.org/divider/
https://rsuitejs.com/components/divider/
https://chakra-ui.com/docs/components/divider
https://mui.com/material-ui/react-divider/
https://ant.design/components/divider
https://mantine.dev/core/divider/
https://nextui.org/docs/components/divider

## Skeletons
https://ui.shadcn.com/docs/components/skeleton
https://primereact.org/skeleton/
https://chakra-ui.com/docs/components/skeleton
https://mui.com/material-ui/react-skeleton/
https://ant.design/components/skeleton
https://mantine.dev/core/skeleton/
https://nextui.org/docs/components/skeleton

