# 12. New Tweet Component



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/aEAUnJhyqCw?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=259" id="widget260" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-chirper-app/commit/c53a69a8b09a0dcab378761f683781c49ead072d)



## Adding a New Tweet

Let’s now work on the logic of adding a new tweet. Once the user  submits a new tweet, it should show up in the list of all of tweets and  be added to our database. Since this tweet will be used by more than one component, we know that we want to make sure the store is modified to  reflect the updated list of tweets. Recording tweets in a database is an asynchronous operation, so we can use [Redux Thunk](https://github.com/gaearon/redux-thunk) to issue the API request.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/MyjJlyv2H0I?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=261" id="widget262" width="640" height="360" frameborder="0"></iframe>



Let’s quickly cover a common JavaScript bug at this point.

Make sure that whenever an arrow function has curly braces, you’re using a `return` statement, if you want to return something. 



### Question 1 of 2

- ![image-20200510113637910](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson7-Real_World_with_Redux\images\12-quiz-1)

We know that our store looks like this:

```js
{
  tweets: {
    tweetId: { tweetId, authorId, timestamp, text, likes, replies, replyingTo}, 
    tweetId: { tweetId, authorId, timestamp, text, likes, replies, replyingTo}
  },
  users: {
    userId: {userId, userName, avatar, tweets array},
    userId: {userId, userName, avatar, tweets array}
  },
  authedUser: userId
}
```

Let’s start working on the New Tweet Reducer. How will we be modifying the state to reflect the new tweet?

This is going to be a two-part process:

1. the new tweet needs to be added to the list of tweets
2. an already existing tweet needs to be modified if the new tweet is a response to another tweet

In this reducer, we'll 1) concatenate the new tweet to the list of the already-existing tweets. Remember that the [object spread operator](https://redux.js.org/recipes/using-object-spread-operator) offers us the most concise way of doing that; and 2) modify the `replies` property of the tweet the new tweet is replying to.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/YdmgH1-U5jM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=263" id="widget264" width="640" height="360" frameborder="0"></iframe>



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/hWGIn12dGOM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=265" id="widget266" width="640" height="360" frameborder="0"></iframe>



[Here are the changes for adding the new tweet logic-handling code..](https://github.com/udacity/reactnd-chirper-app/commit/993f1b903e62bbd9ba78afdf4e8d698b7a0b8c66)



 In Step 2 of the Planning Stage, we determined that the New Tweet  Component will show up inside of the App Component when the user goes to the `/new` page and that it will be inside of the Tweet Page Component when the user is on the `/tweet/:id` page. 

When the user is at the `/new` route, the new tweet will not be attached to another tweet. When the user is at the `tweet/:id` route, the new tweet will be attached to the already-displayed tweet.  Notice that the route already contains the parent tweet’s `id`. We can just pass the `id` from the route to the New Tweet Component whenever we’re creating a reply tweet. 

What happens when someone clicks “Submit” to add a new tweet? The New Tweet Component will need to communicate with our store. We communicate with the store by dispatching actions. `dispatch` is a method on the store. That means that the New Tweet Component needs to be `connect()`ed to Redux. Once a component is connected to the store, it will have `dispatch` on its `props`.



### Question 2 of 2

![image-20200510113805121](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson7-Real_World_with_Redux\images\12-quiz-2)

- > `mapStateToProps` is called whenever the store is updated 

- 

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/4g9l8T2MLt4?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=267" id="widget268" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-chirper-app/commit/171ed69e495cadab991aff900b9ad5e2f4005c20)



### Lesson Challenge

Suppose we replaced the `case ADD_TWEET:` portion of the code in the `reducers/tweets` file with the code below.

- Would the state change in the same way? Why or why not?
- Would the new tweet appear on the page? Why or why not?

Run the code to check your answer.

```js
...
case ADD_TWEET :
   const { tweet } = action

   let replyingTo = {}
   if (tweet.replyingTo !== null) {
      const allReplies = state[tweet.replyingTo].replies.concat([tweet.id]);

      return {
      ...state,
      [action.tweet.id]: action.tweet,
      [action.tweet.replyingTo.replies]: allReplies
      }
   }

   return {
      ...state,
      [action.tweet.id]: action.tweet,
      ...replyingTo,
   }
...
```



#### Further Learning

Carefully go over the [Immutable Update Patterns](https://redux.js.org/recipes/structuringreducers/immutableupdatepatterns) and [Designing the State Shape](https://redux.js.org/basics/reducers#designing-the-state-shape) pages in the Redux documentation.



Remember, that [doing a shallow copy of the top level is not sufficient - [nestedState objects\] should be copied as well.](https://redux.js.org/recipes/structuringreducers/immutableupdatepatterns)