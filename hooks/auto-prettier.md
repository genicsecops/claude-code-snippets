# Auto Prettier Hook

Automatically format your code with Prettier after every file edit, ensuring consistent code style across your project.

## Hook Configuration

Add to your `.claude/settings.json` in your project root:

```json
{
  // ...
  "hooks": {
    // ...
    "PostToolUse": [
      {
        "matcher": "Write|Edit|MultiEdit",
        "hooks": [
          {
            "type": "command",
            "command": "file_path=$(jq -r '.tool_input.file_path'); if [[ \"$file_path\" =~ \\.(ts|js|tsx|jsx|json|css|scss|html)$ ]]; then npx prettier --write \"$file_path\"; fi"
          }
        ]
      }
    ]
  }
}
```

## What It Does

- **Automatic Formatting**: Runs Prettier after every file edit
- **Supported Files**: TypeScript, JavaScript, JSX/TSX, JSON, CSS, SCSS, HTML
- **Zero Manual Work**: No need to remember to format files
- **Consistent Style**: Ensures all code follows the same formatting rules

## Prerequisites

- Prettier installed in your project: `npm install --save-dev prettier`
- Optional: `.prettierrc` configuration file in your project root

## How It Works

1. Claude edits a file (using Write, Edit, or MultiEdit tools)
2. Hook checks if the file extension matches supported types
3. If match found, runs `npx prettier --write` on the file
4. File is automatically formatted according to your Prettier config

## Customization

### Add More File Types

Modify the regex pattern to include additional extensions:

```bash
# Original
\\.(ts|js|tsx|jsx|json|css|scss|html)$

# With Python and YAML
\\.(ts|js|tsx|jsx|json|css|scss|html|py|yml|yaml)$
```

### Use Different Formatter

Replace the prettier command with your preferred formatter:

```bash
# ESLint
npx eslint --fix \"$file_path\"

# Black (Python)
black \"$file_path\"

# Rustfmt (Rust)
rustfmt \"$file_path\"
```

## Troubleshooting

- **Hook not running**: Ensure `.claude/settings.json` is properly formatted
- **Prettier not found**: Install prettier in your project
- **Formatting errors**: Check your `.prettierrc` configuration
