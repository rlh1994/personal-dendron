---
id: Wr1o9Pw3UjgT5uBbGujOw
title: VScode
desc: ''
updated: 1642087974028
created: 1641833074867
---

> Visual Studio Code is a streamlined code editor with support for development operations like debugging, task running, and version control. It aims to provide just the tools a developer needs for a quick code-build-debug cycle

VSCode comes with a lot of useful things out of the box, but it's real power shines in the use of [[tools.vscode.extensions]] which can go from simple to hugely complex. It comes with in built git functionality, a terminal (<kbd>Ctrl</kbd>+<kbd>'</kbd>), and the ability to split and organise your panes as you wish (within reason).

When using VScode the single most important keyboard shortcut to learn is 
<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> which brings up the Command Palette, from which you can access any number of commands, including a list of all keyboard shortcuts! 

## Folders and Workspaces

When you first open VSCode you will find it is a blank workspace, meaning you can open and work with files but you are based in your root directory and there is no folder tree in the sidebar. You can open a folder in VScode which makes this visible in your sidebar for file exploration, and sets your path in terminal to that folder meaning any commands you run will be ran from that folder - this is great as it means everything can use a relative path, but there is even more functionality in workspaces.

A workspace is a special type of instance in VScode that can be configured in multiple unique ways. The first is that you can enable/disable extensions per workspace and even change individual settings per workspace - this is great if you have very different types of project that might need very different extensions or even themes and settings. A workspace exists at some root (for the terminal) but you can add folders from anywhere on your machine, this does mean at times you may need to be careful with paths, but it also means you can _remove_ folders from your workspace which means you can see a reduced set of folders in a master folder, or any mix of them! This means you can functionally have 2 or more very different VScode setups running at the same time and easily swap between them (even easier if you use the below extension).
![[tools.vscode.extensions#project-manager:#*]]

## Multi-line Editing

A cool feature of a text editor if you haven't used one before is a multi-line cursor, where you can place your cursor in mutliple positions and edit them at the same time. A common use case is when you want to prefix all lines by some text, or wrap each line in quotes, put a comma at the end of each line etc. An easy way to do this is:
1. Highlight all lines you are interested in (doesn't have to be the whole line highlighted)
2. Press <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>I</kbd> to create a cursor at each line
3. Use <kbd>Home</kbd>, <kbd>End</kbd>, etc to navigate and then type on each line
4. Press <kbd>Esc</kbd> to return to a single cursor

Combined with an extension like the one below, you can now do lots of editing very quickly! ![[tools.vscode.extensions#vscode-input-sequence:#*]]













