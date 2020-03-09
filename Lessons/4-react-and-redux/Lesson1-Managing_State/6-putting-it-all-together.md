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

## 