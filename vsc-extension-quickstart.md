# Welcome to your VS Code Extension

## What's in the folder

- This folder contains all of the files necessary for your extension.
- `package.json` - this is the manifest file that defines the location of the grammar file and specifies the language configuration.
- `syntaxes/sql-tagged-template.tmLanguage.json` - this is the Text mate grammar file that is used for tokenization.
- `language-configuration.json` - this the language configuration, defining the tokens that are used for comments and brackets.

## Get up and running straight away

- Press `F5` to open a new window with your extension loaded.
- Create a new file with a file type supported by your grammar.
- Verify that syntax highlighting works.

## Make changes

- You can relaunch the extension from the debug toolbar after making changes to the files listed above.
- You can also reload (`Ctrl+R` or `Cmd+R` on Mac) the VS Code window with your extension to load your changes.

## Install your extension

- To start using your extension with VS Code copy it into the `<user home>/.vscode/extensions` folder and restart Code.
- To share your extension with others, package it:
  ```bash
  npm install -g @vscode/vsce
  vsce package
  ```

## Development workflow

1. Make changes to grammar in `syntaxes/sql-tagged-template.tmLanguage.json`
2. Press F5 to launch Extension Development Host
3. Test your changes
4. Use `Developer: Inspect Editor Tokens and Scopes` command to debug
