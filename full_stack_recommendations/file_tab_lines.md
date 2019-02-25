# Add Indent Lines To Your File Tree

Add this to the bottom of this file (VS Code will say there is a corrupt file but you can trust me _wink_ lol):

Mac: `/Applications/Visual\ Studio\ Code.app/Contents/Resources/app/out/vs/workbench/workbench.main.css`

Windows: `/mnt/c/Users/steve/AppData/Local/Programs/Microsoft\ VS\ Code/resources/app/out/vs/workbench/workbench.main.css`

Linux: `/usr/share/code/resources/app/out/vs/workbench/workbench.main.css`

```css
.monaco-tree-row {
  overflow: visible;
  position: relative;
}

.monaco-tree .monaco-tree-rows > .monaco-tree-row {
  overflow: visible;
}

.monaco-tree-row:before {
  content: '';
  position: absolute;
  width: 1px;
  height: 100%;
}

.monaco-tree-row:after {
  content: '';
  background: rgba(255, 255, 255, 0.2);
  position: absolute;
  width: 24px;
  height: 1px;
  top: 50%;
}

.monaco-tree-row[aria-expanded]:after {
  width: 12px;
}

.monaco-tree-row[aria-level='2']:before {
  box-shadow: -1px 0 0 0 rgba(255, 255, 255, 0.2);
}

.monaco-tree-row[aria-level='3']:before {
  box-shadow: -1px -11px 0 0 rgba(255, 255, 255, 0.2), -21px 0 0 0 rgba(255, 255, 255, 0.2);
}

.monaco-tree-row[aria-level='4']:before {
  box-shadow: -1px -11px 0 0 rgba(255, 255, 255, 0.2), -21px -11px 0 0 rgba(255, 255, 255, 0.2),
    -41px 0 0 0 rgba(255, 255, 255, 0.2);
}

.monaco-tree-row[aria-level='5']:before {
  box-shadow: -1px -11px 0 0 rgba(255, 255, 255, 0.2), -21px -11px 0 0 rgba(255, 255, 255, 0.2),
    -41px -11px 0 0 rgba(255, 255, 255, 0.2), -61px 0 0 0 rgba(255, 255, 255, 0.2);
}

.monaco-tree-row[aria-level='6']:before {
  box-shadow: -1px -11px 0 0 rgba(255, 255, 255, 0.2), -21px -11px 0 0 rgba(255, 255, 255, 0.2),
    -41px -11px 0 0 rgba(255, 255, 255, 0.2), -61px -11px 0 0 rgba(255, 255, 255, 0.2),
    -81px 0 0 0 rgba(255, 255, 255, 0.2);
}

.monaco-tree-row[aria-level='7']:before {
  box-shadow: -1px -11px 0 0 rgba(255, 255, 255, 0.2), -21px -11px 0 0 rgba(255, 255, 255, 0.2),
    -41px -11px 0 0 rgba(255, 255, 255, 0.2), -61px -11px 0 0 rgba(255, 255, 255, 0.2),
    -81px -11px 0 0 rgba(255, 255, 255, 0.2), -101px 0 0 0 rgba(255, 255, 255, 0.2);
}

.monaco-tree-row[aria-level='8']:before {
  box-shadow: -1px -11px 0 0 rgba(255, 255, 255, 0.2), -21px -11px 0 0 rgba(255, 255, 255, 0.2),
    -41px -11px 0 0 rgba(255, 255, 255, 0.2), -61px -11px 0 0 rgba(255, 255, 255, 0.2),
    -81px -11px 0 0 rgba(255, 255, 255, 0.2), -101px -11px 0 0 rgba(255, 255, 255, 0.2),
    -121px 0 0 0 rgba(255, 255, 255, 0.2);
}

.monaco-tree-row[aria-level='9']:before {
  box-shadow: -1px -11px 0 0 rgba(255, 255, 255, 0.2), -21px -11px 0 0 rgba(255, 255, 255, 0.2),
    -41px -11px 0 0 rgba(255, 255, 255, 0.2), -61px -11px 0 0 rgba(255, 255, 255, 0.2),
    -81px -11px 0 0 rgba(255, 255, 255, 0.2), -101px -11px 0 0 rgba(255, 255, 255, 0.2),
    -121px -11px 0 0 rgba(255, 255, 255, 0.2), -141px 0 0 0 rgba(255, 255, 255, 0.2);
}

.monaco-tree-row[aria-level='10']:before {
  box-shadow: -1px -11px 0 0 rgba(255, 255, 255, 0.2), -21px -11px 0 0 rgba(255, 255, 255, 0.2),
    -41px -11px 0 0 rgba(255, 255, 255, 0.2), -61px -11px 0 0 rgba(255, 255, 255, 0.2),
    -81px -11px 0 0 rgba(255, 255, 255, 0.2), -101px -11px 0 0 rgba(255, 255, 255, 0.2),
    -121px -11px 0 0 rgba(255, 255, 255, 0.2), -141px -11px 0 0 rgba(255, 255, 255, 0.2),
    -161px 0 0 0 rgba(255, 255, 255, 0.2);
}

.monaco-tree-row[aria-level='1'] {
  padding-left: 0px !important;
}
.monaco-tree-row[aria-level='2'] {
  padding-left: 20px !important;
}
.monaco-tree-row[aria-level='3'] {
  padding-left: 40px !important;
}
.monaco-tree-row[aria-level='4'] {
  padding-left: 60px !important;
}
.monaco-tree-row[aria-level='5'] {
  padding-left: 80px !important;
}
.monaco-tree-row[aria-level='6'] {
  padding-left: 100px !important;
}
.monaco-tree-row[aria-level='7'] {
  padding-left: 120px !important;
}
.monaco-tree-row[aria-level='8'] {
  padding-left: 140px !important;
}
.monaco-tree-row[aria-level='9'] {
  padding-left: 160px !important;
}
.monaco-tree-row[aria-level='10'] {
  padding-left: 180px !important;
}

.monaco-tree-row[aria-level='1']:before {
  display: none;
}
.monaco-tree-row[aria-level='2']:before {
  left: 11px;
}
.monaco-tree-row[aria-level='3']:before {
  left: 31px;
}
.monaco-tree-row[aria-level='4']:before {
  left: 51px;
}
.monaco-tree-row[aria-level='5']:before {
  left: 71px;
}
.monaco-tree-row[aria-level='6']:before {
  left: 91px;
}
.monaco-tree-row[aria-level='7']:before {
  left: 111px;
}
.monaco-tree-row[aria-level='8']:before {
  left: 131px;
}
.monaco-tree-row[aria-level='9']:before {
  left: 151px;
}
.monaco-tree-row[aria-level='10']:before {
  left: 171px;
}

.monaco-tree-row[aria-level='1']:after {
  display: none;
}
.monaco-tree-row[aria-level='2']:after {
  left: 11px;
}
.monaco-tree-row[aria-level='3']:after {
  left: 31px;
}
.monaco-tree-row[aria-level='4']:after {
  left: 51px;
}
.monaco-tree-row[aria-level='5']:after {
  left: 71px;
}
.monaco-tree-row[aria-level='6']:after {
  left: 91px;
}
.monaco-tree-row[aria-level='7']:after {
  left: 111px;
}
.monaco-tree-row[aria-level='8']:after {
  left: 131px;
}
.monaco-tree-row[aria-level='9']:after {
  left: 151px;
}
.monaco-tree-row[aria-level='10']:after {
  left: 171px;
}
```
