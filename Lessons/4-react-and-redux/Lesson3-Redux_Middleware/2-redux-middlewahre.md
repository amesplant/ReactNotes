# 2. Redux Middleware



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/WOEUwVOI0iw?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=141" id="widget142" width="640" height="360" frameborder="0"></iframe>



You’ve learned how Redux makes state management more predictable: in order to  change the store’s state, an action describing that change must be  dispatched to the reducer. In turn, the reducer produces the *new* state. This new state replaces the previous state in the store. So the next time `store.getState()` is called, the new, most up-to-date state is returned.

Between the dispatching of an action and the reducer running, we can introduce code called **middleware** to *intercept* the action before the reducer is invoked. The [Redux docs](http://redux.js.org/docs/advanced/Middleware.html) describe middleware as:



What's great about middleware is that once it receives the action, it can carry out a number of operations, including:

- producing a side effect (e.g., logging information about the store)
- processing the action itself (e.g., making an asynchronous HTTP request)
- redirecting the action (e.g., to another piece of middleware)
- dispatching supplementary actions

…or even some combination of the above! Middleware can do any of these *before* passing the action along to the reducer.

Let's replace our `checkAndDispatch()` function with a real Redux middleware function.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/2Dx7OBAEhV0?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=143" id="widget144" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/e1e96d97cd1566a35a34623fc5b43d1a0ba5d3ef)

# Where Middleware Fits

The way we had to structure our code originally, our `checkAndDispatch()` function *had* to run *before* `store.dispatch()`. Why is this? Because when `store.dispatch()` is invoked, it immediately calls the reducer that was passed in when `createStore()` was invoked. If you remember back to the first lesson, this is what our `dispatch()` function looked like (and is very similar to the real Redux `dispatch()` function):

```js
const dispatch = (action) => {
 state = reducer(state, action)
 listeners.forEach((listener) => listener())
}
```

So you can see that calling `store.dispatch()` will *immediately* invoke the `reducer()` function. There's no way to run anything in between the two function calls. So that's why we had to make our `checkAndDispatch()` so that we can run verification code *before* calling `store.dispatch()`.

However, this isn't maintainable. If we wanted to add another check, then we'd need to write *another* preceding function, that then calls `checkAndDispatch()` that *then* calls `store.dispatch()`. Not maintainable at all.

With Redux's middleware feature, we can run code *between* the call to `store.dispatch()` and `reducer()`. The reason this works, is because Redux's version of `dispatch()` is a bit more sophisticated than ours was, and because we provide the middleware functions when we create the store.

```js
const store = Redux.createStore( <reducer-function>, <middleware-functions> )
```

Redux's `createStore()` method takes the reducer function  as its first argument, but then it can take a second argument of the  middleware functions to run. Because we set up the Redux store with  knowledge of the middleware function, it runs the middleware function  between `store.dispatch()` and the invocation of the reducer.



## Applying Middleware

Just as we saw in the previous video, we can implement middleware  into a Redux app by passing it in when creating the store. More  specifically, we can pass in the `applyMiddleware()` function as an optional argument into `createStore()`. Here's `applyMiddleware()`'s signature:

```js
applyMiddleware(...middlewares)
```

Note the spread operator on the `middlewares` parameter.  This means that we can pass in as many different middleware as we want!  Middleware is called in the order in which they were provided to `applyMiddleware()`. 

We currently have the `checker` middleware applied to our app, but we'll soon add a new `logger` middleware as well. To create a Redux store that uses our `checker` middleware, we can do the following:

```js
const store = Redux.createStore(rootReducer, Redux.applyMiddleware(checker))
```



> ## 💡Functions Returning Functions 💡
>
> Redux middleware leverages a concept called **higher-order functions**. A higher-order function is a function that either:
>
> - *accepts* a function as an argument 
> - *returns* a function
>
> Higher-order functions are a powerful programming technique that  allow functions to be significantly more dynamic. You've actually  already written a higher-order function in this course. The `createRemoveButton()` function is a higher-order function because the `onClick` parameter is expected to be a function (because `onClick` is set up as an event listener callback function.
>
> For a refresher on higher-order functions, feel free to check out Lesson 2 in [Object-Oriented JavaScript](https://www.udacity.com/course/object-oriented-javascript--ud711).

![image-20200510105132609](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson3-Redux_Middleware\images\2-quiz-1)

### A New Middleware: Logging

Currently, our application is making use of a single middleware: `checker`. Because we can use multiple middleware functions in a single application, let's create a new middleware function called `logger` that will log out information about the state and action.

The benefits of this `logger()` middleware function are  huge while developing the application. We'll use this middleware to  intercept all dispatch calls and log out what the action is that's being dispatched and what the state changes to *after* the reducer has run. Being able to see this kind of information will be immensely  helpful while we're developing our app. We can use this info to help us  know what's going on in our app and to help us track down any pesky bugs that creep in. 



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/GWrRJOTCfI8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=145" id="widget146" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/e07e1785e0bf90b2128eac3a63674ec9c8daabac)

![image-20200510105242109](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson3-Redux_Middleware\images\2-quiz-2)

# Summary

In this section, we looked at using middleware. According to the Redux docs:

> Middleware is the suggested way to extend Redux with custom functionality.

Middleware is added to the Redux store using `Redux.applyMiddleware()`. You can only add middleware when you initially create the store:

```js
const store = Redux.createStore( <reducer-function>, Redux.applyMiddleware(<middleware-functions>) )
```



## Further Research

The following might be a bit advanced at this point, but give them a  quick read through right now and definitely bookmark them to come back  and read later:

- [Middleware Docs](https://redux.js.org/advanced/middleware)
- [API for Redux's Middleware](https://redux.js.org/api-reference/applymiddleware)