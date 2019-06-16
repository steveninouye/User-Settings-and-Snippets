# Visual Studio Code Setup

## Install 'code' Command in PATH

- Open Visual Studio Code
- Open the Command Palette (⇧⌘P) and search for `Shell Command: Install 'code' command in PATH`

## Extensions

- Bracket Pair Colorizer 2
- VSCode Great Icons
- Monokai Night
- Simple Ruby ERB
- ESlint
- Rubocop
- Ruby

## User Settings

Preferences > Settings > Open `settings.json`

```
{
  "workbench.startupEditor": "newUntitledFile",
  "window.zoomLevel": 0,
  "workbench.iconTheme": "vscode-icons",
  "workbench.colorTheme": "Monokai Night",
  "files.autoSave": "afterDelay",
  "editor.acceptSuggestionOnCommitCharacter": false,
  "editor.wordWrap": "on",
  "editor.formatOnSave": true,
  "editor.tabSize": 2,
  "editor.rulers": [
    80,
    120
  ],
  "breadcrumbs.enabled": true,
  "editor.fontSize": 12,
  "editor.fontWeight": "400",
  "editor.fontFamily": "Fira Code, Monaco",
  "editor.fontLigatures": true,
  "editor.parameterHints.enabled": false,
  "terminal.integrated.fontFamily": "Fira Code, Inconsolata, Monaco",
  "terminal.integrated.lineHeight": 1.1,
  "terminal.integrated.fontSize": 12,
  "extensions.ignoreRecommendations": false,
  "html.format.wrapAttributes": "aligned-multiple",
  "editor.minimap.enabled": false,
  "terminal.integrated.fontWeight": "400",
  "workbench.activityBar.visible": false,
  "explorer.autoReveal": false,
  "editor.renderFinalNewline": true,
  "workbench.colorCustomizations": {
    // "editor.selectionBackground": "#575757",
    // "editor.selectionHighlightBackground": "#575757"
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
