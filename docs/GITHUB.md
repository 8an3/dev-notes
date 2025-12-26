

## GitHub Tools

## Table of Contents

- [Repo Management](#repo-management)
- [Open Repo in Browser](#open-repo-in-browser)
- [Open Repo at File](#open-repo-at-file)
- [Pro7 Archiver](#pro7-archiver)

### Repo Management

Comprehensive GitHub repository management and functionality accessible from multiple locations

**Access Options:**
- Status bar → DevStack Quick Pick
- Right-click editor → GitHub → Select option

**Features:**
- Complete repository management
- Git operations integration
- Direct browser access
- File-specific navigation

See DevStack Quick Pick documentation for full feature outline.

![GitHub Functions](https://raw.githubusercontent.com/8an3/dev-notes/main/github/github-pic.jpg?raw=true)
![GitHub Context Menu](https://raw.githubusercontent.com/8an3/dev-notes/main/github/contextr.jpg?raw=true)


### Open Repo in Browser

Open your GitHub repository in browser directly from any file in your workspace

**Access:** Right-click → Open GitHub Repo

**Features:**
- Instant browser access
- Works from any file
- Automatic repository detection
- No manual URL entry needed

[Video Demo](https://youtu.be/CQ2rYtbZKJk)


### Open Repo at File

Navigate directly to a specific file's location in your GitHub repository

**Access:** Right-click → Open GitHub at File

**Features:**
- Direct file navigation
- Opens exact file location in GitHub
- Preserves directory structure
- Line number support

[Video Demo](https://youtu.be/0CLkYvWSVqI)


### Pro7 Archiver

Create password-encrypted archives containing sensitive files for safe inclusion in your GitHub repository

**Access Options:**
- DevStack Quick Pick menu
- Automatically runs in `G4 & .vsix` workflow
- Custom command sequences (concurrent/sequential objects)

**How It Works:**

1. **Configuration Scan:**
   - Scans workspace root for `.pro7` config file
   - If found: collects files specified in `.pro7` (similar to `.gitignore` but for inclusion)
   - If not found: defaults to including `.env` file only

2. **Password Setup:**
   - Checks `.env` file for `PRO7_PASSWORD` value
   - If not found: prompts for password input
   - Uses password to encrypt archive

3. **Archive Creation:**
   - Creates password-protected `.7z` archive
   - Places archive in workspace root
   - Updates archive automatically with latest changes

4. **Integration:**
   - Runs automatically in `G4 & .vsix` workflow
   - Ensures archive is up-to-date before GitHub push
   - Zero extra effort required

**`.pro7` Configuration Example:**

```
.env
.secrets.env
config/
secrets/
*.key
*.pem
api-keys.json
```

**Custom Command Integration:**

To include Pro7 Archiver in custom command sequences:

```json
{
  "label": "Your Label",
  "type": "command",
  "path": "ocrmnavigator.pro7Archiver",
  "hidden": true
}
```

**Alternative: Standalone Script**

If the extension version doesn't work reliably, use the standalone script approach:

1. Place `pro7.js` in your autorun folder
2. Set extension setting to false: `"ocrmnavigator.PRO7": false`
3. Script runs separately from other autorun scripts

**Why Separate Script?** Microsoft's antivirus checks flag password-protected archives within `.vsix` files, causing potential issues.

<details>
<summary><b>pro7.js - Standalone Script</b></summary>

```javascript
const fs = require('fs');
const path = require('path');
const { glob } = require('glob');
const sevenBin = require('7zip-bin');
const { extractFull, add, list } = require('node-7z');

const WORKSPACE_ROOT = path.join(__dirname, '..', '..');
const PRO7_FILE = path.join(WORKSPACE_ROOT, '.pro7');
const ENV_FILE = path.join(WORKSPACE_ROOT, '.env');
const OUTPUT_PATH = path.join(WORKSPACE_ROOT, `pro7-${Date.now()}.7z`);
require('dotenv').config({ path: ENV_FILE });

async function pro7Archiver() {
    try {
        const password = process.env.PRO7_PASSWORD;
        if (!password) {
            console.error('✗ PRO7_PASSWORD is not set in .env file!');
            console.log('\nPlease set PRO7_PASSWORD in your .env file');
            process.exit(1);
        }

        let filesToArchive = [];

        if (fs.existsSync(ENV_FILE)) {
            filesToArchive.push(ENV_FILE);
            console.log('\n✓ Found .env file');
        }

        if (fs.existsSync(PRO7_FILE)) {
            console.log('✓ Found .pro7 file');

            const content = fs.readFileSync(PRO7_FILE, 'utf8');
            const lines = content.split('\n');

            for (const line of lines) {
                const trimmed = line.trim();

                if (!trimmed || trimmed.startsWith('#')) continue;

                if (trimmed.includes('*')) {
                    const globFiles = await glob(trimmed, { cwd: WORKSPACE_ROOT, absolute: true });
                    filesToArchive.push(...globFiles);
                    console.log(`✓ Found ${globFiles.length} files`);
                } else {
                    const fullPath = path.join(WORKSPACE_ROOT, trimmed);
                    if (fs.existsSync(fullPath)) {
                        filesToArchive.push(fullPath);
                        console.log(`✓ Added: ${trimmed}`);
                    } else {
                        console.log(`✗ Not found: ${trimmed}`);
                    }
                }
            }

            filesToArchive = [...new Set(filesToArchive)];
        } else {
            console.log('✗ .pro7 file not found');
        }

        if (filesToArchive.length === 0) {
            console.error('\n✗ No files to archive!');
            process.exit(1);
        }

        console.log('\n✓ Cleaning up old archives...');
        const existingArchives = await glob('pro7-*.7z', { cwd: WORKSPACE_ROOT, absolute: true });
        for (const archive of existingArchives) {
            fs.unlinkSync(archive);
            console.log(`  Deleted: ${path.basename(archive)}`);
        }

        const stream = add(OUTPUT_PATH, filesToArchive, {
            password: password,
            method: ['0=BCJ2', '1=LZMA2'],
            $bin: sevenBin.path7za,
            $progress: true
        });

        await new Promise((resolve, reject) => {
            stream.on('end', resolve);
            stream.on('error', reject);
        });

        console.log('✓ Archive path:', OUTPUT_PATH);

        const listStream = list(OUTPUT_PATH, {
            password: password,
            $bin: sevenBin.path7za
        });

        let fileCount = 0;
        listStream.on('data', (data) => {
            if (data.file) fileCount++;
        });

        await new Promise((resolve, reject) => {
            listStream.on('end', resolve);
            listStream.on('error', reject);
        });

        console.log(`✓ Archive contains `);
        console.log(`✓ ARCHIVING COMPLETED SUCCESSFULLY - CONTAINS ${fileCount} ${fileCount === 1 ? 'FILE' : 'FILES'}`);

    } catch (error) {
        console.error('\n' + '='.repeat(60));
        console.error('✗ ARCHIVE CREATION FAILED');
        console.error('='.repeat(60));
        console.error('\nError message:', error.message);
        console.error('Stack trace:', error.stack);
        process.exit(1);
    }
}

console.log('='.repeat(60));
console.log('PRO7 ARCHIVER');
console.log('='.repeat(60));
pro7Archiver();
```


</details>
---

[🡄 Return](https://github.com/8an3/DevStack)
