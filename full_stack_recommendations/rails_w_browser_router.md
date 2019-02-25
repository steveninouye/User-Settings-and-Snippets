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
