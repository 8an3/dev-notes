# A Deterministic AI Engine Compiler

**Reliable AI Outputs • Predictable Results • No More Headaches • Works With Any Engine • No Instance Locks**

Eliminates 99% of AI prompt issues and frustrations across all AI engines.

---

## Struggling with AI prompts? Tired of frustrating interactions and inconsistent results?

Using AI as you develop is unreliable to say the least. Over 40 critical problems make AI-assisted development feel like a chaotic experiment instead of a professional, precision tool.

> Pre-Prompt transformed my understanding of AI's potential—revealing countless use cases I hadn't considered. It 10x'd my code output while simultaneously improving prompt effectiveness and eliminating the verbose, unhelpful responses that typically plague AI interactions.

---

## The Problems

### Core System Problems
- Inconsistent AI outputs across different sessions - AI produces different code styles, patterns, and structures when working on the same project across multiple conversations
- Non-reproducible results - Same inputs generate different outputs, making it impossible to reliably recreate solutions
- Loss of context between sessions - AI 'forgets' previously established patterns, variables, functions, and architectural decisions when starting new conversations
- Inability to scale projects - Without persistent knowledge, AI cannot contribute to large-scale applications requiring coordination across multiple files and sessions
- Hidden AI assumptions - AI makes assumptions without informing users, leading to unexpected behavior and difficult-to-diagnose bugs
- Lack of cumulative learning - AI cannot recall previously created functions, components, or variables for reuse in subsequent work
- No debugging visibility - Users cannot see what assumptions or decisions the AI made when generating code
- Inconsistent code quality - Different instances produce code following different standards, patterns, and best practices

### Development Workflow Problems
- Incomplete implementations - AI provides placeholder code, TODO comments, or non-functional 'mock' features instead of production-ready solutions
- Over-formatting responses - Excessive use of bullet points, headers, and formatting that obscures actual information
- Unnecessary code refactoring - AI restructures working code when only asked to make simple changes
- Variable/object renaming confusion - AI changes data structures when only asked to rename variables
- Missing interactive functionality - Buttons without handlers, forms without submission logic, search that doesn't actually search
- Inconsistent component patterns - Same type of component built differently across the codebase
- Import path errors - Incorrect or inconsistent import statements causing compilation failures
- Type safety issues - Inconsistent type handling throughout data flow (string vs string[], Json parsing)

### Code Quality Problems
- Hard-coded values - Color codes, magic numbers, and non-configurable constants scattered throughout code
- Poor error handling - Missing try-catch blocks, no validation, inadequate error messages
- Incomplete data flows - Form submissions that don't update the database, database changes that don't reflect in UI
- Missing edge cases - No handling for empty states, loading states, error states, or null values
- Accessibility oversights - Missing ARIA labels, keyboard navigation, screen reader support
- Performance blind spots - No consideration for large datasets, missing memoization, inefficient rendering

### Component Development Problems
- Recreating existing components - Rebuilding shadCN/ui components that already exist in the library
- Inconsistent component APIs - Different props patterns and naming conventions across similar components
- Missing component documentation - No usage examples, prop descriptions, or implementation guides
- Non-reusable components - Tightly coupled code that can't be easily reused across projects
- Missing default values - Components requiring extensive configuration instead of sensible defaults
- Poor variant support - Inability to handle multiple visual/behavioral variants of components

### Project Management Problems
- No component tracking - Cannot maintain inventory of available components and their capabilities
- Missing dependency management - Unclear what libraries and versions are required
- Inconsistent file organization - Different folder structures and naming patterns across the project
- No version control for components - Cannot track changes or manage multiple variants
- Poor knowledge transfer - New sessions cannot access information from previous work

### Framework-Specific Problems
- Incorrect loader/action patterns - Not following Remix conventions for data fetching and mutations
- Missing authentication checks - No user validation in loaders and actions
- Improper form handling - Not using Remix Form or fetcher patterns correctly
- Inconsistent data loading - Different patterns for returning data from loaders
- Missing meta and links exports - Incomplete route file structure

### User Experience Problems
- Verbose AI responses - Too much explanation, not enough actionable code
- No scope adherence - AI does more than asked, adding unwanted 'improvements'
- Missing decision transparency - AI doesn't explain why it made specific choices
- Poor error explanations - Vague error messages without actionable solutions
- Inconsistent tone - AI switches between formal and casual unexpectedly

### Documentation Problems
- Missing usage examples - No practical demonstrations of how to implement components
- Incomplete prop documentation - Missing type information, defaults, and descriptions
- No basic usage guides - Users don't know minimal implementation requirements
- Missing demo code - No working examples to reference
- Poor categorization - Difficult to find relevant components in the library

### Quality Assurance Problems
- No pre-execution verification - Code not mentally tested before output
- Missing state synchronization - UI state doesn't match backend state
- Incomplete execution paths - Missing steps in user interaction flows
- No consideration for responsive design - Desktop-only thinking
- Missing loading/success feedback - No visual confirmation of user actions

### Architecture Problems
- Poor separation of concerns - Business logic mixed with UI components
- Difficult to test code - Tightly coupled dependencies, side effects everywhere
- No consideration for maintainability - Code that's hard to modify or extend
- Missing error boundaries - No graceful degradation when things fail
- Inconsistent data modeling - Same data structured differently in different parts of the app

### Enterprise/Scale Problems
- No McDonald's-level consistency - Cannot guarantee same output regardless of who/when/where it's generated
- Difficult to onboard new developers - No standardized patterns or conventions
- No real-time patch capability - Cannot quickly fix issues across all instances
- Limited ability for large projects - System breaks down with complex, multi-file applications

### VSCode Extension Problems
- Inconsistent command registration - Different patterns for registering extension commands
- Poor resource management - Not properly disposing of resources
- Missing proper error handling - Extensions crash without informative errors
- Inconsistent helper function organization - Logic scattered throughout extension.ts

### Template/Block Management Problems
- Manual file organization - No automated system for organizing component variants
- Inconsistent naming conventions - Different patterns for variant naming
- Missing variant tracking - Cannot determine next variant number automatically
- No centralized data management - Component metadata scattered across files

> This solution addresses significantly more issues than initially outlined. Through extensive testing, I've found it can overcome nearly all AI limitations except the fundamental intelligence ceiling of the model itself.

> One of the key innovations is addressing the root cause of most AI-related issues that stem from the unconstrained vectors through which AI makes assumptions. AI generates multiple assumptions per response, each backed by different "facts" that shift between instances. This inconsistency makes it virtually impossible for users to identify patterns or determine where to begin troubleshooting, as the underlying issues appear to have no consistent behavior to trace. By controlling these assumption vectors, this solution eliminates the seemingly random behavior that makes AI troubleshooting so difficult.

---

## The Solution

An elegantly simple solution accessible to users of all experience levels, making AI interactions effortless and effective.

A markdown-based pre-prompt system that transforms AI development workflows, eliminating frustration and unlocking new possibilities.

### Core System Solutions
- Absolute Output Consistency - Enforces identical code styles, patterns, and structures across all sessions through explicit templates and conventions
- 100% Reproducible Results - Standardized inputs and strict adherence rules guarantee identical outputs every time
- Persistent Context Management - 'Available Functions/Components' and 'Available Variables' sections maintain cumulative knowledge across all sessions
- Enterprise-Scale Project Support - Context persistence and cumulative knowledge enable coordination across unlimited files and sessions
- Transparent Decision Making - 'Decision Transparency' section forces AI to explicitly state all assumptions before proceeding
- Cumulative Learning System - 'Continuous Growth and Experience' section catalogs all created functions, components, and variables for permanent reuse
- Full Debugging Visibility - 'Debug AI Outputs' capability exposes every assumption and decision the AI makes during code generation
- Enforced Code Standards - Absolute Code Standards section mandates consistent patterns, naming, and best practices across all instances

### Development Workflow Solutions
- Production-Ready Code Only - Critical Functional Requirements mandate all features must be fully functional with no placeholders or TODOs
- Minimal Formatting Policy - Explicit guidelines restrict bullet points and headers, delivering concise, actionable code instead of verbose explanations
- Strict Scope Adherence - 'Only do what is explicitly asked' rule prevents unwanted refactoring and unauthorized code changes
- Variable Naming Preservation - 'DO NOT Rename Variables/Components/Functions' directive ensures structural integrity when making simple changes
- Mandatory Interactive Features - All buttons, forms, and search inputs must have complete working logic with real handlers and functionality
- Standardized Component Patterns - Templates and examples enforce uniform component architecture across the entire codebase
- Correct Import Paths - Platform & Technology Stack section provides exact import paths for all libraries and components
- Type Safety Enforcement - Pre-Execution Verification requires checking that all types match throughout the data flow before output

### Code Quality Solutions
- Semantic Color System - Mandates Tailwind semantic classes only (bg-background, text-foreground) with zero hard-coded color values
- Comprehensive Error Handling - Error Handling section requires try-catch blocks, validation, and informative error messages for all operations
- Complete Data Flow Implementation - Complete Flow Implementation ensures full execution paths from form to database to UI update
- Edge Case Requirements - Solution Depth & Completeness mandates handling for empty, loading, error, and success states in all features
- Built-in Accessibility - Proactive Architecture Decisions section requires ARIA labels, keyboard navigation, and screen reader support
- Performance Optimization - Automatic consideration for large datasets, memoization, virtualization, and efficient rendering patterns

### Component Development Solutions
- Component Reuse Enforcement - Catalyst UI/shadCN Component Usage section lists all existing components to prevent recreation
- Standardized Component APIs - Props interface templates and conventions ensure uniform patterns across all components
- Mandatory Documentation - Required Demo Function, basicusage section, and props section ensure complete component documentation
- Reusable Component Architecture - Mimic Building Technique uses shadCN patterns for maximum portability and reusability
- Sensible Default Values - Props Default Values requirement minimizes end-user configuration with intelligent defaults for all props
- Native Variant Support - CVA (class-variance-authority) integration provides built-in support for multiple visual and behavioral variants

### Project Management Solutions
- Automated Component Inventory - UI Library Object requirement creates centralized tracking with metadata for all components
- Explicit Dependency Management - Dependencies field in UI Library Object documents all required libraries and versions
- Standardized File Organization - File structure templates and naming conventions enforce consistent organization project-wide
- Built-in Version Control - Variant naming system (component-variant-N) and value tracking enable version management
- Perfect Knowledge Transfer - Continuous Growth and Experience section ensures all session knowledge persists permanently

### Framework-Specific Solutions
- Correct Loader/Action Patterns - Remix-Run Route Section provides exact templates for proper data fetching and mutations
- Built-in Authentication - User variable template with optionalAuth ensures consistent authentication checks in all loaders and actions
- Proper Form Handling - Templates demonstrate correct Remix Form and fetcher.submit() patterns with intent-based routing
- Standardized Data Loading - Loader template mandates consistent pattern for returning json data to components
- Complete Route Structure - Required meta and links exports ensure all route files have proper SEO and resource loading

### User Experience Solutions
- Concise AI Responses - 'Do not output extra comments or talking points' directive eliminates verbose explanations
- Strict Scope Boundaries - Scope Adherence section prevents AI from adding unwanted improvements or features
- Required Decision Transparency - 'ASSUMPTION: [what I'm assuming]' format forces AI to explain all choices explicitly
- Actionable Error Solutions - Error handling guidelines require specific fixes ranked by likelihood of success
- Consistent Professional Tone - Tone and Formatting guidelines maintain appropriate formality throughout interactions

### Documentation Solutions
- Required Usage Examples - Demo Function requirement provides 2 practical implementation examples for every component
- Complete Prop Documentation - Props section mandates type, default value, and description for every component property
- Basic Usage Guides - Basicusage section shows minimal implementation requirements in simplest form possible
- Working Demo Code - Demo functions must be fully functional, not placeholders, demonstrating real component usage
- Intelligent Categorization - Category, tags, and features fields enable powerful searching and filtering in the library

### Quality Assurance Solutions
- Pre-Execution Mental Testing - Pre-Execution Verification requires AI to mentally execute code line-by-line before output
- State Synchronization Checks - Context Retention & State Tracking ensures UI state matches backend state at all times
- Complete Execution Paths - Complete Flow Implementation traces full user interaction flows from trigger to feedback
- Responsive Design Consideration - Proactive Architecture Decisions includes mobile and responsive design in all solutions
- User Feedback Requirements - User Experience Defaults mandate loading states, error display, and success confirmation for all actions

### Architecture Solutions
- Clear Separation of Concerns - Code Organization Principles separate UI components, business logic, and data access into distinct layers
- Testable Code Structure - Testing Mindset section ensures pure functions, clear inputs/outputs, and minimal side effects
- Maintainability Focus - Code Quality Beyond Functional emphasizes code that's easy to modify, debug, and extend
- Error Boundary Implementation - Error Prevention Priorities require graceful degradation and proper error handling at all levels
- Consistent Data Modeling - Holistic System Thinking ensures data structures remain consistent throughout the application

### Enterprise/Scale Solutions
- McDonald's-Level Consistency - Output consistency mechanisms guarantee identical results regardless of who, when, or where code is generated
- Standardized Onboarding - Templates, conventions, and documentation enable rapid developer onboarding with zero ambiguity
- Real-Time Patch System - Patch Fixes section allows immediate correction of issues across all instances simultaneously
- Unlimited Project Scale - Cumulative knowledge and context persistence enable projects of any size and complexity

### VSCode Extension Solutions
- Standardized Command Registration - Command Registration Pattern template ensures consistent command structure with proper disposal
- Proper Resource Management - Extension guidelines require context.subscriptions.push() for all disposables with proper cleanup
- Comprehensive Error Handling - Error Handling requirement includes proper try-catch blocks and user notifications for all async operations
- Organized Helper Functions - File Organization section separates helper functions into dedicated files for maintainability

### Template/Block Management Solutions
- Automated File Organization - Script-based system automatically organizes component variants into proper folder structures
- Consistent Naming Conventions - Variant naming system (component-variant-N) enforces uniform naming across all templates
- Automatic Variant Tracking - Script detects existing variants and automatically assigns next sequential number
- Centralized Data Management - UI Library Object consolidates all component metadata in standardized, queryable format

---

## Core Capabilities

- Output consistency across engines, sessions, users
- Reproducibility - same input = same output, always
- Context persistence - state carries across sessions
- Cumulative knowledge - AI gains experience over time
- Enterprise scalability - McDonald's-level consistency
- Debug AI outputs - see every assumption made
- Real-time patch fixes for recurring issues
- Unlocked abilities beyond standard AI limits
- Single pre-prompt dictates entire instance behavior
- Click-based UI for any skill level

---

## How It Works

### Step 1: Create Your Pre-Prompt
Define standards, patterns, and requirements and or solutions to repeated problems within an prompts response, in a markdown file

### Step 2: Insert at the start of each AI interaction
(or with every prompt for optimal results, particularly with models like DeepSeek that reset context within conversations)

Pasting your pre-prompt followed by your instructions

### Step 3: Rinse & Repeat
Adjust your predefined pre-prompt whenever you come across any new issues that arises, or any new requirements that need to be met.

To achieve optimal results, focus your pre-prompt around specific development areas. For example, if you're coding a VS Code extension, create a pre-prompt specifically tailored to that context. Then create another pre-prompt for your building project, allowing you to provide extremely specific details for each use case.

Essentially, you become the AI engine's external memory system—storing context, conventions, and domain-specific knowledge that the model can reference for more accurate and relevant responses.

### Step 4: Share successful pre-prompt with team members
Allowing you to scale indefinitely. Works across teams, projects, and unlimited complexity.

Granting different people, the same results over time, regardless of skill level. Giving you a reliable result, that businesses can actually work with.

---

## Proven Results: Real Test Data Across 5 AI Engines

130 total tests with only 1 prompt per instruction. No retries, no corrections, no human editing. With a 1 prompt, 1 response rule. Not allowing me to readjust or "fix" anything as the test went on.

### Components
- **Test:** 25 reusable UI library components across 5 AI engines. Each engine built 5 commonly used components following strict architectural guidelines and build parameters.
- **Result:** 96% success rate producing professional, production-ready components.

### Templates
- **Test:** 63 SSR page templates of varying complexity across 5 AI engines. Included requirements notoriously difficult for AI—tasks that typically fail on platforms like Remix Run.
- **Result:** 98.41% success rate.

### Stress Test
- **Test:** 42 deliberately challenging tasks designed to cause AI failure.
- **Result:** 95.24% success rate on scenarios engineered to break standard AI workflows.
- **Note:** For this test, I had specifically chosen designs I have seen it fail at before, or just have hard time coding them in general for an SSR based platform. Responses and its code were tested using remix-run.

> Throughout testing, I never reviewed or validated any engine's output, not even when the test was completed with all responses given. I only viewed each file to grab the files main function to call it, in order to render it on the page to test if the code was successful. Only after viewing the rendered code, did I go back to review files several times, as I was shocked that the respective function even worked. The results were staggering: a combined 96.54% success rate across all engines. Even more remarkable—all testing was conducted exclusively on free-tier accounts. This eliminates instance locks, session locks, and even engine locks. You can now strategically route questions to whichever engine excels at that specific problem type. This granular engine selection delivers the absolute best possible results for every task.

### Engines used during testing
- Claude
- CodeGeek
- Gemini
- Deepseek
- Copilot

---

## Real World Impact

400+ components built in hours for a UI components library. Running 6 AI engines simultaneously, building components faster than I could have done alone.

### Traditional AI Development: Using AI prompts without pre-prompt
- Inconsistent outputs require constant review
- Multiple retry cycles for each component
- Heavy manual editing and debugging or adjusting original instructions given to gain a better result
- Can't trust output enough to work in parallel

### Implementing Pre-Prompt: Using the designed solution with AI engines
- Download and use code immediately, no review needed. Making each engines response, reliably successful to use in your codebase
- One prompt, one response. No more going back and forth to fine tune the response to get it working
- Zero manual editing required, once the response has been provided
- Run 6+ engines in parallel with confidence, or as many as you would like
- No concern for being locked to an instance
- Obtain reliable result across log in sessions / AI engines
- Unlocking the ability to build bigger more complex systems with AI, no matter the size of what you need to build
- 10x-100x productivity increase: When you can trust AI to deliver production-ready code on the first try, you unlock parallel workflows and exponential productivity gains
- and the list continues...

---

## Demos

Here are a couple of videos demonstrating some of its strengths and uses:

- [Instance locks](https://youtu.be/8viFywR-WF8)
- [One prompt, one response](https://youtu.be/x5W8HcfH5Hk)
- [AI Engine to build code, using given parameters and build techniques](https://youtu.be/gWr__Y2jJ04)
- [Consistent responses across engines / sessions / instances](https://youtu.be/ICDcjmxynvA)

---

## Web App Coming Soon!

**Multi-Engine Support • Smart Routing • Click-Based UI**

AI prompt system with built-in pre-prompt architecture. Easily create and design pre-prompts targeting specific coding tasks. Effortlessly leverage multiple AI engines with click-based interface. Guaranteed to obtain the best result available by questioning the appropriate engine for each task.

### Features
- **Multi-Engine Support:** Connect as many of your AI engines in one interface, switching engines with a simple click
- **Smart Routing:** Automatically route tasks to best-suited engine
- **Click-Based UI:** No markdown editing or file creation necessary, just click and build your pre-prompt adding predefined sections to create your own customized pre-prompt


## Examples

- [Pre-Prompt V6](https://github.com/8an3/dev-notes/blob/main/docs/Pre-Prompt-V6.md)
- [Reusable Components - Pre-Prompt](https://github.com/8an3/dev-notes/blob/main/docs/Reusable-Components-Pre-Prompt.md)
- [Demo test](https://github.com/8an3/dev-notes/blob/main/docs/Demo-test.md)
- [Default Pre-Prompt](https://github.com/8an3/dev-notes/blob/main/docs/Default-Pre-Prompt.md)
- [Extension feature example pre-prompt](https://github.com/8an3/dev-notes/blob/main/docs/Extension-feature-example-pre-prompt.md)
- [VSCode Extension Pre-Prompt](https://github.com/8an3/dev-notes/blob/main/docs/VSCode-Extension-Pre-Prompt.md)

---

[🡄 Return](https://github.com/8an3/DevStack)