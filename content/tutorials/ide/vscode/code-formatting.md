---
title: Code formatting
---

Code formatting (or code refactoring) refers to ways of organizing and structuring your code. It is an essential aspect of software development with the ultimate goal to make yor codebase more consistent, readable, and maintainable. [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) is an excellent extension that makes code formatting in VS Code become much simpler. Follow the steps below to install and config Prettier.

## Installation

Go to Extensions (`Ctrl + Shift + X`), search for `Prettier - Code formatter`, and install it.

## Configuration

Set Prettier as your default formatter in `settings.json` (you can do this via GUI).

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}
```

## Recommended settings

To save your time and typing, you can modify the settings to tell Prettier to automatically format your code whenever you save the file.

```json
{
  "editor.formatOnSave": true
}
```
