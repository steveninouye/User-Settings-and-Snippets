# Visual Studio Code Setup

## Install 'code' Command in PATH

-   Open Visual Studio Code
-   Open the Command Palette (⇧⌘P) and search for `Shell Command: Install 'code' command in PATH`

## User Settings

Preferences > Settings > Open `settings.json`

```
{
    "editor.acceptSuggestionOnCommitCharacter": false,
    "workbench.startupEditor": "newUntitledFile",
    "editor.formatOnSave": true,
    "editor.wordWrap": "on",
    "prettier.tabWidth": 4,
    "prettier.singleQuote": true,
    "prettier.arrowParens": "always",
    "window.zoomLevel": 0,
    "breadcrumbs.enabled": true,
    "editor.fontSize": 12.3,
    "editor.fontFamily": "Fira Code, Inconsolata",
    "editor.fontLigatures": true,
    "terminal.integrated.fontFamily": "Inconsolata, Monospace",
    "terminal.integrated.lineHeight": 1.1,
    "terminal.integrated.fontSize": 14,
    "window.zoomLevel": -0.001,
    "files.autoSave": "afterDelay",
    "files.autoSaveDelay": 1000,
    "extensions.ignoreRecommendations": false,
    "html.format.wrapAttributes": "aligned-multiple",
    "editor.minimap.enabled": false,
    "workbench.iconTheme": "vscode-icons"
}
```

## Extensions

-   Bracket Pair Colorizer 2
-   vscode-icons
-   Prettier

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
