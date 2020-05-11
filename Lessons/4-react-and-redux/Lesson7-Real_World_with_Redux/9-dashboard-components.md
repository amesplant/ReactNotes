# 9. Dashboard Component

In Step 4 of the Planning Stage, we determined that our store should look like this:

In our application, normalized state would look like this:

```js
{
  tweets: {
    tweetId: { tweet id, author’s id, timestamp, text, likes, replies, replyingTo},
    tweetId: { tweet id, author’s id, timestamp, text, likes, replies, replyingTo}
  },
  users: {
    userId: {user’s id, user’s name, avatar, tweets array},
    userId: {user’s id, user’s name, avatar, tweets array}
  }
}
```

In the Planning Stage, we also determined that the Dashboard Component will be a container since it will need access to the `tweets` part of the store in order to display the list of tweets.

To make a container, we need to make use the `connect()` function. Remember that the signature of the connect function looks like this:

```js
connect([mapStateToProps], [mapDispatchToProps], [mergeProps], [options])
```

Take a look at the [react-redux documentation](https://github.com/reactjs/react-redux/blob/master/docs/api.md) if you need a refresher.

These details about `mapStateToProps` and `mapDispatchToProps` are crucial:

> mapStateToProps - If this argument is specified, the new component  will subscribe to Redux store updates. This means that any time the  store is updated, mapStateToProps will be called. The results of  mapStateToProps must be a plain object, which will be merged into the  component’s props. If you don't want to subscribe to store updates, pass null or undefined in place of mapStateToProps.

> mapDispatchToProps - If an object is passed, each function inside it  is assumed to be a Redux action creator. An object with the same  function names, but with every action creator wrapped into a dispatch  call so they may be invoked directly, will be merged into the  component’s props. If a function is passed, it will be given dispatch as the first  parameter. It’s up to you to return an object that somehow uses dispatch to bind action creators in your own way. (Tip: you may use the [bindActionCreators()](https://redux.js.org/api-reference/bindactioncreators) helper from Redux.)

Do you remember the Component Hierarchy we made in Step 2 of the  Planning Stage? We said that the Tweet Component will be inside of the  Dashboard Component. If the Dashboard Component knows the ID of the  tweet that needs to be displayed, it can just pass that ID to the Tweet  Component, which will render the tweet.

Remember that the signature of the `mapStateToProps` function is:

```js
mapStateToProps(state, [ownProps])
```

- `state` is the state inside the store
- `ownProps` are the properties that have been passed to this component from a parent component

Since we only care about the `tweets` part of the store, we can use destructuring to pass the `tweets` part of the state in the store as the parameter to the `mapStateToProps()` function.



[![img](https://video.udacity-data.com/topher/2018/March/5abd6d18_untitled-diagram-21/untitled-diagram-21.png)The breakdown of our `mapStateToProps` function ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/18344f19-6939-4082-b7b4-b0b2644c0bec#)



So this is what the Dashboard Component's `mapStateToProps()` function looks like:

```js
function mapStateToProps( {tweets} ){
  return { tweetIds: Object.keys(tweets) };
}
```

The important things to note are that:

- **tweets** is the slice of the state that this component cares about
- **tweetIds** will show up as a property on this container



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/xjqf3vm3KjY?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=243" id="widget244" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-chirper-app/commit/baadd738d83c0b0905577192df8794d5460c2ba4)