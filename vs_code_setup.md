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
  "breadcrumbs.enabled": true,
  "diffEditor.ignoreTrimWhitespace": false,
  "editor.acceptSuggestionOnCommitCharacter": false,
  "editor.fontFamily": "Fira Code, Monaco",
  "editor.fontLigatures": true,
  "editor.fontSize": 14,
  "editor.fontWeight": "400",
  "editor.minimap.enabled": false,
  "editor.parameterHints.enabled": false,
    "editor.rulers": [
      80
    ],
  "editor.tabSize": 2,
  "editor.wordWrap": "on",
  "eslint.autoFixOnSave": true,
  "eslint.enable": true,
  "explorer.autoReveal": false,
  "extensions.ignoreRecommendations": false,
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,
  "html.format.wrapAttributes": "aligned-multiple",
  "prettier.eslintIntegration": true,
  "prettier.jsxSingleQuote": true,
  "prettier.singleQuote": true,
  "prettier.trailingComma": "all",
  "terminal.integrated.fontFamily": "Fira Code, Inconsolata, Monaco",
  "terminal.integrated.fontSize": 13,
  "terminal.integrated.fontWeight": "400",
  "terminal.integrated.lineHeight": 1.1,
  "window.zoomLevel": -1,
  "workbench.activityBar.visible": true,
  "workbench.colorCustomizations": {
    "editor.selectionBackground": "#575757",
    "editor.selectionHighlightBackground": "#575757"
  },
  "workbench.colorTheme": "Monokai Night",
  "workbench.iconTheme": "vscode-great-icons",
  "workbench.startupEditor": "newUntitledFile",
  "[javascript]": {
    "editor.defaultFormatter": "vscode.typescript-language-features"
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
