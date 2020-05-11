## 5. Updating State

Let's step back one more time and think about *what* Redux is all about. The whole goal of Redux is to increase predictability:

> Redux is a predictable state container for JavaScript apps.

With this in mind, let's see dig into how we can use actions and our state tree to predictably manage an application's state.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/15sTwJsyWbU?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=21" id="widget22" width="640" height="360" frameborder="0"></iframe>



And we've got our second rule!

> The function that returns the new state needs to be a pure function.

So far, our rules are:

1. Only an event can change the state of the store.
2. The function that returns the new state needs to be a pure function.

A [pure function](https://en.wikipedia.org/wiki/Pure_function) can be a bit theoretical, so we'll take it step by step and explain why a pure function is so powerful and how it helps improve predictability.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/o9cWPrOMuyU?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=23" id="widget24" width="640" height="360" frameborder="0"></iframe>



## What are Pure Functions?

**Pure functions** are integral to how state in Redux applications is updated. By definition, pure functions:

1. Return the same result if the same arguments are passed in
2. Depend solely on the arguments passed into them
3. Do not produce side effects, such as API requests and I/O operations

Let’s check out an example of a pure function, `square()`:

```js
// `square()` is a pure function

const square = x => x * x;
```

`square()` is a pure function because it outputs the same  value every single time, given that the same argument is passed into it. There is no dependence on any other values to produce that result, and  we can safely expect *just* that result to be returned -- no side effects (more on this in a bit!).

On the other hand, let’s check out an example of an *impure* function, `calculateTip()`:

```js
// `calculateTip()` is an impure function

const tipPercentage = 0.15;

const calculateTip = cost => cost * tipPercentage;
```

`calculateTip()` calculates and returns a number value. However, it relies on a variable (`tipPercentage`) that lives *outside* the function to produce that value. Since it fails one of the requirements of pure functions, `calculateTip()` is an impure function. However, we could convert this function to a pure function by passing in the outside variable, `tipPercentage`, as a second argument to this function!

```js
const calculateTip = (cost, tipPercentage = 0.15) => cost * tipPercentage;
```

### Why Pure Functions Are Great

For our purposes, the most important feature of a pure function is  that it's predictable. If we have a function that takes in our state and an action that occurred, the function should (if it's pure!) return the exact same result *every single time*. 

You're going to be sick of this by the end ;-) but this course (and Redux!) are all about predictability!



### Question 1 of 4

![image-20200510100041211](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\images\5-quiz-q1)

### Question 2 of 4

![image-20200510100150471](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\images\5-quiz-q2)

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/QU_WvPaC6cM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=25" id="widget26" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/blob/the-reducer-function/index.js)



> ⚠️ Please, *do not use* default parameters in the following  programming quiz. It will throw an error when evaluating the response  and you'll not be able to get the correct answer.



```js
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
 
const DELETE_FLAVOR = 'DELETE_FLAVOR';

function appReducer (state, action) { 
  if (action.type === 'DELETE_FLAVOR') {
    return state.concat([action.deleteFlavor]);
  }

  return state;
}

// Action Creator
const deleteFlavor = flavor => ({
  type: DELETE_FLAVOR,
  flavor
});

// the Store
function createStore () {
  // The store should have four parts
  // 1. The state
  // 2. Get the state.
  // 3. Listen to changes on the state.
  // 4. Update the state

  let state = [
      { 
          flavor: 'Chocolate', 
          count: 0
      }, 
      { 
          flavor: 'Vanilla', 
          count: 0
      }];
      
  let listeners = []

  const getState = () => state;

  const subscribe = (listener) => {
    listeners.push(listener)
    return () => {
      listeners = listeners.filter((l) => l !== listener)
    }
  }

  return {
    getState,
    subscribe
  }
}


const store = createStore();
store.subscribe();
deleteFlavor('chocholate');

store.subscribe(() => {
    console.log("The new state is: ", store.getState());
});
```





<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/z5yJhTOxmMU?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=27" id="widget28" width="640" height="360" frameborder="0"></iframe>



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/wIyRfRSpvDo?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=29" id="widget30" width="640" height="360" frameborder="0"></iframe>



### Question 4 of 4

![image-20200510100344816](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\images\5-quiz-q4)

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/P09BK4IXzmk?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=31" id="widget32" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/blob/create-store-dispatch/index.js)



The new `dispatch()` method is pretty small, but is vital to our functioning store code. To briefly recap how the method functions:

- `dispatch()` is called with an Action
- the reducer that was passed to `createStore()` is called with the current state tree and the action...this updates the state tree
- because the state has (potentially) changed, all listener functions that have been registered with the `subscribe()` method are called



# Summary

In this section, we learned about a number of important points about  Redux. We learned about pure functions, a Reducer function (which,  itself, needs to be a pure function), dispatching changes in our store,  and identifying which parts of our code are generic library code and  which are specific to our app.