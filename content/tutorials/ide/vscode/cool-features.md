---
title: Cool features
---

## Zen mode

Zen mode is distract-free mode that hides away unnecessary detail and allows you focus just on the code. The zen mode can be toggled using `Ctrl + K Z`. You can also quickly exit the zen mode by double pressing `Esc`.

This is the layout of the normal mode.

![Normal mode](/img/vscode/normal-mode.png)

And this is the layout of the zen mode.

![Zen mode](/img/vscode/zen-mode.png)

## Minimap

For a large file with many lines of code, you can quickly scroll up and down the file using the minimap on the right side of the editor.

Mini map functionality can be toggled on/off using command palette (search for `minimap`). You should turn minimap off if you don't have much screen estate.

## Zoom

You can zoom in/out the whole IDE by change the zoom setting. It is convenient when you want to demo your code on a presentation. By default, the zoom level is 0. If you increase/decrease the zoom level by 1 unit, your IDE will be zoomed in/out by 20%. Press `Ctrl + 0` to reset zoom.

You can change the zoom level in the settings or by using shortcuts: `Ctrl + +` for zooming in and `Ctrl + -` for zooming out.

## Fast scrolling

If you hold the `Alt` key and scroll, you will be 5 times faster. This is particularly helpful when navigating a long file.

## Select lines

You can quickly select the entire current line by putting the cursor at it and hit `Ctrl + L`. This works with paragraph as well.

## Move lines up or down

You can move a line up or down by putting the cursor at the line and then use `Alt + Up` or `Alt + Down` to move it up or down. This works with a whole paragraph as well.

If you want to move multiple lines (or paragraphs), you can select the lines (or paragraphs) then use `Alt + Up` or `Alt + Down`.

## Duplicate lines

Put the cursor at the line you want to duplicate and then hit `Shift + Alt + Up` to make a duplicate above. To make a duplicate below, hit `Shift + Alt + Down`.

## Go to definition

You can go to the definition of a function by holding `Ctrl` and click on the function.

## Mass rename

If you select a chunk of text (a variable name for example) and press `F2`, VS Code will allow you to rename all the occurrences of the text at once.
