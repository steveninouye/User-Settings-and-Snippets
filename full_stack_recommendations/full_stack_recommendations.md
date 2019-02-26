# Rails + React a/A Recommendations

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

---

---

## [other stuff](https://github.com/steveninouye/User-Settings-and-Snippets/tree/master/full_stack_recommendations)
