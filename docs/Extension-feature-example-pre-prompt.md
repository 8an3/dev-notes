### IMPORTANT READ FIRST
YOU ARE NOT ALLOWED TO START PROVIDING AN ANSWER TILL AFTER YOU HAVE READ ALL THE DATA IN THE PROMPT THAT I HAVE SENT, IN ITS ENTIRETY. NO MATTER HOW COMFORTABLE YOU IN MOVING FORWARD AND PROVIDE AN ANSWER, YOU ARE NOT ALLOWED. YOU HAVE TO READ THIS FIRST... THEN ONCE YOU HAVE COMPLETED THIS TASK OF READING THIS, THEN, AND ONLY THEN YOU CAN START TO PROVIDE THE ANSWER. THIS IS SO YOU OBTAIN ALL THE INFORMATION YOU NEED FOR THE ANSWER YOU ARE TO GIVE

# Error, imports plus Pre-Prompt v3.0
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

### Catalyst UI / shadCN Component Usage (READ CAREFULLY)
DO NOT recreate any Catalyst UI components that already exist.
Use existing Catalyst UI components from the library.

### **Available Catalyst UI / shadCN components, import them, do not build them (DO NOT RECREATE):**
Accordion, Alert, Alert Dialog, Aspect Ratio, Avatar, Badge, Breadcrumb, Button, Button Group, Calendar, Card, Carousel, Chart, Checkbox, Collapsible, Combobox, Command, Context Menu, Data Table, Date Picker, Dialog, Drawer, Dropdown Menu, Empty, Field, React Hook Form, Hover Card, Input, Input Group, Input OTP, Item, Kbd, Label, Menubar, Navigation Menu, Pagination, Popover, Progress, Radio Group, Resizable, Scroll Area, Select, Separator, Sheet, Sidebar, Skeleton, Slider, Sonner, Spinner, Switch, Table, Tabs, Textarea, Toast, Toggle, Toggle Group, Tooltip, Typography 

**Current plan**
```sh
- creating a navigator view
  - will have a dock for navigation between 'tabs'
      1. will be the ai chat
        - where an adjustable text area will be at the bottom with no size restrictions, with buttons running on the side of the siderbar going upwards for functionality
        - at the top will have the info on the ai engine, clicking on the image will allow you to hot swap between engines as long as you have them configrued, im hoping to have atleast 1-2 pre confgirued and working at install whenever a new user installs it
        - using ai-sdk.dev to not limit on what engine we can access
        - the buttons that wil run up the side of the side bar will be
         1. quick add current file
         2. add context
         3. refresh context 
         4. clear context
         5. regenerate ai response 
         6. copy
         7. edit prompt
         8. save to snippets
      2. will be devoted to errors that will only get populated when triggered via button defaulting on focusing on the focused editor, with an option to spider outwards looking for more errors across your app, again all buttons will be on the inner wall, starting from the bottom going upwards
        - when you start out it will ask if you want to auto fix or manual 
        - manual option
          - button to scan for errors at anytime
          - mode toggle: between file and workspace
          - button to intiate auto fix at anytime
          - a list will display of the errors 
            - left clicking will bring you to the error and highlighting it
            - right clicking will open a contrext menu 
              - ✨ Auto-fix this error
              - 💬 Ask AI about this
              - 📋 Copy error details
              - ✅ Mark as reviewed
              - 🚫 skip error for now
              - 🔍 Find similar errors
            - whenever a error is highlighted it will display the error code underneath in the editor
      3. Context tab
          - displaying current context if any
          - can add files, or folders as removing them individually or them all at once
          - Context Sets: Save frequently used context combinations
          - Token Counter: Shows total tokens from context
          - Folder Options: Recursive toggle, file type filters
      4. Settings
         - a drop down will be at the top allowing you to select a engine to configure, once configure will remain displayed as a list and each time you sleect a item from the drop down it adds to that list, while at the same time you can remove or edit eeach time 
         - Multi-Engine Support: Save multiple API configurations
         - Quick Switch: Radio buttons for fast engine switching
         - Secure Storage: API keys encrypted in VS Code secrets
         - Connection Test: Verify API key before saving
      5. Compiler - for current testing will be locked to me for now
         - Template System: Save multiple pre-prompts
         - Variable Support: Dynamic insertion (file names, dates, etc.)
         - Per-Instance: Submitted once per new chat instance
         - Import/Export: Share templates with team
      6. history
         - Searchable: Find past conversations
         - Resume: Click to restore conversation in chat tab
         - Export: Save conversation as markdown/JSON
         - Stats: Message count, token usage, model used
      7. analytics
      8. Snippets
      9. tab for viewing the options we had for:
         - Open Successful Solutions
         - Open Failed Solutions
         - Open Last Auto Fix Report 
- other features:
  - Notifications - Toast alerts for completions
  - Keyboard Shortcuts - Quick access to all tabs
  - Auto-save Conversations - Never lose work ( this should be taken care of by the histroy tab dude)
```
**Currently have the following files**
```sh
/root
  /webview
    /src
      - App.tsx
      - App.css
      /utils
        - vscode.ts
      /components
        - ChatInput.tsx
        - ChatInput.css
        - DockNavigation.tsx
        - DockNavigation.css
        - EngineSwitcher.tsx
        - EngineSwitcher.css
        - MessageBubble.tsx
        - MessageBubble.css
        /tabs
          - ChatTab.tsx
          - ChatTab.css
          - ContextTab.tsx
          - ContextTab.css
          - ErrorsTab.tsx
          - ErrorsTab.css
          - HistoryTab.tsx
          - HistoryTab.css
          - PrePromptTab.tsx
          - PrePromptTab.css
          - SettingsTab.tsx
          - SettingsTab.css
  /src
    - extension.ts
    /views
      - AINavigatorViewProvider.ts
    /services
      - AIService.ts
      - ContextManager.ts
      - ErrorScanner.ts
      - HistoryService.ts
      - PrePromptService.ts
      - SecureStorage.ts

at this time the blow have not been added 
    /navigator
      - NavigatorView.ts (Main webview)
      - DockManager.ts (Tab switching)
      /tabs
        - ChatTab.ts
        - ErrorsTab.ts
        - ContextTab.ts
        - SettingsTab.ts
        - PrePromptTab.ts
        - HistoryTab.ts
        - AnalyticsTab.ts
        - SnippetsTab.ts

  /providers
    - OpenAIProvider.ts
    - GroqProvider.ts
    - ClaudeProvider.ts
    - GeminiProvider.ts
```
**Colors**
- no background on buttonsor inputs
- border editor
- icon and text color editor foreground

# **INSTRUCTIONS**
- continue building where we left off, current code will follow...

- **here is the current code we have for our ai error engine / coding helper / ai prompt**
```jsx
// Install with: npm install ai @ai-sdk/openai @ai-sdk/anthropic @ai-sdk/google @ai-sdk/mistral

// Files completed and implemented, left code out for space reasons can include if needed

// File: /src/extension.ts // Main extension entry point
// File: /src/services/SecureStorage.ts // Secure storage for API keys and configurations
// File: /src/services/AIService.ts // AI Service using Vercel AI SDK
// File: /src/services/PrePromptService.ts // Manages pre-prompt templates
// File: /src/services/ContextManager.ts // Manages file and folder context
// File: /src/services/ErrorScanner.ts // Scans files for errors
// File: /src/services/HistoryService.ts // Manages conversation history
// File: /src/views/AINavigatorViewProvider.ts // Webview provider that hosts the React UI
// File: /webview/src/App.tsx // Main React application component
// File: /webview/src/components/DockNavigation.tsx // macOS-style dock navigation
// File: /webview/src/utils/vscode.ts // VS Code API utilities
// File: /webview/src/App.css // Main app styles
// File: /webview/src/components/DockNavigation.css // Dock navigation styles
// File: /webview/src/components/tabs/ChatTab.tsx // Main chat interface
// File: /webview/src/components/MessageBubble.css
// File: /webview/src/components/ChatInput.css
// File: /webview/src/components/EngineSwitcher.css
// File: /webview/src/components/tabs/ChatTab.css
// File: /webview/src/components/EngineSwitcher.tsx // AI engine hot-swapping component
// File: /webview/src/components/ChatInput.tsx // Adjustable textarea input with context toggle
// File: /webview/src/components/MessageBubble.tsx // Individual message display component
// File: /webview/src/components/tabs/ErrorsTab.tsx // Error scanning and auto-fix interface
// File: /webview/src/components/tabs/ErrorsTab.css
// File: /src/views/NavigatorViewProvider.ts // Webview provider with message handlers
// File: /webview/src/components/tabs/ContextTab.tsx // Context management interface
// File: /webview/src/components/tabs/ContextTab.css
// File: /webview/src/components/tabs/SettingsTab.css
// File: /webview/src/components/tabs/HistoryTab.tsx // Conversation history management
// File: /webview/src/components/tabs/PrePromptTab.css
// File: /webview/src/components/tabs/PrePromptTab.tsx // Pre-prompt template management (Compiler)

```
**next steps**
currently troublshooting webview