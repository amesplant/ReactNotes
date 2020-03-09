### 4. This is Redux

We're going to transition away from our custom code to using the actual  Redux library. While we're working on this simple project, we'll be  linking to the hosted version of the Redux library. In the following  video, we'll use this code to link to redux:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/redux/3.7.2/redux.min.js"></script>
```

This will replace all of our *Library Code* so we can remove it from our app.

```js
// Library Code
function createStore (reducer) {
    // The store should have four parts
    // 1. The state
    // 2. Get the state.
    // 3. Listen to changes on the state.
    // 4. Update the state

      let state;
      let listeners = [];

      const getState = () => state;

      const subscribe = (listener) => {
        listeners.push(listener);
        return () => {
            listeners = listeners.filter((l) => l !== listener);
        }
      };

      const dispatch = (action) => {
        state = reducer(state, action);
        listeners.forEach((listener) => listener());
      };

      return {
        getState,
        subscribe,
        dispatch,
      };
    }
```

And now when we create the store, instead of creating our **createStore** we will call `Redux.createStore`.

Redux will also have a **combineReducers** function, so we can remove our **app** function:

```js
function app (state = {}, action) {
    return {
        todos: todos(state.todos, action),
        goals: goals(state.goals, action),
    }
}
```

and our **store** changes from

```js
const store = Redux.createStore(app);
```

to

```js
cons store = Redux.createStore(Redux.combineReducers({
    todos,
    goals,
}))
```

#### Quiz - root reducer

```js
import { combineReducers } from 'redux';
import booksReducer from './books_reducer';
import userReducer from './user_reducer';

const rootReducer = combineReducers({
    books: booksReducer,
    users: userReducer
});

export default rootReducer;
```

