## 7. Managing More State

As of right now, our code is handling the `ADD_TODO` action. There are still a couple more actions that our app is supposed to be able to handle:

- the `REMOVE_TODO` action
- the `TOGGLE_TODO` action



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/a3giVoHKkHE?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=63" id="widget64" width="640" height="360" frameborder="0"></iframe>



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Yqeks3OSY6M?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=65" id="widget66" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/blob/more-actions/index.js)



## Recap of New Actions

Our app can not only handle *adding* todo items -- it can now handle *removing* a todo item, as well as *toggling* a todo item (as complete or incomplete)! To make this all possible, we updated our `todos` reducer to be able to respond to actions of the `type` `REMOVE_TODO` and `TOGGLE_TODO`. 

Before moving on, let's make sure we're on the same page on how this was all implemented. Our `todos` reducer originally looked like the following:

```js
function todos (state = [], action) {
  if (action.type === 'ADD_TODO') {
    return state.concat([action.todo]);
  }

  return state;
}
```

To resolve additional action types, we added a few more conditions to our reducer logic:

```js
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
```

Note that just like the original `todos` reducer, we simply return the original state if the reducer receives an action type that it's not concerned with.

To remove a todo item, we called `filter()` on the state. This returns a new state (an array) with only todo items whose `id`'s *do not* match the `id` of the todo we want to remove:

```js
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
```

To handle toggling a todo item, we want to change the value of the `complete` property on whatever `id` is passed along on the action. We mapped over the entire state, and if `todo.id` matched `action.id`, we used `Object.assign()` to return a new object with merged properties:

```js
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
```

We then refactored our entire `todos` reducer to use a `switch` statement rather than multiple `if`/`else` statements:

```js
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
```

In the above snippet, we matched `cases` against an expression (i.e., `action.type`), and executed statements associated with that particular `case`. 

Let's now extend our app with some additional functionality!



## Adding Goals to our App

Currently, the app keeps track of a single piece of state - a list of todo items.

Let's make the app a bit more complicated and add in a second piece of state for our app to track - goals.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/kPYmzsY2RAo?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=67" id="widget68" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/blob/goals-reducer/index.js)



##### It's best if you're working with the code directly and following along, so make sure to check off each of the following:

Task List

- [ ] Create a `goals` reducer
- [ ] My `goals` reducer contains a  `ADD_GOAL` action type
- [ ] My `goals` reducer contains a  `REMOVE_GOAL` action type
- [ ] My `goals` reducer handles the default case



I kind of pointed it out at the end of the previous screencast, but we now have *two* reducer functions:

- `todos`
- `goals`

However, the `createStore()` function we built can only handle a *single* reducer function:

```js
// createStore takes one reducer function as an argument
const store = createStore(todos);
```

We can't call `createStore()` passing it two reducer functions:

```js
// this will not work
const store = createStore(todos, goals);
```

So we've got a problem...



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/QTNV7BP7dWs?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=69" id="widget70" width="640" height="360" frameborder="0"></iframe>



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/qL0HB_kmiQ0?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=71" id="widget72" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/blob/combine-reducers/index.js)



Whenever `dispatch` is called, we invoke our `app` function. The `app` function will then invoke the `todos` reducer as well as the `goals` reducer. Those will return their specific portions of the state. And then, the `app` function will return a state object with a `todos` property (the value of which is what the `todos` reducer returned) and a `goals` property (the value of which is what the `goals` reducer returned).

```js
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
```



### Quiz Question

Select all statements that are true.

- Reducers must be pure
- Though each reducer handles a different slice of state, we must combine reducers into a single reducer to pass to the store
- `createStore()` takes only one `reducer` argument
- Reducers are typically named after the slices of state they manage

# Summary

In this section, we bolstered our application to handle a number of  different actions as well as an entirely new piece of state! In addition to our app handling the `ADD_TODO` action, it now handles:

- the `REMOVE_TODO` action
- the `TOGGLE_TODO` action

We also created the `goals` reducer which handles:

- an `ADD_GOAL` action
- a `REMOVE_GOAL` action

So our application can now manage the state of our todos and goals, and it can do all of this, predictably!

In the next and final section of this lesson, we'll look at how we  can convert some of our existing functionality to follow best practices.