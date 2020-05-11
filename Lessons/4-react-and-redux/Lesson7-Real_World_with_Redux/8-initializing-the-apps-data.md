# 8. Initializing the App's Data



We have previously determined that we need to get the `users` and `tweets` data from our database and send that data to our store, along with the `authedUser` data, when the home page loads.

We have also created a thunk action creator that gets the data from  the database and then dispatches actions to the store to set the three  pieces of state we have in our store:

- `users`
- `tweets`
- `authedUser`

Here's what the `handleInitialData()` thunk action creator looks like:

```js
function handleInitialData () {
  return (dispatch) => {
    return getInitialData()
      .then(({ users, tweets }) => {
        dispatch(receiveUsers(users));
        dispatch(receiveTweets(tweets));
        dispatch(setAuthedUser(AUTHED_ID));
      });
  };
}
```

Now, the question is *where* do we dispatch this action creator?



### Quiz Question

![image-20200510113139191](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson7-Real_World_with_Redux\images\8-quiz)

- > That’s right! It is true that the root route will load correctly, but if we go to a different route -- `tweets/:id`, for example -- our store will still be empty and the tweet will not be found.

When we walked through the architecture of our app, we saw that the *App* Component will contain every other component. If we load the initial data (by dispatching the `handleInitialData()` action creator) from the App component, then no matter which route our users goes to, they’ll see all of the correct data.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/ydXVJmVqebQ?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=241" id="widget242" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-chirper-app/commit/a81f80deee8ba2692f805ba445b761aeb7357398)



Using the `connect()` function upgrades a component to a container. Containers can read state from the store and dispatch actions. Read more about our ability to  customize our container’s relationship with the store in the [`react-redux` API documentation](https://github.com/reactjs/react-redux/blob/master/docs/api.md). Make sure to go through the excellent examples  that are provided in the linked documentation to gain a deeper  understanding of Redux.