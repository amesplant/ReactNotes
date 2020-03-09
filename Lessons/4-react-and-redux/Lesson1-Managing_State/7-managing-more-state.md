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

> The `**filter()**` method **creates a new array** with all elements that pass the test implemented by the provided function.

```js
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

// create a new array with the words in the 'words' array where the word has more than 6 characters
const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```



This returns a new state (an array) with only todo items whose `id`'s do not match the `id` of the todo we want to remove.

````js
function todos (state = [], action) {
  if (action.type === 'ADD_TODO') {
    return state.concat([action.todo]);
  } else if (action.type === 'REMOVE_TODO') {
      // return a new array with to do items that include all todo items except for the one that we are trying to remove
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

- Todos Reducer
- Goals Reducer

Each is responsible for handling their specific slice of the state tree.

#### Issue

When we called **createStore**, we passed to it our single **Todos** reducer. Whenever **dispatch** was called, we'd call this reducer, passing it the current **state** and the **action** which was dispatched, and we'd get back the new state.

Well, now we have *not only* our **Todos** reducer, but we also have our **Goals** reducer, and each are expected to receive their specific slice of the **state** tree whenever an **action** is **dispatched**.

What we need to do, is instead of passing **createStore** our single **Todos reducer**, we want to create a *root reducer function* which will be responsible for calling the correct reducer whenever specific actions are dispatched.

#### Solution

Create a brand new **reducer** *app* , which will take in the **state** as well as an **action**, and whatever app *returns* is going to be the new state of our application.

Instead of our state just being an array of todo items, we now want our state to be an object that is going to have two properties, **todos** as well as **goals**.

````js
// when app is invoked for the first time, state will be undefined, so we set it to an empty object
function app(state = {}, action) {
    return {
        todos: todos(state.todos, action);
        goals: goals(state.goals, action);
    }
}

// todos reducer - state.todos
// goals reducer - state.goals
````

and now when we create the store, we can pass **createStore** our main app *root reducer*, so now whenever dispatch is called, we invoke our *app function*, and our *app function* is going to invoke the **todos reducer** as well as the **goals reducer**.

````js
const store = createStore(app);
````



**app.js**

````js
function todos (state = [], action) {
  switch(action.type) {
    case 'ADD_TODO' :
      return state.concat([action.todo])
    case 'REMOVE_TODO' :
      return state.filter((todo) => todo.id !== action.id)
    case 'TOGGLE_TODO' :
      return state.map((todo) => todo.id !== action.id ? todo :
        Object.assign({}, todo, { complete: !todo.complete }))
    default :
      return state
  }
}

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

function app (state = {}, action) {
  return {
    todos: todos(state.todos, action),
    goals: goals(state.goals, action),
  }
}

/*
Passing the root reducer to our store since our createStore function can only take one reducer.
*/

const store = createStore(app);
````

