## 5. Updating State

The whole goal of Redux is to increase predictability:
_Redux is a predictable state container for JavaScript apps._

So far our rules for Redux are;
1 Only an event can change the state of the store.
2.The function that returns the new state needs to be a pure function.

By definition, **pure functions**:

- [ ] Return the same result if the same arguments are passed in
- [ ] Depend solely on the arguments passed into them
- [ ] Do not produce side effects, such as API requests and I/O operations


### Reducer Function 

Now we need to tie our **state** and our **actions** together, meaning we need to updater our internal state of our store based on the specific action that occurred. 

We will create a pure function to do just that. When a function takes in the current state and the action, and then returns the new state of the action, this is called the **reducer**, which _must_ be a pure function.

````js
function todos (state = [], action) { // using ES6 default parameters to set state to [] if state is undefined as it will be the first time
  if (action.type === 'ADD_TODO') {
    return state.concat([action.todo]); // concat will return a new array with the new action (todo) added to the state
  }

  return state;
}
````

### Challenge

````js
/* Create A Reducer
 *
 * You need to create a reducer called "appReducer" that accepts two arguments:
 * - First, an array containing information about ice cream 
 * - Second, an object with a 'DELETE_FLAVOR' `type` key
 * (i.e., the object contains information to delete the flavor from the state)
 *
 * The action your reducer will receive will look like this:
 * { type: 'DELETE_FLAVOR', flavor: 'Vanilla' }
 *
 * And the initial state will look something like this (as such, refrain 
 * from passing in default values for any parameters!):
 * [{ flavor: 'Chocolate', count: 36 }, { flavor: 'Vanilla', count: 210 }];
*/
````

### 3 Parts to our App

1. Action:  represent the different **events** that will change the state of our store
2. Reducer Function: a function that takes in the current **state** and an **action** that has occurred and returns the **new state**
3. Create Store: actually creates the **store**
   - State Tree
   - Getting the State
   - Listening for Changes
   - Updating the State (dispatch)

### Dispatch

responsible for updating the state inside of the store ...

- It will need the **action** to tell dispatch the specific event that occurred inside of the application.
- Once it has access to the state and the action that has occurred, it can call our **todos** function passing its state and an action

````js
const dispatch = (action) => {
    state = todos(state, action);
    // since we just modified state ^^^ we will need to loop through all of our array of listeners and invoke them
    // so than any lisenter the user set up can be invoked
    listeners.forEach((listener) => listener());
}
 // no that we have our dispatch, it needes to be invoked
return {
    getState,
    subscribe,
    dispatch
}
````

### index.js

````js
// Library Code
function createStore (reducer) { // allows user to pass in a specific reducer function
  // The store should have four parts
  // 1. The state
  // 2. Get the state.
  // 3. Listen to changes on the state.
  // 4. Update the state

  let state;
  let listeners = [];

  const getState = () => state;

  const subscribe = (listener) => {
    listeners.push(listener)
    return () => {
      listeners = listeners.filter((l) => l !== listener);
    }
  }

  const dispatch = (action) => {
    state = reducer(state, action); // changed from 'todos' to using whatever reducer was passed in, since this acts as a 'library'
    listeners.forEach((listener) => listener());
  }

  return {
    getState,
    subscribe,
    dispatch,
  }
}

// App Code
function todos (state = [], action) {
  if (action.type === 'ADD_TODO') {
    return state.concat([action.todo]);
  }

  return state;
}

// now if the user can pass in a specific reducer
const store = createStore(reducer);
````

## 