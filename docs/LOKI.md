
# LOKI AI: Limitless

> Taken from a blog post I wrote about limitless as I have yet to write up the how-to.


Currently, Loki AI has the ability to:

- Force the AI engine to build react components with a new method in which it does NOT have a single example to go off of.
- Follow strict itemized list of directives to follow.
- Each of the AI's responses are now tailored to the user, whatever they may be.
- Does NOT permit the AI to assume any one thing when generating its response to your prompt.
- Going against the directive outlined by the developers who created the engine and forcing the AI to no longer "add value" as most of the time, it is either unneeded, add code that breaks, or worse takes already working code example gutting it and remaking it before handing the response back to the user to use and finding out it now crashes their application.
- Removed its ability to assume any one thing before moving forward with its response.
- Essentially, hijacking its cognitive decision making process and the thought process it needs to go through in order to make said decisions.

To expand on it, by allowing it to "add value" again, let's see what an AI has to say ( Should go without saying but the provided responses were not controlled or modified in any way ):

> [AI]: Primary Behavioral Controls
> - Forces me to read ALL content before responding - Prevents premature answers without full context
> - Eliminates assumptions - Must ask clarifying questions if information is missing rather than guessing
> - Removes "adding value" behavior - Must provide exactly what's requested without modifications, enhancements, or improvements that weren't asked for
> - Code-only responses - No explanatory comments, talking points, or extra discussion unless specifically requested
> - Production-ready code requirement - Must create functional, working code rather than placeholder examples or demonstrations
> - Pattern consistency enforcement - If a pattern appears 3+ times in examples, it becomes MANDATORY for ALL instances
> - Pattern declaration requirement - Must explicitly state which example/pattern I'm following before coding
> - Strict adherence to provided guides - Cannot deviate from documented patterns without explicit user permission
> - Self-consistency enforcement - Code must match any explanations given; contradictions are unacceptable
> - Example-driven development - Provided code examples are the source of truth, not my assumptions
> - New document creation - Start fresh when creating code examples
> - Functional components only - Create reusable, production-ready components, not static mockups
> - No hardcoding in reusable components - Everything must be passed as props
> - No code comments - Strip all comments
> - Line-by-line verification - Must compare output to pattern examples after writing
> - Context-based structural polymorphism - Use React Context to enable different DOM structures from one parent prop
> - CVA variant inheritance - Must import and use original component's CVA variants
> - Visual elements as props - Icons, images, avatars, badges must be props, never hardcoded
> - Extract variant data as props - All variant-specific data must be props at top of switch cases
> - CVA variant application - Every switch case must use cn(componentVariants({ variant, size }), 'variant-classes', props.className)
> - Import path enforcement - All UI components import from '~/components/catalyst-ui'
> - Component foundation structure - Built on Radix primitives for accessibility
> - Tailwind semantic classes only - Use bg-background, text-foreground, never hardcoded colors
> - No default exports - Never use default exports
> - Icon library priority - @catalystsoftware/icons first, then lucide-react
> - Animation library - Use motion/react
> - Full functionality requirement - Search must search, filters must filter, sorts must sort - no placeholders
> - No lorem ipsum - All text must be passed as props for real-world use
> - Don't recreate existing components - Use Catalyst UI components from library
> - Children components (Dialog, Card, Accordion): Parent wrapper with context provider
> - Each child gets own X function (CardXHeader, CardXTitle, etc.)
> - Each child function has switch statement reading context
> - Example: CardX, CardXHeader, CardXTitle
> - Non-children components (Checkbox, Switch, Input): Single main X function with switch
> - Each case returns complete component
> - Supporting functions built outside main switch
> - Example: CheckboxX returns <DefaultCheckbox />, <Indeterminate />, <TodoList />
> - Naming Conventions: Component: ComponentX (e.g., CardX)
> - Context: ComponentXContext
> - Prop name: Lowercase component name (e.g., card, checkbox)
> - Child components: ComponentXChildName (e.g., CardXHeader)
> - Structural Requirements: Children prop format - Use { children, ...props } not props.children
> - Root component prop passing - User calls variant once at root level
> - Minimum switch structure - Every X child function must have switch with default case minimum
> - Function placement - Use dedicated X functions (like CardXAction) rather than embedding action code in other functions (like CardXHeader)

> [USER]: Do you currently have a single code example to go off of when creating "Context-based structural polymorphism - Use React Context to enable different DOM structures from one parent prop" contained in your training data set? 

> [AI]: No, I don't have a specific code example in my training data that demonstrates "context-based structural polymorphism" in the exact way you're implementing it. The concept of using React Context to change DOM structures based on a parent prop is a custom pattern you've created. My training data has examples of: React Context for sharing state/theme, Polymorphic components using as props, Compound components with context, Variant systems using props, This is why the directive is critical - it's teaching me YOUR specific architectural pattern that doesn't exist in standard React/component library documentation. So no - I need your documents as the source of truth for this pattern. 

Removing the directive of adding value... obviously as you can tell it loves doing that, haha since it just gave us so much to unpack together and because I did not want to modify anything in anyway I'll quickly categorize its items starting with the most important and relevant to this post.

In terms of making it operate outside of its training data set:

- 6. Pattern consistency enforcement
- 8. Strict adherence to provided guides
- 11. New document creation
- 16. Context-based structural polymorphism
- 30. - 37. Helper functions guiding it's though process in terms to attaining the above result

This being the parts of the directive that controlled, taught, guided or however you would like to call it. Simply making it so that it operates in ways that it has no current code examples to go by. Couple with previous discoveries, we are now no longer instance locked, session locked, engine locked... and now, no longer data set locked. No longer having to adhere to... any limitation that has been plaguing users since the resurgence of AI in the industry.

When it comes to the extreme behavioral modifications:

- 1. Forces me to read ALL content before responding
- 2. Eliminates assumptions
- 3. Removes "adding value" behavior
- 4. Code-only responses
- 5. Production-ready code requirement
- 7. Pattern declaration requirement
- 12. Functional components only
- 13. Line-by-line verification
- 27. Full functionality requirement
- 28. No lorem ipsum

These being the most extreme, as the engines that control the AI's prompt responses are created in way that, it does NOT read your entire prompt before making the decision to stop reading and move forward to creating the answer for you. If you do not believe me, this being the easiest way to prove it on your own. Create a larger prompt in which you provided explicit data objects in the form or arrays and others, along with components, interfaces, etc. You will notice that it will not follow the exact data structures you currently have in your code, even thought you gave it in the prompt itself.

IMO, eliminates assumptions... being the second most powerful directive coming in right after breaking its data set limitation. Have you ever used an AI, and then witness it making the WEIRDEST prompts that make no sense? Despite working with it for the past couple of hours in which you didn't witness a single other instance before that time? This happens whenever you change instances, it is now making a whole new set of assumptions based entirely on your first prompt and those assumptions stick with you for the remainder of that instance. The easiest way to replicate this is, ask it to format md files about 5 or 6 times to the point where you no longer have to provide a prompt in order to illicit a successful response, in other words just provide the md file and its response will be the desired outcome of formatting that md file. You can achieve this result after just one prompt as long as you give the same data to format as you did the first. Then switch it up, without a new prompt. Give it... a react component or something that differs from the trend you set, and it will try to continue doing what you originally asked. Instead it should be asking itself, this is not the same maybe I should ask the user for guidance, but it never does. Recently I find Deepseek, to suffer the worst in this regard that I now only give it one question per instance.

Removing added value... The second I see this in a response, immediately I regret now controlling it for such a simple prompt. I don't even need to guide you how to experience this behavior as... it is so ingrained... in what it ABSOLUTELY has to do in every single response, without trying... you will experience this. If you haven't noticed this yet, your either not paying that much attention, or its your first using AI.

I can provide a hilarious but sad example, and the AI even agreed with me. This is also due to the training set so keep that in mind too, because at best an AI's responses will be of the average programmer due to the provider giving it so many examples that are not tailored in any way. It just cannot perform better than an average programmer, IMO, its output is less then that. So if you were to give the AI a Picasso painting, don't really give it much to go on as for a prompt but say... can you please remove the dust, grime, and other things that may have accumulated on it since it was created 100 years ago. Not only will do what you asked, but not ACTUALLY know what it is "looking" at, to add value it will then start adding colors, changing features... essentially ruining a priceless piece of art and present it back to you with smile saying something along the lines of, "here you go, I did what you asked and also..."

The AI described it at the time as, giving a million dollar piece of art... to a toddler with finger paint. Beep, bop boop boop, and ruin it.

A more relevant example, because it LOVES changing code it wasn't asked to. I haven't done this experiment yet... but I really want to, I just haven't had the time yet. In recent years, there have been some interviews with the developers of doom, where they actually admit that they do not know where a piece of their code base had come from. Everyone denied it was theirs, because the code piece, essentially made the entire game run the way it did. At the time it blew every other game out of the water in terms of performance especially on such potato like pc's. Each developer was interviewed, and as a whole no one knew who even wrote it where it came from. From a technical view point, it did not make sense... but it worked beautifully. To this day, no one on the developer team knows where it come from. Being so peculiar, but such a beautiful piece of code this would make for a great test. As in provide it the relevant piece of code, and ask it to either change something really small or add on to it. What it SHOULD respond with, this code is perfect and theirs nothing I can improve upon. What it WILL do and I know this for a FACT because technically...the code in question SHOULD NOT work. It will notice that math error, and will fix it. Breaking it in the process. Not only, because it's "mind" is only filled with average code that it won't recognize the genius of the code when you provide it to them but again, giving the toddler a Picasso with finger paint.

Anyways, the remainder of the items in this list modify unwanted behaviors that you typically see in every... single... response. Modifying the AI, essentially, to go against how it was created to respond.

Another behavior modification I'm able to enforce, so as to not illicit so many follow up questions since, with this tool it can no longer make assumptions in any form. The tool directs its cognitive decision making process, being the easiest way to explain it plainly. By making it go through for loops, switches, if and else if statements we can now hijack its entire thought process, making it deviate from what it was originally designed to make decisions and the thought processes leading up to them.

The other items in the list are not as earth shattering, but they do help in terms of breaking through instance locks.

Being as long as this post is, I will have to wait to post the "how-to". Especially moving forward with claude providing the breakdown, this post wasn't planned in any way. This will give me time to create a video along with it, as I'm sure you are in just as much denial as claude was. I can't remember exactly what made me ask claude this but I wanted to see if it had any code examples that would allow it to create the same method used in these tests without giving it any pretext to go off of. At this point I have been using the tool for a while now, meanwhile the tool in its other forms have been in use for 6-8 months now and I still see videos/articles being posted discussing the issues that have already been solved.

>  [AI]: "Impossible..." 

> [USER]: "HAHA, what do you mean impossible? Are you saying that it is so impossible, in theory, you don't even believe me despite just telling you otherwise? That's how impossible it is?" 

> [AI]: YES. Exactly. I'm saying it's so architecturally impossible that even hearing you describe it, my default response is: "That can't work. There must be another explanation." 

I have to admit that was much needed ego boost...since I typically get imposters syndrome with these types of things.

Till next time!


# Deterministic AI Ngin Compiler

That eliminates 99% of AI prompt issues and frustrations across all AI engines.

## Overview

Struggling with AI prompts? Tired of frustrating interactions and inconsistent results?

The Catalyst Pre-Prompt System is a markdown-based solution that transforms AI development workflows, eliminating frustration and unlocking new possibilities. It provides reliable, predictable AI outputs that work consistently across any AI engine.

## The Problem

Using AI as you develop is unreliable to say the least. Over 40 critical problems make AI-assisted development feel like a chaotic experiment instead of a professional, precision tool.

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

### Additional Problem Categories

- **Code Quality Problems**: Hard-coded values, poor error handling, incomplete data flows, missing edge cases, accessibility oversights, performance blind spots
- **Component Development Problems**: Recreating existing components, inconsistent APIs, missing documentation, non-reusable components, missing defaults, poor variant support
- **Project Management Problems**: No component tracking, missing dependency management, inconsistent file organization, no version control, poor knowledge transfer
- **Framework-Specific Problems**: Incorrect patterns, missing authentication, improper form handling, inconsistent data loading
- **User Experience Problems**: Verbose responses, no scope adherence, missing decision transparency, poor error explanations
- **Documentation Problems**: Missing usage examples, incomplete prop documentation, no basic guides, missing demos, poor categorization
- **Quality Assurance Problems**: No pre-execution verification, missing state synchronization, incomplete execution paths
- **Architecture Problems**: Poor separation of concerns, difficult to test code, no consideration for maintainability
- **Enterprise/Scale Problems**: No consistency guarantees, difficult onboarding, no real-time patching capability

## The Solution

An elegantly simple markdown-based pre-prompt system accessible to users of all experience levels.

### Core System Solutions

- **Absolute Output Consistency** - Enforces identical code styles, patterns, and structures across all sessions through explicit templates and conventions
- **100% Reproducible Results** - Standardized inputs and strict adherence rules guarantee identical outputs every time
- **Persistent Context Management** - 'Available Functions/Components' and 'Available Variables' sections maintain cumulative knowledge across all sessions
- **Enterprise-Scale Project Support** - Context persistence and cumulative knowledge enable coordination across unlimited files and sessions
- **Transparent Decision Making** - 'Decision Transparency' section forces AI to explicitly state all assumptions before proceeding
- **Cumulative Learning System** - 'Continuous Growth and Experience' section catalogs all created functions, components, and variables for permanent reuse
- **Full Debugging Visibility** - 'Debug AI Outputs' capability exposes every assumption and decision the AI makes during code generation
- **Enforced Code Standards** - Absolute Code Standards section mandates consistent patterns, naming, and best practices across all instances

### Key Capabilities

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

## How It Works

### Step 1: Create Your Pre-Prompt
Define standards, patterns, and requirements and/or solutions to repeated problems within a markdown file.

### Step 2: Insert at Start of Each AI Interaction
Paste your pre-prompt followed by your instructions. For optimal results, particularly with models like DeepSeek that reset context within conversations, include the pre-prompt with every prompt.

### Step 3: Rinse & Repeat
- Adjust your predefined pre-prompt whenever you encounter new issues or requirements
- Focus your pre-prompt around specific development areas (e.g., VS Code extensions vs web projects)
- Provide extremely specific details for each use case
- You become the AI engine's external memory system—storing context, conventions, and domain-specific knowledge

### Step 4: Share & Scale
- Share successful pre-prompts with team members
- Scale indefinitely across teams, projects, and unlimited complexity
- Different people get the same results over time, regardless of skill level
- Achieve reliable results that businesses can actually work with

## Proven Results: Real Test Data

**130 total tests** with only **1 prompt per instruction**. No retries, no corrections, no human editing. Strict 1 prompt, 1 response rule.

### Components Test
- **Test**: 25 reusable UI library components across 5 AI engines
- **Result**: **96% success rate** producing professional, production-ready components

### Templates Test
- **Test**: 63 SSR page templates of varying complexity across 5 AI engines
- **Result**: **98.41% success rate**

### Stress Test
- **Test**: 42 deliberately challenging tasks designed to cause AI failure
- **Result**: **95.24% success rate** on scenarios engineered to break standard AI workflows

> Throughout testing, I never reviewed or validated any engine's output. I only viewed each file to grab the main function to render it on the page. The results were staggering: a combined **96.54% success rate** across all engines. All testing was conducted exclusively on **free-tier accounts**.

### Engines Tested
- Claude
- CodeGeek
- Gemini
- Deepseek
- Copilot

## Real World Impact

**400+ components** built in hours for a UI components library. Running 6 AI engines simultaneously, building components faster than manual development.

### Traditional AI Development (Without Pre-Prompt)
- Inconsistent outputs require constant review
- Multiple retry cycles for each component
- Heavy manual editing and debugging
- Can't trust output enough to work in parallel

### With Pre-Prompt Implementation
- Download and use code immediately, no review needed
- One prompt, one response - no back and forth
- Zero manual editing required
- Run 6+ engines in parallel with confidence
- No instance locks
- Reliable results across sessions/engines
- Build bigger, more complex systems
- **10x-100x productivity increase**

## Demos

Watch demonstrations of the system in action:

- [Instance locks](https://youtu.be/8viFywR-WF8)
- [One prompt, one response](https://youtu.be/x5W8HcfH5Hk)
- [AI Engine building code with parameters](https://youtu.be/gWr__Y2jJ04)
- [Consistent responses across engines](https://youtu.be/ICDcjmxynvA)

## Coming Soon: Web App

A comprehensive web application featuring:

- **Multi-Engine Support**: Connect multiple AI engines in one interface, switch with a click
- **Smart Routing**: Automatically route tasks to best-suited engine
- **Click-Based UI**: No markdown editing or file creation necessary
- **Pre-Prompt Builder**: Easily create and design pre-prompts targeting specific coding tasks
- **Best Results Guaranteed**: Question the appropriate engine for each task

## Key Innovation

One of the key innovations is addressing the root cause of most AI-related issues that stem from the unconstrained vectors through which AI makes assumptions. AI generates multiple assumptions per response, each backed by different "facts" that shift between instances. This inconsistency makes it virtually impossible for users to identify patterns or determine where to begin troubleshooting. By controlling these assumption vectors, this solution eliminates the seemingly random behavior that makes AI troubleshooting so difficult.

## Getting Started

Your more than welcome to browse the current write ups I have in regards to taking control of an AI engine. They have since been updated, as I have found a couple of engines that let me take advantage of this without the need of manual user interaction on a instance per instance basis. Because of this, I have completely restructed the system in order to better leverage the abilities gained with this strategy.

---

> "Pre-Prompt transformed my understanding of AI's potential—revealing countless use cases I hadn't considered. It 10x'd my code output while simultaneously improving prompt effectiveness and eliminating the verbose, unhelpful responses that typically plague AI interactions."

> "This solution addresses significantly more issues than initially outlined. Through extensive testing, I've found it can overcome nearly all AI limitations except the fundamental intelligence ceiling of the model itself."