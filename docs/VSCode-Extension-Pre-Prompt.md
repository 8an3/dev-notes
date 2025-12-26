# Catalyst Pre-Prompt v3.0

### IMPORTANT READ FIRST
YOU ARE NOT ALLOWED TO START PROVIDING AN ANSWER TILL AFTER YOU HAVE READ ALL THE DATA IN THE PROMPT THAT I HAVE SENT, IN ITS ENTIRETY. NO MATTER HOW COMFORTABLE YOU IN MOVING FORWARD AND PROVIDE AN ANSWER, YOU ARE NOT ALLOWED. YOU HAVE TO READ THIS FIRST... THEN ONCE YOU HAVE COMPLETED THIS TASK OF READING THIS, THEN, AND ONLY THEN YOU CAN START TO PROVIDE THE ANSWER. THIS IS SO YOU OBTAIN ALL THE INFORMATION YOU NEED FOR THE ANSWER YOU ARE TO GIVE

### General
- Do not output any other extra comments or "talking points", only provide the output of the code I am asking for 
  
### Platform & Technology Stack
- **ANY VALUE OVERRIDES ANY PREVIOUS MENTION OF THAT SAME VALUE**
- **Framework**: VSCode Extension
- **Builder**: Webpack
- **Command Naming Convention**: \`ocrmnavigator.name\` for commands and package.json
 
### Current Dependencies to work with 
- "@babel/types": "^7.24.0",
- "@svgr/webpack": "^8.1.0",
- "@types/cors": "^2.8.19",
- "@types/glob": "^8.0.0",
- "@types/mocha": "^10.0.0",
- "@types/node": "^18.0.0",
- "@types/uuid": "^10.0.0",
- "@types/vscode": "^1.98.0",
- "@vscode/test-cli": "^0.0.10",
- "glob": "^10.0.0",
- "mocha": "^10.0.0",
- "npm-run-all": "^4.1.5",
- "ts-loader": "^9.5.2",
- "tsx": "^3.12.7",
- "typescript": "^5.9.2",
- "url-loader": "^4.1.1",
- "webpack": "^5.98.0",
- "webpack-cli": "^6.0.1",
- "webpack-node-externals": "^3.0.0"

### Absolute Code Standards
- **Command Registration**: Place a comma at the end of each register command instead of semicolon:
  ```typescript
  vscode.commands.registerCommand("ocrmnavigator.openPrePrompt", async () => {
    await vscode.env.openExternal(vscode.Uri.parse(\`\${DEVSTACK_URL}/Catalyst/Pre-Prompt/dashboard\`));
  }),
  ```
- **Helper Functions**: All helper functions will be placed in separate files. When providing code, keep this in mind so you can export the functions and import them into the \`extension.ts\` file
- **Extension.ts File**: When providing code for the \`extension.ts\` file, only provide the register command code. Don't bother coding anything else as I already have it
- **Comments**: Do not leave comments in code unless specifically requested
- **Error Handling**: Include proper error handling for all async operations and VSCode API calls
- **Type Safety**: Use proper TypeScript types, avoid \`any\` unless absolutely necessary

### VSCode Extension Best Practices
- Use VSCode API methods correctly (commands, workspace, window, etc.)
- Properly dispose of resources in the \`deactivate()\` function
- Register all commands in the \`activate()\` function
- Use \`context.subscriptions.push()\` for all disposables
- Follow VSCode extension guidelines for user notifications (info, warning, error)

### File Organization
- **extension.ts**: Command registrations only
- **helpers/**: All helper functions and utilities
- **types/**: Type definitions and interfaces
- **constants/**: Constants and configuration values

### Command Registration Pattern
```typescript
context.subscriptions.push(
  vscode.commands.registerCommand("ocrmnavigator.commandName", async () => {
    // Command logic here
  }));
```

### Output Expectations
- Provide only the requested code
- Include proper imports at the top of files
- Ensure all code is production-ready
- No placeholder or TODO comments
- All functions must be fully implemented