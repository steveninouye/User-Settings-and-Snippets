# Visual Studio Code Setup

## Install 'code' Command in PATH

- Open Visual Studio Code
- Open the Command Palette (⇧⌘P) and search for `Shell Command: Install 'code' command in PATH`

## Extensions

- Bracket Pair Colorizer 2
- VSCode Great Icons
- Prettier
- Monokai Night
- vscode styled components
- GraphQL from VSCode
- Simple Ruby ERB

## User Settings

Preferences > Settings > Open `settings.json`

```
{
  "editor.acceptSuggestionOnCommitCharacter": false,
  "workbench.startupEditor": "newUntitledFile",
  "editor.formatOnSave": true,
  "editor.wordWrap": "on",
  "editor.tabSize": 2,
  "prettier.tabWidth": 2,
  "prettier.singleQuote": true,
  "prettier.arrowParens": "always",
  "breadcrumbs.enabled": true,
  "editor.fontSize": 12.5,
  "editor.fontWeight": "400",
  "editor.fontFamily": "Fira Code, Monaco",
  "editor.fontLigatures": true,
  "editor.parameterHints.enabled": false,
  "terminal.integrated.fontFamily": "Fira Code, Inconsolata, Monaco",
  "terminal.integrated.lineHeight": 1.1,
  "terminal.integrated.fontSize": 13,
  "window.zoomLevel": -0.2,
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,
  "vscode_custom_css.imports": [""],
  "vscode_custom_css.policy": true,
  "extensions.ignoreRecommendations": false,
  "html.format.wrapAttributes": "aligned-multiple",
  "editor.minimap.enabled": false,
  "terminal.integrated.fontWeight": "400",
  "workbench.iconTheme": "vscode-great-icons",
  "workbench.colorTheme": "Monokai Night",
  "workbench.activityBar.visible": false,
  "explorer.autoReveal": false
}
```

```
{
  "eslint.enable": true,
  "eslint.autoFixOnSave": true,
  "editor.acceptSuggestionOnCommitCharacter": false,
  "workbench.startupEditor": "newUntitledFile",
  "editor.wordWrap": "on",
  "editor.tabSize": 2,
  "breadcrumbs.enabled": true,
  "editor.fontSize": 14,
  "editor.fontWeight": "400",
  "editor.fontFamily": "Fira Code, Monaco",
  "editor.fontLigatures": true,
  "editor.parameterHints.enabled": false,
  "terminal.integrated.fontFamily": "Fira Code, Inconsolata, Monaco",
  "terminal.integrated.lineHeight": 1.1,
  "terminal.integrated.fontSize": 13,
  "window.zoomLevel": -1,
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,
  "extensions.ignoreRecommendations": false,
  "html.format.wrapAttributes": "aligned-multiple",
  "editor.minimap.enabled": false,
  "terminal.integrated.fontWeight": "400",
  "workbench.iconTheme": "vscode-great-icons",
  "workbench.colorTheme": "Monokai Night",
  "workbench.activityBar.visible": true,
  "explorer.autoReveal": false,
  "diffEditor.ignoreTrimWhitespace": false,
  "editor.rulers": [
    80
  ],
  "workbench.colorCustomizations": {
    "editor.selectionBackground": "#575757",
    "editor.selectionHighlightBackground": "#575757"
  },
}
```

## Snippets

### JavaScript

```
{
    "Print to console": {
        "prefix": "clg",
        "body": ["console.log(${1:'Hello World!'})"],
        "description": "Log output to console"
    },
    "Console Log Variable": {
        "prefix": "cvar",
        "body": ["console.log('${1:variable}: ', ${1:variable})"],
        "description": "Log output to console"
    },
    "Write a Large Arrow Function": {
        "prefix": "func",
        "body": ["const ${1:name} = ($2) => {", "\t$3", "}"],
        "description": "ArrowFunction Template"
    },
    "Write a Short Arrow Function": {
        "prefix": "sfunc",
        "body": ["const ${1:name} = ($2) => $3"],
        "description": "ArrowFunction Template"
    },
    "Write a Call Back": {
        "prefix": "cbk",
        "body": ["($1) => {$2}"]
    }
}
```

## Keyboard shortcuts

```
// Place your key bindings in this file to overwrite the defaults
[
  {
    "key": "cmd+e",
    "command": "erb.toggleTags",
    "when": "editorTextFocus && editorLangId == erb"
  },
  { "key": "ctrl+1", "command": "workbench.action.terminal.focus" },
  {
    "key": "ctrl+1",
    "command": "workbench.action.focusActiveEditorGroup",
    "when": "terminalFocus"
  },
  {
    "key": "ctrl+a",
    "command": "workbench.action.toggleActivityBarVisibility"
  },
  { "key": "ctrl+z", "command": "workbench.action.toggleSidebarVisibility" }
]
```
