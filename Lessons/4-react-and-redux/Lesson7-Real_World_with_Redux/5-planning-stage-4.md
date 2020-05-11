# 5. Planning Stage: Step 4 - Data and the Store



# Determine What Data Lives in the Store

Remember that the main problems that Redux (and the react-redux bindings!)  was meant to solve were:

- Propagation of props through the entire component tree.
- Ensuring consistency and predictability of the state across the app.

According to Dan Abramov, the creator of Redux, we should follow the  following principle for determining whether to store a piece of data in  the store or in a React component:

> "Use Redux for state that matters globally or is mutated in complex ways… The rule of thumb is: do whatever is less awkward."

Take a look at [Organizing State](https://redux.js.org/faq/organizing-state) and [How to choose between Redux's store and React's state?](https://github.com/reactjs/redux/issues/1287) for further information about this.

For each piece of data from Step 3, let's see whether it's used by multiple components or mutated in a complex way.

*Text of the new tweet* *Used by*: New Tweet Component

This piece of data is not used by multiple components and is not  mutated in a complex way. That means that it's a great candidate for  component state instead of app state that resides in the store.

*Tweets* *Used by*: Dashboard Component, Tweet Page Component, Tweet Component

In the Tweet Page Component, we need to show the reply tweets. Let's take a look at our starter code in the `_Data.js` file. This is how the tweets are stored in the database:

```js
let tweets = {
  tweetId: {
    id: tweetId,
    text: tweetText,
    author: userId,
    timestamp: timestamp,
    likes: [userId1, userId2],
    replies: [tweetId1, tweetId2],
    replyingTo: tweetId_OR_null
  }
};
```

To get the reply tweets, we can get the tweet with a specific id from the list of all of the tweets and access its `replies` property.

In the Dashboard Component, we need to access the current list of  tweets. If the Dashboard Component knows the ID of the tweet that needs  to be displayed, it can just pass that ID to the Tweet Component, which  will render the tweet.

In the Tweet Component, we need to pick out a tweet with a specific id from the current list of tweets. 

That means that we can store the tweets in the store and make the  Tweet Page Component, the Dashboard Component, and the Tweet Component  into containers (components that have access to the store via the `connect` function).

As soon as that data changes — if someone likes the tweet, for example — all of the components that use that data will update.



[![img](https://video.udacity-data.com/topher/2018/March/5abd64fe_1-2/1-2.png)The Store contains a tweets property. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/7eef8e73-7871-4526-b12a-23e3a15a3a16#)



Keep in mind that each tweet contains the author's name and the author's avatar. One way we could model our state is:

```js
tweets: {
  tweetId: {tweetId, authorId, authorName, authorAvatar, timestamp, text, likes, replies, replyingTo},
  tweetId: {tweetId, authorId, authorName, authorAvatar, timestamp, text, likes, replies, replyingTo}
}
```

Modeling the state this way is not wrong, but it's inconvenient if we want to extend the functionality of our application in the future to be able to find tweets made by a particular author. 

Moreover, this way of storing the data mixes the two types of objects:

- tweets data
- user data

This goes against the recommendation to normalize our state. According to the [Redux documentation](https://redux.js.org/recipes/structuring-reducers/normalizing-state-shape), here are the principles of state normalization:

- Each *type* of data gets its own "table" in the state.
- Each "data table" should store the individual items in an object,  with the IDs of the items as keys and the items themselves as the  values.
- Any references to individual items should be done by storing the item's ID.
- Arrays of IDs should be used to indicate ordering.

In our application, normalized state would look like this:

```js
{
  tweets: {
    tweetId: { tweetId, authorId, timestamp, text, likes, replies, replyingTo},
    tweetId: { tweetId, authorId, timestamp, text, likes, replies, replyingTo}
  },
  users: {
    userId: {userId, userName, avatar, tweetsArray},
    userId: {userId, userName, avatar, tweetsArray}
  }
}
```

Our store at this point:



[![img](https://video.udacity-data.com/topher/2018/March/5abd6595_1/1.png)The Store contains a tweets property and a users property. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/7eef8e73-7871-4526-b12a-23e3a15a3a16#)



Let's continue going through our data. 

*authedUser* *Used by*: Tweet Component, New Tweet Component

Each Tweet Component needs to show whether the logged in used has  liked a tweet. In order to do that, we need to know who the logged in  user is. From looking at our Component Hierarchy from Step 2, we know  that the Tweet Component gets used by multiple components. Therefore, we need to upgrade this component to a container so it could access the `authedUser` piece of data from the store to see whether to show a red heart.

We also know that for every new tweet, we'll have to record who the  tweet's author (authedUser) is. The React way of storing state is to put the state in the most parent component and then pass it down to all the children that need it. In this app, that would mean storing in the App  Component.

One way to do that is to store the authedUser in the App Component  and then pass it down to the components that need access to it. While  this works, it's inconvenient. It would be much simpler to just store  the autheredUser in the store and then provide the Tweet Component  access to the store. The New Tweet Component could then just dispatch an action with the text of the new tweet and the id of the tweet we're  replying to as parameters in order to save the new tweet. 

Saving a tweet is an asynchronous operation and we could use redux  thunks to do that. Thunks give us access to the store, so we could have  the following action creator: 

```js
function handleAddTweet(text, replyingTo) {
  return (dispatch, getState) => {
    const { authedUser } = getState();

    return saveTweetToDatabase({
      text,
      author: authedUser,
      replyingTo
    }).then(tweet => dispatch(addTweet(tweet)));
  };
}
```

Generally, accessing the store from an action creator is [considered an anti-pattern](https://stackoverflow.com/questions/35667249/accessing-redux-state-in-an-action-creator/35674575#35674575). Dan Abramov says that the few use cases where it's acceptable to do that are:

> to check cached data before you make a request or to check whether  you are authenticated (in other words, doing a conditional dispatch).

Another reason we would want to keep the `authedUser`  piece of data in the store is that if we extend our application to  include the ability to sign in and sign out, this functionality would be easy to manage with Redux.

The New Tweet Component doesn't need to access the `authedUser` piece of state, but it *does* need to be able to dispatch an action to let the reducers know that a new tweet has been made. In order to have access to the `dispatch` method, a component must be connected to the store. In other words, it  must be a container. So, we know that both the Tweet Component and the  New Tweet Component will be upgraded to containers.



[![img](https://video.udacity-data.com/topher/2018/March/5abd5886_1/1.png)The Store contains a tweets property, a users property, and an authedUser property. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/7eef8e73-7871-4526-b12a-23e3a15a3a16#)



We are done making our store! While we were making our store, we also  determined which components will be upgraded to containers, so our  skeleton app is now even more complete.

We are now at a good point to start coding. We will go view by view and fill in the details of our skeleton along the way.