# Atom Text Editor Setup
## Install 'atom' Shell Command
- Open Atom
- Open Command Palette (⇧⌘P) and search for `Window: Install Shell Commands`


## Snippets
```
'.source.ruby':  # Ruby
  'Print Variable To Console':
    'prefix': 'clg'
    'body': 'print "${0:var} => "; p ${0:var}'
  'Print Hello World':
    'prefix': 'hw'
    'body': 'puts "Hello World!"'
'.source.js':    # Javascript
  'Print Variable To Console':
    'prefix': 'clg'
    'body': 'console.log("${0:var}: ", ${0:var})'
  'Print Hello World':
    'prefix': 'hw'
    'body': 'console.log("Hello World!")'
  'Large Arrow Function':
    'prefix': 'func'
    'body': 'const ${1:var} = ($2) => {$0}'
  'Short Arrow Function':
    'prefix': 'sfunc'
    'body': 'const ${1:var} = ($2} => $0'
  'Call Back':
    'prefix': 'cbk'
    'body': '($1) => {$0}'
```
## Packages
- atom-beautify
- autosave-onchange
- emmet
- file-icons
- highlight-selected
- pigments
- todo