# Agentforce Vibes Safe Commands

> **📖 Official Documentation Available**
>
> This wiki page has been updated. For the most current and comprehensive information, please refer to the official documentation:
>
> **[Set Up Agentforce Vibes Extension - Add to Agentforce Vibes Safe Commands](https://developer.salesforce.com/docs/platform/einstein-for-devs/guide/einstein-setup.html#add-to-agentforce-vibes-safe-commands)**

## Overview

Agentforce Vibes safe commands are a list of commands that Agentforce can automatically run without prompting the user for approval. The list of safe commands is user controlled. Ensure any commands you add have been reviewed for security considerations.

## How to Access Safe Commands

1. Click **Auto-approve** in the Agentforce chat panel to open Auto-approve settings
2. Click **Safe Commands Allowlist** to open the `a4d_safe_commands` file
3. Add commands (one per line)
4. Save the file - changes are automatically reloaded

## Command Matching Types

The safe commands feature supports three types of command matching:

### 1. Exact Matching (Recommended)
List commands exactly as they appear. The entire command must match precisely.

**Example:**
```
git status
npm run lint
sf project retrieve start
```

### 2. Multi-Command Support
Commands joined with `&&`, `||`, `;`, or `&` are supported. Each part is validated separately.

**Example:**
```
npm run build && npm test
git add . && git status
```

### 3. Flexible Matching (Advanced)
Add `...` after a command to match it with any arguments.

**Example:**
```
git checkout...
sf project deploy start...
npm run...
```

## Example Safe Commands File

```
# Safe Commands List
# Lines beginning with "#" are comments and ignored.

# Git commands
git status
git diff
git log

# Salesforce CLI commands
sf project retrieve start
sf org display

# Build and test
npm run lint
npm run build && npm test

# Advanced: Flexible matching
# git checkout...
```

## Additional Information

For complete details including:
- Step-by-step setup instructions
- Detailed examples and use cases
- Best practices and tips
- Latest feature updates

Please visit the [official documentation](https://developer.salesforce.com/docs/platform/einstein-for-devs/guide/einstein-setup.html#add-to-agentforce-vibes-safe-commands).

