

## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Create Export Index && Create Named Export Index

Generate index files that act as registries for easier imports across your project.

**Access:** Right-click any folder → Create Export Index

**Use Case Example:**

Instead of importing each component individually:
```javascript
import DemoOne from './blocks/DemoOne';
import DemoTwo from './blocks/DemoTwo';
import LoanApp from './blocks/LoanApp';
// ... 1550+ more imports
```

Create a registry and import once:
```javascript
import * as Components from './index';

// Then use:
<Components.LoanApp />
<Components.ServiceRepairForm />
<Components.DemoOne />
```

**Features:**
- Recursive export generation
- Works with any folder structure
- Saves massive time on large component libraries
- Enables find-and-replace workflows
- Creates index.tsx automatically

**Real-World Impact:** Converted 1550+ individual imports to single registry import using find-and-replace in seconds.

![Registry](https://raw.githubusercontent.com/8an3/midgardr-notes/main/config/registry.jpg)

---


## <img src="https://raw.githubusercontent.com/8an3/midgardr-notes/main/utils/vulknut.png" width="32"  style="vertical-align: middle; margin-bottom: 4px;"> Markdown Pre-Processor