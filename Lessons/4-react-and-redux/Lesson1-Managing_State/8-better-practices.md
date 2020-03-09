## 8. Better Practices

Use a **constant** to set the **action types** to ensure an error will be thrown for misspelled action types when using strings for acction types.

```js
const ADD_TODO = 'ADD_TODO';
const REMOVE_TODO = 'REMOVE_TODO';
const TOGGLE_TODO = 'TOGGLE_TODO';
```



#### Action Creators

This is currently how we are calling store.dispatch

```js
store.dispatch({
    type: ADD_TODO,
    todo: {
        id: 0,
        name: 'Walk the dog',
        complete: false,
    }
});

store.dispatch({
    type: ADD_TODO,
    todo: {
        id: 1,
        name: 'Wash the car',
        complete: false,
    }
});
```

Create a function whose job is to return an object to dispatch, these are called **action creators**

```js
function addToDoAction(todo) {
    return {
        type: ADD_TODO,
        todo,
    }
}

function removeDoAction(id) {
    return {
        type: REMOVE_TODO,
        id,
    }
}

function toggleToDoAction(id) {
    return {
        type: TOGGLE_TODO,
        id,
    }
}
```

and now when **dispatch** is called, it can be simplified from:

```js
store.dispatch({
    type: ADD_TODO,
    todo: {
        id: 1,
        name: 'Wash the car',
        complete: false,
    }
});

store.dispatch({
    type: REMOVE_TODO,
    id: 1
});
```

to ...

```js
store.dispatch(addToDoAction({
    id: 1,
    name: 'Wash the car',
    complete: false,
}));

store.dispatch(removeToDoAcction(1));
```

