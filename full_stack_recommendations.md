# Rails + React a/A Recommendations

## ~~Hash Router~~ < Browser Router (sexy urls)

```ruby
# config/routes.rb

Rails.application.routes.draw do
  root "static_pages#root"
  match "*path", to: "static_pages#root", via: :all
end
```

```javascript
// Root.jsx

import React from 'react';
import { Provider } from 'react-redux';
import { BrowserRouter, HashRouter } from 'react-router-dom';

import RootRoutes from './RootRoutes';

const Root = ({ store }) => (
  <Provider store={store}>
    <BrowserRouter>
      <RootRoutes />
    </BrowserRouter>
  </Provider>
);

export default Root;
```

```javascript
// RootRoutes.jsx

import React from 'react';
import { Switch, Route } from 'react-router-dom';

const RootRoutes = () => {
  return (
    <>
      <Switch>
        <.......................>
        <Route path="*" component={Page404Container} />
      </Switch>
      <HomeFooter />
    </>
  );
};
export default RootRoutes;
```

# Configure Root Reducer (or Store)

Configure root reducer (or store.js) so that it will only run the redux-logger when in development

```javascript
// root_reducer.js
// this might be split between your root_reducer.js and store.js file
// I just combined root_reducer and store.js into one file

import { combineReducers, createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import logger from 'redux-logger';

import errorsReducer from './errors_reducer.js';
import entitiesReducer from './entities_reducer.js';
import sessionSwitch from './session/session_switch.js';
import UiSwitch from './ui/ui_switch.js';

const rootReducer = combineReducers({
  entities: entitiesReducer,
  errors: errorsReducer,
  session: sessionSwitch,
  ui: UiSwitch
});

const configureStore = (preloadedState = {}) =>
  process.env.NODE_ENV === 'production'
    ? createStore(rootReducer, preloadedState, applyMiddleware(thunk))
    : createStore(rootReducer, preloadedState, applyMiddleware(thunk, logger));

export default configureStore;
```

# Set Current User

Extract Current User from App.jsx for cleaner code

```javascript
// App.jsx

import React from 'react';
import ReactDOM from 'react-dom';

import Root from './components/Root';

import configureStore from './reducers/root_reducer';
import setCurrentUser from './utils/set_current_user';

document.addEventListener('DOMContentLoaded', () => {
  let store = setCurrentUser(configureStore);
  ReactDOM.render(<Root store={store} />, document.getElementById('root'));
});
```

```javascript
// utils/set_current_user

const setCurrentUser = (configureStore) => {
  if (window.currentUser) {
    const preloadedState = {
      session: window.currentUser.id,
      entities: {
        users: { [window.currentUser.id]: window.currentUser }
      }
    };
    delete window.currentUser;
    return configureStore(preloadedState);
  } else {
    return configureStore();
  }
};

export default setCurrentUser;
```

# Use Rails Public Directory

Anything you put into the `/public` directory is easily referenced in your HTML/CSS. Great for static content or placeholders during CSS

Example:

```
/public/puppy.jpg
/public/images/smile.png
```

```html
<img src="/puppy.jpg" /> <img src="/images/smile.png" />
```

# Optimize Your NPM Development Scripts

Use awesome libraries like `concurrently`

```json
{
  "scripts": {
    "start": "concurrently -r -k \"webpack --watch --mode=development\" \"rails s\""
  }
}
```

## Use WebPack Dev Server (Advance Users)

If you are really good at webpack you can configure `webpack-dev-server` which will save you a lot of time because you won't need to reload your application ever time you update. Webpack Dev Server automatically reloads your application for you which is super cool.

# Minimize Your Production Build

Add `-p` to your `webpack` command to minimize your javascipt build when you deploy

```json
package.json

{
  "scripts": {
    "postinstall": "webpack -p"
  }
}
```

# Navigate Quickly

Awesome hot keys

`CMD + P` => search for a file

`CMD + SHIFT + F` => search entire project

`CMD + D` => Highlight _NOT_ highlighted word

`CMD + SHIFT + L` => Highlight all strings in file matching highlighted section

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
