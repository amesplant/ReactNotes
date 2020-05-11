## 6. Putting it All Together

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/HEQR3KYjG24?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=33" id="widget34" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/blob/putting-it-all-together/index.js)



[![The Store contains the state tree and provides ways to interact with the state tree.](https://video.udacity-data.com/topher/2018/March/5abbd27d_nd019-redux-l1-04-the-store/nd019-redux-l1-04-the-store.png)The Store contains the state tree and provides ways to interact with the state tree. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/5b8c33c7-29d0-4fa4-9a03-ba49d1a2cb35/concepts/933bd456-6ed9-436e-bcc2-961bd79a6059#)



We've finally finished creating the `createStore` function! Using the image above as a guide, let's break down what we've accomplished: 

- we created a function called `createStore()` that returns a *store* object
- `createStore()` must be passed a "reducer" function when invoked
- the store object has three methods on it:
  - `.getState()` - used to get the current state from the store
  - `.subscribe()` - used to provide a listener function the store will call when the state changes
  - `.dispatch()` - used to make changes to the store's state
- the store object's methods have access to the state of the store via closure



### Quiz Question

![image-20200510095821539](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\6-quiz)

# Summary

Up until this point, we've been building out the `createStore()` function, piece by piece. In this section, we put all of those pieces  together to create a fully functioning project. Then we took that code  and demoed it working in the console. We showed that subscribing to the  store returned a function we could use to unsubscribe later. We also  dispatched an action and saw how the state was updated as a result.

In the next section, we'll keep building up our app-specific parts of the code to handle different actions and to be more error-proof.