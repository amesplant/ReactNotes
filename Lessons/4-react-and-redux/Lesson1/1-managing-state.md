[Home](https://github.com/amesplant/ReactNotes#react-notes) / [Lessons](https://github.com/amesplant/ReactNotes/tree/master/Lessons) / Redux

# Lesson 1: Managing State

## 3. The Store
We combine the three items below and the state tree object itself into one unit which we call the **store**. 

- [ ] getting the state
- [ ] listening for changes to the state
- [ ] updating the state

## 4. Create Store: Getting and Listening

We'll start with a blank `index.js` file and create a factory function that creates store objects. Then we'll have the store keep track of the state, and we'll write the method to get the state from the store.

**index.js
The state should have four parts
1. The state
2. Get the state
3. Listen to changes on the state
4. Update the state

#### 1. Set the state and 2. Get the state

````js
function createStore() {

    let state; // 1. set the tate

    const getState = () => state;
    
    // 2. returns the state of the application
    return {
        getState
    }
}
````

#### 3. Listen to the changes on the state:

It would be nice if we provide to the user a subscribe method, they then could pass subscribe a callback function ... and whenever the state changes internally, we can invoke the callback function ....

````js
function createStore() {

    let state; // 1. set the tate

    const getState = () => state 
    
    // 2. returns the state of the application
    return {
        getState
    }
}

const store = createStoree();

store.subscribe(() => {
    console.log("The new state is: ", store.getState());
})

// they might want to subscribe more than one time ...
store.subscribe(() => {
    console.log("The store changed: ", store.getState());
})

````

Internally, we need to keep track every time the user calls subscribe.
And then eventually, when we add the functionality to be able to change the state of our store, we need to call every function that was passed in when subscribe was invoked....

````js
function createStore() {

    let state; 
    let listeners = []; // create a new array

    const getState = () => state 

    // create our subscribe method .. they could then pass subscribe a callback function
    // and when the state changes internally .. we invoke the callback function
    const subscribe = (listener) => { 
        listeners.push(listener);
    }
    
    return {
        getState,
        subscribe // return subscribe
    }
}

const store = createState();

store.subscribe(() => {
    console.log("The new state is: ", store.getState());
})

store.subscribe(() => {
    console.log("The store changed: ", store.getState());
})

````
### unsubscribe

````js
function createStore() {

    let state; 
    let listeners = []; 

    const getState = () => state 

    const subscribe = (listener) => { 
        listeners.push(listener);
        return () => {
            listener = listeners.filter((l) l = !== listener);
        }
    }
    
    return {
        getState,
        subscribe // return subscribe
    }
}

const store = createState();

store.subscribe(() => {
    console.log("The new state is: ", store.getState());
})

const unsubscribe = store.subscribe(() => {
    console.log("The store changed: ", store.getState());
})

// now invoke to remove that specific listener
unsubscribe();

````

#### 4. Update the state
> Rule #1: Only an event can change the state of the store.

When an event takes place in a Redux application, we use a plain JavaScript object to keep track of what the specific event was. This object is called an **Action**.
````js
{
  type: "ADD_PRODUCT_TO_CART"
}
````
What makes this plain JavaScript object special in Redux, is that every Action must have a **type** property. The purpose of the type property is to let our app (Redux) know exactly what event just took place. 

Now, since an Action is just a regular object, we can include extra data about the event that took place:
````js
{
  type: "ADD_PRODUCT_TO_CART",
  productId: 17
}
````
Pass as little data as possible in each action. That is, prefer passing the index or ID of a product rather than the entire product object itself.

**Action Creators** are functions that _create/return_ action objects. For example:
````js
const addItem = item => ({
  type: ADD_ITEM,
  item
});
````
### Quiz Results
````js
// Valid Action Creator
const receivePost = post => ({
  type: RECEIVE_POST,
  post
});

// Valid Action Crator
const receivePost = post => ({
  type: RECEIVE_POST,
  post: post
}); 

// Valid Action
const clearErrors = {
  type: CLEAR_ERRORS
};

// Valid Action
const addSeven = {
  type: 'ADD_NUMBER',
  number: 7
};

// Not Valid Action -- missing type
const removeComments = {
  comments: null
};
````
Both **receivePost** functions are _action creators_, which extrapolate the creation of an action object to a function. 
**clearErrors** and **addSeven**, on the other hand, are _action objects_ with a valid **type** key and optional payload. 
**removeComments** does not include a type key and is an invalid action.


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

## 6. Putting it All Together
We've finally finished creating the createStore function!
- we created a function called `createStore()` that returns a **store** object
- `createStore()` must be passed a **reducer** function when invoked
- the **store** object has three methods on it:
  - .getState() - used to get the current state from the store
  - .subscribe() - used to provide a listener function the store will call when the state changes
  - .dispatch() - used to make changes to the store's state
- the **store** object's _methods_ have access to the state of the store via closure




````js
// Library Code
function createStore (reducer) {
  // The store should have four parts
  // 1. The state
  // 2. Get the state.
  // 3. Listen to changes on the state.
  // 4. Update the state

  let state
  let listeners = []

  const getState = () => state

  const subscribe = (listener) => {
    listeners.push(listener)
    return () => {
      listeners = listeners.filter((l) => l !== listener)
    }
  }

  const dispatch = (action) => {
    state = reducer(state, action)
    listeners.forEach((listener) => listener())
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
    return state.concat([action.todo])
  }

  return state
}

const store = createStore(todos);
// createStore() gives us access to 
// 1. getState()
// 2. subscribe()
// 3. dispatch()

store.subscribe(() => {
  console.log('The new state is: ', store.getState());
})

store.dispatch({
  type: 'ADD_TODO',
  todo: {
    id: 0,
    name: 'Learn Redux',
    complete: false
  }
})
````

## 7. Managing More State
As of right now, our code is handling the `ADD_TODO` action. There are still a couple more actions that our app is supposed to be able to handle:
- the `REMOVE_TODO` action
- the `TOGGLE_TODO` action

Our todos **reducer** originally looked like the following:
````js
function todos (state = [], action) {
  if (action.type === 'ADD_TODO') {
    return state.concat([action.todo]);
  }

  return state;
}
````
To resolve additional action types, we added a few more conditions to our reducer logic:
````js
function todos (state = [], action) {
  if (action.type === 'ADD_TODO') {
    return state.concat([action.todo]);
  } else if (action.type === 'REMOVE_TODO') {
    // ...
  } else if (action.type === 'TOGGLE_TODO') {
    // ...
  } else {
    return state;
  }
}
````

To remove a todo item, we can call `filter()` on the state. 
This returns a new state (an array) with only todo items whose `id`'s do not match the `id` of the todo we want to remove.
````js
function todos (state = [], action) {
  if (action.type === 'ADD_TODO') {
    return state.concat([action.todo]);
  } else if (action.type === 'REMOVE_TODO') {
    return state.filter((todo) => todo.id !== action.id);
  } else if (action.type === 'TOGGLE_TODO') {
    // ...
  } else {
    return state;
  }
}
````

To handle toggling a todo item, we want to change the value of the complete property on whatever `id` is passed along on the action. 
We cna map over the entire state, and if `todo.id` matches `action.id`, we can use `Object.assign()` to return a new object with merged properties:
````js
function todos (state = [], action) {
  if (action.type === 'ADD_TODO') {
    return state.concat([action.todo]);
  } else if (action.type === 'REMOVE_TODO') {
    return state.filter((todo) => todo.id !== action.id);
  } else if (action.type === 'TOGGLE_TODO') {
    return state.map((todo) => todo.id !== action.id ? todo :
    Object.assign({}, todo, { complete: !todo.complete }));
  } else {
    return state;
  }
}
````

Refactoring our entire `todos` reducer to use a `switch` statement rather than multiple `if/else` statements:
````js
function todos (state = [], action) {
  switch(action.type) {
    case 'ADD_TODO' :
      return state.concat([action.todo]);
    case 'REMOVE_TODO' :
      return state.filter((todo) => todo.id !== action.id);
    case 'TOGGLE_TODO' :
      return state.map((todo) => todo.id !== action.id ? todo :
      Object.assign({}, todo, { complete: !todo.complete }));
    default :
      return state;
  }
}
````

### Putting it all together
````js
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
  }

  const dispatch = (action) => {
    state = reducer(state, action);
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
  switch(action.type) {
    case 'ADD_TODO' :
      return state.concat([action.todo]);  //concat (does not directly change state)
    case 'REMOVE_TODO' :
      return state.filter((todo) => todo.id !== action.id);  // filter (does not directly change state)
    case 'TOGGLE_TODO' :
      return state.map((todo) => todo.id !== action.id ? todo :  
        Object.assign({}, todo, { complete: !todo.complete })) //map (does not directly change state)
    default :
      return state;
  }
}

const store = createStore(todos)

store.subscribe(() => {
  console.log('The new state is: ', store.getState());
})



store.dispatch({
  type: 'ADD_TODO',
  todo: {
    id: 0,
    name: 'Learn Redux',
    complete: false
  }
});
````

### Adding Goals to our App
Currently, the app keeps track of a single piece of state - a list of todo items.
Let's make the app a bit more complicated and add in a second piece of state for our app to track - goals.

````js
function goals (state = [], action) {
  switch(action.type) {
    case 'ADD_GOAL' :
      return state.concat([action.goal])
    case 'REMOVE_GOAL' :
      return state.filter((goal) => goal.id !== action.id)
    default :
      return state
  }
}
````

We now have two reducers, but our dispatch can only handle one reducer.

