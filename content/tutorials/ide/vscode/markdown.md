---
title: Markdown
---

## Default support

VS Code supports Markdown natively, meaning that it recognizes any file with `.md` extensions as a Markdown file and provides various supports such as syntax highlighting, outline, snippets, etc.

### Smart text editing

VS Code supports many hotkeys that mimic those that you normally find when working with a rich text editor like Microsoft Word. Here are some examples.

- Make **bold** with `Ctrl + B`
- Make _italic_ with `Ctrl + I`
- Auto extend list items, block quotes, when hitting `Enter`
- Auto extend blockquote when hitting `Enter`

It also provides some convenient hotkeys.

- Expand selection: `Ctrl + Shift + Right`
- Shrink selection: `Ctrl + Shift + Left`

### Document outline

The outline for headings in your current Markdown document is listed at the Outline section in the Side Bar when you are in the Explorer activity. You can click on a heading and the cursor will immediately jumps to that section.

![Outline](/img/vscode/markdown-outline.png)

### Go to heading

If you want to quickly jump to a heading without having to look at the outline, then press `Ctrl + Shift + O`. A search box with a dropdown list of headings will appear and you can type in a few keyword for the heading and hit `Enter` to jump to that section.

![Go to heading](/img/vscode/markdown-go-to-heading.png)

### Path completion

When typing the path an image, you can type part of the file name, and VS Code will suggest you all the paths matching what you type. You then just need to hit `Enter` to complete the full path. You can even drag and drop the image into the editor and VS Code will fill the correct path.

### Preview

You can preview the rendering of a Markdown document by pressing `Ctrl + K V`. A preview window will open in a separate tab group. This way you can simultaneously editing and previewing changes.

## Extensions

Although VS Code has an excellent support for Markdown, you can still make it better with extensions. In this sections, I will give you some useful extensions that will give you much smoother experience when working with Markdown files. You can read more about what each of them does in the associated link.

- [Markdown All In One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
- [Dictionary Completion](https://marketplace.visualstudio.com/items?itemName=yzhang.dictionary-completion)
- [Markdown Lint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)

## Settings

The following is my recommended settings for Markdown that I find useful.

```json
{
  "markdown.extension.orderedList.marker": "one",
  "[markdown]": {
    "editor.tabCompletion": "off",
    "editor.acceptSuggestionOnEnter": "on",
    "editor.quickSuggestions": {
      "other": true,
      "comments": true,
      "strings": true
    }
  }
}
```
