---
title: Settings
---

Settings allow you to customize VS Code in various aspects so that you feel most comfortable and productive.

## User and workspace settings

There are two types of settings: user and workspace.

1. **User settings** apply globally for every project whenever you open VS Code.
1. **Workspace settings** only apply to the project that is currently open.

## Open settings

Settings can be accessed and modified either through GUI or through the JSON file. I prefer the latter although it seems intimidating at first.

Both the GUI and JSON settings can be opened using the Command Palette and then searching for the keywords `settings`. The GUI settings can also be opened by pressing `Ctrl + ,`. A window with a search box will appear and let you type in the keywords to search for the setting you want.

## Recommended settings

Here are my personal settings for VS Code.

### Editor

- Font size: `18px`
- Word wrap: `on`
- Word wrap column: `80`

Note: to show ruler for word wrap, you can modify `settings.json` as follows.

```json
{
  // Show the ruler
  "editor.rulers": [80]
}
```

### Themes

- Color theme: `One Dark Pro Flat`
- File Icon theme: `Material Icon`
- Product Icon theme: `Fluent Icons`

## Other settings

```json
{
  // Format on save
  "editor.formatOnSave": true,

  // Default formatter
  "editor.defaultFormatter": "esbenp.prettier-vscode",

  // Formatter for Python
  "python.formatting.provider": "black",
  "[python]": {
    "editor.defaultFormatter": "ms-python.black-formatter"
  },

  // Linting with pylint
  "python.linting.enabled": true,
  "python.linting.pylintEnabled": true,

  // Spell checking
  "cSpell.diagnosticLevel": "Hint",

  // Prevent VS Code from adding trailing line
  // when formatting a file or a Jupyter code cell
  "files.insertFinalNewline": false,

  // However, Prettier extension will add a blank EOF line
  // You have to disable it manually for every language
  "[markdown]": {
    "files.insertFinalNewline": false,
    "files.trimFinalNewlines": true
  },

  "[python]": {
    "files.insertFinalNewline": false,
    "files.trimFinalNewlines": true
  },

  // Default tab size = 2 spaces
  "editor.tabSize": 2
}
```
