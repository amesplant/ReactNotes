## 4. Create Store: Getting and Listening

In this section, we'll be building the store. If you remember from the  previous section, the store has the following information:

- the state tree
- a way to get the state tree
- a way to listen and respond to the state changing
- a way to update the state



[![img](https://video.udacity-data.com/topher/2018/March/5abbd27d_nd019-redux-l1-04-the-store/nd019-redux-l1-04-the-store.png)The Store contains the state tree and provides ways to interact with the state tree. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/5b8c33c7-29d0-4fa4-9a03-ba49d1a2cb35/concepts/d137f3e4-6ddc-4c1f-b6e8-84fecaa19748#)



So this is what we're going to do in this lesson - we're going to actually *create* the store code ourselves, from scratch.

In the following video, we'll start with a blank `index.js` file and create a factory function that creates *store* objects. Then we'll have the store keep track of the state, and we'll write the method to get the state from the store.

Pop open your code editor, and let's get started!



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/YqmnAPNCxkQ?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=11" id="widget12" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/blob/getting-the-state/index.js)



In this screencast, we started building out the `createStore` function. Currently, this factory function:

- takes in no arguments
- sets up a local (private) variable to hold the state
- sets up a `getState()` function
- returns an object that publicly exposes the `getState()` function

Let's take a look at the `getState()` function



### Question 1 of 5

![image-20200510100454849](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\images\4-quiz-q1)

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/AWOuF_qoEh8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=13" id="widget14" width="640" height="360" frameborder="0"></iframe>



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/5jVn0L7nlBA?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=15" id="widget16" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/blob/listening-to-changes/index.js)



Keep in mind that 

```js
const subscribe = (listener) => {
    listeners.push(listener)
    return () => {
      listeners = listeners.filter((l) => l !== listener)
    }
  }
```

is equivalent to the following ES5: 

```js
var subscribe = function subscribe(listener) {
  listeners.push(listener);
  return function () {
    listeners = listeners.filter(function (l) {
      return l !== listener;
    });
  };
};
```



### Question 2 of 5

![image-20200510100601246](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\images\4-quiz-q2)

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/-MtD_RCqKK4?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=17" id="widget18" width="640" height="360" frameborder="0"></iframe>



We've got our first rule!

> Only an event can change the state of the store.

Ok...well, without knowing what an "event" is, this rule is less than helpful :-\ Fear not, because we're going to look at what events are in this video:



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/4SSkRoVunbI?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=19" id="widget20" width="640" height="360" frameborder="0"></iframe>



When an event takes place in a Redux application, we use a plain JavaScript  object to keep track of what the specific event was. This object is  called an **Action**. 

Let's take another look at an Action:

```js
{
  type: "ADD_PRODUCT_TO_CART"
}
```

As you can see, an Action is clearly just a **plain JavaScript object**. What makes this plain JavaScript object special in Redux, is that *every Action must have a `type` property*. The purpose of the `type` property is to let our app (Redux) know *exactly* what event just took place. This Action tells us that a product was  added to the cart. That's incredibly descriptive and quite helpful,  isn't it?

Now, since an Action is just a regular object, we can include extra data about the event that took place:

```js
{
  type: "ADD_PRODUCT_TO_CART",
  productId: 17
}
```

In this Action, we're including the `productId` field. Now we know exactly which product was added to the store! 

One more note to keep in mind as you build your Action objects: it's  better practice to pass as little data as possible in each action. That  is, prefer passing the index or ID of a product rather than the *entire product object* itself.

**Action Creators** are functions that create/return action objects. For example: 

```js
const addItem = item => ({
  type: ADD_ITEM,
  item
});
```

or in ES5:

```js
var addItem = function addItem(item) {
  return {
    type: ADD_ITEM,
    item: item
  };
};
```



### Question 3 of 5

![image-20200510100641321](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\images\4-quiz-q3)

### Question 4 of 5

![image-20200510100710158](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\images\4-quiz-q4)

# Quiz: Valid Action?

Consider the following five options for the next quiz:

```js
// A

const receivePost = post => ({
  type: RECEIVE_POST,
  post
});
// B

const receivePost = post => ({
  type: RECEIVE_POST,
  post: post
}); 
// C

const clearErrors = {
  type: CLEAR_ERRORS
};
// D

const addSeven = {
  type: 'ADD_NUMBER',
  number: 7
};
// E

const removeComments = {
  comments: null
};
```



### Question 5 of 5

![image-20200510100746315](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\images\4-quiz-q5)

# Summary

In this section, we started creating our store by building out a `createStore()` function. So far, this function keeps track of the state, and provides a method to get the state and one to keep track of listener functions  that will be run whenever the state changes.

In the next section, we'll add a method to handle updating the state.