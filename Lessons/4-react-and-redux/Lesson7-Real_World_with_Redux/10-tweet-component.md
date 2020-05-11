# 10. Tweet Component

In Step 4 of the Planning Stage, we saw that this component will need access to the following data:

- `users`
- `tweets`
- `authedUser`. 

Let's connect this component to the store!



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Q6sAKQaQTJ8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=245" id="widget246" width="640" height="360" frameborder="0"></iframe>



Notice how we're passing an `id` prop along to the Tweet component:

```js
<Tweet id={id} />
```

Because we're doing this, the `mapStateToProps` function's second argument (`ownProps`) will be an object that has an `id` property with this value.



[![img](https://video.udacity-data.com/topher/2018/March/5abd6d97_untitled-diagram-21-4/untitled-diagram-21-4.png)Arguments inside the `mapStateToProps` function ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/3be2fe87-b450-4384-a64f-c42e9756b0f6#)



So as of right now, this is what the `mapStateToProps` function looks like:

```js
function mapStateToProps ({authedUser, users, tweets}, { id }) {
  const tweet = tweets[id];

  return {
    authedUser,
    tweet: formatTweet(tweet, users[tweet.author], authedUser)
  };
}
```

The important thing to notice here is that `mapStateToProps` accepts two arguments:

- the state of the store
- the props passed to the Tweet component

We're destructuring both arguments. From the store, we're extracting:

- the `authedUser` data 
- the users data
- the tweets data

Then we're getting the `id` from the props passed to the  Tweets Component. We need both of these pieces of data (coming from the  store's state and coming from the component) so that we can determine  which Tweet should be displayed by Tweet Component.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/fNHUigCJpkY?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=247" id="widget248" width="640" height="360" frameborder="0"></iframe>



So this is what the final state of the Tweet Component's `mapStateToProps` function looks like:

```js
function mapStateToProps ({authedUser, users, tweets}, { id }) {
  const tweet = tweets[id];
  const parentTweet = tweet ? tweets[tweet.replyingTo] : null;

  return {
    authedUser,
    tweet: tweet
      ? formatTweet(tweet, users[tweet.author], authedUser, parentTweet)
      : null
  };
}
```

Now that we're getting all of the data we need from the store, we can actually build the UI for the Tweet Component. 



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/es890SLMDqM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=249" id="widget250" width="640" height="360" frameborder="0"></iframe>



[Here are the code changes for building out the Tweet Component.](https://github.com/udacity/reactnd-chirper-app/commit/6db39add5b99c8e4996896ff3454c0239de4d5cc)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/FvmgIlJPjQ8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=251" id="widget252" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-chirper-app/commit/1fdbaaa20d45fbb94dc461405f756f17815f20fd)



#### Further Research

- [The Perils of Using a Common Redux Anti-Patterns](https://itnext.io/the-perils-of-using-a-common-redux-anti-pattern-344d778e59da)