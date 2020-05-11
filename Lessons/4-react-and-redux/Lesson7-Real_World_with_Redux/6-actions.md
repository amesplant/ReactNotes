# 6. Actions



Let's start from the Dashboard View. Our Dashboard View displays a list of tweets and a menu.

We need to take a look at *what* is happening in this view. Let's determine what actions the app or the user is performing **on the data** - is the data being set, modified, or deleted?

Remember that in Step 4 of the Planning Stage, we determined that our store will look like this:



[![img](https://video.udacity-data.com/topher/2018/March/5abd65c5_1/1.png)The Store contains a tweets property, a users property, and an authedUser property. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/7292f959-73ad-43e5-b95b-d2d9dbfa5657#)



When the app loads, the Dashboard View is displayed. The Dashboard Component therefore needs to:

- *get* the **tweets**
- *get* the **users**
- *get* the **authedUser**

This data is stored in a database. For this view to load all of the  tweets (including their author's avatars), we need to 1) get the `tweets` and `users` data from the database; and then 2) to pass that data into the component.



![image-20200510112520183](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson7-Real_World_with_Redux\images\6-quiz-1)



![image-20200510112737624](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson7-Real_World_with_Redux\images\6-quiz-2)



Remember how normal Action Creators return actions - simple Javascript objects  that then go to all of our reducers? Making an API request is an  asynchronous action, so we cannot just send a plain Javascript object to our reducers. Redux middleware can gain access to an action when it's  on its way to the reducers. We'll be using the `redux-thunk` middleware in this example. 

If the Redux Thunk middleware is enabled (which is done via the `applyMiddleware()` function), then any time your action creator returns a function instead of a Javascript object, it will go to the `redux-thunk` middleware.

Dan Abramov [describes](https://stackoverflow.com/questions/35411423/how-to-dispatch-a-redux-action-with-a-timeout/35415559#35415559) what happens next: 

> “The middleware will call that function with dispatch method itself  as the first argument...The action will only reach the reducers once the API request is completed. It will also “swallow” such actions so don't worry about your reducers  receiving weird function arguments. Your reducers will only receive  plain object actions—either emitted directly, or emitted by the  functions as we just described.”

Here's what a thunk action creator looks like:

```js
function handleInitialData () { 
 return function (dispatch) {}
}
```

Which is equivalent to this in ES6:

```js
function handleInitialData () {
 return (dispatch) => {}
}
```

Now, we need to give our components access to the data that came in. In other words, we need to populate the store with `tweets` and `users`.



[![img](https://video.udacity-data.com/topher/2018/March/5abd66ac_image5/image5.png)The Model of Our Store ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/7292f959-73ad-43e5-b95b-d2d9dbfa5657#)



The **tweets** slice of the state in the store will be modified by actions that go through the *tweets* reducer. The **users** slice of the state in the store will be modified by actions that go through the *users* reducer. And, similarly, the **authedUser** portion of the state in the store will be modified by actions that go through the *authedUser* reducer.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Px3vpZBHhHI?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=231" id="widget232" width="640" height="360" frameborder="0"></iframe>



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/-cqWNcFKB5E?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=233" id="widget234" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in the previous videos.](https://github.com/udacity/reactnd-chirper-app/commit/acc11b20446b9e19dc861ab9ec46d9de57aa6ea8)