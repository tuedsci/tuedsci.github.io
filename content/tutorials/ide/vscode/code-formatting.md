---
title: Code formatting
notoc: true
---

Step 1: Install the [Prettier extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode).

Step 2: Set Prettier as the default formatter in `settings.json` (you can do this via GUI).

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}
```

Step 3: Set other recommended options in `settings.json`.

```json
{
  "editor.formatOnSave": true
}
```
