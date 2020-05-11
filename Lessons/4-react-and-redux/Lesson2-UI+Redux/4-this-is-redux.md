## 4. This is Redux

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/06YeYJkrGaw?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=109" id="widget110" width="640" height="360" frameborder="0"></iframe>



We're going to transition away from our custom code to using the actual Redux library. While we're working on this simple project, we'll be linkin to the hosted version of the Redux library. In the following video, we'll  use this code to link to redux:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/redux/3.7.2/redux.min.js"></script>
```



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Sg482OZsFzM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=111" id="widget112" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/d4975c2245e6d590f637e0873d30ae8d6454e372)

Reducer composition sounds intimidating, but it's simpler than you might think. The idea is that you can create a reducer to manage not only each  section of your Redux store, but also any nested data as well. Let's say we were dealing with a state tree like had this structure

```js
{
  users: {},
  setting: {},
  tweets: {
    btyxlj: {
      id: 'btyxlj',
      text: 'What is a jQuery?',
      author: {
        name: 'Tyler McGinnis',
        id: 'tylermcginnis',
        avatar: 'twt.com/tm.png'
      }   
    }
  }  
}
```

We have three main properties on our state tree: users, settings, and tweets. Naturally, we'd create an individual reducer for both of those  and then create a single root reducer using Redux's `combineReducers` method.

```js
const reducer = combineReducers({
  users,
  settings,
  tweets
})
```

`combineReducers`, under the hood, is our first look at reducer composition. `combineReducers` is responsible for invoking all the other reducers, passing them the  portion of their state that they care about. We're making one root  reducer, by composing a bunch of other reducers together. With that in  mind, let's take a closer look at our tweets reducer and how we can  leverage reducer composition again to make it more compartmentalized.  Specifically, let's look how a user might change their avatar with the  way our store is currently structured. Here's the skeleton with what  we'll start out with -

```js
function tweets (state = {}, action) {
  switch(action.type){
      case ADD_TWEET :
        ...
      case REMOVE_TWEET :
        ...
      case UPDATE_AVATAR :
        ???
  }
}
```

What we're interested in is that last one, `UPDATE_AVATAR`. This one is interesting because we have some nested data - and  remember, reducers have to be pure and can't mutate any state. Here's  one approach.

```js
function tweets (state = {}, action) {
  switch(action.type){
      case ADD_TWEET :
        ...
      case REMOVE_TWEET :
        ...
      case UPDATE_AVATAR :
        return {
          ...state,
          [action.tweetId]: {
            ...state[action.tweetId],
            author: {
              ...state[action.tweetId].author,
              avatar: action.newAvatar 
            }
          }
        }
  }
}
```

That's a lot of spread operators. The reason for that is because, for every layer, we're wanting to spread all the properties of that layer  on the new objects we're creating (because, immutability). What if, just like we separated our tweets, users, and settings reducers by passing  them the slice of the state tree they care about, what if we do the same thing for our tweets reducer and its nested data. Doing that, the code above would be transformed to look like this

```js
function author (state, action) {
  switch (action.type) {
      case : UPDATE_AVATAR
        return {
          ...state,
          avatar: action.newAvatar
        }
      default :
        state
  }
}

function tweet (state, action) {
  switch (action.type) {
      case ADD_TWEET :
        ...
      case REMOVE_TWEET :
        ...
      case : UPDATE_AVATAR
        return {
          ...state,
          author: author(state.author, action)
        }
      default :
        state
  }
}

function tweets (state = {}, action) {
  switch(action.type){
      case ADD_TWEET :
        ...
      case REMOVE_TWEET :
        ...
      case UPDATE_AVATAR :
        return {
          ...state,
          [action.tweetId]: tweet(state[action.tweetId], action)
        }
      default :
        state
  }
}
```

All we've done is separated out each layer of our nested tweets data  into their own reducers. Then, just like we did with our root reducer,  we're passing those reducers the slice of the state they care about.



### Quiz Question

![image-20200510103807678](C:\Users\14144\AppData\Roaming\Typora\typora-user-images\image-20200510103807678.png)

# Summary

In this section, we replaced the code we wrote in the previous lesson with the actual Redux library code. We saw that swapping out our code  with Redux's code didn't change anything with how our application  functions or how our app-specific code works. Redux is *just* a predictable state container.

What's key to understand is that you've already learned 90% of Redux! Everything else from here on out will be handling specific use cases  (combining Redux with a React application, how to work with asynchronous data modification, etc.). So we'll be adding more concepts on top of  what you know now, so if you feel comfortable with your understanding of Redux, then keep going. If you're a bit hazy on how a specific part  works, I definitely recommend you get they hazy bits nailed down now  before proceeding on to more complicated content. Feel free to return to the first lesson to review specific Redux functionalities to iron out  any confusing parts before moving on.