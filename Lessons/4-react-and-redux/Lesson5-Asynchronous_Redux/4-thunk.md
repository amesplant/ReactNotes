# 4. Thunk



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/WHbfLpT0Ftg?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=165" id="widget166" width="640" height="360" frameborder="0"></iframe>



Currently, our code for removing a todo item looks like this:

```js
removeItem(item) {
  const { dispatch } = this.props.store

  dispatch(removeTodoAction(item.id))

  return API.deleteTodo(item.id)
    .catch(() => {
      dispatch(addTodoAction(item))
      alert('An error occured. Try again.')
    })
  }
}
```

Do you see how we are mixing our component-specific code with the  API-specific code? If we move the data-fetching logic from our component to the action creator, our final `removeItem()` method might look like this:

```js
removeItem(item) {
  const { dispatch } = this.props.store

  return dispatch(handleDeleteTodo(item))
}
```

This is much better! The `removeItem()` function only has one task; dispatching that a specific item needs to be deleted. 

However, we need to make it so our `handleDeleteTodo` action creator makes an asynchronous request before it returns the action. What if we just return a promise from `handleDeleteTodo` that resolves with the action once we get the data? Well, that won't  quite work; as of right now, every action creator needs to return an *object*, not a promise:

```js
function asyncActionCreator (id) {
  return {
    type: ADD_USER,
    user: ??
  };
}
```

What if we used our knowledge of functional programming along with  our knowledge of Redux middleware to solve this? Remember that  middleware sits *between* the dispatching of an action, and the  running of the reducer. The reducer expects to receive an action object, but what if, instead of returning an object, we have our action creator return a function?

We could use some middleware to check if the returned action is  either a function or an object. If the action is an object, then things  will work as normal - it will call the reducer passing it the action.  However, if the action is a function, it can invoke the function and  pass it whatever information it needs (e.g. a reference to the `dispatch()` method). This function could do anything it needs to do, like making asynchronous network requests, and can then dispatch a *different* action (that returns a regular object) when its finished.

An action creator that returns a function might look something like this:

```js
function asyncActionCreator (id) {
  return (dispatch) => {
    return API.fetchUser(id)
    .then((user) => {
      dispatch(addUser(user));
    });
  };
}
```

Notice that we’re no longer returning the action itself! Instead,  we’re returning a function that is being passed dispatch. We then call  this function when we have the data. 

Now, this won’t work out of the box, but there's some good news: we  can add some middleware to our app to support it! Let’s go ahead and see what that actually looks like.



We'll be adding the [redux-thunk library](https://github.com/gaearon/redux-thunk) in the following video, so you'll need this:

```html
<script src="https://unpkg.com/redux-thunk@2.2.0/dist/redux-thunk.min.js"></script>
```



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/rrEV_gNSvmM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=167" id="widget168" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/524066483d154851d417e6567e50edca9b85109b)



💫Remember middleware executes in the order it is listed in the `applyMiddleware()` function.



## Benefits of Thunks

Out of the box, the Redux store can only support the *synchronous* flow of data. Middleware like **thunk** helps support *asynchronicity* in a Redux application. You can think of thunk as a wrapper for the store’s `dispatch()` method; rather than returning action objects, we can use thunk action creators to dispatch functions (or even or Promises).

Without thunks, synchronous dispatches are the default. We *could* still make API calls from React components (e.g., using the `componentDidMount()` lifecycle method to make these requests) -- but using thunk middleware  gives us a cleaner separation of concerns. Components don't need to  handle what happens after an asynchronous call, since API logic is *moved away* from components to action creators. This also lends itself to greater  predictability, since action creators will become the source of every  change in state. With thunks, we can dispatch an action only when the  server request is resolved!

![image-20200510105908665](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson5-Asynchronous_Redux\images\4-quiz-1)

### Question 2 of 2

Take a look at this example:

```js
export const fetchTodos = () => dispatch => (
  TodoAPIUtil
      .fetchTodos()
      .then(todos => dispatch(receiveTodos(todos)))
);
```



If a web application requires interaction with a server, applying middleware such as **thunk** helps solve the issue of asynchronous data flow. Thunk middleware allows us to write action creators that return *functions* rather than objects. 

By calling our API in an action creator, we make the *action creator* responsible for fetching the data it needs to create the action. Since  we move the data-fetching code to action creators, we build a cleaner  separation between our UI logic and our data-fetching logic. As a  result, thunks can then be used to delay an action dispatch, or to  dispatch only if a certain condition is met (e.g., a request is  resolved). 



## Further Research

- [Redux Thunk on GitHub](https://github.com/gaearon/redux-thunk)
- [Async Flow from the Redux docs](http://redux.js.org/docs/advanced/AsyncFlow.html)
- [Dan Abramov's Stack Overflow on Asynchronicity in Redux](http://stackoverflow.com/questions/35411423/how-to-dispatch-a-redux-action-with-a-timeout/35415559#35415559)