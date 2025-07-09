# HomeTab Dynamic Updates Property Descriptions

## HomeTab Updates Property Descriptions

### `badge: string`
**Required** - A short text label displayed as a badge on the update card.

**Example Values**:
```typescript
    "RemixAI Assistant"
    "v0.59.0 Release"
    "IMPORTANT"
    "FEATURE"
    ...
```

### `title: string`
**Required** - The main headline or title of the update.

**Example Values**:
```typescript
    "New Solidity Compiler Version Available"
    "Enhanced Debugger Features Released"
    "Security Update for Contract Verification"
    "New Plugin Manager Interface"
    ...
```

### `description: string`
**Required** - A short description of the update or announcement.

**Example Values**:
```typescript
    "Updated to Solidity 0.8.19 with improved gas optimization and new language features. Includes better error messages and enhanced type checking."
    "Added support for step-by-step debugging with variable inspection, call stack navigation, and breakpoint management for smart contracts."
    "Critical security patches applied to prevent potential vulnerabilities in contract verification. All users are recommended to update immediately."
    "Completely redesigned plugin manager with improved search, categorization, and installation workflow for better user experience."
    ...
```

### `icon: string`
**Required** - CSS class name for the update's icon.

**Description**: This defines the icon displayed alongside the update information. It should use Font Awesome, Remix-specific icon classes, or other icon libraries to visually represent the type of update.

**Example Values**:
```typescript
    "fa-solid fa-download"
    "fa-solid fa-star"
    "fa-solid fa-shield-halved"
    "fa-solid fa-rocket"
    ...
```

#### `action.type: 'link' | 'methodCall'`
**Required** - Specifies the type of action to perform.

**Possible Values**:
- `"link"` - Opens an external URL in a new tab
- `"methodCall"` - Calls an internal plugin method

#### `action.label: string`
**Required** - The text displayed on the action button.

**Example Values**:
```typescript
    "Download Now"
    "Learn More"
    "Update Now"
    "View Changelog"
    ...
```

#### `action.url?: string`
**Optional** - The external URL to open when `action.type` is `"link"`.

**Example Values**:
```typescript
    "https://github.com/ethereum/remix-project/releases"
    "https://remix-ide.readthedocs.io/en/latest/new_features.html"
    "https://docs.soliditylang.org/en/latest/080-breaking-changes.html"
    "https://ethereum.org/developers/docs/smart-contracts/debugging/"
    ...
```

#### `action.pluginName?: string`
**Optional** - The name of the plugin to call when `action.type` is `"methodCall"`.

**Example Values**:
```typescript
    "menuicons"
    "pluginManager"
    "settings"
    "themeModule"
    ...
```

#### `action.pluginMethod?: string`
**Optional** - The method name to call on the specified plugin when `action.type` is `"methodCall"`.

**Example Values**:
```typescript
    "select"
    "activate"
    "open"
    "update"
    ...
```

#### `action.pluginArgs?: (string | number | boolean | object | null)[]`
**Optional** - Arguments to pass to the plugin method when `action.type` is `"methodCall"`.

**Example Values**:
```typescript
    ["compiler"]
    [true]
    [{ version: "latest", autoUpdate: true }]
    ...
```

### `theme: string`
**Required** - Defines the visual theme or styling for the update card.

**Example Values**:
```typescript
"primary"      // Blue theme for general updates
"success"      // Green theme for new features
"warning"      // Yellow theme for important notices
"danger"       // Red theme for critical updates
"info"         // Light blue theme for informational updates
"secondary"    // Gray theme for minor updates
"dark"         // Dark theme for special announcements
"light"        // Light theme for subtle notifications
"ai"            // AI theme
```

The `theme` property typically maps to Bootstrap CSS classes:

- `"primary"` → `.text-primary`, `.bg-primary`
- `"success"` → `.text-success`, `.bg-success`
- `"warning"` → `.text-warning`, `.bg-warning`
- `"danger"` → `.text-danger`, `.bg-danger`
- `"info"` → `.text-info`, `.bg-info`
- `"secondary"` → `.text-secondary`, `.bg-secondary`
- `"dark"` → `.text-dark`, `.bg-dark`
- `"light"` → `.text-light`, `.bg-light`

### Complete Examples

#### Plugin Update
```typescript
const pluginUpdate = {
  badge: "UPDATE",
  title: "New Plugin Manager Interface",
  description: "Completely redesigned plugin manager with improved search, categorization, and installation workflow. Find and install plugins more easily with the new intuitive interface.",
  icon: "fa-solid fa-puzzle-piece",
  action: {
    type: "methodCall",
    label: "Open Plugin Manager",
    pluginName: "menuicons",
    pluginMethod: "select",
    pluginArgs: ["pluginManager"]
  },
  theme: "primary"
}
```

#### Documentation Update
```typescript
const docUpdate = {
  badge: "INFO",
  title: "Updated Documentation Available",
  description: "Comprehensive documentation has been updated with new tutorials, best practices, and troubleshooting guides. Learn about the latest features and improve your development workflow.",
  icon: "fa-solid fa-book",
  action: {
    type: "link",
    label: "View Documentation",
    url: "https://remix-ide.readthedocs.io/en/latest/"
  },
  theme: "info"
}
```


## Plugin List Property Descriptions
### `pluginId: string`
**Required** - A valid name of a registered plugin on Remix-IDE (e.g LearnEth). 

**Example Values**:
```typescript
    "desktopClient",
    "LearnEth",
    "noir-compiler",
    "remixaiassistant"
    ...
```

### `pluginTitle: string`
**Required** - The display name of the plugin shown in the hometab plugin list.

**Example Values**:
```typescript
    "Solidity Compiler"
    "Debugger"
    "Deploy & Run Transactions"
    "File Explorer"
    ...
```

#### `action.type: string`
**Required** - Specifies the type of action to perform.

**Possible Values**:
- `"link"` - Opens an external URL in a new tab
- `"methodCall"` - Calls an internal plugin method

#### `action.label: string`
**Required** - The text displayed on the action button.

**Example Values**:
```typescript
    "View Documentation"
    "Open Plugin"
    "Learn More"
    "Get Started"
    "Read Guide"
    ...
```

#### `action.url?: string`
**Optional** - The external URL to open when `action.type` is `"link"`.

**Example Values**:
```typescript
"https://remix-ide.readthedocs.io/en/latest/solidity_editor.html"
"https://docs.soliditylang.org/"
"https://ethereum.org/developers/docs/"
```

#### `action.pluginName?: string`
**Optional** - The name of the plugin to call when `action.type` is `"methodCall"`.

**Example Values**:
```typescript
    "desktopClient",
    "LearnEth",
    "noir-compiler",
    "remixaiassistant"
    ...
```

#### `action.pluginMethod?: string`
**Optional** - The method name to call on the specified plugin when `action.type` is `"methodCall"`.

**Example Values**:
```typescript
    "select"
    "open"
    "compile"
    "debug"
    ...
```

#### `action.pluginArgs?: (string | number | boolean | object | null)[]`
**Optional** - Arguments to pass to the plugin method when `action.type` is `"methodCall"`.

**Example Values**:
```typescript
    ["pluginManager"]
    ["file.sol"]
    [true]
    [{ network: "mainnet", gas: 3000000 }]
    ...
```

### `iconClass: string`
**Required** - CSS class name for the plugin's icon.

**Description**: This defines the icon displayed next to the plugin title. It should use Font Awesome or Remix-specific icon classes.

**Example Values**:
```typescript
    "fa-solid fa-code"
    "fa-solid fa-bug"
    "fa-solid fa-rocket"
    "fa-solid fa-folder"
    ...
```

### `maintainedByRemix: boolean`
**Required** - Indicates whether the plugin is officially maintained by the Remix team.

**Possible Values**:
```typescript
    true   // Official Remix plugin
    false  // Community plugin
```

### `description: string`
**Required** - A brief description of what the plugin does.

**Example Values**:
```typescript
    "Compile Solidity smart contracts and view compilation details"
    "Debug smart contracts step by step with breakpoints and variable inspection"
    "Deploy contracts and interact with them on various networks"
    "Browse and manage files in your workspace"
    ...
```

### Complete Example

```typescript
const examplePlugin = {   
    pluginId: "LearnEth",
    pluginTitle: "LearnEth Tutorials",
    action: {
        type: "methodCall",
        label: "Start learning",
        pluginName: "learnEth",
        pluginMethod: "activatePlugin",
        pluginArgs: []
    },
    iconClass: "fa-solid fa-book",
    maintainedByRemix: true,
    description: "Learn about Remix, Solidity, and other Web3 projects."
}

const externalLinkPlugin: PluginInfo = {
    pluginId: "contract-verification",
    pluginTitle: "Contract Verification",
    action: {
        type: "link",
        label: "Open documentation",
        url: "https://remix-ide.readthedocs.io/en/latest/contract_verification.html"
    },
    iconClass: "fa-solid fa-file-contract",
    maintainedByRemix: true,
    description: "Verify your contracts on multiple services at the same time."
}
```