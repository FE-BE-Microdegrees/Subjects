# Visual Studio Code Tips

![VS Code Tips](VSCode-Tips.webp)

Image source: Dall-E by OpenAI

In this course, we've used Visual Studio Code (VS Code) as a primary tool. VS Code is a powerful editor with many features and extensions that can make the development process faster and more convenient.

## Learning Outcomes

After completing this topic, you will be able to:

- Use VS Code keyboard shortcuts effectively.
- Utilize VS Code extensions.

## Keyboard Shortcuts

Keyboard shortcuts are a quick way to use VS Code features. Here are some useful keyboard shortcuts:

### Search

- `Ctrl (Cmd) + P` - Opens quick search, where you can search files within the project folder.
- `Ctrl (Cmd) + F` - Opens search within the current file.
- `Ctrl (Cmd) + Shift + F` - Opens global search across the entire project folder.
- `Ctrl (Cmd) + H` - Opens find and replace within the current file.
- `Ctrl (Cmd) + Shift + H` - Opens global find and replace across the entire project folder.

### VS Code Keyboard Shortcuts - Comments

- `Alt (Option) + Shift + A` - Toggles commenting for the selected lines (block comment).

### Copying/Cutting/Deleting/Selecting

- `Alt (Option) + Shift + Arrow up` - Copies the selected lines upward.
- `Alt (Option) + Shift + Arrow down` - Copies the selected lines downward.
- `Ctrl (Cmd) + C` - Copies the selected line (even if no text is selected).
- `Ctrl (Cmd) + X` - Cuts the selected line (even if no text is selected).
- `Ctrl (Cmd) + Shift + K` - Deletes the selected line where the cursor is located (without sending it to the clipboard).
- `Ctrl (Cmd) + Shift + L` - Selects all occurrences of the cursor position.
- `Ctrl (Cmd) + D` - Selects the next occurrence of the cursor position.

### Other

- `Ctrl (Cmd) + Shift + E` - Opens the sidebar where you can see all project files and folders.
- `Ctrl (Cmd) + Shift + X` - Opens the sidebar where you can see all extensions.
- `Ctrl (Cmd) + Shift + P` - Opens the command palette where you can search for all VS Code features.
- `Ctrl (Cmd) + Alt (Option) + Arrow up/Arrow down` - Multiple cursors up/down.

## Useful Extensions

VS Code extensions are very helpful as they allow you to extend VS Code's functionality. To install extensions, go to `View -> Extensions` or press the shortcut `Ctrl + Shift + X` and search by extension name. Here are some useful extensions:

- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) - Easier editing and previewing of Markdown files.
- [Markdown Preview Mermaid Support](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid) - Mermaid diagram support in Markdown preview.
- [Markdown Lint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) - Lints Markdown files for correctness and style requirements.
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - Automatic code formatting.
- [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph) - Visual representation of Git history.
- [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments) - Colors comments based on their type.
- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) - Launch a development server and automatically refresh webpages.
- [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) - Real-time collaboration with other developers.
- [Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens) - Highlights errors and warnings in the code.
- [Icon Themes](https://marketplace.visualstudio.com/items?itemName=vscode-icons-team.vscode-icons) - Changes icon themes according to file types.
- [Marp](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode) - Creates Markdown presentations in VS Code.

## Code Snippets

In VS Code, you can create your own custom code snippets, which can be used for quickly writing code. These snippets can be used for different code blocks, templates, or repetitive code sections. In VS Code, they work by replacing the name of the code snippet with the corresponding code block when you type the predefined abbreviation.

Here are some examples of custom code snippets:

```json
{
  "Print to console": {
    "prefix": "log",
    "body": ["console.log('$1');", "$2"],
    "description": "Log output to console"
  },
  "For loop": {
    "prefix": "for",
    "body": [
      "for (let ${1:i} = 0; ${1:i} < ${2:array}.length; ${1:i}++) {",
      "\t$3",
      "}"
    ],
    "description": "For loop"
  }
}
```

In the above code example, when you type `log` using the defined shortcut, the following code snippet will be inserted:

```javascript
console.log("");
```

Similarly, typing `for` will insert the following code:

```javascript
for (let i = 0; i < array.length; i++) {
  // code here
}
```

Custom code snippets can be created from VS Code's settings by selecting `File -> Preferences -> Configure User Snippets` (`Code -> Settings -> Configure Snippets`).

You can also use code snippets created by others, which can be found in VS Code extensions. For example, you can use the [JavaScript (ES6) code snippets](https://marketplace.visualstudio.com/items?itemName=xabikos.JavaScriptSnippets) extension, which contains many useful snippets for JavaScript.

To learn more about `Code Snippets`, you can read [here](https://code.visualstudio.com/docs/editor/userdefinedsnippets).
