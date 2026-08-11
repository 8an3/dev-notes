## CUSTOM_FUNCTION_BREAKDOWNS

> [!TIP]
> Any use of a package manager in any breakdown first checks to see what package manager you currently are using within the project and executes the desired command with that mgr.
>
> Any time that format package.json, convert readme, etc needs to have the extensions settings to be configured to allow it to run. 
>
> Whenever each process reaches the final steps, there is a delay coded in between install, save all and reload window, due to early tests showing that the execution was executing too fast resulting in steps being skipped



<pre style="max-width: 800px; white-space: pre-wrap; overflow-wrap: break-word;">
/ Order 1/
├── 1. Save all
├── 2. format package.json 
├── 3. Convert readme.md 
├── 4. Compile 
│       ├── if using vsce to create the archive executes vsce, then publish
│       └── if not, uses custom archiver to create the vsix archive
├── 5. Install vsix
├── 6. save all, incase you kept coding while the above was being executed 
└── 7. reload window
</pre>

<pre style="max-width: 800px; white-space: pre-wrap; overflow-wrap: break-word;">
/ Order 2/
├── 1. Save all
├── 2. trigger autorun folder
├── 3. format package.json 
├── 4. Convert readme.md 
├── 5. Compile 
│       ├── if using vsce to create the archive executes vsce, then publish
│       └── if not, uses custom archiver to create the vsix archive
├── 6. Install vsix
├── 7. save all, incase you kept coding while the above was being executed 
└── 8. reload window
</pre>

<pre style="max-width: 800px; white-space: pre-wrap; overflow-wrap: break-word;">
/ Order 3/
├── 1. Save all ( dont use this one as it is coded for personal use)
├── 2. start icons build and push processs
├── 3. start ui build and push processs
├── 4. format package.json 
├── 5. Compile 
│       ├── if using vsce to create the archive executes vsce, then publish
│       └── if not, uses custom archiver to create the vsix archive
├── 6. Install vsix
├── 7. save all, incase you kept coding while the above was being executed 
└── 8. reload window
</pre>

<pre style="max-width: 800px; white-space: pre-wrap; overflow-wrap: break-word;">
/ Order 4/
├── 1. Save all ( dont use this one as it is coded for personal use)
├── 2. start icons build and push processs
├── 3. start ui build and push processs
├── 4. trigger autorun 
├── 5. format package.json 
├── 6. convert readme 
├── 7. Compile 
│       ├── if using vsce to create the archive executes vsce, then publish
│       └── if not, uses custom archiver to create the vsix archive
├── 8. Install vsix
├── 9. push vsix via rest api
├── 10. save all, incase you kept coding while the above was being executed 
└── 11. reload window
</pre>

<pre style="max-width: 800px; white-space: pre-wrap; overflow-wrap: break-word;">
/ Order 5/
├── 1. Save all 
├── 2. bump patch
├── 3. format package.json 
├── 4. Compile 
│       ├── if using vsce to create the archive executes vsce, then publish
│       └── if not, uses custom archiver to create the vsix archive
├── 5. Install vsix
├── 6. push vsix via rest api
├── 7. save all, incase you kept coding while the above was being executed 
└── 8. reload window
</pre>

<pre style="max-width: 800px; white-space: pre-wrap; overflow-wrap: break-word;">
/ Order 10/
├── 1. Save all 
├── 2. git add
├── 3. git commit 
└── 4. git push 
</pre>






