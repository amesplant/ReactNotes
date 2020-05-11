# 7. Reducers & Middleware



# Reducers

A [Reducer](https://redux.js.org/basics/reducers) describes *how* an application's state changes. You’ll often see the [Object Spread Operator](https://redux.js.org/recipes/using-object-spread-operator) (`...`) used inside of a reducer because a reducer **must return a \*new\* object** instead of mutating the old state. If you need a refresher on the spread operator, check out [this ES6 lesson](https://classroom.udacity.com/nanodegrees/nd019/parts/290ec447-6555-41bf-ac39-457220a09aae/modules/9c5b7af0-0943-4d6e-b672-520440885aba/lessons/42383e89-ac6a-491a-b7d0-198851287bbe/concepts/398d36e6-3393-4c50-b870-44a4dffb0ac4).

If you want to know *why* Redux requires immutability, check out the [Immutable Data Section of the docs:](https://redux.js.org/faq/immutable-data#why-is-immutability-required).

Reducers have the following signature:

```js
(previousState, action) => newState
```

In our app, the `tweets` reducer will determine how the `tweets` part of the state changes. The `users` reducer will determine how the `users` part of the state changes, and so forth:



[![img](https://video.udacity-data.com/topher/2018/March/5abd6717_image5/image5.png)This is how our state will be modified. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/95858356-82cd-48eb-82ed-27c70683fbd9#)



# Initializing State

There are 2 ways to initialize the state inside the store:

- You can pass the initial state (or a part of the initial state) as `preloadedState` to the `createStore` function.

For example: 

```js
const store = createStore (
  rootReducer,
  { tweets: {} }
);
```

- You can include a default state parameter as the first argument inside a particular reducer function.

For example: 

```js
function tweets (state = {}, action) {
}
```

To see how these approaches interact, check out the [Initializing State section of the documentation](https://redux.js.org/recipes/structuring-reducers/initializing-state).



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/QnntUz8r9lo?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=235" id="widget236" width="640" height="360" frameborder="0"></iframe>



In our app, we initialized each slice of the store by setting a default `state` value as the first parameter inside each reducer function.

At this point, our store looks like this:



[![img](https://video.udacity-data.com/topher/2018/March/5abd6ca3_image4/image4.png)Initialized State Inside the Store ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/95858356-82cd-48eb-82ed-27c70683fbd9#)



The **tweets** slice of the state in the store has been initialized to an empty object. The **users** slice of the state in the store has been initialized to an empty object. And, the **authedUser** slice of the state in the store has been initialized to null.



So, we have a `tweets` to manage the *tweets* slice of the state, a `users` reducer to manage the *users* slice of the state, and an `authedUser` reducer to manage the *authedUser* portion of the state. Each of these reducers will manage just its own part of the state. 

We will combine all of these reducers into one main, root reducer, which will combine the results of calling the `tweets` reducer, `users` reducer, and `authedUser` reducer into a single state object. Remember, we need to do this because the `createStore` function only accepts a single reducer.

```js
combineReducers({
  authedUser: authedUser,
  tweets: tweets,
  users: users
});
```

Or using ES6's [property shorthand](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer), it can just be:

```js
combineReducers({
  authedUser,
  tweets,
  users
});
```



Now that all of our reducers are set up, we need to actually create the  store and provide it to our application. To actually use any of the code that we've written up to this point, we need to install the `redux` package. Then, to provide the store to our application, we'll also need to install the `react-redux` package.

So install these packages and then restart your terminal:

```bash
yarn add react-redux redux
```



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Ac3-sWH49XY?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=237" id="widget238" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in the previous videos.](https://github.com/udacity/reactnd-chirper-app/commit/99605e45670d8beabb571c77a8943d7c64f9be75)



Redux applications have a single store. We have to pass the Root Reducer to our `createStore()` function in order for the store to know what pieces of state it should  have. The point of creating a store is to allow components to be able to access it without having to pass the data down through multiple  components.

The `Provider` component (which comes from the `react-redux` package) makes it possible for all components to access the store via the `connect()` function.



# Middleware

Our last bit of setup involves setting up the app's Middleware  functions. Just like in the previous Todos application, we're going to  create a *logger* middleware that will help us view the actions and state of the store as we interact with our application. Also, since the `handleInitialData()` action creator in `src/actions/shared.js` returns a function, we'll need to install the `react-thunk` package:

```bash
yarn add redux-thunk
```



In the next video, we’ll hook up our `redux-thunk` middleware, so our thunk action creators actually work. We’ll also put  in logger middleware to make debugging easier. Do you remember how to  build custom middleware?

All middleware follows this currying pattern:

```js
const logger = (store) => (next) => (action) => {
 // ...
}
```

Use [the Babel Repl](http://babeljs.io/repl/#?babili=false&browsers=&build=&builtIns=false&code_lz=Q&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=true&fileSize=false&lineWrap=false&presets=latest%2Creact%2Cstage-2&prettier=false&targets=&version=6.26.0&envVersion=) if you want to see this code in ES5.

The variable `logger` is assigned to a function that takes the `store` as its argument. That function returns another function, which is passed `next` (which is the next middleware in line or the dispatch function). That  other function return another function which is passed an `action`. Once inside that third function, we have access to `store`, `next`, and `action`.

It’s important to note that the value of the `next` parameter will be determined by the `applyMiddleware` function. Why? All middleware will be called in the order it is listed in that function. In our case, the `next` will be `dispatch` because `logger` is the last middleware listed in that function.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/HXYqXy4uflw?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=239" id="widget240" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-chirper-app/commit/6176c497a95b10c101a0d9104a160d44645b40f2)



Here’s our middleware wiring: 

```js
export default applyMiddleware(
  thunk,
  logger
);
```

Each thing returned by an action creator - be it an action or a  function - will go through our thunk middleware. This is the source code for the thunk middleware:

```js
function createThunkMiddleware(extraArgument) {
  return ({ dispatch, getState }) => next => action => {
    if (typeof action === 'function') {
      return action(dispatch, getState, extraArgument);
    }
    return next(action);
  };
}

const thunk = createThunkMiddleware();
thunk.withExtraArgument = createThunkMiddleware;

export default thunk;
```

If the thunk middleware sees an *action*, that action will be sent to the next middleware in line - the logger middleware. If it sees a *function*, the `thunk` middleware will call that function. That function can contain side  effects - such as API calls - and dispatch actions, simple Javascript  objects. These dispatched actions will again go to all of the  middleware. The thunk middleware will see that it’s a simple action and  pass the action on to the next middleware, the logger.

Once inside the logger:

```js
const logger = store => next => action => {
  console.group(action.type); 
  console.log("The action:", action);
  const returnValue = next(action);
  console.log("The new state:", store.getState());
  console.groupEnd();
  return returnValue;
};
```



### Quiz Question

Would these two pieces of code make the logger produce the same output in the console?

```js
export default applyMiddleware(
  logger,
  thunk
);
export default applyMiddleware(
  thunk,
  logger
);
```

- > No, the middleware is called in the order it is listed in this function. The thunk action creators we're using to load initial date, save tweets,  and toggle tweets are functions. So if they go to the logger middleware *before* going to the thunk middleware (which takes the functions and executes them, thereby obtaining `action`s to pass to the reducers), we're going to be logging function, not the actual actions.