## 3. The Store

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/A1ZW3cRS65g?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=5" id="widget6" width="640" height="360" frameborder="0"></iframe>



A traditional app might look something like this:



[![img](https://video.udacity-data.com/topher/2018/March/5abbd1cd_nd019-redux-l1-01-state-is-everywhere/nd019-redux-l1-01-state-is-everywhere.png)The application's data is sprinkled throughout the app. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/5b8c33c7-29d0-4fa4-9a03-ba49d1a2cb35/concepts/48125931-551a-462f-8828-fd910e0cb0e9#)



Notice in the image above, that this simple application has a lot of state:

- There are the images in the sidebar on the left.
- There are rows of tracks in the main area.
- Each Track will have its own information that it's maintaining.
- There's the search field at the top that introduces new state to the app (the searched for artist/track information).

And this is just one, simple page of this application. In most sites  you use, there is information littered throughout every single page of  the entire app.

Remember that the main goal of Redux is to make the state management of an  application more predictable. Let's see what that might look like: 



[![img](https://video.udacity-data.com/topher/2018/March/5abbd217_nd019-redux-l1-02-isolated-state/nd019-redux-l1-02-isolated-state.png)Application data is stored outside of the app and is just referenced by the app. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/5b8c33c7-29d0-4fa4-9a03-ba49d1a2cb35/concepts/48125931-551a-462f-8828-fd910e0cb0e9#)



In this example, the app appears exactly the same to the end user,  however, it's functioning quite differently under the hood. All of the  data is stored *outside of the UI code* and is just *referenced* from the UI code. 

With a change like this, if the data needs to be modified at all,  then all of the data is located in one place and needs to be only  changed once. Then the areas of the app that are referencing pieces of  data, will be updated since the source they're pulling from has changed.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/IDdb6baBQyo?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=7" id="widget8" width="640" height="360" frameborder="0"></iframe>



## State Tree

One of the key points of Redux is that all of the data is stored in a single object called the *state tree*. But what does a state tree actually look like? Good question! Here's an example:

```js
{
  recipes: [
    { … },
    { … },
    { … }
  ],
  ingredients: [
    { … },
    { … },
    { … },
    { … },
    { … },
    { … }
  ],
  products: [
    { … },
    { … },
    { … },
    { … }
  ]
}
```

See how all of the data for this imaginary cooking site is stored in a single object? So all of the state (or "application data") for this  site is stored in one, single location. This is what we mean when we say "state tree"...it's just all of the data stored in a single object.

Throughout this course, whenever we refer to an application's "state tree", we'll use a triangle to convey this concept.



[![img](https://video.udacity-data.com/topher/2018/March/5abbd23c_nd019-redux-l1-03-state-tree/nd019-redux-l1-03-state-tree.png)This is how we'll represent the "state tree". ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/5b8c33c7-29d0-4fa4-9a03-ba49d1a2cb35/concepts/48125931-551a-462f-8828-fd910e0cb0e9#)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/o8cEkLqR7VU?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=9" id="widget10" width="640" height="360" frameborder="0"></iframe>



### Quiz Question

  ![image-20200510100921612](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\images\3-quiz)

# Summary

In this lesson, we looked at the data in an application. We saw that  in traditional apps, the data is mixed in with the UI and markup. This  can lead to hard-to-find bugs where updating the state in one location  doesn't update it in every location. 

We learned that the main goal that Redux is trying to offer is  predictable state management. The way that Redux tries to accomplish  this is through having a *single* *state tree*. This state tree is an object that stores the entire state for an application. Now  that all state is stored in one location, we discovered three ways to  interact with it:

1. getting the state
2. listening for changes to the state
3. updating the state

Then we combine the three items above and the state tree object itself into one unit which we called *the store*. We'll look at creating this store in the next lesson.