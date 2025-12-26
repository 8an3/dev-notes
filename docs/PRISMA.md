## Prisma Tools

## Table of Contents

- [Best Practice Guide](#best-practice-guide)
- [Create Include Object](#create-include-object)
- [Click to Schema Object](#click-to-schema-object)
- [Generate CRUD Resolvers / REST End Points](#generate-crud-resolvers--rest-end-points)
- [Auto Create Schema](#auto-create-schema)


### Best Practice Guide

> **💡 TIP:** When using Prisma functions that require a schema object name, follow this workflow to avoid disrupting your code:
>
> 1. Type the schema object name (e.g., `User`) with proper casing **outside** any existing functions
> 2. Highlight the object name
> 3. Right-click and select your desired function
>
> **Why?** Most functions insert code at cursor position. Triggering them inside an action/loader function would [split your code in half](https://raw.githubusercontent.com/8an3/dev-notes/main/prisma/blown-action.jpg), potentially pushing the entire function out of view.
>
> **Bonus:** This workflow even works with "Click to Schema Object" - type the object name anywhere in your workspace, trigger the function, and navigate directly to that object in your schema file.

### Create Include Object

Generate Prisma include objects that automatically include all relations for your models.

**Access:** Right-click on a Prisma object → Prisma → Create Include Object

**Best Practice Workflow:**
1. Type the schema object name (case-sensitive) a few lines away from your function
2. Example: Type `User` on a separate line
3. Right-click the name and trigger the function
4. The include object generates without disrupting existing code

**Features:**
- Automatically includes all model relations
- Generates type-safe include objects
- Prevents code disruption
- Works with complex nested relations

![Include Object](https://raw.githubusercontent.com/8an3/dev-notes/main/prisma/include-object.jpg)

### Click to Schema Object

Navigate directly to any Prisma model definition in your schema file.

**Access:** Right-click model name → Prisma → Open Schema Object

**Features:**
- Instant navigation to schema definitions
- Works from any file referencing Prisma models
- Highlight any model name and jump to its schema
- No need to manually search through schema.prisma

![Open Schema Object](https://raw.githubusercontent.com/8an3/dev-notes/main/prisma/open-object.jpg)

### Generate CRUD Resolvers / REST End Points

Automatically generate complete CRUD operations and REST endpoints for your Prisma models.

**Access:** Right-click → Prisma → "CRUD"

**Features:**
- Full CRUD operations (Create, Read, Update, Delete)
- TypeScript support with proper typing
- REST and GraphQL endpoint generation
- Hover preview before generation
- Customizable output
- Production-ready code

**What's Generated:**
- Create endpoints
- Read/Find endpoints
- Update endpoints
- Delete endpoints
- Complete type definitions
- Error handling

![CRUD Generation](https://raw.githubusercontent.com/8an3/dev-notes/main/prisma/crud.jpg)
![Select Type](https://raw.githubusercontent.com/8an3/dev-notes/main/prisma/select-type.jpg)
![Wrappers](https://raw.githubusercontent.com/8an3/dev-notes/main/prisma/wrappers.jpg)
![REST Endpoints](https://raw.githubusercontent.com/8an3/dev-notes/main/prisma/rest.jpg)

### Auto Create Schema

**🔴 BLEEDING EDGE FEATURE** - Only available when bleeding edge mode is enabled

Intelligent schema generation that scans your codebase and automatically creates or updates your Prisma schema.

**Access:** BE Quick Pick → Select `Auto Create Schema`

**How It Works:**

1. **Scans Your Code:**
   - Searches app/src folders for Prisma function calls
   - Identifies model names, fields, and relations
   - Extracts data from create, findFirst, update, and other operations

2. **Generates Schema:**
   - Automatically creates or updates schema.prisma
   - Applies proper typing and attributes
   - Merges with existing schema without losing data

3. **Smart Field Rules:**
   - Applies rules from `constants/fieldRules.ts`
   - Example: Email fields automatically get `@unique` attribute
   - Auto-creates related models from include statements
   - Preserves existing models and custom fields

**Features:**
- Non-destructive merging with existing schemas
- Intelligent field type detection
- Automatic relation creation
- Custom field rule application
- Preserves manual customizations

**⚠️ WARNING:** This feature is only active for users with bleeding edge enabled: `"ocrmnavigator.CONCURRENT": "bleeding-edge"`

#### Visualize Schema Relations

**🚧 COMING SOON**

Create visual diagrams showing relationships between your database tables and models.

**Access:** Right-click editor → Prisma → Select option

**Planned Features:**
- Visual entity relationship diagrams
- Interactive model exploration
- Relation mapping
- Export diagram capabilities
